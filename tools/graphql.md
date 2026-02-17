# GraphQL

## Overview

- GraphQL is an API query language and a server-side runtime for executing queries
- GraphQL query language is basically about selecting fields on objects
- GraphQL services are created by defining types and their fields, and a function for each field to provide the required data (resolvers)
- Running GraphQL services receive GraphQL queries to validate and execute from clients
- Clients can make queries to the API that mirror the structure of the data that they need and then receive just that data in the expected shape with a single request
- Unlike REST, it uses a type system to define data structure and allows fetching multiple resources in a single request, reducing over-fetching (getting unnecessary data) and under-fetching problems (multiple requests needed)
- API to evolve without the overhead of API versioning
- Client tooling will encourage developers to use new fields and remove usage of deprecated fields

## Schemas and types

- GraphQL type system describes what data can be queried from the API
- Collection of those capabilities is referred to as the service’s **schema**
- Every GraphQL service defines a set of types that completely describe the set of possible data that can be queried on that service
- Clients can use that schema to send queries to the API that return predictable results
- When requests come in, they are validated and executed against the schema

### Type system

- "Root" object

### Object types and fields

- **Object types:** Most basic components of a GraphQL schema, represent a kind of object you can fetch from a service, and what fields it has

```graphql
type Character {
  name: String!
  appearsIn: [Episode!]!
}
```

- `Character`: Object type (type with some fields)
- `name`, `appearsIn`: Fields (on the `Character` type), those two are the only fields that can appear in queries that operate on `Character`
- `String`: Built-in scalar type (type that resolves to a single scalar value, can't have any sub-selections in a query)
- `!`: The field is a non-null type, contract with which GraphQL services promise to return a value whenever this field is queried
- `[Episode!]!`: List type of `Episode` objects; when a list is non-null, an array ca  be expected (with zero or more items) when the field is queried

```graphql
type Starhsip {
  id: ID!
  name: String!
  length(unit: LengthUnit = METER): Float
}
```

- **Arguments:** Every field on a GraphQL Object type can have zero or more arguments (e.g., `length` field)
- All arguments are named and passed by name specifically
- Arguments can either be required or optional; when an argument i optional, we can define a default value (`unit` has a default value of `METER`)

```graphql
type Query {
  droid(id: ID!): Droid
}
```

- **Query:** Object type
- Every GraphQL schema must support `query` operations
- Shape of a GraphQL query closely matches the result
- Schemas may also support `mutation` and `subscription` operations by adding additional Mutation and Subscription types, then defining fields
- `Query`, `Mutation`, and `Subscription` types are the same as any other GraphQL Object type

### Scalar types

- Represent leaf values of a query
- Scalar type fields don't have any sub-fields
- Default scalar types:
  - `Int`: Signed 32-bit integer
  - `Float`: Signed double-precision floating-point
  - `String`: UTF-8 character sequence
  - `Boolean`: `true` or `false`
  - `ID`: Unique identifier, serialized the same way as a `String` (`ID` signifies it's not intended to be human-readable)
- You can specify custom scalar types, e.g., `scalar Date`

### Enum types

- Special kind of scalar, restricted to a set of allowed values
- Allows you to validate any arguments of this type
- Allows you to communicate through the type system that a field will always be one of a finite set of values

```graphql
enum Episode {
  NEWHOPE
  EMPIRE
  JEDI
}
```

### Type modifiers









## Queries

- Shape of a GraphQL query closely matches the result
- 

## Fields
### Variables
### Aliases
### Arguments
### Directives
### Fragments

## Mutations
### Multiple fields in mutations
### Operation name

## Subscriptions
### Event based subscriptions
### Live queries
### `@defer` and `@stream` directives

## Schema
### Type system
### Fields
### Scalars
### Enums
### Lists
### Unions
### Objects
### Interfaces
### Arguments

## Validation

## Execution
### Root fields
### Resolvers
### Synchronous resolvers
### Asynchronous resolvers
### Scalar coercion
### Lists
### Validation
### Results

## GraphQL over HTTP
### Specification
### Caching
### Batching
### Authorization

## GraphQL over WebSockets
### Specification
### Realtime
### Authorization

## Pagination

## Implementations

## Servers

## Clients

## Credits

- [https://graphql.org/learn/](https://graphql.org/learn/introduction/)
- [https://graphql.org/learn/schema/](https://graphql.org/learn/schema/)
