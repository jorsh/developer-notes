# GraphQL
- GraphQL is a new API standard that provides a more efficient, powerful and flexible alternative to REST. 
- It was developed and open-sourced by Facebook 
- Is now maintained by a large community of companies and individuals from all over the world.
- GraphQL is a query language for APIs - not databases. 

At its core, GraphQL enables declarative data fetching where a client can specify exactly what data it needs from an API. Instead of multiple endpoints that return fixed data structures, a GraphQL server only exposes a single endpoint and responds with precisely the data a client asked for.

Perhaps the greatest feature of GraphQL is that it hides all of the backend complexity from clients. No matter how many backends your app uses, all the client will see is a single GraphQL endpoint with a simple, self-documenting API for your application.

> It’s database agnostic and effectively can be used in any context where an API is used.

## Advantages of using GraphQL
- Flexible and eficient
- No more Overfetching/Underfertching
- Uses a strong type system to define capabilities of an API
- Once the schema is defined, frontend and backend teams can work independently from one another

> Overfetching means that a client downloads more information than is actually required in the app.

> Underfetching generally means that a specific endpoint doesn’t provide enough of the required information. The client will have to make additional requests to fetch everything it needs

## Schemas
- The schema specifies the capabilities of the API and defines how clients can request the data. 
- It is often seen as a contract between the server and client.
 
### Types
GraphQL has its own type system that’s used to define the schema of an API.

The syntax for writing schemas is called **Schema Definition Language (SDL).**

*A simple type called Person*

    type Person {
      name: String!
      age: Int!
    }


> The `!` following the type means that this field is required.

There are some special root types:
- `type Query { ... }`
- `type Mutation { ... }`
- `type Subscription { ... }`

The Query type would have to be written as follows:

    type Query {
      allPersons: [Person!]!
    }


## Querys
### Arguments
### Fragments
### Aliases
### Variables

### Introspection
Clients can discover what is accessible through a GraphQL API by querying the __schema meta-field, which is always available on the root type of a Query per the spec.
```
query {
  __schema {
    types {
      name
      description
    }
  }
}
```

### Mutations
To make changes to the data stored in the backend GraphQL uses the so-called mutations. 

There generally are three kinds of mutations:
- **Creating** new data
- **Uptating** existing data
- **Deleting** existing data

Mutations always need to start with the `mutation` keyword.

    mutation {
      createPerson(name: "Bob", age: 36) {
        name
        age
      }
    }


## Subscriptions
Subscriptions allow to have a realtime connection to the server in order to get immediately informed about important events. 
When a client subscribes to an event, it will initiate and hold a steady connection to the server. Whenever that event then happens, the server pushes the corresponding data to the client. 

    subscription {
      newPerson {
        name
        age
      }
    }


## Architectures
- GraphQL server with a connected database
- GraphQL server that is a thin layer in front of a number of third party or legacy systems and integrates them through a single GraphQL API
- A hybrid approach of a connected database and third party or legacy systems that can all be accessed through the same GraphQL API

## Resolvers
Resolvers are just functions mapped to GraphQL fields, with their actual behavior.
specify how the types and fields in the schema are connected to various backends
GraphQL resolve functions can contain arbitrary code, which means a GraphQL server can to talk to any kind of backend, even other GraphQL server

---

## FRONTEND
### Relay vs Apollo
| | Relay | Apollo|
|---|---|---|
| **Frameworks** | React, React-Native| Framework agnostic |
| **GraphQL API** | Requires custom schema | Works with any schema |
| **Flexibility** | Fixed structure | Very flexible |
| **Productivity** | Great DX but high entry barrier | More manual work |
| **Difficulty** | New concepts & high entry barrier | Easy to get started |
| **Subscriptions** | No subscriptions support yet | Yes: _subscriptions-transport-ws_ |
| **Schema check** | Build-time via Babel (required) | Optional tools |


### Apollo
#### Connectors
- A connector is the piece of code that links a GraphQL server to a specific backend (eg. MySQL, MongoDB, S3, neo4j). 
- Each backend will have its own connector. 

## FAQs
**Is GraphQL a Database Technology?**  
No. GraphQL is a query language for APIs - not databases. It's database agnostic and can be used with any kind of database or even no database at all.

**Is GraphQL only for React / Javascript Developers?**  
No. GraphQL is an API technology so it can be used in any context where an API is required.

**How to do Authentication and Authorization?**  
Authentication in GraphQL can be implemented with common patterns such as OAuth.
To implement authorization, it is recommended to delegate any data access logic to the business logic layer and not handle it directly in the GraphQL implementation.

**How to do Error Handling?**  
A successful GraphQL query is supposed to return a JSON object with a root field called "data". If the request fails a second root field called "errors" is added to the response:
```
{
    "data": { ... },
    "errors": [ ... ]
}
```

**Does GraphQL Support Offline Usage?**  
The caching abilities of Relay and Apollo might already be enough for some use cases, but there isn’t a popular solution for actually persisting stored data yet.

## Resources
- [Batched Resolving](https://github.com/facebook/dataloader "Batched Resolving")
- [GraphiQL](https://github.com/graphql/graphiql)
- [Apollo](https://www.apollographql.com/)
- [Relay](https://facebook.github.io/relay/)
- [Graphcool](https://www.graph.cool/)
