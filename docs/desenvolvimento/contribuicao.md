# Guia de Contribuição

Documento que descreve os padrões de contribuição para o projeto TPPE-Autocampos.

## Branches - Conventional Branches [Link de acesso](https://conventional-branch.github.io/)

Estrutura:

```bash
<tipo>/<descrição-curta>
```

### Tipos de branch

- feature/: Para novas funcionalidades.
- fix/: Para correções de bugs.
- hotfix/: Para correções urgentes.
- chore/: Para tarefas de manutenção.
- docs/: Para documentação.
- refactor/: Para refatoração de código.
- test/: Para testes.

### Exemplo

```bash
git checkout -b feature/nova-funcionalidade
```

## Padrão de Commits - Conventional commits

[Link de acesso](https://www.conventionalcommits.org/en/v1.0.0/)

### Estrutura:

```bash
<tipo>: <descrição>
```

### Tipos de commit

- feat: Para novas funcionalidades.
- fix: Para correções de bugs.
- docs: Para documentação.
- style: Para formatação de código (espaços, vírgulas, etc).
- refactor: Para refatoração de código.
- test: Para testes.
- chore: Para tarefas de manutenção.

### Exemplo

```bash
git commit -m "feat: adicionar nova funcionalidade"
```
