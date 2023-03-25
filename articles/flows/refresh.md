# Refresh Token Flow

The Refresh Token flow is a grant type in OAuth 2.0 that allows the client to obtain a new access token and refresh token pair by presenting a valid refresh token to the authorization server. This flow is useful when the access token has expired or become invalid, but the client wants to continue accessing the protected resources without requiring the user to reauthenticate.

## Flow Overview

The Refresh Token flow consists of the following steps:

1. The client makes a request to the authorization server to exchange a refresh token for a new access token.
1. The authorization server verifies the refresh token and issues a new access token and refresh token pair.
1. The authorization server returns the new access token and refresh token pair to the client.
1. The client can now use the new access token to access the protected resources and store the new refresh token for future use.

The following diagram shows the sequence of steps involved in the Refresh Token flow:

```mermaid
sequenceDiagram
    participant Client
    participant AuthorizationServer
    
    Client->>AuthorizationServer: Refresh Token Request
    AuthorizationServer->>AuthorizationServer: Verify Refresh Token
    AuthorizationServer->>Client: New Access Token & Refresh Token
    Client->>Client: Store New Refresh Token
```

## Example Request

The Refresh Token flow uses the following request parameters:

- `grant_type`: The value of this parameter must be set to refresh_token.
- `refresh_token`: The refresh token issued to the client during the previous authorization request.

The following is an example of a Refresh Token request:

```http
POST /token HTTP/1.1
Host: authorization-server.com
Content-Type: application/x-www-form-urlencoded

grant_type=refresh_token
&refresh_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

## Example Response

The Refresh Token flow returns the following response parameters:

- `access_token`: The new access token issued by the authorization server.
- `token_type`: The type of the access token, which is typically set to Bearer.
- `expires_in`: The expiration time of the access token in seconds.
- `refresh_token`: The new refresh token issued by the authorization server.
- `scope`: The scope of the access token.

The following is an example of a Refresh Token response:

```http
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyLCJleHAiOjE1MTYyMzkwMjIsInNjb3BlIjoiYXV0aCIsImV4dCI6MTUxNjIzOTAyMn0.tZrJquZn6M-WcX1Gxkjs-Gmg6_-y7eKjJ6AJz7p1BYk",
  "token_type": "Bearer",
  "expires_in
```
