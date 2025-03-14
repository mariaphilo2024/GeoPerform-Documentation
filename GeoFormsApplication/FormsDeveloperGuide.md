# Setting Up the Local Development Environment for GeoForms 🚀

## Prerequisites

### Required Software
- **Visual Studio 2022**
- **.NET Core 7+**
- **Git**
- **SQL Server** (for the database)

## Clone the Repository

```sh
git clone https://github.com/Geoservedmcc/geo-forms.git
```

Navigate to the `aspnet-core` folder and open `GeoForms.sln` in Visual Studio.

Refer to **Technology Stack Details** and install the required packages.

## Configure Connection Strings

1. Right-click on the `GeoForms.HttpApi.Host` project and select **Manage User Secrets**.
2. This opens the `secrets.json` file.
3. Replace the content as follows:

```json
{
  "App": {
    "SelfUrl": "https://localhost:44382",
    "ClientUrl": "http://localhost:5010",
    "CorsOrigins": "https://*.GeoForms.com,http://localhost:5010",
    "RedirectAllowedUrls": "http://localhost:5010,https://localhost:44358"
  },
  "MyAppCertificate": {
    "X590": "agyge$56nunasopj"
  },
  "ConnectionStrings": {
    "Default": "Server=tcp:geoforms-qa-dbserver.database.windows.net,1433;Initial Catalog=geoforms-qa-db;Persist Security Info=False;User ID=geoforms-qa-user;Password=T4^x9!g&7P@LqZ#oM2wR;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;"
  },
  "AuthServer": {
    "Authority": "https://localhost:44382",
    "RequireHttpsMetadata": "false",
    "SwaggerClientId": "GeoForms_Swagger",
    "RefreshTokenLifeTime": 20
  },
  "StringEncryption": {
    "DefaultPassPhrase": "oBAy0DZ4kcQFRU22"
  }
}
```

## Apply Database Migrations

1. Set `GeoForms.DbMigrator` as the **Startup Project**.
2. Run the application using:

```sh
Ctrl + F5
```

3. The initial seed data creates the **admin** user (password: `1q2w3E*`).

### Update Database using EF Core

Use the Ef Core `Update-Database` command which applies pending schema migrations during development time.

- Right-click on the `GeoForms.HttpApi.Host` project and select **Set as StartUp Project**.
- Open the **Package Manager Console**, select the `GeoForms.EntityFrameworkCore` project as the **Default Project**, and run the `Update-Database` command:

```sh
Update-Database
```

## Run the Application

Ensure that `GeoForms.HttpApi.Host` is the startup project and run the application. 
A **Swagger UI** will open in your browser.

Use `Ctrl + F5` in Visual Studio for a faster execution without debugging.

### Authorization for Swagger UI
To test authorized APIs, log in manually at `https://localhost:**/Account/Login` using:
- **Username:** `admin`
- **Password:** `1q2w3E*`

## UI Setup - Angular (Web)

### Pre-Requirements
- **Visual Studio Code**
- **npm & yarn**
- **Angular CLI**
-  **Node.js**
  
### Clone the Frontend Repository

```sh
git clone https://github.com/Geoservedmcc/geo-perform-website-primeng-forms.git
```
Refer to **Technology Stack Details** and install the required packages.

### Run the Angular App

1. Open the `angular` folder.
2. Open `GeoForms.code-workspace` in VS Code.
3. Install dependencies:

```sh
npm install
```

4. Start the development server:

```sh
yarn start
```

### Development Server

```sh
ng serve
```

Navigate to `http://localhost:4200/` to see the app in action.

### Code Scaffolding
Generate a new component:

```sh
ng generate component component-name
```

### Build

```sh
ng build --prod
```

### Running Tests

```sh
ng test
```

### Running End-to-End Tests

```sh
ng e2e
```

## Further Help
For more help, use:

```sh
ng help
```

Or check out the [Angular CLI Documentation](https://angular.io/cli).

## Running the Application in Production

Ensure that the `GeoForms.HttpApi.Host` project is the startup project and run it to launch the API.


## Logs & Debugging
- Logs are stored in the `/logs` folder.

## Troubleshooting

### Issue: Unable to connect to the database
**Solution:** Verify its connected to **VPN.**

### Issue: Backend not running
**Solution:** Check `.NET SDK` version and ensure dependencies are installed.

### Issue: Frontend build fails
**Solution:** Run `npm install` and ensure correct version of Angular CLI is installed.

## Conclusion
By following these steps, you should have a fully functional local development environment for GeoForms. 
