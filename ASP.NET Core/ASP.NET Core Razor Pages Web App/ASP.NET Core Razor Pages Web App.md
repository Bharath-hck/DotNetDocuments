# ASP.NET Core Razor Pages Web App

In this chapter, we will learn how to build an ASP.NET Core Razor Pages Web App

### Razor Pages

* Razor Pages is a new aspect of ASP.NET Core MVC introduced in `ASP.NET Core 2.0`
* It offers a "**page-based**" approach for building server-side rendered apps in ASP.NET Core
* It can coexist with "traditional" MVC or Web API controllers

### The Razor Page Model

Razor Pages are built on top of MVC, but they use a slightly different paradigm than the MVC pattern. With MVC the controller typically provides the logic and behavior for an action, ultimately producing a view model which contains data that is used to render the view. Razor Pages takes a slightly different approach, by using a **Page Model**.

Compared to MVC, the page model acts as both a mini-controller and the view model for the view. It's responsible for both the behavior of the page and for exposing the data used to generate the view.

In technical terms a Razor Page is very similar to a Razor view, except it has an @page directive at the top of the file:

```html
@page

<div>The time is @DateTime.Now</div>
```

As with Razor views, any HTML in the Razor page is rendered to the client, and you can use the `@` symbol to render C# values or use C# control structures. See the documentation for a complete reference guide to Razor syntax.

Adding `@page` is all that's required to expose your page, but this page doesn't use a page model yet. More typically you create a class that derives from `PageModel` and associate it with your `cshtml` file. You can include your `PageModel` and Razor view in the same `cshtml` file if you wish, but best practice is to keep the `PageModel` in a "**code-behind**" file, and only include presentational data in the `cshtml` file. By convention, if your razor page is called `MyPage.cshtml`, the code-behind file should be named `MyPage.cshtml.cs`: