# Developer Guide: Setting Up the Local Development Environment for GeoForms

## Prerequisites

### Required Software
- **Visual Studio 2022**
- **.NET Core 7+**
- **Git**
- **Node.js & npm**
- **Angular CLI**
- **SQL Server** (for the database)

## Clone the Repository

```sh
git clone https://github.com/Geoservedmcc/geo-forms.git
```

Navigate to the `aspnet-core` folder and open `GeoForms.sln` in Visual Studio.

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

### Alternative: Update Database using EF Core

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

### Clone the Frontend Repository

```sh
git clone https://github.com/Geoservedmcc/geo-perform-website-primeng-forms.git
```

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
