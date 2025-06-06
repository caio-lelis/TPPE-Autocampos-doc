**docker-compose.yml**:

```yaml
services:
  db:
    image: postgres:13
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}
    volumes:
      - postgres_data:/var/lib/postgresql/data/
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}"]
      interval: 10s
      timeout: 10s
      retries: 10

  db_test: # Novo serviço para testes
    image: postgres:13
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}_test # Nome diferente para o banco de testes
    volumes:
      - postgres_test_data:/var/lib/postgresql/data/
    ports:
      - "5433:5432" # Porta diferente para evitar conflito
    healthcheck:
      test:
        ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}_test"]
      interval: 5s
      timeout: 5s
      retries: 5

  web:
    build:
      context: .
      dockerfile: Dockerfile
      args:
        PYTHON_VERSION: 3.9-slim
    ports:
      - "8000:8000"
    volumes:
      - .:/app
      - ./data/assets:/app/data/assets
    environment:
      - APP_ENV=development
      - PYTHONUNBUFFERED=1
      - DATABASE_URL=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@db:5432/${POSTGRES_DB}
    depends_on:
      db:
        condition: service_healthy
    restart: unless-stopped
    command: sh -c "sleep 5 && uvicorn main:app --host 0.0.0.0 --port 8000 --reload"

  tests:
    build:
      context: .
    environment:
      - APP_ENV=testing
      - DATABASE_URL=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@db_test:5432/${POSTGRES_DB}_test
    depends_on:
      db_test:
        condition: service_healthy
    volumes:
      - .:/app
    command: >
      sh -c "sleep 5 &&
      pytest -v --cov=. --cov-report=term-missing src/tests/
      "

volumes:
  postgres_data:
  postgres_test_data: # Volume separado para os testes
```

```

```
