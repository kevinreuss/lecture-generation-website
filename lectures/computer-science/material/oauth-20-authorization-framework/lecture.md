# OAuth 2.0 Authorization Framework

OAuth 2.0, an authorization framework, enables third-party applications to obtain limited access to an HTTP service. It has two main parts: obtaining an access token and using the access token to make requests.

## Obtaining an Access Token

The client first sends a GET request to an authorization server, which includes the client's id, redirect uri, and requested scopes. Below is an example request.

```http
GET /authorize?response_type=code&client_id=s6BhdRkqt3&state=xyz&redirect_uri=https%3A%2F%2Fclient%2Eexample%2Ecom%2Fcb HTTP/1.1
Host: server.example.com
```

The server replies with a code in the redirect URI. The client will then exchange the code for an access token by sending a POST request.

```http
POST /token HTTP/1.1
Host: server.example.com
Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code=SplxlOBeZQQYbYS6WxSbIA&redirect_uri=https%3A%2F%2Fclient%2Eexample%2Ecom%2Fcb
```

## Using Access Token

The client can then use the access token to make requests on behalf of the user, by including the access token in the Authorization header. Here's an example.

```http
GET /resource HTTP/1.1
Host: server.example.com
Authorization: Bearer mF_9.B5f-4.1JqM
```

In OAuth 2.0, access tokens are opaque to clients. They are meant to be understood by the resource server, but not by the client.

## Refreshing Access Token

Access tokens usually have a finite lifetime. When the token expires, the client can use the refresh token to get a new access token without requiring the user's interaction.

```http
POST /token HTTP/1.1
Host: server.example.com
Authorization: Basic czZCaGRSa3F0MzpnWDFmQmF0M2JW
Content-Type: application/x-www-form-urlencoded

grant_type=refresh_token&refresh_token=tGzv3JOkF0XG5Qx2TlKWIA
```

OAuth 2.0 is a flexible protocol that relies on SSL for security, which is designed to work with HTTP. It allows you to authorize devices, APIs, servers, and applications with different access token types.