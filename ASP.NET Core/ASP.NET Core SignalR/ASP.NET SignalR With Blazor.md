# ASP.NET Core SignalR with Blazor

## Practical Exercise

In this exercise we will learn the basics of building a real-time app using SignalR with Blazor.

* Create a Blazor project
* Add the SignalR client library
* Add a SignalR hub
* Add SignalR services and an endpoint for the SignalR hub
* Add Razor component code for chat

At the end of this tutorial, you'll have a working chat app.

### Create a Blazor Server app

1. Create a new project.
1. Select the **Blazor Server App** template. Select **Next**.
2. Type `BlazorServerSignalRApp` in the **Project name** field. Confirm the **Location** entry is correct or provide a location for the project. Select **Next**.
3. Select **Create**.

### Add the SignalR client library

1. In **Solution Explorer**, right-click the `BlazorServerSignalRApp` project and select **Manage NuGet Packages**.
2. In the **Manage NuGet Packages** dialog, confirm that the **Package source** is set to `nuget.org`.
3. With **Browse** selected, type `Microsoft.AspNetCore.SignalR.Client` in the search box.
4. In the search results, select the **Microsoft.AspNetCore.SignalR.Client** package. Set the version to match the shared framework of the app. Select **Install**.
5. If the **Preview Changes** dialog appears, select **OK**.
6. If the **License Acceptance** dialog appears, select **I Accept** if you agree with the license terms.

### Add a SignalR hub

Create a `Hubs` (plural) folder and add the following `ChatHub` class (`Hubs/ChatHub.cs`):

```cs
using Microsoft.AspNetCore.SignalR;

namespace BlazorServerSignalRApp.Server.Hubs;

public class ChatHub : Hub
{
    public async Task SendMessage(string user, string message)
    {
        await Clients.All.SendAsync("ReceiveMessage", user, message);
    }
}
```
### Add services and an endpoint for the SignalR hub

1. Open the `Program.cs` file.
2. Add the namespaces for `Microsoft.AspNetCore.ResponseCompression` and the `ChatHub` class to the top of the file:

```cs
using Microsoft.AspNetCore.ResponseCompression;
using BlazorServerSignalRApp.Server.Hubs;
```
3. Add Response Compression Middleware services to `Program.cs`:

```cs
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();
builder.Services.AddSingleton<WeatherForecastService>();
builder.Services.AddResponseCompression(opts =>
{
    opts.MimeTypes = ResponseCompressionDefaults.MimeTypes.Concat(
        new[] { "application/octet-stream" });
});
```

4. In `Program.cs`:
   * Use Response Compression Middleware at the top of the processing pipeline's configuration.
   * Between the endpoints for mapping the Blazor hub and the client-side fallback, add an endpoint for the hub.

```cs
app.UseResponseCompression();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();

app.UseStaticFiles();

app.UseRouting();

app.MapBlazorHub();
app.MapHub<ChatHub>("/chathub");
app.MapFallbackToPage("/_Host");

app.Run();
```

### Add Razor component code for chat

1. Open the `Pages/Index.razor` file.
2. Replace the markup with the following code:

```HTML+RAZOR
@page "/"
@using Microsoft.AspNetCore.SignalR.Client
@inject NavigationManager Navigation
@implements IAsyncDisposable

<PageTitle>Index</PageTitle>

<div class="form-group">
    <label>
        User:
        <input @bind="userInput" />
    </label>
</div>
<div class="form-group">
    <label>
        Message:
        <input @bind="messageInput" size="50" />
    </label>
</div>
<button @onclick="Send" disabled="@(!IsConnected)">Send</button>

<hr>

<ul id="messagesList">
    @foreach (var message in messages)
    {
        <li>@message</li>
    }
</ul>

@code {
    private HubConnection? hubConnection;
    private List<string> messages = new List<string>();
    private string? userInput;
    private string? messageInput;

    protected override async Task OnInitializedAsync()
    {
        hubConnection = new HubConnectionBuilder()
            .WithUrl(Navigation.ToAbsoluteUri("/chathub"))
            .Build();

        hubConnection.On<string, string>("ReceiveMessage", (user, message) =>
        {
            var encodedMsg = $"{user}: {message}";
            messages.Add(encodedMsg);
            InvokeAsync(StateHasChanged);
        });

        await hubConnection.StartAsync();
    }

    private async Task Send()
    {
        if (hubConnection is not null)
            {
                await hubConnection.SendAsync("SendMessage", userInput, messageInput);
            }
    }

    public bool IsConnected =>
        hubConnection?.State == HubConnectionState.Connected;

    public async ValueTask DisposeAsync()
    {
        if (hubConnection is not null)
        {
            await hubConnection.DisposeAsync();
        }
    }
}
```

### Run the app

1. Press <kbd>Ctrl</kbd> + <kbd>F5</kbd> (Windows) to run the app without debugging.
2. Copy the URL from the address bar, open another browser instance or tab, and paste the URL in the address bar.
3. Choose either browser, enter a name and message, and select the button to send the message. The name and message are displayed on both pages instantly:
