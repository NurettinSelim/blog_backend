# Post API

### [Documentation](documentation.md)
## Create Amplify Project
    
```bash
amplify init
```

## Implement GraphQL API

```bash
amplify add api
```

## Implement Authentication

```bash
amplify add auth
```

## Define the GraphQL Schema
```graphql
type Post @model @auth(rules: [{ allow: owner }]) {
  id: ID!
  title: String!
  description: String!
  owner: String @auth(rules: [{ allow: owner, operations: [read, delete] }])
}
```
Check this schema at [schema.graphql](amplify/backend/api/blogbackend/schema.graphql)

## Deploy the API

```bash
amplify push
```

---

## About @model and @auth annotations
The `@model` annotation is a directive provided by the Amplify CLI and AWS AppSync that streamlines the process of creating CRUD (Create, Read, Update, Delete) operations for a GraphQL API. When a type is annotated with `@model`, the API will automatically generate query and mutation operations for that type, including mutations for create, update, and delete, as well as queries for list and get. This can help developers save time and reduce the amount of code they need to write.

The `@auth` annotation is another directive provided by AWS AppSync that allows you to specify authorization rules for your API. You can use the `@auth` directive to specify which operations are allowed for a given field or type. In the schema you provided, the `Post` type has an `@auth` directive that specifies that only the `owner` of a post is allowed to perform certain operations. Specifically, the `owner` field has an `@auth` directive that specifies that the `owner` is allowed to perform `read` and `delete` operations on their own posts.

Overall, `@model` and `@auth` are powerful tools that can simplify the process of building secure and scalable GraphQL APIs on AWS AppSync.