# 🚀 Introdução ao Strapi e docker-compose com Postgres

## 📖 Sobre

Este repositório contém um exemplo de como utilizar o Strapi com docker-compose e banco Postgres.

## 📋 Pré-requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Node.js](https://nodejs.org/en/download/)

## ⚙️ Como executar

Criar um novo projeto com o Strapi:

```bash
npx create-strapi-app my-project --quickstart
```

Editar o arquivo config/database.js dentro do projeto Strapi com o seguinte conteúdo (alterando os valores de acordo com a sua configuração do Postgres):

```js
// path: ./config/database.js

module.exports = ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      host: env('DATABASE_HOST', '127.0.0.1'),
      port: env.int('DATABASE_PORT', 5432),
      database: env('DATABASE_NAME', 'strapi'),
      user: env('DATABASE_USERNAME', 'strapi'),
      password: env('DATABASE_PASSWORD', 'strapi'),
      schema: env('DATABASE_SCHEMA', 'public'), // Not required
      ssl: {
        rejectUnauthorized: env.bool('DATABASE_SSL_SELF', false), // For self-signed certificates
      },
    },
    debug: false,
  },
});

```

#### Criar o arquivo docker-compose.yml e Dockerfile com o seguinte conteúdo:

Execute dentro de uma pasta de projeto Strapi existente o seguinte comando e siga as instruções da CLI conforme a necessidade de seu projeto:
    
```bash
npx @strapi-community/dockerize@latest
```

Em seguida iniciar o docker-compose na pasta do projeto:

```bash
docker-compose up -d
```

Com isso, o Strapi estará disponível em [http://localhost:1337](http://localhost:1337)

## 📝 Créditos

- Este projeto foi criado com base no projeto [strapi-community/strapi-tool-dockerize] [GitHub](github.com/strapi-community/strapi-tool-dockerize)
- E no artigo [Database configuration](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/configurations/required/databases.html#configuration-structure)

## 💻 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](https://github.com/joaopaulovieira-dev/strapi-docker-postgres/blob/master/LICENSE.md) para mais detalhes.

## 🙋‍♂️ Autor

- [**@joaopaulovieira-dev**](github.com/joaopaulovieira-dev)
