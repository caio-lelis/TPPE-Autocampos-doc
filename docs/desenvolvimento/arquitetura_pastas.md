# Arquitetura de Pastas

Abaixo está a estrutura de diretórios do projeto **AutoCampos**, organizada para promover clareza, modularidade e facilidade de manutenção.

```text
.
├── data
│   └── assets
└── src
    ├── api
    ├── core
    ├── models
    ├── schemas
    ├── services
    └── tests
        └── unit
            └── models
```

## Descrição dos Diretórios

- **`data/assets/`**  
  Contém arquivos estáticos e recursos auxiliares, como imagens, diagramas e outros ativos utilizados na documentação ou interface.

- **`src/api/`**  
  Responsável pelas rotas da aplicação (endpoints). Aqui ficam os controladores que recebem as requisições HTTP e interagem com os serviços e modelos.

- **`src/core/`**  
  Contém configurações centrais do projeto, como variáveis de ambiente, inicialização da aplicação, middlewares e autenticação.

- **`src/models/`**  
  Define os modelos de dados que representam as tabelas do banco de dados, geralmente utilizando um ORM como SQLAlchemy.

- **`src/schemas/`**  
  Contém os esquemas de validação de dados (Pydantic), usados para entrada e saída de dados nas APIs.

- **`src/services/`**  
  Implementa a lógica de negócio da aplicação. Os serviços são responsáveis por processar dados, aplicar regras e interagir com os modelos.

---

Essa organização segue boas práticas de desenvolvimento, facilitando a escalabilidade e a colaboração entre desenvolvedores.
