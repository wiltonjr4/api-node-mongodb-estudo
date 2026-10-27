# API REST de Biblioteca

API desenvolvida em **Node.js e Express** para praticar o desenvolvimento back-end com persistência de dados em **MongoDB**, utilizando **Mongoose** para modelar documentos e interagir com o banco.

> **Contexto:** projeto de estudo, construído para exercitar rotas HTTP, operações CRUD e integração entre uma API e um banco NoSQL. Não é um sistema de biblioteca em produção.

## Tecnologias

- **JavaScript** com módulos ES (`import` / `export`)
- **Node.js** e **Express**
- **MongoDB** e **Mongoose**
- **dotenv** para configuração da conexão
- **Nodemon** durante o desenvolvimento

## Funcionalidades

O recurso `livros` oferece operações para:

- Cadastrar um livro.
- Consultar todos os livros.
- Consultar um livro pelo identificador.
- Atualizar os dados de um livro.
- Excluir um livro.

As rotas ficam em `src/routes/livrosRoutes.js`, e a conexão com o banco é configurada em `src/config/dbConnect.js`.

## Rotas da API

Com o servidor em execução em `http://localhost:3000`:

| Método | Rota | Finalidade |
| --- | --- | --- |
| `GET` | `/livros` | Listar livros |
| `GET` | `/livros/:id` | Consultar um livro pelo ID |
| `POST` | `/livros` | Cadastrar um livro |
| `PUT` | `/livros/:id` | Atualizar um livro |
| `DELETE` | `/livros/:id` | Excluir um livro |

A aplicação também possui uma rota `GET /` que retorna uma mensagem simples de identificação.

### Exemplo de corpo de requisição

O modelo de livro contempla os campos `titulo`, `editora`, `preco` e `paginas`. O campo `titulo` é obrigatório no schema.

```json
{
  "titulo": "Algoritmos e Estruturas de Dados",
  "editora": "Editora Exemplo",
  "preco": 79.9,
  "paginas": 320
}
```

Use o corpo acima em `POST /livros` com `Content-Type: application/json` no Postman ou em outro cliente HTTP.

## Executar localmente

**Pré-requisitos:** Node.js, npm e acesso a uma instância MongoDB (local ou hospedada).

1. Clone o repositório e entre na pasta:

   ```bash
   git clone https://github.com/wiltonjr4/api-node-mongodb-estudo.git
   cd api-node-mongodb-estudo
   ```

2. Instale as dependências:

   ```bash
   npm install
   ```

3. Crie um arquivo `.env` na raiz, com a variável exigida pela conexão:

   ```dotenv
   DB_CONNECTION_STRING=mongodb://127.0.0.1:27017/biblioteca
   ```

   A URI acima é apenas um **exemplo para MongoDB local**. Para serviços hospedados, use sua própria URI e mantenha credenciais fora do Git.

4. Inicie a aplicação:

   ```bash
   npm run dev
   ```

5. Faça uma chamada para `http://localhost:3000/livros`.

## Organização do código

```text
server.js                  # Inicialização do servidor HTTP (porta 3000)
src/
  app.js                   # Instância Express, conexão e montagem das rotas
  config/dbConnect.js      # Conexão com MongoDB por variável de ambiente
  routes/                  # Definições das rotas HTTP
  controllers/             # Tratamento das requisições
  models/                  # Schema do livro com Mongoose
```

## O que o projeto demonstra

- Definição de endpoints REST e uso de métodos HTTP.
- Modelagem de documentos com Mongoose.
- Separação básica de responsabilidades entre rotas, controllers e models.
- Uso de variável de ambiente para configuração de acesso ao banco.

## Limitações e evolução

Este é um projeto educacional. **Não há uma suíte de testes automatizados configurada no script `npm test` do repositório atual.** Entre as próximas evoluções estão testes de API, padronização do tratamento de erros, validação de entradas e documentação de exemplos de resposta.

---

Desenvolvido por [Wilton Junior](https://github.com/wiltonjr4) como parte de seus estudos em desenvolvimento back-end.
