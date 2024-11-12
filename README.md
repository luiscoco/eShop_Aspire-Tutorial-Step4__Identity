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

![image](https://github.com/user-attachments/assets/197f5589-1db0-4db7-9e48-9a2de1e2920a)

Note: in this image we selected .NET 8, because I am explaining this sample in a computer with .NET 8, but in your computer you should install and select .NET 9

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

IMPORTANT NOTE: we have to delete the **Migrations** folder

![image](https://github.com/user-attachments/assets/c7570d09-c064-4a8f-8d35-0482294f8a0f)

## 8. We 

