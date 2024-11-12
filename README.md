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

We have to open a new command prompt window and run this command to install the IdentityServer4 templates:

```
dotnet new -i IdentityServer4.Templates
```

![image](https://github.com/user-attachments/assets/be93e246-267b-44d5-9913-458b7c2cb697)

We can also verify the templates installation in Visual Studio

![image](https://github.com/user-attachments/assets/b22a5deb-7736-493e-9e30-18d40779e37f)

## 3. We o




