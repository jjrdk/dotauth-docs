# Client Credentials Flow

The Client Credentials flow is used when the client is a confidential client (e.g., a server-side web application) and wishes to obtain an access token to access its own resources.

## Flow Diagram

The following diagram illustrates the flow of the Client Credentials flow:

```mermaid
sequenceDiagram
  participant Client
  participant AuthorizationServer
  Client->>+AuthorizationServer: Send Client Credentials
  AuthorizationServer->>+AuthorizationServer: Authenticate Client
  AuthorizationServer->>+Client: Send Access Token
  Client->>+AuthorizationServer: Send API Request
  AuthorizationServer->>+Client: Send API Response
```

## Example Request

The Client Credentials flow requires the following parameters in the request:

- `grant_type`: The value of this parameter must be set to client_credentials.
- `client_id`: The client identifier issued by the authorization server.
- `client_secret`: The client secret issued by the authorization server.
- `scope (optional)`: The scope of the access request.

The following is an example of a Client Credentials Request:

```http
POST /token HTTP/1.1
Host: authorization-server.com
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
&client_id=s6BhdRkqt3
&client_secret=7Fj
&scope=read write
```

## Example Response

The response to the Client Credentials request will contain the following parameters:

- `access_token`: The access token that the client will use to access the protected resources.
- `token_type`: The type of token, which is typically set to Bearer.
- `expires_in`: The lifetime of the access token, in seconds.
- `scope`: The scope of the access token, which may be different from the scope requested by the client.

The following is an example of a Client Credentials Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "access_token": "2YotnFZFEjr1zCsicMWpAA",
  "token_type": "Bearer",
  "expires_in": 3600,
  "scope": "read write"
}
```

## Using the Access Token

To use the access token obtained from the Client Credentials request, the client includes the access token in the `Authorization` header of its API requests:

```http
GET /api/resource HTTP/1.1
Host: api.server.com
Authorization: Bearer 2YotnFZFEjr1zCsicMWpAA
```
