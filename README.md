# Building 'eShop' from Zero to Hero: We add IdentityServer4

For start working with this sample we have to download open in Visual Studio 2022 the solution in this github repo: 

https://github.com/luiscoco/eShop_Aspire-Tutorial-Step3_WebApp_Catalog


## 1. Introduction about IdentityServer4

**IdentityServer4** is an **open-source** framework for implementing **Authentication** and **Authorization** in **ASP.NET Core** applications

It's based on the **OpenID Connect** and **OAuth 2.0** protocols, enabling secure identity management and access control for APIs, SPAs (Single Page Applications), web applications, and mobile apps

**Key Features**

**Authentication & Single Sign-On (SSO)**: IdentityServer4 allows applications to authenticate users and provide SSO across multiple applications

**OAuth 2.0 and OpenID Connect Protocols**: It supports these widely used standards for secure authorization and authentication

**API Protection**: Protects APIs by issuing access tokens that can be used to authorize API requests

**Flexible Identity Management**: It can manage users internally, or integrate with external identity providers (e.g., Google, Facebook, Azure AD)

**Token Management**: Issues secure access tokens (JWT or reference tokens), ID tokens, and refresh tokens

For more information about IdentityServer4 please visit these sites:

https://identityserver4.readthedocs.io/en/latest/

https://github.com/IdentityServer/IdentityServer4

## 2. How to start working with IdentityServer4

First of all, we have to install the IdentityServer4 templates for Visual Studio

Inside the IdentityServer4 documentation site, we can navigate to QuickStart and then to Preparation site:

![image](https://github.com/user-attachments/assets/8ed25bb2-2d35-4939-83d0-56f54667c1c5)

We have to open a new command prompt window and run this command to **install the IdentityServer4 templates**:

```
dotnet new -i IdentityServer4.Templates
```

We can also verify the templates installation in Visual Studio

![image](https://github.com/user-attachments/assets/b22a5deb-7736-493e-9e30-18d40779e37f)

## 3. We Create a new IdentityServer4 project

We have to download the application from this repo:

https://github.com/luiscoco/eShop_Aspire-Tutorial-Step3_WebApp_Catalog

We unzip the application and se open it with the File Explorer:

![image](https://github.com/user-attachments/assets/eb79ebe2-4bcc-433d-a496-69a8039dfc8a)

We create a subfolder inside our solution

![image](https://github.com/user-attachments/assets/ae94bb34-0a8c-492b-b65f-5210e42adb35)

We run this command ```dotnet new is4aspid``` for creating a new project with the template **IdentityServer4 with ASP.NET Core Identity**

![image](https://github.com/user-attachments/assets/dc641980-7d89-40b7-b7cc-87cf0603e4c5)

We can verify the folders and files created for the new IdentityServer4 project

![image](https://github.com/user-attachments/assets/af146df4-3e72-4cf2-bd55-28e33c54e927)

## 4. We Create a new project Identity.API project in the eShop solution

Now we have to run Visual Studio 2022 Community Edition and we Open the Solution previously downloaded from our github repo

https://github.com/luiscoco/eShop_Aspire-Tutorial-Step3_WebApp_Catalog

![image](https://github.com/user-attachments/assets/ba546711-de02-4221-83d6-38faca3b58b5)

We right click on the Solution name and select **Add -> New Projec...** 

![image](https://github.com/user-attachments/assets/e0792ba6-34ee-469b-849e-d71076d43391)

We select the **ASP.NET Core Web App (Model-View-Controller)** template and press on Next button

![image](https://github.com/user-attachments/assets/1dfb59c2-0c4e-4c25-82e0-39806550e3b7)

We set the project name **Identity.API**, location, and press on the Next button 

![image](https://github.com/user-attachments/assets/239b21b9-1f6c-4c76-9ad4-656c9b21b999)

We select the **.NET 9** framework and press the Create button

![image](https://github.com/user-attachments/assets/0b8e3218-3340-4879-95f1-045fff664aa5)

We verify the **Identity.API** project folders and files structure

![image](https://github.com/user-attachments/assets/78450c31-0dc4-4ecd-8eab-8d2cfe5ea9fb)

## 5. We Delete Controllers, Models and Views folders 

![image](https://github.com/user-attachments/assets/2286cda7-1818-4a2d-80f7-395da29ea7e9)

The project now should look like this

![image](https://github.com/user-attachments/assets/7b5a87b2-26da-4d4c-b495-1fe1b99d8f97)

## 6. We Create the Identity.API project folders structure

![image](https://github.com/user-attachments/assets/0a37954a-15dd-48ec-98fe-927d42c33977)

## 7. We Copy the IdentityServer4 project content inside the Identity.API project

We copy the folders content in UI into the Identity.API project

![image](https://github.com/user-attachments/assets/42bbbf4d-e895-4cf4-a8a3-3d55ecf7b240)

We verify the new files copied 

![image](https://github.com/user-attachments/assets/32e1f30b-ecdf-4538-b4e7-6e758ed1f6a9)

**IMPORTANT NOTE**: we have to **delete** the **Migrations** folder

![image](https://github.com/user-attachments/assets/c7570d09-c064-4a8f-8d35-0482294f8a0f)

We also have to **delete** the **Migrations** folder in the **File Explorer**

![image](https://github.com/user-attachments/assets/01d84ce7-1938-4048-bd02-4902792c0c2c)

## 8. We Create three folder inside the Models folder

![image](https://github.com/user-attachments/assets/c3933d4b-ed53-44af-9d86-88cdb0f6b37d)

## 9. We move the models files from Quickstart->Account to Models->AccountViewModels

![image](https://github.com/user-attachments/assets/19e164b2-aed0-42ff-a523-d9cc4ac90acc)

We verify the result

![image](https://github.com/user-attachments/assets/002c0fa0-50ed-4905-8179-4b397ec4d6b2)

## 10. We move the models files from Quickstart->Consent to Models->ConsentViewModels

![image](https://github.com/user-attachments/assets/2e0688c6-9c7b-49b2-aef5-fc857f62df44)

We verify the final results

![image](https://github.com/user-attachments/assets/2de00e90-5c1b-4c1f-8df3-751934a75aeb)

## 11. We copy the files inside the Models->ManageViewModels folder

![image](https://github.com/user-attachments/assets/46f02659-cc99-4fc4-a7b0-04e7158642b4)

## 12. We copy the JavaSript files in the wwwroot content

![image](https://github.com/user-attachments/assets/4c16ee35-1936-4833-86dc-127eaf7d6f99)

**signin-redirect.js**

```javascript
window.location.href = document.querySelector("meta[http-equiv=refresh]").getAttribute("data-url");
```

**signout-redirect.js**

```javascript
window.addEventListener("load", function () {
    var a = document.querySelector("a.PostLogoutRedirectUri");
    if (a) {
        window.location = a.href;
    }
});
```

## 13. We copy the fonts and images in the wwwroot folder

![image](https://github.com/user-attachments/assets/317e5e8f-c017-418e-8559-c35a65bfe462)

## 14. We also have to copy the icons and _references.js file in the wwwroot folder

![image](https://github.com/user-attachments/assets/75d8bd49-d30b-4add-8269-d04b94199874)

**_references.js**

```javascript
/// <autosync enabled="true" />
/// <reference path="js/site.js" />
/// <reference path="lib/bootstrap/dist/js/bootstrap.js" />
/// <reference path="lib/jquery/dist/jquery.js" />
/// <reference path="lib/jquery-validation/dist/jquery.validate.js" />
/// <reference path="lib/jquery-validation-unobtrusive/jquery.validate.unobtrusive.js" />
```

## 15. We add .NET Aspire Orchestrator Support to the Identity.API project

We right click on the Identity.API project name and we select the menu option **.NET Aspire Orchestrator Support...**

![image](https://github.com/user-attachments/assets/859bf34e-1a1c-48f3-ace0-0e34cf94709c)

We verify in the **eShop.AppHost** project was added the **Identity.API** project reference

![image](https://github.com/user-attachments/assets/1330049b-4cf0-480d-b4c3-182e2b1d1f15)

## 16. We load the Nuget Packages in the Identity.API project

We right click on the **Dependencies** folder and select the menu option **Manage Nuget Packages...**

![image](https://github.com/user-attachments/assets/7c1e57ff-a964-47cb-8494-442fe553175c)

We load the following Nuget packages

![image](https://github.com/user-attachments/assets/0b101afe-0d9e-4f81-85f6-7e9dc160f914)

**Aspire.Npgsql.EntityFrameworkCore.PostgreSQL**: integrates **PostgreSQL** with **Entity Framework Core** in .NET applications

It simplifies database connectivity by registering the **DbContext** in the dependency injection container, enabling features such as connection pooling, automatic retries, health checks, logging, and telemetry 

This package streamlines the setup process, allowing developers to focus on application logic while ensuring efficient and reliable database interactions

**AutoMapper**: is a popular **object-to-object mapping** library in .NET. It helps streamline the process of copying data between objects, particularly when the objects have similar structures but are used for different purposes, such as transferring data between a **Data Transfer Object (DTO)** and a domain model

**Duende IdentityServer**: is a powerful and flexible framework for implementing **OpenID Connect (OIDC)** and **OAuth 2.0** standards in .NET applications

It enables secure user authentication and API access management in modern applications

**Duende.IdentityServer.AspNetIdentity**: is an integration package that combines the features of **Duende IdentityServer** with **ASP.NET Core Identity**, providing a comprehensive solution for managing user authentication and authorization in .NET applications

**Duende.IdentityServer.EntityFramework**: is an extension package for **Duende IdentityServer** that enables the use of **Entity Framework Core (EF Core)** to manage the configuration and operational data of IdentityServer in a database

It provides a way to persist IdentityServer data such as clients, resources, and tokens in relational databases

**Duende.IdentityServer.Storage**¨: is a foundational package in the Duende IdentityServer ecosystem

It defines the core interfaces, abstractions, and data storage mechanisms used by IdentityServer to manage its configuration and operational data

**Microsoft.AspNetCore.Identity.EntityFrameworkCore**: This package provides an integration of ASP.NET Core Identity with Entity Framework Core

It includes functionality for managing user accounts, roles, claims, and other security-related features

Useful for applications where you want to store identity data (users, roles, etc.) in a database using Entity Framework Core

**Microsoft.AspNetCore.Identity.UI**: Provides pre-built Razor Pages for ASP.NET Core Identity. Includes views and pages for authentication, registration, password management, and account-related functionality

Helps developers quickly scaffold UI for common identity-related tasks without writing the code manually

**Microsoft.EntityFrameworkCore.Tools**: Provides tools for working with Entity Framework Core in the development environment. 

Enables commands like migrations, scaffolding, and database updates via the .NET CLI or Package Manager Console

Essential for managing and maintaining the database schema in EF Core-based projects

**Microsoft.Web.LibraryManager.Build**: A build-time library manager that facilitates managing client-side libraries (like JavaScript and CSS frameworks)

Helps restore libraries (e.g., jQuery, Bootstrap) defined in a libman.json file during the build process

Useful for automating the inclusion and management of front-end libraries in web projects

**Newtonsoft.Json**: A widely used library for working with JSON data in .NET. Provides functionality for serializing and deserializing objects to/from JSON and manipulating JSON data

Known for its ease of use and flexibility in handling JSON

**Npgsql.EntityFrameworkCore.PostgreSQL**: An Entity Framework Core provider for PostgreSQL databases. Enables EF Core to interact with PostgreSQL, supporting its specific features (e.g., arrays, JSON, hstore)

Essential for applications using PostgreSQL as the database with Entity Framework Core

## 17. We confirm the "eShop.ServiceDefaulst" project was added as a reference in the Identity.API project

![image](https://github.com/user-attachments/assets/e3876eda-617c-4ce4-ac4b-fc050ac03b57)

## 18. We add Nuget Packages in the eShop.ServiceDefaulst project

![image](https://github.com/user-attachments/assets/7bf310d7-eae9-4940-a1a7-a01ffe804dd1)

**Microsoft.AspNetCore.Authentication.JwtBearer**:  is a library that provides functionality for integrating JSON Web Token (JWT) authentication into ASP.NET Core applications. It is specifically designed for applications that use bearer tokens to authenticate and authorize API requests

Key Features:

Token Validation: Automatically validates JWTs issued by trusted authentication servers or identity providers

Integration: Easily integrates with ASP.NET Core's authentication middleware

Claims Extraction: Extracts user claims from the validated token, making them available in the application

Configuration: Supports customization of token validation parameters, including issuer, audience, signing keys, and token lifetime

Security Standards: Implements standard security practices for JWT validation, such as signature validation and checking token expiration

Common Use Cases:

Securing RESTful APIs

Implementing authentication and authorization workflows for applications using OpenID Connect or custom JWT providers

Enabling token-based authentication for microservices

**OpenTelemetry.Contrib.Instrumentation.GrpcCore**: provides client and server interceptors for gRPC Core, enabling the collection of telemetry data such as traces and metrics within .NET applications

By integrating this package, developers can monitor and analyze gRPC communications, facilitating observability and performance optimization

Key Features:

Client and Server Interceptors: Offers interceptors for both gRPC clients and servers, allowing comprehensive telemetry collection across gRPC interactions

OpenTelemetry Integration: Seamlessly integrates with the OpenTelemetry .NET SDK, supporting standardized telemetry data collection and export

.NET Standard 2.0 Compatibility: Targets .NET Standard 2.0, ensuring compatibility with a wide range of .NET implementations

## 19. We add new files in the eShop.ServiceDefaulst project

![image](https://github.com/user-attachments/assets/4a11792c-a7e0-4f5a-8666-4e9af48e024b)

**AuthenticationExtensions.cs**

```csharp
namespace eShop.ServiceDefaults;

public static class AuthenticationExtensions
{
    public static IServiceCollection AddDefaultAuthentication(this IHostApplicationBuilder builder)
    {
        var services = builder.Services;
        var configuration = builder.Configuration;

        // {
        //   "Identity": {
        //     "Url": "http://identity",
        //     "Audience": "basket"
        //    }
        // }

        var identitySection = configuration.GetSection("Identity");

        if (!identitySection.Exists())
        {
            // No identity section, so no authentication
            return services;
        }

        // prevent from mapping "sub" claim to nameidentifier.
        JsonWebTokenHandler.DefaultInboundClaimTypeMap.Remove("sub");

        services.AddAuthentication().AddJwtBearer(options =>
        {
            var identityUrl = identitySection.GetRequiredValue("Url");
            var audience = identitySection.GetRequiredValue("Audience");

            options.Authority = identityUrl;
            options.RequireHttpsMetadata = false;
            options.Audience = audience;
            
#if DEBUG
            //Needed if using Android Emulator Locally. See https://learn.microsoft.com/en-us/dotnet/maui/data-cloud/local-web-services?view=net-maui-8.0#android
            options.TokenValidationParameters.ValidIssuers = [identityUrl, "https://10.0.2.2:5243"];
#else
            options.TokenValidationParameters.ValidIssuers = [identityUrl];
#endif
            
            options.TokenValidationParameters.ValidateAudience = false;
        });

        services.AddAuthorization();

        return services;
    }
```

**ClaimsPrincipalExtensions.cs**

```csharp
namespace eShop.ServiceDefaults;

public static class ClaimsPrincipalExtensions
{
    public static string? GetUserId(this ClaimsPrincipal principal)
        => principal.FindFirst("sub")?.Value;

    public static string? GetUserName(this ClaimsPrincipal principal) =>
        principal.FindFirst(x => x.Type == ClaimTypes.Name)?.Value;
}
```

**HttpClientExtensions.cs**

```csharp
namespace eShop.ServiceDefaults;

public static class HttpClientExtensions
{
    public static IHttpClientBuilder AddAuthToken(this IHttpClientBuilder builder)
    {
        builder.Services.AddHttpContextAccessor();

        builder.Services.TryAddTransient<HttpClientAuthorizationDelegatingHandler>();

        builder.AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>();

        return builder;
    }

    private class HttpClientAuthorizationDelegatingHandler : DelegatingHandler
    {
        private readonly IHttpContextAccessor _httpContextAccessor;

        public HttpClientAuthorizationDelegatingHandler(IHttpContextAccessor httpContextAccessor)
        {
            _httpContextAccessor = httpContextAccessor;
        }

        public HttpClientAuthorizationDelegatingHandler(IHttpContextAccessor httpContextAccessor, HttpMessageHandler innerHandler) : base(innerHandler)
        {
            _httpContextAccessor = httpContextAccessor;
        }

        protected override async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken cancellationToken)
        {
            if (_httpContextAccessor.HttpContext is HttpContext context)
            {
                var accessToken = await context.GetTokenAsync("access_token");

                if (accessToken is not null)
                {
                    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);
                }
            }

            return await base.SendAsync(request, cancellationToken);
        }
    }
}
```

## 20. We update the middleware(Program.cs) in the eShop.AppHost project

![image](https://github.com/user-attachments/assets/671753b1-5ea7-4806-9299-bf8ef84cee5f)

**Program.cs**

```csharp
var builder = DistributedApplication.CreateBuilder(args);

var postgres = builder.AddPostgres("postgres")
    .WithImage("ankane/pgvector")
    .WithImageTag("latest")
    .WithLifetime(ContainerLifetime.Persistent);

var catalogDb = postgres.AddDatabase("catalogdb");
var identityDb = postgres.AddDatabase("identitydb");

var launchProfileName = ShouldUseHttpForEndpoints() ? "http" : "https";

var identityApi = builder.AddProject<Projects.Identity_API>("identity-api", launchProfileName)
    .WithExternalHttpEndpoints()
    .WithReference(identityDb);

var identityEndpoint = identityApi.GetEndpoint(launchProfileName);

var catalogApi = builder.AddProject<Projects.Catalog_API>("catalog-api")
    .WithReference(catalogDb);

var webApp = builder.AddProject<Projects.WebApp>("webapp")
    .WithExternalHttpEndpoints()
    .WithReference(catalogApi)
    .WithEnvironment("IdentityUrl", identityEndpoint);

webApp.WithEnvironment("CallBackUrl", webApp.GetEndpoint(launchProfileName));

// Identity has a reference to all of the apps for callback urls, this is a cyclic reference
identityApi.WithEnvironment("WebAppClient", webApp.GetEndpoint(launchProfileName));

builder.AddProject<Projects.Identity_API>("identity-api");

builder.Build().Run();
static bool ShouldUseHttpForEndpoints()
{
    const string EnvVarName = "ESHOP_USE_HTTP_ENDPOINTS";
    var envValue = Environment.GetEnvironmentVariable(EnvVarName);

    // Attempt to parse the environment variable value; return true if it's exactly "1".
    return int.TryParse(envValue, out int result) && result == 1;
}
```

## 21. We add the "User" folder inside "Pages" folder in the WebApp project

![image](https://github.com/user-attachments/assets/dae6a02f-272b-4d1f-b93e-255f6144b331)

## 22. We add the User "Login.razor" and "Logout.razor" components

![image](https://github.com/user-attachments/assets/7b734cca-4049-4fb9-b8d1-aec6aeac3d6c)

**LogIn.razor**

```csharp
@page "/user/login"
@inject NavigationManager Nav
@attribute [Authorize]
@code {
    [SupplyParameterFromQuery]
    public string? ReturnUrl { get; set; }

    [CascadingParameter]
    public HttpContext? HttpContext { get; set; }

    protected override async Task OnInitializedAsync()
    {
        var returnUrl = ReturnUrl ?? "/";
        var url = new Uri(returnUrl, UriKind.RelativeOrAbsolute);
        Nav.NavigateTo(url.IsAbsoluteUri ? "/" : returnUrl);
        await base.OnInitializedAsync();
    }

    public static string Url(NavigationManager nav)
        => $"user/login?returnUrl={Uri.EscapeDataString(nav.ToBaseRelativePath(nav.Uri))}";
}
```

**LogOut.razor**

```csharp
@page "/user/logout"
@*
    When the 'log out' form is posted, it is handled inside UserMenu.razor.
    This page only exists to create an endpoint that accepts the form post.
*@
```

## 23. We update the appsettings.json file in the Identity.API project

**appsettings.json**

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "MauiCallback": "maui://authcallback",
  "UseCustomizationData": false,
  "TokenLifetimeMinutes": 120,
  "PermanentTokenLifetimeDays": 365
}
```

**appsettings.Development.json**

```json
{
  "ConnectionStrings": {
    "IdentityDB": "Host=localhost;Database=IdentityDB;Username=postgres;Password=yourWeak(!)Password"
  }
}
```

## 24. We add the UsersSeed.cs file in the Identity.API project

![image](https://github.com/user-attachments/assets/a4f77f32-48d3-4ba2-9842-5df19b390161)

**UsersSeed.cs**

```csharp

namespace eShop.Identity.API;

public class UsersSeed(ILogger<UsersSeed> logger, UserManager<ApplicationUser> userManager) : IDbSeeder<ApplicationDbContext>
{
    public async Task SeedAsync(ApplicationDbContext context)
    {
        var alice = await userManager.FindByNameAsync("alice");

        if (alice == null)
        {
            alice = new ApplicationUser
            {
                UserName = "alice",
                Email = "AliceSmith@email.com",
                EmailConfirmed = true,
                CardHolderName = "Alice Smith",
                CardNumber = "XXXXXXXXXXXX1881",
                CardType = 1,
                City = "Redmond",
                Country = "U.S.",
                Expiration = "12/24",
                Id = Guid.NewGuid().ToString(),
                LastName = "Smith",
                Name = "Alice",
                PhoneNumber = "1234567890",
                ZipCode = "98052",
                State = "WA",
                Street = "15703 NE 61st Ct",
                SecurityNumber = "123"
            };

            var result = userManager.CreateAsync(alice, "Pass123$").Result;

            if (!result.Succeeded)
            {
                throw new Exception(result.Errors.First().Description);
            }

            if (logger.IsEnabled(LogLevel.Debug))
            {
                logger.LogDebug("alice created");
            }
        }
        else
        {
            if (logger.IsEnabled(LogLevel.Debug))
            {
                logger.LogDebug("alice already exists");
            }
        }

        var bob = await userManager.FindByNameAsync("bob");

        if (bob == null)
        {
            bob = new ApplicationUser
            {
                UserName = "bob",
                Email = "BobSmith@email.com",
                EmailConfirmed = true,
                CardHolderName = "Bob Smith",
                CardNumber = "XXXXXXXXXXXX1881",
                CardType = 1,
                City = "Redmond",
                Country = "U.S.",
                Expiration = "12/24",
                Id = Guid.NewGuid().ToString(),
                LastName = "Smith",
                Name = "Bob",
                PhoneNumber = "1234567890",
                ZipCode = "98052",
                State = "WA",
                Street = "15703 NE 61st Ct",
                SecurityNumber = "456"
            };

            var result = await userManager.CreateAsync(bob, "Pass123$");

            if (!result.Succeeded)
            {
                throw new Exception(result.Errors.First().Description);
            }

            if (logger.IsEnabled(LogLevel.Debug))
            {
                logger.LogDebug("bob created");
            }
        }
        else
        {
            if (logger.IsEnabled(LogLevel.Debug))
            {
                logger.LogDebug("bob already exists");
            }
        }
    }
}
```

## 25. We add the Config.cs file

![image](https://github.com/user-attachments/assets/af1cfe26-ae63-4fd4-a36b-ce87a41c4de7)

**Config.cs**

```csharp
using Duende.IdentityServer;
using Duende.IdentityServer.Models;

namespace eShop.Identity.API.Configuration
{
    public class Config
    {
        // ApiResources define the apis in your system
        public static IEnumerable<ApiResource> GetApis()
        {
            return new List<ApiResource>
            {
                new ApiResource("orders", "Orders Service"),
                new ApiResource("basket", "Basket Service"),
                new ApiResource("webhooks", "Webhooks registration Service"),
            };
        }

        // ApiScope is used to protect the API 
        //The effect is the same as that of API resources in IdentityServer 3.x
        public static IEnumerable<ApiScope> GetApiScopes()
        {
            return new List<ApiScope>
            {
                new ApiScope("orders", "Orders Service"),
                new ApiScope("basket", "Basket Service"),
                new ApiScope("webhooks", "Webhooks registration Service"),
            };
        }

        // Identity resources are data like user ID, name, or email address of a user
        // see: http://docs.identityserver.io/en/release/configuration/resources.html
        public static IEnumerable<IdentityResource> GetResources()
        {
            return new List<IdentityResource>
            {
                new IdentityResources.OpenId(),
                new IdentityResources.Profile()
            };
        }

        // client want to access resources (aka scopes)
        public static IEnumerable<Client> GetClients(IConfiguration configuration)
        {
            return new List<Client>
            {
                new Client
                {
                    ClientId = "maui",
                    ClientName = "eShop MAUI OpenId Client",
                    AllowedGrantTypes = GrantTypes.Code,                    
                    //Used to retrieve the access token on the back channel.
                    ClientSecrets =
                    {
                        new Secret("secret".Sha256())
                    },
                    RedirectUris = { configuration["MauiCallback"] },
                    RequireConsent = false,
                    RequirePkce = true,
                    PostLogoutRedirectUris = { $"{configuration["MauiCallback"]}/Account/Redirecting" },
                    //AllowedCorsOrigins = { "http://eshopxamarin" },
                    AllowedScopes = new List<string>
                    {
                        IdentityServerConstants.StandardScopes.OpenId,
                        IdentityServerConstants.StandardScopes.Profile,
                        IdentityServerConstants.StandardScopes.OfflineAccess,
                        "orders",
                        "basket",
                        "mobileshoppingagg",
                        "webhooks"
                    },
                    //Allow requesting refresh tokens for long lived API access
                    AllowOfflineAccess = true,
                    AllowAccessTokensViaBrowser = true,
                    AlwaysIncludeUserClaimsInIdToken = true,
                    AccessTokenLifetime = 60*60*2, // 2 hours
                    IdentityTokenLifetime= 60*60*2 // 2 hours
                },
                new Client
                {
                    ClientId = "webapp",
                    ClientName = "WebApp Client",
                    ClientSecrets = new List<Secret>
                    {
                        new Secret("secret".Sha256())
                    },
                    ClientUri = $"{configuration["WebAppClient"]}",                             // public uri of the client
                    AllowedGrantTypes = GrantTypes.Code,
                    AllowAccessTokensViaBrowser = false,
                    RequireConsent = false,
                    AllowOfflineAccess = true,
                    AlwaysIncludeUserClaimsInIdToken = true,
                    RequirePkce = false,
                    RedirectUris = new List<string>
                    {
                        $"{configuration["WebAppClient"]}/signin-oidc"
                    },
                    PostLogoutRedirectUris = new List<string>
                    {
                        $"{configuration["WebAppClient"]}/signout-callback-oidc"
                    },
                    AllowedScopes = new List<string>
                    {
                        IdentityServerConstants.StandardScopes.OpenId,
                        IdentityServerConstants.StandardScopes.Profile,
                        IdentityServerConstants.StandardScopes.OfflineAccess,
                        "orders",
                        "basket",
                        "webshoppingagg",
                        "webhooks"
                    },
                    AccessTokenLifetime = 60*60*2, // 2 hours
                    IdentityTokenLifetime= 60*60*2 // 2 hours
                },
                new Client
                {
                    ClientId = "webhooksclient",
                    ClientName = "Webhooks Client",
                    ClientSecrets = new List<Secret>
                    {
                        new Secret("secret".Sha256())
                    },
                    ClientUri = $"{configuration["WebhooksWebClient"]}",                             // public uri of the client
                    AllowedGrantTypes = GrantTypes.Code,
                    AllowAccessTokensViaBrowser = false,
                    RequireConsent = false,
                    AllowOfflineAccess = true,
                    AlwaysIncludeUserClaimsInIdToken = true,
                    RedirectUris = new List<string>
                    {
                        $"{configuration["WebhooksWebClient"]}/signin-oidc"
                    },
                    PostLogoutRedirectUris = new List<string>
                    {
                        $"{configuration["WebhooksWebClient"]}/signout-callback-oidc"
                    },
                    AllowedScopes = new List<string>
                    {
                        IdentityServerConstants.StandardScopes.OpenId,
                        IdentityServerConstants.StandardScopes.Profile,
                        IdentityServerConstants.StandardScopes.OfflineAccess,
                        "webhooks"
                    },
                    AccessTokenLifetime = 60*60*2, // 2 hours
                    IdentityTokenLifetime= 60*60*2 // 2 hours
                },
                new Client
                {
                    ClientId = "basketswaggerui",
                    ClientName = "Basket Swagger UI",
                    AllowedGrantTypes = GrantTypes.Implicit,
                    AllowAccessTokensViaBrowser = true,

                    RedirectUris = { $"{configuration["BasketApiClient"]}/swagger/oauth2-redirect.html" },
                    PostLogoutRedirectUris = { $"{configuration["BasketApiClient"]}/swagger/" },

                    AllowedScopes =
                    {
                        "basket"
                    }
                },
                new Client
                {
                    ClientId = "orderingswaggerui",
                    ClientName = "Ordering Swagger UI",
                    AllowedGrantTypes = GrantTypes.Implicit,
                    AllowAccessTokensViaBrowser = true,

                    RedirectUris = { $"{configuration["OrderingApiClient"]}/swagger/oauth2-redirect.html" },
                    PostLogoutRedirectUris = { $"{configuration["OrderingApiClient"]}/swagger/" },

                    AllowedScopes =
                    {
                        "orders"
                    }
                },
                new Client
                {
                    ClientId = "webhooksswaggerui",
                    ClientName = "WebHooks Service Swagger UI",
                    AllowedGrantTypes = GrantTypes.Implicit,
                    AllowAccessTokensViaBrowser = true,

                    RedirectUris = { $"{configuration["WebhooksApiClient"]}/swagger/oauth2-redirect.html" },
                    PostLogoutRedirectUris = { $"{configuration["WebhooksApiClient"]}/swagger/" },

                    AllowedScopes =
                    {
                        "webhooks"
                    }
                }
            };
        }
    }
}
```

## 26. We add the Services in the Identity.API project 

![image](https://github.com/user-attachments/assets/ff5deba0-c31b-4cd2-8fa4-ace5cea0c2ce)

## 27. We add the Extension files in the Identity.API project

![image](https://github.com/user-attachments/assets/324d34f4-4bb9-4ef5-8825-2cf94de35e74)

**AtivityExtensions.cs**

```csharp
using System.Diagnostics;

internal static class ActivityExtensions
{
    // See https://opentelemetry.io/docs/specs/otel/trace/semantic_conventions/exceptions/
    public static void SetExceptionTags(this Activity activity, Exception ex)
    {
        if (activity is null)
        {
            return;
        }

        activity.AddTag("exception.message", ex.Message);
        activity.AddTag("exception.stacktrace", ex.ToString());
        activity.AddTag("exception.type", ex.GetType().FullName);
        activity.SetStatus(ActivityStatusCode.Error);
    }
}
```

**MigrateDbContextExtensions.cs**

```csharp
using System.Diagnostics;

namespace Microsoft.AspNetCore.Hosting;

internal static class MigrateDbContextExtensions
{
    private static readonly string ActivitySourceName = "DbMigrations";
    private static readonly ActivitySource ActivitySource = new(ActivitySourceName);

    public static IServiceCollection AddMigration<TContext>(this IServiceCollection services)
        where TContext : DbContext
        => services.AddMigration<TContext>((_, _) => Task.CompletedTask);

    public static IServiceCollection AddMigration<TContext>(this IServiceCollection services, Func<TContext, IServiceProvider, Task> seeder)
        where TContext : DbContext
    {
        // Enable migration tracing
        services.AddOpenTelemetry().WithTracing(tracing => tracing.AddSource(ActivitySourceName));

        return services.AddHostedService(sp => new MigrationHostedService<TContext>(sp, seeder));
    }

    public static IServiceCollection AddMigration<TContext, TDbSeeder>(this IServiceCollection services)
        where TContext : DbContext
        where TDbSeeder : class, IDbSeeder<TContext>
    {
        services.AddScoped<IDbSeeder<TContext>, TDbSeeder>();
        return services.AddMigration<TContext>((context, sp) => sp.GetRequiredService<IDbSeeder<TContext>>().SeedAsync(context));
    }

    private static async Task MigrateDbContextAsync<TContext>(this IServiceProvider services, Func<TContext, IServiceProvider, Task> seeder) where TContext : DbContext
    {
        using var scope = services.CreateScope();
        var scopeServices = scope.ServiceProvider;
        var logger = scopeServices.GetRequiredService<ILogger<TContext>>();
        var context = scopeServices.GetService<TContext>();

        using var activity = ActivitySource.StartActivity($"Migration operation {typeof(TContext).Name}");

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            var strategy = context.Database.CreateExecutionStrategy();

            await strategy.ExecuteAsync(() => InvokeSeeder(seeder, context, scopeServices));
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);

            activity.SetExceptionTags(ex);

            throw;
        }
    }

    private static async Task InvokeSeeder<TContext>(Func<TContext, IServiceProvider, Task> seeder, TContext context, IServiceProvider services)
        where TContext : DbContext
    {
        using var activity = ActivitySource.StartActivity($"Migrating {typeof(TContext).Name}");

        try
        {
            await context.Database.MigrateAsync();
            await seeder(context, services);
        }
        catch (Exception ex)
        {
            activity.SetExceptionTags(ex);

            throw;
        }
    }

    private class MigrationHostedService<TContext>(IServiceProvider serviceProvider, Func<TContext, IServiceProvider, Task> seeder)
        : BackgroundService where TContext : DbContext
    {
        public override Task StartAsync(CancellationToken cancellationToken)
        {
            return serviceProvider.MigrateDbContextAsync(seeder);
        }

        protected override Task ExecuteAsync(CancellationToken stoppingToken)
        {
            return Task.CompletedTask;
        }
    }
}
public interface IDbSeeder<in TContext> where TContext : DbContext
{
    Task SeedAsync(TContext context);
}
```

## 28. We update the ApplicationUser.cs file

**ApplicationUser.cs**

```csharp
namespace eShop.Identity.API.Models
{
    // Add profile data for application users by adding properties to the ApplicationUser class
    public class ApplicationUser : IdentityUser
    {
        [Required]
        public string CardNumber { get; set; }
        [Required]
        public string SecurityNumber { get; set; }
        [Required]
        [RegularExpression(@"(0[1-9]|1[0-2])\/[0-9]{2}", ErrorMessage = "Expiration should match a valid MM/YY value")]
        public string Expiration { get; set; }
        [Required]
        public string CardHolderName { get; set; }
        public int CardType { get; set; }
        [Required]
        public string Street { get; set; }
        [Required]
        public string City { get; set; }
        [Required]
        public string State { get; set; }
        [Required]
        public string Country { get; set; }
        [Required]
        public string ZipCode { get; set; }
        [Required]
        public string Name { get; set; }
        [Required]
        public string LastName { get; set; }
    }
}
```

## 29. We migrate the Identity database

We right click on the **Identity.API** project and we select **Set as StartUp project**

![image](https://github.com/user-attachments/assets/d330cc53-d45b-4ca7-85d7-85312ba8ae51)

Then select the menu option **Tools->NuGet Package Manager->Package Manger Console** 

![image](https://github.com/user-attachments/assets/91d42fbd-81e0-45f6-a9df-ed43654e0fd3)

And we select the **Identity.API** project in the dropdown list

We run this command to **add the first database migration**

```
Add-Migration databaseinitial
```

![image](https://github.com/user-attachments/assets/87440613-35fa-4a73-9304-2210fb2dd6b9)

We verify the **Migrations** folder was already created, containing the database migrations files

![image](https://github.com/user-attachments/assets/e94ce495-526e-49b1-9878-daf958135b41)

## 30. We modify the launchSettings.json file in the Identity.API project

![image](https://github.com/user-attachments/assets/9014c842-c720-43b1-b2c4-8d1ad3db6055)

**launchSettings.json**

```json
{
  "profiles": {
    "http": {
      "commandName": "Project",
      "launchBrowser": true,
      "applicationUrl": "http://localhost:5223",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "https": {
      "commandName": "Project",
      "launchBrowser": true,
      "applicationUrl": "https://localhost:5243;http://localhost:5223",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

## 30. We run the application

We select the **eShop.AppHost** project as the **StartUp project**

![image](https://github.com/user-attachments/assets/7e63a0b7-36e3-4201-a14e-a555bb390726)

We run the application and verify the results

