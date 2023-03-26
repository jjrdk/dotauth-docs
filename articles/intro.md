# DotAuth

DotAuth provides an SDK to build an OAuth, OpenId and UMA2 server. In addition it provides a client library which can be used to retrieve tokens in your own mobile or desktop app. For development purposes there is also a dotnet tool which helps retrieve access tokens from the command line.

## Features

- Support for multiple grant types, including the authorization code, refresh token, client credentials, resource owner, and device authorization grant flows.
- Customizable user authentication and authorization with pluggable strategies.
- Configurable client management with support for client secrets, scopes, and redirect URIs.
- Built-in support for JSON Web Tokens (JWT) for access token encoding and decoding.
- Integration with popular C# frameworks, including ASP.NET and .NET Core.

The acceptance criteria for the features are described using the gherkin syntax in the [features](../features/index.md) section.

## Installation

To install DotAuth, you can either download the source code from the [GitHub](https://github.com/jjrdk/dotauth) repository or install it via NuGet package manager:

```shell
dotnet add package DotAuth
```

## Contributing

Contributions to DotAuth are always welcome! If you find a bug or would like to suggest an improvement, please create an issue on GitHub. If you would like to contribute code, please fork the repository and submit a pull request.

## License

DotAuth is released under the MIT License.
