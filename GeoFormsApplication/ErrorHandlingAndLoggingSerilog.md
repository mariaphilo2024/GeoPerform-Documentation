#  Mechanisms for Exception Handling and Logging using Serilog 🚨

## 1. Install Required NuGet Packages

Run the following commands in **Package Manager Console** or **.NET CLI**:

```sh
Install-Package Serilog.AspNetCore
Install-Package Serilog.Sinks.Console
Install-Package Serilog.Sinks.File
Install-Package Serilog.Sinks.MSSqlServer (if Enable Logging to SQL Server)
```

These packages provide Serilog logging capabilities and different output destinations (sinks).

---

## 2. Configure Serilog in `Program.cs`

Modify the `Program.cs` file to configure Serilog globally.

```csharp
using System;
using Serilog;
using Serilog.Events;
using Microsoft.AspNetCore.Builder;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args)
    {
        // Step 1: Configure Serilog
        Log.Logger = new LoggerConfiguration()
#if DEBUG
            .MinimumLevel.Debug() // Debug level for development
#else
            .MinimumLevel.Information() // Information level for production
#endif
            .MinimumLevel.Override("Microsoft", LogEventLevel.Information) // Suppresses Microsoft logs below Information
            .MinimumLevel.Override("Microsoft.EntityFrameworkCore", LogEventLevel.Warning) // Suppresses EF Core logs below Warning
            .Enrich.FromLogContext()
            .WriteTo.Console() // Log to console
            .WriteTo.File("Logs/logs.txt", rollingInterval: RollingInterval.Day, retainedFileCountLimit: 30) // Log to a file
            .CreateLogger();

        try
        {
            Log.Information("Starting application...");
            
            var builder = WebApplication.CreateBuilder(args);
            builder.Host.UseSerilog(); // Step 2: Add Serilog to the application

            var app = builder.Build();
            app.Run();
        }
        catch (Exception ex)
        {
            Log.Fatal(ex, "Application terminated unexpectedly!");
        }
        finally
        {
            Log.CloseAndFlush(); // Step 3: Ensure logs are flushed on exit
        }
    }
}
```

---

## 3. Inject Serilog into Services or Controllers

You can inject `ILogger<T>` in services, repositories, and controllers.

### **Example in a Service Class**

```csharp
using Microsoft.Extensions.Logging;

public class MyService
{
    private readonly ILogger<MyService> _logger;

    public MyService(ILogger<MyService> logger)
    {
        _logger = logger;
    }

    public void ProcessData()
    {
        try
        {
            _logger.LogInformation("Processing started...");
            // Business logic here
            _logger.LogInformation("Processing completed successfully.");
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "An error occurred while processing data.");
        }
    }
}
```

---

## 4. Configure Serilog via `appsettings.json`

Another way to configure Serilog is using the `appsettings.json` file.

### **Add Serilog Configuration in `appsettings.json`**

```json
{
  "Serilog": {
    "Using": ["Serilog.Sinks.Console", "Serilog.Sinks.File"],
    "MinimumLevel": {
      "Default": "Information",
      "Override": {
        "Microsoft": "Warning",
        "Microsoft.Hosting.Lifetime": "Information"
      }
    },
    "WriteTo": [
      { "Name": "Console" },
      {
        "Name": "File",
        "Args": { "path": "Logs/logs.txt", "rollingInterval": "Day" }
      }
    ],
    "Enrich": ["FromLogContext"]
  }
}
```

### **Modify `Program.cs` to Read Configuration**

```csharp
var builder = WebApplication.CreateBuilder(args);
builder.Host.UseSerilog((context, configuration) =>
    configuration.ReadFrom.Configuration(context.Configuration));
```

---

## 5. Enable Logging to SQL Server (Optional)

To log messages to a **SQL Server** database:

### **Install the SQL Server Sink Package**

```sh
Install-Package Serilog.Sinks.MSSqlServer
```

### **Modify Serilog Configuration**

```csharp
Log.Logger = new LoggerConfiguration()
    .WriteTo.MSSqlServer(
        connectionString: "Server=myServer;Database=LogsDB;User Id=myUser;Password=myPassword;",
        sinkOptions: new Serilog.Sinks.MSSqlServer.MSSqlServerSinkOptions
        {
            TableName = "LogTable",
            AutoCreateSqlTable = true
        })
    .CreateLogger();
```

---

## 6. Implement Global Exception Handling with Serilog

To catch unhandled exceptions and log them using Serilog, create a middleware.

### **Exception Handling Middleware**

```csharp
using System;
using System.Net;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Serilog;

public class ExceptionHandlingMiddleware
{
    private readonly RequestDelegate _next;

    public ExceptionHandlingMiddleware(RequestDelegate next)
    {
        _next = next;
    }

    public async Task Invoke(HttpContext context)
    {
        try
        {
            await _next(context);
        }
        catch (Exception ex)
        {
            Log.Error(ex, "Unhandled exception occurred.");
            context.Response.StatusCode = (int)HttpStatusCode.InternalServerError;
            await context.Response.WriteAsync("An unexpected error occurred.");
        }
    }
}
```

### **Register Middleware in `Program.cs`**

```csharp
var app = builder.Build();
app.UseMiddleware<ExceptionHandlingMiddleware>(); // Add middleware
app.Run();
```

---

## 7. Logging Levels

Serilog provides different log levels for filtering logs:

- `Log.Debug("Debug message");` – Detailed information, typically useful for debugging.
- `Log.Information("Informational message");` – General application flow.
- `Log.Warning("Warning message");` – Something unexpected happened, but the application continues.
- `Log.Error("Error message");` – A failure that needs attention.
- `Log.Fatal("Fatal error message");` – Critical issue causing application crash.

---

## Conclusion

By following these steps, we can effectively integrate **Serilog** in .NET application, ensuring structured and efficient logging for debugging, monitoring, and error tracking.


