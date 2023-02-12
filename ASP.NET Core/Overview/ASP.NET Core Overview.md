# ASP.NET Core

ASP.NET Core is a cross-platform, high-performance, open-source framework for building modern, cloud-enabled, Internet-connected apps.

With ASP.NET Core, you can:

* Build **web apps** and **services**, **Internet of Things (IoT)** apps, and **mobile backends**
* Use your favorite development tools on `Windows`, `macOS`, and `Linux`
* Deploy to the `cloud` or `on-premises`
* Run on `.NET Core`

### Benefits of ASP.NET Core

ASP.NET Core provides the following benefits:
* Build Web UI
* Build Web APIs
* **Razor Pages** makes coding page-focused scenarios easier and more productive
* **Blazor** lets you use C# in the browser alongside JavaScript. Share server-side and client-side app logic all written with .NET.
Ability to develop and run on `Windows`, `macOS`, and `Linux`
* Open-source
* Integration of modern, client-side frameworks and development workflows (`Angular`, `React`, `Bootstrap`)
* Support for hosting **Remote Procedure Call (RPC)** services using **gRPC**
* A cloud-ready, environment-based configuration system
* Built-in dependency injection
* A lightweight, high-performance, and modular HTTP request pipeline
* Ability to host on the following:
    * `Kestrel`
    * `IIS`
    * `HTTP.sys`
    * `Nginx`
    * `Apache`
    * `Docker`


### ASP.NET Core Application Types

![Object](../Overview/Images/ASP.NET%20Core.png)

### ASP.NET vs ASP.NET Core Comparison

The following table compares ASP.NET Core to ASP.NET 4.x.

ASP.NET Core | ASP.NET 4.x
---------|----------
Build for Windows, macOS, or Linux | Build for Windows
Razor Pages is the recommended approach to create a Web UI as of ASP.NET Core 2.x | Use Web Forms, SignalR, MVC, Web API, WebHooks, or Web Pages
Multiple versions per machine | One version per machine
Develop with Visual Studio, Visual Studio for Mac, or Visual Studio Code using C# or F# | Develop with Visual Studio using C#, VB, or F#
Higher performance than ASP.NET 4.x | Good performance
Use .NET Core runtime | Use .NET Framework runtime

### .NET vs .NET Framework Comparison

The following table compares .NET to .NET Framework

 .NET | .NET Framework
---------|----------
Cross Platform (Windows, Linux & Mac) | Runs on Windows Only 
Open-Source. Anybody can contribute code | Does not take direct contributions
Shipped independently | Installed and updated as part of Windows
Use for New API, Microservices, Container Apps | Continue to extend for existing .NET framework apps

## Fundamentals

Below are the fundamentals for building ASP.NET Core apps:

![Object](../Overview/Images/ASP.NET%20Core%20Fundamentals.png)

### App Startup

ASP.NET Core apps created with the web templates contain the application startup code in the `Program.cs` file. The `Program.cs` file is where:

* `Services` required by the app are configured.
* The app's request handling pipeline is defined as a series of `middleware` components.

The following is the sample app startup code in `Program.cs`

```cs
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddRazorPages();
builder.Services.AddControllersWithViews();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();

app.UseAuthorization();

app.MapGet("/hi", () => "Hello!");

app.MapDefaultControllerRoute();
app.MapRazorPages();

app.Run();
```

### Dependency Injection

ASP.NET Core is designed from scratch to support **Dependency Injection**. ASP.NET Core injects objects of dependency classes through constructor or method by using built-in `IoC container`

The built-in container is represented by `IServiceProvider` implementation that supports constructor injection by default. The types (classes) managed by built-in IoC container are called **services**

There are basically two types of services in ASP.NET Core:

* **Framework Services:** Services which are a part of ASP.NET Core framework such as `IApplicationBuilder`, `IHostingEnvironment`, `ILoggerFactory` etc.

* **Application Services:** The services (custom types or classes) which you as a programmer create for your application.

In order to let the IoC container automatically inject our application services, we first need to register them with IoC container.

#### Understanding Service Lifetime

Built-in IoC container manages the lifetime of a registered service type. It automatically disposes a service instance based on the specified lifetime.


The built-in IoC container supports three kinds of lifetimes:

* **Singleton**: IoC container will create and share a single instance of a service throughout the application's lifetime.
* **Transient**: The IoC container will create a new instance of the specified service type every time you ask for it.
* **Scoped**: IoC container will create an instance of the specified service type once per request and will be shared in a single request.

```cs
builder.Services.AddTransient<ICategoryRepository, CategoryRepository>();
builder.Services.AddScoped<ICategoryRepository, CategoryRepository>();
builder.Services.AddSingleton<ICategoryRepository, CategoryRepository>();
```

#### Dependency Injection Example

Consider a scenario where you want to fetch all the categories from the database and want to show that in the UI layer. So, you will create a service, i.e., a Web API which will be called by the UI layer. Now, in API, we need to create one `GET` method which will call the repository and the repository talks with the database. In order to call the repository, we need to create an instance of the same in API GET method, which means, it’s mandatory to create an instance of the repository for API. We can say the instance of the repository is the dependency of API. Now, let’s see how we can inject this dependency in our core Web API.

* Open Visual Studio and create a new project
* Select API as template and press OK.
* As we are going to fetch the categories, let’s create a `Category` model 
* Create a folder `Models`
* Under `Models` folder, Create a `Category` class which has two fields - `CategoryId` and `CategoryName`.

```cs
public class Category
{
    public int CategoryId { get; set; }
    public string CategoryName { get; set; }
}
```

* Create a folder `Interface`
* Under Interface folder, create an interface of repository having `GetCategories` method which returns the list of `Category` object.

```cs
public interface ICategoryRepository
{
    List<Category> GetCategories();
}
```

* Create a folder `Repository`
* Create `CategoryRepository` class
* Implement the preceding interface and return some sample data. As our target is to understand dependency injection, here, we are not going to fetch the data from database rather returning hard coded ones.

```cs
public class CategoryRepository : ICategoryRepository
{
    public List<Category> GetCategories()
    {
        List<Category> categories = new List<Category>()
        {
            new Category(){ CategoryId =1, CategoryName = "Food" },
            new Category(){ CategoryId =2,CategoryName="Beverages"}
        };

        return categories;
    }
}
```

#### Controller Implementation without Dependency Injection

Assume that we are not aware of the dependency injection. Then, how will we expose the GET method from API? We used to create an instance of `CategoryRepository` and call the `GetCategories` method using that instance. So tomorrow, if there is a change in `CategoryRepository` it will directly affect the GET method of API as it is tightly coupled with that.

```cs
[Route("api/[controller]")]
[ApiController]
public class CategoryController : Controller
{
    [HttpGet]
    public IActionResult Get()
    {
        CategoryRepository categoryRepository = new CategoryRepository();
        List<Category> categories =  categoryRepository.GetCategories();

        return Ok(categories);
    }
}
```

#### Register your service in Dependency Injection container

* Open `Program.cs` file
* Register the service as given below in the startup

```cs
builder.Services.AddTransient<ICategoryRepository, CategoryRepository>();
```

#### Controller Implementation with Dependency Injection

So far, we have added our dependency to the collection. Now, it’s time to inject where we need it, i.e., in the Web API. Our GET method is inside the `CategoryController` and we want an instance of `categoryrepository`. So, let’s create a constructor of `CategoryController` which expects the type of `ICategoryRepository`. From this parameterized constructor, set the private property of type `ICategoryRepository` which will be used to call `GetCategories` from the GET method.

```cs
[Route("api/[controller]")]
[ApiController]
public class CategoryController : Controller
{
    private ICategoryRepository categoryRepository { get; set; }

    // Constructor
    public CategoryController(ICategoryRepository categoryRepository)
    {
        this.categoryRepository = categoryRepository;
    }

    [HttpGet]
    public IActionResult Get()
    {           
        List<Category> categories =  this.categoryRepository.GetCategories();
        return Ok(categories);
    }
}
```
Run the application (`Ctrl`+`F5`) and we will be able to see the result of the GET method of `CategoryController`. Now, even though we haven’t created an instance of `CategoryRepository` which is expected by CategoryController, we are able to call the GET method successfully. The instance of `CategoryRepository` has been resolved dynamically though our Dependency Injection.

#### Output (Response in browser) 

![Object](../Overview/Images/CategoryBrowserOutput.png)

### Middleware

Middleware is software that's assembled into an app pipeline to handle requests and responses. Each component:

* Chooses whether to pass the request to the next component in the pipeline.
* Can perform work before and after the next component in the pipeline.

Request delegates are used to build the request pipeline. The request delegates handle each HTTP request.

Request delegates are configured using `Run`, `Map`, and `Use` extension methods. An individual request delegate can be specified in-line as an anonymous method (called in-line middleware), or it can be defined in a reusable class. These reusable classes and in-line anonymous methods are **middleware**, also called **middleware components**. Each middleware component in the request pipeline is responsible for invoking the next component in the pipeline or short-circuiting the pipeline. When a middleware short-circuits, it's called a `terminal middleware` because it prevents further middleware from processing the request.

#### Create a middleware pipeline with WebApplication

The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other. The following diagram demonstrates the concept. The thread of execution follows the black arrows.

![Object](../Overview/Images/Request-Delegate-Pipeline.png)

Each delegate can perform operations before and after the next delegate. **Exception-handling** delegates should be called early in the pipeline, so they can catch exceptions that occur in later stages of the pipeline.

The simplest possible ASP.NET Core app sets up a single request delegate that handles all requests. This case doesn't include an actual request pipeline. Instead, a single anonymous function is called in response to every HTTP request.

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Run(async context =>
{
    await context.Response.WriteAsync("Hello world!");
});

app.Run();
```
#### Use
Chain multiple request delegates together with `Use`. The next parameter represents the next delegate in the pipeline. You can short-circuit the pipeline by not calling the next parameter. You can typically perform actions both before and after the next delegate, as the following example demonstrates:

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Use(async (context, next) =>
{
    // Do work that can write to the Response.
    await next.Invoke();
    // Do logging or other work that doesn't write to the Response.
});

app.Run(async context =>
{
    await context.Response.WriteAsync("Hello from 2nd delegate.");
});

app.Run();
```
When a delegate doesn't pass a request to the next delegate, it's called `short-circuiting` the request pipeline. Short-circuiting is often desirable because it avoids unnecessary work.

#### Run

* `Run` delegates don't receive a next parameter. 
* The first `Run` delegate is always terminal and terminates the pipeline. Run is a convention. 

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.Use(async (context, next) =>
{
    // Do work that can write to the Response.
    await next.Invoke();
    // Do logging or other work that doesn't write to the Response.
});

app.Run(async context =>
{
    await context.Response.WriteAsync("Hello from 2nd delegate.");
});

app.Run();
```
#### Middleware order

The following diagram shows the complete request processing pipeline for ASP.NET Core MVC and Razor Pages apps. You can see how, in a typical app, existing middlewares are ordered and where custom middlewares are added. You have full control over how to reorder existing middlewares or inject new custom middlewares as necessary for your scenarios.


![Object](../Overview/Images/middleware-pipeline.svg)

The **Endpoint** middleware in the preceding diagram executes the filter pipeline for the corresponding app type—MVC or Razor Pages.

The **Routing** middleware in the preceding diagram is shown following Static Files. This is the order that the project templates implement by explicitly calling `app.UseRouting`. If you don't call `app.UseRouting`, the Routing middleware runs at the beginning of the pipeline by default

![Object](../Overview/Images/mvc-endpoint.svg)

The order that middleware components are added in the Program.cs file defines the order in which the middleware components are invoked on requests and the reverse order for the response. The order is critical for security, performance, and functionality.

The following highlighted code in `Program.cs` adds security-related middleware components in the typical recommended order:

```cs
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(connectionString));
builder.Services.AddDatabaseDeveloperPageExceptionFilter();

builder.Services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
    .AddEntityFrameworkStores<ApplicationDbContext>();
builder.Services.AddRazorPages();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.UseMigrationsEndPoint();
}
else
{
    app.UseExceptionHandler("/Error");    
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseCookiePolicy();
app.UseRouting();
app.UseRequestLocalization();
app.UseCors();
app.UseAuthentication();
app.UseAuthorization();
app.UseSession();
app.UseResponseCompression();
app.UseResponseCaching();
app.MapRazorPages();
app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");

app.Run();
```