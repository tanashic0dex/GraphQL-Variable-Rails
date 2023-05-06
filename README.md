# graphql-ruby

## Installation

Install dependencies:

```
bundle install

rails db:setup
```

Starting the server:

```
rails server
```

Opening the application:

```
open http://localhost:3000/
```

## Sample GraphQL Queries


```graphql
{
  allLinks(first: 10, filter: {descriptionContains: "example"}) {
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

Creates new user:

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

Creates new user token:

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

Creates new link:

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

Creates new vote:

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
