# graphql-ruby

## Instalação

Instalar dependencias:

```
bundle install

rails db:setup
```

Iniciando Server:

```
rails server
```

Executando o App:

```
open http://localhost:3000/
```

## Sample GraphQL Queries


```graphql
{
  allLinks(first: 10, filter: {descriptionContains: "exemplo"}) {
    id
    url
    description
    createdAt
    postedBy {
      id
      name
    }
  }
}

```

Criar Novo Usuário:

```graphql
mutation {
  createUser(
    name: "Tanashi Fofinho",
    authProvider: {
      credentials: { email: "tanashi@exemplo.com.br", password: "fofinho" }
    }
  ) {
    id
    email
    name
  }
}
```

Criar Novo Token User:

```graphql
mutation {
  signinUser(credentials: {email: "tanashi@exemplo.com.br", password: "fofinho"}) {
    token
    user {
      id
      email
      name
    }
  }
}
```

Criar Novo Link de Origem:

```graphql
mutation {
  createLink(url:"http://exemplo.com.br", description:"fofin demais") {
    id
    url
    description
    postedBy {
      id
      name
    }
  }
}
```

Criar Novos Votos:

```graphql
mutation {
  createVote(linkId:"TGluay0yMQ==") {
    user {
      id
      name
    }
    link {
      id
      url
      description
    }
  }
}
```
