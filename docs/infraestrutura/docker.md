2. **Para a seção de Docker**, inclua blocos de código como:

````markdown
```yaml
# docker-compose.yml
version: "3"
services:
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: example
```
````
