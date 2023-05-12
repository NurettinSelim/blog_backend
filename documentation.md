# Post API

## Overview

The post API is a GraphQL API that allows users to create, read, update, and delete posts. The API is built using AWS Amplify and uses AWS services such as AWS AppSync, AWS Cognito, and AWS DynamoDB.


## Before we start:
- [Postman Request Examples](https://www.postman.com/altimetry-technologist-21543379/workspace/aws-assignment/collection/13718644-3b95953a-7f36-480a-81b9-1a5be7e07363)

---

## Authentication

All API endpoints require authentication using AWS Cognito. Users must authenticate using their email and password before they can access any of the endpoints.

## Base URL

```
https://kzfy425tazg73jzhlhinvnuzsi.appsync-api.us-east-1.amazonaws.com
```

## Endpoints

### Create a new post

```
POST /graphql
```

Creates a new post with the specified title and description.

#### Request

The request body must be a JSON object containing the `title` and `description` fields.

```json
{
  "query": "mutation CreatePost($input: CreatePostInput!) { createPost(input: $input) { id title description } }",
  "variables": {
    "input": {
      "title": "My New Post",
      "description": "This is the description of my new post."
    }
  }
}
```

#### Response

The response is a JSON object containing the `id`, `title`, and `description` fields of the newly created post.

```json
{
  "data": {
    "createPost": {
      "id": "e55ac5d9-04e8-451f-bf26-60d89102a398",
      "title": "My New post",
      "description": "This is the description of my new post."
    }
  }
}
```

### Get a list of all posts

```
POST /graphql
```

Gets a list of all posts.

#### Request

The request body must be a JSON object containing the `getAllPosts` field.

```json
{
  "query": "{ listPosts { items { id title description } } }"
}
```

#### Response

The response is a JSON object containing an array of posts, with each post containing the `id`, `title`, and `description` fields.

```json
{
  "data": {
    "listPosts": {
      "items": [
        {
          "id": "b83af2be-3a0f-4082-b729-2f12baced173",
          "title": "My New Post",
          "description": "This is the description of my new post."
        },
        {
          "id": "700ca4ff-f5f2-484f-aa33-61036cc83dfd",
          "title": "Another Post",
          "description": "This is the description of another post."
        }
      ]
    }
  }
}
```

### Get a single post by ID

```
POST /graphql
```

Gets a single post by ID.

#### Request

The request body must be a JSON object containing the `getPostById` field and the `id` argument.

```json
{
  "query": "query GetPost($id: ID!) { getPost(id: $id) { id title description } }",
  "variables": {
    "id": "b83af2be-3a0f-4082-b729-2f12baced173"
  }
}
```

#### Response

The response is a JSON object containing the `id`, `title`, and `description` fields of the post with the specified ID.

```json
{
  "data": {
    "getPostById": {
      "id": "b83af2be-3a0f-4082-b729-2f12baced173",
      "title": "My New Post",
      "description": "This is the description of my new post."
    }
  }
}
```

### Update an existing post

```
POST /graphql
```

Updates an existing post with the specified ID.

#### Request

The request body must be a JSON object containing the `updatePost` field, the `id` argument, and the fields to update.

```json
{
  "query": "mutation UpdatePost($input: UpdatePostInput!) { updatePost(input: $input) { id title description } }",
  "variables": {
    "id": "b83af2be-3a0f-4082-b729-2f12baced173",
    "input": {
      "title": "My Updated Post",
      "description": "This is the description of my updated post."
    }
  }
}
```

#### Response

The response is a JSON object containing the `id`, `title`, and `description` fields of the updated post.

```json
{
  "data": {
    "updatePost": {
      "id": "b83af2be-3a0f-4082-b729-2f12baced173",
      "title": "My Updated Post",
      "description": "This is the description of my updated post."
    }
  }
}
```

### Delete a post

```
POST /graphql
```

Deletes a post with the specified ID.

#### Request

The request body must be a JSON object containing the `deletePost` field and the `id` argument.

```json
{
  "query": "mutation DeletePost($input: DeletePostInput!) { deletePost(input: $input) { id title description } }",
  "variables": {
    "id": "f2978c6b-9902-4015-8d1f-f6cd1881a132"
  }
}
```

#### Response

The response is a JSON object containing the `id`, `title`, and `description` fields of the deleted post.

```json
{
  "data": {
    "deletePost": {
      "id": "f2978c6b-9902-4015-8d1f-f6cd1881a132",
      "title": "My New Post",
      "description": "This is the description of my new post."
    }
  }
}
```