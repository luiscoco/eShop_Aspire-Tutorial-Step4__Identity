# Building 'eShop' from Zero to Hero: We create the Web Application with Aspire .NET 9

The starting point for this sample is the following **github repo**:

https://github.com/luiscoco/eShop_Aspire-Tutorial-Step2_CatalogAPI-Configuring_OpenApi

Please donwload the solution in that repo and start implementing the following changes

![image](https://github.com/user-attachments/assets/1c9d510c-827c-4660-a29a-a27666bd8b31)

## 1. We Download and Open the Solution with Visual Studio 2022

![image](https://github.com/user-attachments/assets/eee32d0d-ddfa-474b-99e4-85283ac2030e)

## 2. We Create the WebAppComponents Project

We right click on the Solution name and we **Add a New Project**

![image](https://github.com/user-attachments/assets/9e8770b5-61c3-4bac-95bd-8ffd1c154a2f)

We select the **Blazor Web App** project template and press the Next button 

![image](https://github.com/user-attachments/assets/df365ec2-fb1d-4c24-8079-2ff777b830ef)

We set the **Project Name and Location** and press the Next button 

![image](https://github.com/user-attachments/assets/77517150-8091-4e6d-ba8a-957600fabdab)

We select the **.NET 9** Framework and press the Create button

![image](https://github.com/user-attachments/assets/48183b0e-6eca-4e3a-812c-763e9716eb13)

We verify the new project added in the solution

![image](https://github.com/user-attachments/assets/6d334da8-87ff-4d40-a2e1-4ac895915ac1)

## 3. We Modify the WebAppComponents Project

We delete/remove from the Blazor Web App project these folders and files:

![image](https://github.com/user-attachments/assets/2a37fbc2-738b-44de-af0c-722d39404ef8)

This is the project structure

![image](https://github.com/user-attachments/assets/47413af9-1b8e-403f-add8-db24aceed90d)

## 4. We Load the Nuget Package in the WebAppComponents Project

**Microsoft.AspNetCore.Components.Web**

![image](https://github.com/user-attachments/assets/cc0352d3-806a-45cc-a063-30593d35353b)

## 5. We Edit the WebAppComponents.csproj File

We replace the actual **Project Sdk "Microsoft.NET.Sdk.Web"**

![image](https://github.com/user-attachments/assets/39dcb3b6-bbe9-4133-b6cb-3528a5627918)

We set a new **Project Sdk "Microsoft.NET.Sdk.Razor"**

![image](https://github.com/user-attachments/assets/befeda3b-fe47-4c28-930d-90d6aa1f420f)

## 6. We Create new folders in the WebAppComponents Project 

We create these folder in the project

![image](https://github.com/user-attachments/assets/08e490d2-7748-486d-beec-d80d729bb5ed)

## 7. We Add the Sevices in the WebAppComponents Project 

This C# code defines an interface, ICatalogService, within the eShop.WebAppComponents.Services namespace. It serves as a contract for any class that will implement catalog-related services in the eShop web application. Here’s a brief breakdown of its purpose and methods:

The code is part of the **eShop.WebAppComponents.Services** namespace, which indicates for organizing services related to an e-commerce catalog

The code imports **System.Collections.Generic** for collections and **System.Threading.Tasks** for asynchronous operations

### 7.1. Interface Definition (ICatalogService)

This interface is designed for flexibility and asynchronicity, allowing the web app to retrieve catalog data efficiently while supporting search, filtering, and pagination

Interfaces in C# define a set of methods that implementing classes must provide

**ICatalogService** outlines methods for catalog-related operations, often interacting with catalog items, brands, and types asynchronously

**Methods**:

**Task<CatalogItem?> GetCatalogItem(int id);**: 

Retrieves a single catalog item by its ID. It returns a CatalogItem (or null if not found) wrapped in a Task for asynchronous operation

**Task<CatalogResult> GetCatalogItems(int pageIndex, int pageSize, int? brand, int? type);**

Fetches a paginated list of catalog items based on the page index and size, as well as optional filters for brand and type. The result is a CatalogResult, possibly containing metadata and a list of items

**Task<List<CatalogItem>> GetCatalogItems(IEnumerable<int> ids);**

Retrieves multiple catalog items based on a list of item IDs. Returns a list of CatalogItem objects wrapped in a Task

**Task<CatalogResult> GetCatalogItemsWithSemanticRelevance(int page, int take, string text);***

Fetches catalog items based on semantic relevance to a given search text, along with pagination (page, take). This could imply a search or recommendation feature

**Task<IEnumerable<CatalogBrand>> GetBrands();**

Returns a list of available catalog brands.

**Task<IEnumerable<CatalogItemType>> GetTypes();**

Returns a list of available catalog item types

**ICatalogService.cs**

```csharp
using System.Collections.Generic;
using System.Threading.Tasks;
using eShop.WebAppComponents.Catalog;

namespace eShop.WebAppComponents.Services
{
    public interface ICatalogService
    {
        Task<CatalogItem?> GetCatalogItem(int id);
        Task<CatalogResult> GetCatalogItems(int pageIndex, int pageSize, int? brand, int? type);
        Task<List<CatalogItem>> GetCatalogItems(IEnumerable<int> ids);
        Task<CatalogResult> GetCatalogItemsWithSemanticRelevance(int page, int take, string text);
        Task<IEnumerable<CatalogBrand>> GetBrands();
        Task<IEnumerable<CatalogItemType>> GetTypes();
    }
}
```

### 7.2. Interface IProductImageUrlProvider

This C# code defines an interface, **IProductImageUrlProvider**, within the **eShop.WebAppComponents.Services** namespace

It provides a structure for any class that will implement functionality for **generating URLs to product images** in an e-commerce context

**string GetProductImageUrl(CatalogItem item) => GetProductImageUrl(item.Id);**

This is a default method implementation in an interface, which is a feature available in C# 8 and later

This method takes a **CatalogItem** object and generates the product image URL by calling the second method (**GetProductImageUrl(int productId**)) with the item’s ID (item.Id)

**string GetProductImageUrl(int productId);**

This method, which must be implemented by any class that uses this interface, takes a product ID and generates the image URL for that product

The **IProductImageUrlProvider** interface provides a unified way to **obtain product image URLs** by either passing a full **CatalogItem** object or just the product’s ID

This design abstracts the **URL generation** details, so other parts of the application can **retrieve image URLs** without needing to know how they’re generated

**IProductImageUrlProvider.cs**

```csharp
using eShop.WebAppComponents.Catalog;

namespace eShop.WebAppComponents.Services;

public interface IProductImageUrlProvider
{
    string GetProductImageUrl(CatalogItem item)
        => GetProductImageUrl(item.Id);

    string GetProductImageUrl(int productId);
}
```

### 7.3. CatalogService class

This C# code defines a **CatalogService** class that implements the **ICatalogService** interface, providing methods for interacting with a remote catalog API in an e-commerce application

The **CatalogService** uses an **HttpClient** to make asynchronous HTTP requests to fetch catalog data

The **CatalogService** class provides a robust, asynchronous interface to retrieve catalog data from a remote API

Each method constructs the appropriate URL for the required resource and uses **HttpClient to fetch data as JSON**

This setup enables the application to interact with catalog items, brands, and types easily, supporting filtering, pagination, and search functionality in a reusable and consistent way

**CatalogService.cs**

```csharp
using System.Net.Http.Json;
using System.Web;
using eShop.WebAppComponents.Catalog;

namespace eShop.WebAppComponents.Services;

public class CatalogService(HttpClient httpClient) : ICatalogService
{
    private readonly string remoteServiceBaseUrl = "/api/catalog/";

    public Task<CatalogItem?> GetCatalogItem(int id)
    {
        var uri = $"{remoteServiceBaseUrl}items/{id}";
        return httpClient.GetFromJsonAsync<CatalogItem>(uri);
    }

    public async Task<CatalogResult> GetCatalogItems(int pageIndex, int pageSize, int? brand, int? type)
    {
        var uri = GetAllCatalogItemsUri(remoteServiceBaseUrl, pageIndex, pageSize, brand, type);
        var result = await httpClient.GetFromJsonAsync<CatalogResult>(uri);
        return result!;
    }

    public async Task<List<CatalogItem>> GetCatalogItems(IEnumerable<int> ids)
    {
        var uri = $"{remoteServiceBaseUrl}items/by?ids={string.Join("&ids=", ids)}";
        var result = await httpClient.GetFromJsonAsync<List<CatalogItem>>(uri);
        return result!;
    }

    public Task<CatalogResult> GetCatalogItemsWithSemanticRelevance(int page, int take, string text)
    {
        var url = $"{remoteServiceBaseUrl}items/withsemanticrelevance/{HttpUtility.UrlEncode(text)}?pageIndex={page}&pageSize={take}";
        var result = httpClient.GetFromJsonAsync<CatalogResult>(url);
        return result!;
    }

    public async Task<IEnumerable<CatalogBrand>> GetBrands()
    {
        var uri = $"{remoteServiceBaseUrl}catalogBrands";
        var result = await httpClient.GetFromJsonAsync<CatalogBrand[]>(uri);
        return result!;
    }

    public async Task<IEnumerable<CatalogItemType>> GetTypes()
    {
        var uri = $"{remoteServiceBaseUrl}catalogTypes";
        var result = await httpClient.GetFromJsonAsync<CatalogItemType[]>(uri);
        return result!;
    }

    private static string GetAllCatalogItemsUri(string baseUri, int pageIndex, int pageSize, int? brand, int? type)
    {
        string filterQs;

        if (type.HasValue)
        {
            var brandQs = brand.HasValue ? brand.Value.ToString() : string.Empty;
            filterQs = $"/type/{type.Value}/brand/{brandQs}";
        }
        else if (brand.HasValue)
        {
            var brandQs = brand.HasValue ? brand.Value.ToString() : string.Empty;
            filterQs = $"/type/all/brand/{brandQs}";
        }
        else
        {
            filterQs = string.Empty;
        }
        return $"{baseUri}items{filterQs}?pageIndex={pageIndex}&pageSize={pageSize}";
    }
}
```


## 8. We Add the ItemHelper.cs File in the WebAppComponents Project 

This code defines a static **helper** class, **ItemHelper**, within the namespace **eShop.WebAppComponents.Item**

The purpose of this **helper** class is to **generate URLs** for individual catalog items in a web application

```csharp
using eShop.WebAppComponents.Catalog;

namespace eShop.WebAppComponents.Item;

public static class ItemHelper
{
    public static string Url(CatalogItem item)
        => $"item/{item.Id}";
}
```

## 9. We Add the Razor Componentes in the WebAppComponents Project 

### 9.1. CatalogItem.cs

This code defines a set of **record types** within the namespace **eShop.WebAppComponents.Catalog**

These records represent different entities related to an e-commerce catalog, likely part of a web application’s data model

This record represents a **detailed catalog item** with basic properties and references to its associated brand and type

This set of records defines the main components for a **catalog system**:

**CatalogItem** for individual items,

**CatalogBrand** and **CatalogItemType** to organize items by brand and type,

and **CatalogResult** to manage paginated lists of catalog items

Using records for these data structures is beneficial because **records** in C# are **immutable reference types** that provide built-in functionality for value equality, making them ideal for data modeling

**CatalogItem.cs**

```csharp
namespace eShop.WebAppComponents.Catalog;

public record CatalogItem(
    int Id,
    string Name,
    string Description,
    decimal Price,
    string PictureUrl,
    int CatalogBrandId,
    CatalogBrand CatalogBrand,
    int CatalogTypeId,
    CatalogItemType CatalogType);

public record CatalogResult(int PageIndex, int PageSize, int Count, List<CatalogItem> Data);
public record CatalogBrand(int Id, string Brand);
public record CatalogItemType(int Id, string Type);
```

### 9.2. CatalogListItem.razor

This code represents a **Razor component** in a Blazor web application for displaying a **catalog item**

It uses several Blazor and ASP.NET features, such as dependency injection and Razor syntax for dynamic HTML generation

This **component dynamically displays a catalog item with its image, name, and price**

It uses dependency injection to load the product image URL and constructs the item’s link dynamically, making it flexible for any catalog item passed to it

**CatalogListItem.razor**

```razor
@using eShop.WebAppComponents.Item
@using eShop.WebAppComponents.Catalog
@using eShop.WebAppComponents.Services

@inject IProductImageUrlProvider ProductImages

<div class="catalog-item">
    <a class="catalog-product" href="@ItemHelper.Url(Item)" data-enhance-nav="false">
        <span class='catalog-product-image'>
            <img alt="@Item.Name" src='@ProductImages.GetProductImageUrl(Item)' />
        </span>
        <span class='catalog-product-content'>
            <span class='name'>@Item.Name</span>
            <span class='price'>$@Item.Price.ToString("0.00")</span>
        </span>
    </a>
</div>

@code {
    [Parameter, EditorRequired]
    public required CatalogItem Item { get; set; }

    [Parameter]
    public bool IsLoggedIn { get; set; }
}
```

### 9.3. CatalogSearch.razor

This code defines a **Razor component** that provides a **filtering** interface for **catalog items** in a Blazor web application

It allows users to **filter products by brand and type**, using injected services to retrieve data and dynamically building URLs for filter links

It **dynamically builds URLs for filtering** and uses dependency injection to access data and navigation services, enhancing interactivity within the web application

**CatalogSearch.razor**

```razor
@using eShop.WebAppComponents.Catalog
@using eShop.WebAppComponents.Services

@inject CatalogService CatalogService
@inject NavigationManager Nav

@if (catalogBrands is not null && catalogItemTypes is not null)
{
    <div class="catalog-search">
        <div class="catalog-search-header">
            <img role="presentation" src="icons/filters.svg" />
            Filters
        </div>
        <div class="catalog-search-types">
            <div class="catalog-search-group">
                <h3>Brand</h3>
                <div class="catalog-search-group-tags">
                    <a href="@BrandUri(null)"
                    class="catalog-search-tag @(BrandId == null ? "active " : "")">
                        All
                    </a>
                    @foreach (var brand in catalogBrands)
                    {
                        <a href="@BrandUri(brand.Id)"
                        class="catalog-search-tag @(BrandId == brand.Id ? "active " : "")">
                            @brand.Brand
                        </a>
                    }
                </div>
            </div>
            <div class="catalog-search-group">
                <h3>Type</h3>

                <div class="catalog-search-group-tags">
                    <a href="@TypeUri(null)"
                    class="catalog-search-tag @(ItemTypeId == null ? "active " : "")">
                    All
                    </a>
                    @foreach (var itemType in catalogItemTypes)
                    {
                        <a href="@TypeUri(itemType.Id)"
                        class="catalog-search-tag @(ItemTypeId == itemType.Id ? "active " : "")">
                            @itemType.Type
                        </a>
                    }
                </div>
            </div>
        </div>
    </div>
}

@code {
    IEnumerable<CatalogBrand>? catalogBrands;
    IEnumerable<CatalogItemType>? catalogItemTypes;
    [Parameter] public int? BrandId { get; set; }
    [Parameter] public int? ItemTypeId { get; set; }

    protected override async Task OnInitializedAsync()
    {
        var brandsTask = CatalogService.GetBrands();
        var itemTypesTask = CatalogService.GetTypes();
        await Task.WhenAll(brandsTask, itemTypesTask);
        catalogBrands = brandsTask.Result;
        catalogItemTypes = itemTypesTask.Result;
    }

    private string BrandUri(int? brandId) => Nav.GetUriWithQueryParameters(new Dictionary<string, object?>()
    {
        { "page", null },
        { "brand", brandId },
    });

    private string TypeUri(int? typeId) => Nav.GetUriWithQueryParameters(new Dictionary<string, object?>()
    {
        { "page", null },
        { "type", typeId },
    });
}
```

## 10. We Create a Blazor Web Application (WebApp project)

We right click on the Solution and we **Add a New Project...**

![image](https://github.com/user-attachments/assets/cb9c616b-a0c4-4b15-9217-257a52ad447e)

We select the **Blazor Web Application** as project template and press the Next button

![image](https://github.com/user-attachments/assets/17bc048b-8e01-4de7-b823-144c14a5de6d)

We input the project name and location and press the Next button

![image](https://github.com/user-attachments/assets/657c3b3e-1d9b-411c-9102-72784a820052)

We select the **.NET 9 Framework** and we press the Create button

![image](https://github.com/user-attachments/assets/21daa4f7-c5a2-4edb-b532-952fc4ee2405)

We review the Solution folders structure

![image](https://github.com/user-attachments/assets/a0956d4c-6daf-489e-95b9-104d52c1075b)

## 11. We Add the Project References in the WebApp project

![image](https://github.com/user-attachments/assets/7644991d-db01-4353-bca9-16db01f4a5fc)

![image](https://github.com/user-attachments/assets/90cffc03-cff0-46a0-9542-2da9e651ff5d)

We verify the two project references were added

![image](https://github.com/user-attachments/assets/2da2482d-cf61-44b4-8399-24fa5b263539)

## 12. We Add the Nuget Packages in the WebApp project

We add the following packages in the WebApp project

**Asp.Versioning.Http.Client**: This library is part of ASP.NET API Versioning tools, designed to help developers handle versioning for their HTTP API clients

It allows you to specify and manage different versions of HTTP APIs in a way that’s seamless and compatible with ASP.NET's API versioning framework

Using this library, clients can easily specify the API version they want to call, making it useful for applications that need to interact with multiple versions of an API or ensure compatibility with evolving APIs

**Microsoft.Extensions.ServiceDiscovery.Yarp**: This package is a service discovery extension for YARP (Yet Another Reverse Proxy) in the Microsoft.Extensions ecosystem

It enables dynamic service discovery for applications using YARP, allowing YARP to automatically locate and route requests to the appropriate service endpoints

This is especially useful in microservices architectures, where services might scale dynamically or move between different hosts

It typically integrates with service registries like Consul, Eureka, or Azure Service Fabric

**Yarp.ReverseProxy**: YARP (Yet Another Reverse Proxy) is an open-source reverse proxy library created by Microsoft, built on .NET

Yarp.ReverseProxy is the core package, providing essential features for creating a reverse proxy server, including request routing, load balancing, and protocol support (such as HTTP/1.1 and HTTP/2)

It’s highly customizable and can be used to route client requests to various backend services, making it valuable in distributed systems and microservices setups

![image](https://github.com/user-attachments/assets/b473f1a6-abf7-464f-98c7-4b9992c93164)

## 13. We Add the Services Folder in the WebApp project

![image](https://github.com/user-attachments/assets/36f4915f-e408-4d76-949b-ff0658ca2a52)

![image](https://github.com/user-attachments/assets/194c9c34-b158-42ab-8887-a445fc93e1bb)

![image](https://github.com/user-attachments/assets/7403827c-828a-459a-bc4e-8a53e104648e)

This code defines a service class, **ProductImageUrlProvider**, within the eShop.WebApp.Services namespace

This class **provides URLs for product images** in the eShop application

The **ProductImageUrlProvider** class is a service that **generates URLs for accessing product images** based on a given product ID

This URL format centralizes image access logic, making it easy to modify in one place if the structure or API version changes in the future

**ProductImageUrlProvider.cs**

```csharp
using eShop.WebAppComponents.Services;

namespace eShop.WebApp.Services;

public class ProductImageUrlProvider : IProductImageUrlProvider
{
    public string GetProductImageUrl(int productId)
        => $"product-images/{productId}?api-version=1.0";
}
```

## 14. We Remove Blazor Web App Default Razor Components in the WebApp project

![image](https://github.com/user-attachments/assets/398f43e6-cb77-4ca4-aac1-845c30c35aa5)

## 15. We Add a New Folder for the Catalog Razor Component in the WebApp project

![image](https://github.com/user-attachments/assets/1eec8373-8d36-43e4-b43e-a5b39088d3f4)

## 16. We Add the Catalog.razor file in the WebApp project

![image](https://github.com/user-attachments/assets/2d11ea71-b0b0-49ff-b764-593090757c04)

This code represents a Blazor page that displays a **Product Catalog with Pagination**

This code **builds a Paginated Catalog Interface that can Filter by Brand and Item Type**, displaying items dynamically based on the URL query parameters and providing pagination controls at the bottom of the catalog

```razor
@using Microsoft.AspNetCore.Components.Sections
@using WebAppComponents.Catalog
@using eShop.WebAppComponents.Services

@page "/"

@inject NavigationManager Nav
@inject CatalogService CatalogService
@attribute [StreamRendering]

<PageTitle>AdventureWorks</PageTitle>
<SectionContent SectionName="page-header-title">Ready for a new adventure?</SectionContent>
<SectionContent SectionName="page-header-subtitle">Start the season with the latest in clothing and equipment.</SectionContent>

<div class="catalog">
    <CatalogSearch BrandId="@BrandId" ItemTypeId="@ItemTypeId" />

    @if (catalogResult is null)
    {
        <p>Loading...</p>
    }
    else
    {
        <div>
            <div class="catalog-items">
                @foreach (var item in catalogResult.Data)
                {
                    <CatalogListItem Item="@item" />
                }
            </div>

            <div class="page-links">
                @foreach (var pageIndex in GetVisiblePageIndexes(catalogResult))
                {
                    <NavLink ActiveClass="active-page" Match="@NavLinkMatch.All" href="@Nav.GetUriWithQueryParameter("page", pageIndex == 1 ? null : pageIndex)">@pageIndex</NavLink>
                }
            </div>
        </div>
    }
</div>

@code {
    const int PageSize = 9;

    [SupplyParameterFromQuery]
    public int? Page { get; set; }

    [SupplyParameterFromQuery(Name = "brand")]
    public int? BrandId { get; set; }

    [SupplyParameterFromQuery(Name = "type")]
    public int? ItemTypeId { get; set; }

    CatalogResult? catalogResult;

    static IEnumerable<int> GetVisiblePageIndexes(CatalogResult result)
        => Enumerable.Range(1, (int)Math.Ceiling(1.0 * result.Count / PageSize));

    protected override async Task OnInitializedAsync()
    {
        catalogResult = await CatalogService.GetCatalogItems(
            Page.GetValueOrDefault(1) - 1,
            PageSize,
            BrandId,
            ItemTypeId);
    }
}
```

## 17. We Add the GlobalUsings.cs file in the WebApp project

![image](https://github.com/user-attachments/assets/8c52685e-e153-439c-9203-5a659198ffcb)

```csharp
global using eShop.WebAppComponents.Services;
global using eShop.WebAppComponents.Catalog;
```

## 18. We Modify the App.razor file in the WebApp project

This is the updated code

```razor
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <base href="/" />
    <link rel="stylesheet" href="css/normalize.css" />
    <link rel="stylesheet" href="css/app.css" />
    <link rel="stylesheet" href="WebApp.styles.css" />
    <link rel="icon" type="image/png" href="favicon.png" />
    <HeadOutlet />
</head>

<body>
    <Routes />
    <script src="_framework/blazor.web.js"></script>
</body>

</html>
```

## 19. We Modify the Routes.razor file in the WebApp project

```razor
<Router AppAssembly="typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(Layout.MainLayout)" />
        <FocusOnNavigate RouteData="@routeData" Selector="h1" />
    </Found>
</Router>
```

## 20. We Remove the NavMenu.razor file in the WebApp project

![image](https://github.com/user-attachments/assets/cdda2d72-a141-44ab-ac8e-c293f9a82413)

We verify the project folders and files structure

![image](https://github.com/user-attachments/assets/8b28a09c-26ff-4191-8dd4-21e62daa3062)

## 21. We Modify the MainLayout.razor file in the WebApp project

We input the following code in the **MainLayout.razor** file

We have commented the Chatbot component, because it is not included in the scope or work of this sample

```razor
@* @using eShop.WebApp.Components.Chatbot *@
@inherits LayoutComponentBase

<HeaderBar />
@Body
@* <ShowChatbotButton /> *@
<FooterBar />

<div id="blazor-error-ui">
    An unhandled error has occurred.
    <a href="" class="reload">Reload</a>
    <a class="dismiss">🗙</a>
</div>
```

## 22. We Add the HeaderBar.razor and FooterBar.razor componentes in the WebApp project

![image](https://github.com/user-attachments/assets/9eb6065f-e32f-432b-a79d-6d929e413292)

**HeaderBar.razor**

```razor
@using Microsoft.AspNetCore.Components.Endpoints
@using Microsoft.AspNetCore.Components.Sections;

<div class="eshop-header @(IsCatalog? "home" : "")">
    <div class="eshop-header-hero">
        @{
            var headerImage = IsCatalog ? "images/header-home.webp" : "images/header.webp";
        }
        <img role="presentation" src="@headerImage" />
    </div>
    <div class="eshop-header-container">
        <nav class="eshop-header-navbar">
            <a class="logo logo-header" href="">
                <img alt="AdventureWorks" src="images/logo-header.svg" class="logo logo-header" />
            </a>
            
        @*  <UserMenu />
            <CartMenu /> *@
        </nav>
        <div class="eshop-header-intro">
            <h1><SectionOutlet SectionName="page-header-title" /></h1>
            <p><SectionOutlet SectionName="page-header-subtitle" /></p>
        </div>
    </div>
</div>

@code {
    [CascadingParameter]
    public HttpContext? HttpContext { get; set; }

    // We can use Endpoint Metadata to determine the page currently being visited
    private Type? PageComponentType => HttpContext?.GetEndpoint()?.Metadata.OfType<ComponentTypeMetadata>().FirstOrDefault()?.Type;
    private bool IsCatalog => PageComponentType == typeof(Pages.Catalog.Catalog);
}
```

**FooterBar.razor**

```razor
<footer class='eshop-footer'>
  <div class='eshop-footer-content'>
    <div class='eshop-footer-row'>
      <img role="presentation" src='images/logo-footer.svg' class='logo logo-footer' />
      <p>© AdventureWorks</p>
    </div>
  </div>
</footer>
```

## 23. We Add .NET Aspire Orchestrator Support in the WebApp project

![image](https://github.com/user-attachments/assets/dfa0790e-140a-4e6c-a0d8-13193024057c)

We verify the new reference was added in the **eShop.AppHost** project

![image](https://github.com/user-attachments/assets/abcc41b8-1b88-4004-8428-2f2b208ed64f)

We also verify the **Program.cs** file in the WebApp project

![image](https://github.com/user-attachments/assets/3c1a277e-63f9-4ace-b1bd-05093a56f739)

## 24. We Modify the Program.cs in the WebApp project

This code sets up an **HTTP forwarder with service discovery**, registers a singleton **service for providing product image URLs**, and configures an HTTP client to communicate with a versioned API for the catalog service

```csharp
builder.Services.AddHttpForwarderWithServiceDiscovery();

builder.Services.AddSingleton<IProductImageUrlProvider, ProductImageUrlProvider>();
builder.Services.AddHttpClient<CatalogService>(o => o.BaseAddress = new("http://localhost:5301"))
    .AddApiVersion(1.0);
```

and this code

```csharp
app.MapForwarder("/product-images/{id}", "http://localhost:5301", "/api/catalog/items/{id}/pic");
```

We can review the WebApp project whole middleware code:

**Program.cs**

```csharp

using WebApp.Components;
using eShop.WebApp.Services;

var builder = WebApplication.CreateBuilder(args);

builder.AddServiceDefaults();

// Add services to the container.
builder.Services.AddRazorComponents()
.AddInteractiveServerComponents();

builder.Services.AddHttpForwarderWithServiceDiscovery();

builder.Services.AddSingleton<IProductImageUrlProvider, ProductImageUrlProvider>();
builder.Services.AddHttpClient<CatalogService>(o => o.BaseAddress = new("http://localhost:5301"))
    .AddApiVersion(1.0);

var app = builder.Build();

app.MapDefaultEndpoints();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error", createScopeForErrors: true);
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}

app.UseHttpsRedirection();

app.UseAntiforgery();

app.MapStaticAssets();
app.MapRazorComponents<App>()
    .AddInteractiveServerRenderMode();

app.MapForwarder("/product-images/{id}", "http://localhost:5301", "/api/catalog/items/{id}/pic");

app.Run();
```

## 25. We Modify the Program.cs file in the eShop.AppHost project

We have to register the **WebApp** project in the **middleware** with this code

```csharp
var webApp = builder.AddProject<Projects.WebApp>("webapp")
    .WithExternalHttpEndpoints()
    .WithReference(catalogApi);
```

We review the **Program.cs** whole code in the **eShop.AppHost** project

This code snippet defines a **distributed application setup** using a **builder pattern**, for a containerized **microservices** architecture that involves **PostgreSQL** as a database

```csharp
var builder = DistributedApplication.CreateBuilder(args);

var postgres = builder.AddPostgres("postgres")
    .WithImage("ankane/pgvector")
    .WithImageTag("latest")
    .WithLifetime(ContainerLifetime.Persistent);

var catalogDb = postgres.AddDatabase("catalogdb");

var catalogApi = builder.AddProject<Projects.Catalog_API>("catalog-api")
    .WithReference(catalogDb);

var webApp = builder.AddProject<Projects.WebApp>("webapp")
    .WithExternalHttpEndpoints()
    .WithReference(catalogApi);

builder.Build().Run();
```

The code sets up a distributed application with a **PostgreSQL database** (using a **pgvector** image), a **Catalog API service** that connects to this database, and a web application that accesses the Catalog API

Each component is configured as a **containerized service**, and the entire application is built and run through the builder

**Initialize the Builder**:

```csharp
var builder = DistributedApplication.CreateBuilder(args);
```

This line initializes a **DistributedApplication** builder with any command-line arguments (args)

This builder will be used to configure and build the application with various services and dependencies

**Configure PostgreSQL with pgvector**:

```csharp
var postgres = builder.AddPostgres("postgres")
    .WithImage("ankane/pgvector")
    .WithImageTag("latest")
    .WithLifetime(ContainerLifetime.Persistent);
```

Here, a **PostgreSQL service** is being configured:

**AddPostgres("postgres")** adds a PostgreSQL database service named "postgres"

**WithImage("ankane/pgvector")** specifies a custom Docker image for PostgreSQL that includes pgvector (a popular extension for storing and querying vectors in PostgreSQL)

**WithImageTag("latest")** pulls the latest version of this image

**WithLifetime(ContainerLifetime.Persistent)** sets the container's lifecycle to "persistent," meaning it will maintain its data even if restarted

**Add a Database to PostgreSQL**:

```csharp
var catalogDb = postgres.AddDatabase("catalogdb");
```

This line creates a **new database** within the PostgreSQL service, named "catalogdb"

This database will store application-specific data related to a "catalog" or inventory system

**Configure the Catalog API Project**:

```csharp
var catalogApi = builder.AddProject<Projects.Catalog_API>("catalog-api")
    .WithReference(catalogDb);
```

**AddProject<Projects.Catalog_API>("catalog-api")** adds a project called "catalog-api," representing the Catalog API service

**WithReference(catalogDb)** links the catalogApi service to the catalogDb database, enabling it to access the PostgreSQL database

**Configure the Web Application**:

```csharp
var webApp = builder.AddProject<Projects.WebApp>("webapp")
    .WithExternalHttpEndpoints()
    .WithReference(catalogApi);
```

**AddProject<Projects.WebApp>("webapp")** adds a "webapp" project representing the web application

**WithExternalHttpEndpoints()** allows external HTTP connections to this web app, making it accessible to users

**WithReference(catalogApi)** links the web application to the Catalog API, establishing a dependency so the web app can interact with the Catalog API

**Build and Run**:

```csharp
builder.Build().Run();
```

This final line **builds the entire application** with the specified configurations and dependencies, and then runs it

## 26. We Copy in the wwwroot folder the images, fonts, icons and css files

![image](https://github.com/user-attachments/assets/fccd994d-1b21-452b-af77-44f5ede72c25)

![image](https://github.com/user-attachments/assets/17096851-2559-4e48-a206-8177cddb4072)

## 27. We Run the Application and Verify the Results

![image](https://github.com/user-attachments/assets/db7e70c8-6643-43bb-bc76-642273661c1f)

![image](https://github.com/user-attachments/assets/cbdb953f-0514-43df-be87-601f27eed050)

![image](https://github.com/user-attachments/assets/f14cd0a8-f459-4650-a6de-5f624844ef13)

![image](https://github.com/user-attachments/assets/ed94ba0c-c107-47ba-b63b-951b59914b5f)


