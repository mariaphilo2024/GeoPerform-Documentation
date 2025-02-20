## **Serilog Integration in GeoForms Backend (.NET)**

### **1. Installing Serilog Packages**
To integrate Serilog, install the following NuGet packages:
```sh
Install-Package Serilog.AspNetCore
Install-Package Serilog.Sinks.Console
Install-Package Serilog.Sinks.File
Install-Package Serilog.Sinks.MSSqlServer
```

### **2. Configuring Serilog in `Program.cs`**
Modify `Program.cs` to configure Serilog for logging.

#### **Updated `Program.cs` for Serilog:**
```csharp
using System;
using System.Threading.Tasks;
using Serilog;
using Serilog.Events;
using Microsoft.AspNetCore.Builder;
using Microsoft.Extensions.Hosting;

public class Program
{
    public async static Task<int> Main(string[] args)
    {
        // Configure Serilog for logging
        Log.Logger = new LoggerConfiguration()
#if DEBUG
            .MinimumLevel.Debug() // Set log level to Debug in development mode
#else
            .MinimumLevel.Information() // Set log level to Information in production
#endif
            .MinimumLevel.Override("Microsoft", LogEventLevel.Information)
            .MinimumLevel.Override("Microsoft.EntityFrameworkCore", LogEventLevel.Warning)
            .Enrich.FromLogContext()
            .WriteTo.Async(c => c.File("Logs/logs.txt", rollingInterval: RollingInterval.Day, retainedFileCountLimit: 20)) // Log to file
#if DEBUG
            .WriteTo.Async(c => c.Console()) // Log to console in development
#endif
            .CreateLogger();

        try
        {
            Log.Information("Starting GeoForms.HttpApi.Host.");
            var builder = WebApplication.CreateBuilder(args);
            builder.Host.UseSerilog(); // Integrate Serilog with application
            var app = builder.Build();
            await app.RunAsync();
            return 0;
        }
        catch (Exception ex)
        {
            Log.Fatal(ex, "Host terminated unexpectedly!"); // Log fatal errors
            return 1;
        }
        finally
        {
            Log.CloseAndFlush(); // Ensure logs are flushed before exit
        }
    }
}
```

### **3. Using Serilog in a Class**
To log information within a class, inject `ILogger<T>`.

#### **Example in a Service Class:**
```csharp
using Microsoft.Extensions.Logging;

public class SampleService
{
    private readonly ILogger<SampleService> _logger;

    public SampleService(ILogger<SampleService> logger)
    {
        _logger = logger;
    }

    public void ProcessData()
    {
        try
        {
            _logger.LogInformation("Processing data started.");
            // Business logic here
            _logger.LogInformation("Processing data completed successfully.");
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "An error occurred while processing data.");
        }
    }
}
```

### **4. Logging Levels in Serilog**
Serilog provides different logging levels:
- `Log.Debug("Debug message");`
- `Log.Information("Informational message");`
- `Log.Warning("Warning message");`
- `Log.Error("Error message");`
- `Log.Fatal("Fatal error message");`

### **5. Logging to SQL Server**
Example configuration for logging to SQL Server:
```csharp
Log.Logger = new LoggerConfiguration()
    .WriteTo.MSSqlServer("Server=yourServer;Database=LogsDB;User Id=yourUser;Password=yourPassword;",
        new Serilog.Sinks.MSSqlServer.ColumnOptions())
    .CreateLogger();
```
Serilog is a powerful, flexible logging library for .NET applications. It supports structured logging,
multiple sinks (e.g., file, console, database), and asynchronous logging for improved performance.
By integrating Serilog, developers can efficiently monitor application behavior and troubleshoot issues effectively.

