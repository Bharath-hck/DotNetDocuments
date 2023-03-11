# ASP.NET Core Blazor Web APP

## Practical Exercise I

In this exercise, we will build a simple counter app with Blazor

### Create your app

1. Start **Visual Studio** and select **Create a new project**.
2. In the **Create a new project** window, type **Blazor** on the search box and hit **Enter**.
3. Select the **Blazor Server App** template and select Next.
4. In the Configure your new project window, enter **BlazorApp** as the project name and select **Next**.
5. In the Additional information window, select **.NET 7.0 (Standard Term Support)** in the Framework drop-down if not already selected and click the **Create** button.

Your project is created and loaded in Visual Studio. Take a look at the contents of your project using **Solution Explorer**.

### Run your app

1. Press <kbd>Ctrl</kbd> + <kbd>F5</kbd> to run the app.
2. The displayed page is defined by the `Index.razor` file located inside the `Pages` directory. This is what its contents look like:

```HTML+RAZOR
@page "/"

<PageTitle>Index</PageTitle>

<h1>Hello, world!</h1>

Welcome to your new app.

<SurveyPrompt Title="How is Blazor working for you?" />
```
![Image](/ASP.NET%20Core/ASP.NET%20Core%20Blazor%20Web%20App/Images/screenshot-blazor-tutorial-run.png)

### Try the counter

1. Navigate to the **Counter page** by clicking the `Counter` tab in the sidebar on the left
2. Select the <kbd>Click me</kbd> button to increment the count without a page refresh
3. Incrementing a counter in a webpage normally requires writing `JavaScript`, but with **Blazor** you can use `C#`.
4. You can find the implementation of the `Counter` component at `Counter.razor` file located inside the `Pages` directory.

```HTML+RAZOR
@page "/counter"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}

```

![Image](/ASP.NET%20Core/ASP.NET%20Core%20Blazor%20Web%20App/Images/screenshot-blazor-tutorial-try.png)

A request for `/counter` in the browser, as specified by the `@page` directive at the top, causes the `Counter` component to render its content.

Each time the **Click me** button is selected:

* The `onclick` event is fired.
* The `IncrementCount` method is called.
* The `currentCount` is incremented.
* The `component` is rendered to show the updated count.


### Add a component

1. Each of the `.razor` files defines a UI component that can be reused.
2. Open the `Index.razor` file in Visual Studio.
3. The `Index.razor` file already exists, and it was created when you created the project. 
4. It's located in the `Pages` folder inside the `BlazorApp` directory that was created earlier.
5. Add a `Counter` component to the app's homepage by adding a `<Counter />` element at the end of the `Index.razor` file.

```HTML+RAZOR
@page "/"

<PageTitle>Index</PageTitle>

<h1>Hello, world!</h1>

Welcome to your new app.

<SurveyPrompt Title="How is Blazor working for you?" />

<Counter />
```

6. Click the **Hot Reload** button to apply the change to the running app
7. The **Counter** component will then show up on the home page.

![Image](/ASP.NET%20Core/ASP.NET%20Core%20Blazor%20Web%20App/Images/screenshot-blazor-tutorial-add.png)

### Modify a component

1. Component parameters are specified using **attributes** or child content, which allow you to set properties on the child component.
2. Define a **parameter** on the **Counter** component for specifying how much it increments with every button click:
   * Add a public property for `IncrementAmount` with a `[Parameter]` attribute.
   * Change the `IncrementCount` method to use the `IncrementAmount` when incrementing the value of `currentCount`.

The following code shows how to achieve that. The highlighted lines show the changes.

```HTML+RAZOR
@page "/counter"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    private void IncrementCount()
    {
        currentCount += IncrementAmount;
    }
}

```

In `Index.razor`, update the `<Counter>` element to add an `IncrementAmount` attribute that changes the increment amount to ten as shown by the highlighted line in the following code:

```HTML+RAZOR
@page "/"

<h1>Hello, world!</h1>

Welcome to your new app.

<SurveyPrompt Title="How is Blazor working for you?" />

<Counter IncrementAmount="10" />

```

* Apply the change to the app by clicking the **Hot Reload** button. 
* The **Index** component now has its own `counter` that increments by **ten** each time the **Click me** button is selected, as shown in the following image. 
* The **Counter** component (`Counter.razor`) at `/counter` continues to increment by **one**.

![Image](/ASP.NET%20Core/ASP.NET%20Core%20Blazor%20Web%20App/Images/screenshot-blazor-tutorial-modify.png)

### Congratulations, you've built and run your first Blazor app!

## Practical Exercise II

### In this exercise, we will learn how to build and modify a Blazor app

* Create a todo list Blazor app project
* Modify Razor components
* Use event handling and data binding in components
* Use routing in a Blazor app

At the end of this tutorial, you'll have a working todo list app.

### Create a Blazor app

1. Start **Visual Studio** and select **Create a new project**.
2. In the **Create a new project** window, type **Blazor** on the search box and hit **Enter**.
3. Select the **Blazor Server App** template and select Next.
4. In the Configure your new project window, enter **TodoList** as the project name and select **Next**.
5. In the Additional information window, select **.NET 7.0 (Standard Term Support)** in the Framework drop-down if not already selected and click the **Create** button.

Your project is created and loaded in Visual Studio. Take a look at the contents of your project using **Solution Explorer**.

### Build a todo list Blazor app

1. Add a new `Todo` Razor component to the app under `Pages` folder
2. Open the `Todo` component in any file editor and add an `@page` Razor directive to the top of the file with a relative URL of `/todo`.

**Pages/Todo.razor:**

```HTML+RAZOR
@page "/todo"

<PageTitle>Todo</PageTitle>

<h1>Todo</h1>

@code {

}
```
3. Save the `Pages/Todo.razor` file.
4. Add the `Todo` component to the **navigation bar**.
5. In the navigation element content of the `NavMenu` component, add the following <div> element for the `Todo` component.

In **Shared/NavMenu.razor**:

```HTML
<div class="nav-item px-3">
    <NavLink class="nav-link" href="todo">
        <span class="oi oi-list-rich" aria-hidden="true"></span> Todo
    </NavLink>
</div>
```
6. Save the `Shared/NavMenu.razor` file.
7. **Build** and **Run** the app
8. Visit the new Todo page by selecting the **Todo** link in the app's navigation bar
9. This loads the page  at `/todo`
10. Add a `TodoItem.cs` file to the root of the project

`TodoItem.cs:`

```cs
public class TodoItem
{
    public string? Title { get; set; }
    public bool IsDone { get; set; }
}
```
11. Return to the **Todo** component and perform the following tasks:

    * Add a field for the todo items in the `@code` block. The **Todo** component uses this field to maintain the state of the todo list.
    * Add unordered list markup and a foreach loop to render each **todo** item as a list item (`<li>`)
  
`Pages/Todo.razor:`

```HTML+RAZOR
@page "/todo"

<PageTitle>Todo</PageTitle>

<h1>Todo</h1>

<ul>
    @foreach (var todo in todos)
    {
        <li>@todo.Title</li>
    }
</ul>

@code {
    private List<TodoItem> todos = new();
}
```
12. The app requires UI elements for adding **todo** items to the list. 
13. Add a text input (`<input>`) and a button (`<button>`) below the unordered list (`<ul>...</ul>`):

```HTML+RAZOR
@page "/todo"

<PageTitle>Todo</PageTitle>

<h1>Todo</h1>

<ul>
    @foreach (var todo in todos)
    {
        <li>@todo.Title</li>
    }
</ul>

<input placeholder="Something todo" />
<button>Add todo</button>

@code {
    private List<TodoItem> todos = new();
}
```
14. To get the title of the new todo item, add a `newTodo` string field at the top of the `@code` block:

```cs
private string? newTodo;
```
15. Modify the text `<input>` element to bind newTodo with the `@bind` attribute:

```HTML+RAZOR
<input placeholder="Something todo" @bind="newTodo" />
```

16. Update the `AddTodo` method to add the `TodoItem` with the specified `title` to the list. Clear the value of the text input by setting `newTodo` to an empty string:

```HTML+RAZOR
@page "/todo"

<PageTitle>Todo</PageTitle>

<h1>Todo</h1>

<ul>
    @foreach (var todo in todos)
    {
        <li>@todo.Title</li>
    }
</ul>

<input placeholder="Something todo" @bind="newTodo" />
<button @onclick="AddTodo">Add todo</button>

@code {
    private List<TodoItem> todos = new();
    private string? newTodo;

    private void AddTodo()
    {
        if (!string.IsNullOrWhiteSpace(newTodo))
        {
            todos.Add(new TodoItem { Title = newTodo });
            newTodo = string.Empty;
        }
    }
}
```
17. Save the `Pages/Todo.razor` file.
18. The title text for each `todo` item can be made editable, and a checkbox can help the user keep track of completed items. Add a checkbox input for each todo item and bind its value to the IsDone property. Change `@todo.Title` to an `<input>` element bound to todo.Title with `@bind`:

```HTML+RAZOR
<ul>
    @foreach (var todo in todos)
    {
        <li>
            <input type="checkbox" @bind="todo.IsDone" />
            <input @bind="todo.Title" />
        </li>
    }
</ul>
```

19. Update the `<h1>` header to show a count of the number of todo items that aren't complete

```HTML+RAZOR
<h1>Todo (@todos.Count(todo => !todo.IsDone))</h1>
```

20. The completed **Todo** component (`Pages/Todo.razor`) looks like below:

```HTML+RAZOR
@page "/todo"

<PageTitle>Todo</PageTitle>

<h1>Todo (@todos.Count(todo => !todo.IsDone))</h1>

<ul>
    @foreach (var todo in todos)
    {
        <li>
            <input type="checkbox" @bind="todo.IsDone" />
            <input @bind="todo.Title" />
        </li>
    }
</ul>

<input placeholder="Something todo" @bind="newTodo" />
<button @onclick="AddTodo">Add todo</button>

@code {
    private List<TodoItem> todos = new();
    private string? newTodo;

    private void AddTodo()
    {
        if (!string.IsNullOrWhiteSpace(newTodo))
        {
            todos.Add(new TodoItem { Title = newTodo });
            newTodo = string.Empty;
        }
    }
}
```
21. Save the `Pages/Todo.razor` file
22. **Build** and **Run** the app
23. Test the ToDo app by adding items and making some of the items as complete
24. When finished, shut down the app in the command shell (<kbd>Ctrl</kbd> + <kbd>C</kbd>)