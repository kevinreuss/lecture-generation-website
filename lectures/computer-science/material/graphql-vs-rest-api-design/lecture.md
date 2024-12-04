# GraphQL vs REST API Design

GraphQL and REST API Design are both approaches to building web services, but they offer different advantages and usage scenarios. Let's dive into some key differences.

## Data Fetching

In REST, to fetch related resources, multiple round trips are required or complex nested resources must be created. In contrast, GraphQL allows clients to fetch all related data in a single request. 

For example, if you want to fetch a user and their posts in REST, you might have to make requests like:

```javascript
GET /users/1
GET /users/1/posts
```

In GraphQL, this can be achieved with a single query:

```javascript
{
  user(id: 1) {
    name
    posts {
      title
    }
  }
}
```

## Over-fetching and Under-fetching

REST APIs often suffer from over-fetching and under-fetching. The server defines what data is included in the response for each endpoint, which may be more or less than the client needs.

GraphQL addresses this issue by allowing the client to specify exactly what data it needs. For example:

```javascript
{
  user(id: 1) {
    name
  }
}
```

This only retrieves the `name` of the user, avoiding unnecessary data transfer.

## Versioning

In REST, changes to the data structure often lead to a new version of the API. But in GraphQL, new fields can be added to the responses and old fields can be deprecated, maintaining backward compatibility.

## Error Handling

REST uses HTTP status codes to indicate the status of a response. GraphQL, on the other hand, always returns a 200 OK status. Errors are included in the response body, which can provide more detailed error information.

```javascript
{
  "errors": [{
    "message": "Name for character with ID 1002 could not be fetched.",
    "locations": [ { "line": 6, "column": 7 } ],
    "path": [ "hero", "heroFriends", 1, "name" ]
  }],
  "data": { /*...*/ }
}
```

These points highlight some key technical differences between GraphQL and REST API Design. It is important to choose the one that best fits the needs of your specific project.