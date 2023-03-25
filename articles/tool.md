# CLI Tool

The CLI tool allows you to retrieve a token from an authentication server.

## Configuration

The first step to take is to configure the tool so that it knows which client to authenticate the user as.

```shell
%> token configure -i client_id -s client_secret -a authority_url
```

The following values can be configured:

|Short Name|Long Name|Required|Default Value|Description|
|---|---|---|---|---|
|-i|--client-id|Required| |Sets the client id for the tool client.|
|-s|--client-secret|Required| |Sets the client secret for the tool client.|
|-a|--authority|Required| |Sets the issuing authority for the tool.|
|-r|--redirect-url| |[http://localhost:65001/signin](http://localhost:65001/signin)|Sets the redirect url for the authentication flow.|
|-c|--code-challenge-method| |S256|Sets the code challenge method.|
| |--help| | |Display this help screen.|
| |--version| | |Display version information.|

To reconfigure any of the values, simply run the configure command again, and the configuration will be updated.

## Token Retrieval

Once the tool is configured, you can retrieve a token by initiating the authentication code flow.

```shell
%> token
```

The default token request only requests a token for the ```openid``` scope. If you want to specify other scopes you can use this command:

``` shell
%> token -s comma,separated,list,of,scopes
```

The following parameters can be provided to the token retrieval:

|Short Name|Long Name|Required|Default Value|Description|
|---|---|---|---|---|
|-s|--scopes| |openid|Sets the scopes to request token for.|
|-r|--response-mode| |query|Sets the client id for the login request.|

## Token Refresh

The tool allows the retrieval of a refreshed token using a previously granted ```refresh token```.

To refresh an already granted access token, run the ```refresh``` command with the granted ```refresh token```.

```shell
%> token refresh -t current_refresh_token
```

The command has the following parameters:

|Short Name|Long Name|Required|Default Value|Description|
|---|---|---|---|---|
|-t|--token|Required| |The refresh token to get the refreshed access token from.|
