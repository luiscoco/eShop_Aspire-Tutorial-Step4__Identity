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



## 20. We update the middleware(Program.cs) in the eShop.AppHost project



## 21. We add the "User" folder inside "Pages" folder in the WebApp project



## 22. We add the User "Login.razor" and "Logout.razor" components

![image](https://github.com/user-attachments/assets/7b734cca-4049-4fb9-b8d1-aec6aeac3d6c)

## 23. 


