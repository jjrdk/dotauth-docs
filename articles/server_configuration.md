# Configuring a DotAuth as an Authentication Provider in ASP.NET Core

ASP.NET Core provides built-in support for authentication and authorization, and it's possible to use OAuth 2.0 as an authentication provider. This document describes how to configure a generic OAuth provider as an authentication provider in an ASP.NET Core application.

## Prerequisites

- An ASP.NET Core 6.0 or later project.
- A DotAuth server with a client ID and client secret configured for the ASP.NET application.

# Steps

1. Install the Microsoft.AspNetCore.Authentication.OAuth package:

```shell
dotnet add package Microsoft.AspNetCore.Authentication.OAuth
dotnet add package DotAuth
```

2. Configure the OAuth provider in the ConfigureServices method of the Startup.cs file:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthentication(options =>
    {
        options.DefaultScheme = "cookie";
        options.DefaultChallengeScheme = "oauth";
    })
    .AddCookie("cookie")
    .AddOAuth("oauth", options =>
    {
        options.ClientId = "<Client ID>";
        options.ClientSecret = "<Client Secret>";
        options.CallbackPath = new PathString("/signin-oauth");
        options.AuthorizationEndpoint = "<Authorization Endpoint>";
        options.TokenEndpoint = "<Token Endpoint>";
        options.UserInformationEndpoint = "<User Information Endpoint>";
        options.SaveTokens = true;
    });

    services.AddControllersWithViews();
}
```

3. In the Configure method, add the authentication middleware:

```csharp
public void Configure(IApplicationBuilder app)
{
    app.UseAuthentication();
    app.UseAuthorization();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapDefaultControllerRoute();
    });
}
```

4. Decorate a controller or action to trigger the authentication flow:

```csharp
[Authorize]
[HttpGet("/signin")]
public IActionResult SomeAction()
{
    return Ok("Hello, World!")
}
```
