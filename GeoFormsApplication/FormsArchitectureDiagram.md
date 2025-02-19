# GeoForms Architecture

![image](https://github.com/user-attachments/assets/63eb97ca-4882-4074-b95d-e63fb0d93a4a)


## **Frontend (Angular)**
- Handles UI and user interactions.
- Communicates with the backend via API calls.

## **Backend (.NET 7, ABP Framework)**
- Processes business logic.
- Exposes REST APIs for the frontend.
- Manages authentication, authorization, and background jobs.

## **Database (SQL Server 2022)**
- Stores form data, users, permissions, and logs.
- Backend interacts with the database via Entity Framework Core.

## **Flow of Data**
1. The user interacts with the Angular UI.
2. Angular sends requests to the .NET API.
3. .NET processes requests and interacts with SQL Server.
4. SQL Server returns the requested data to .NET.
5. .NET formats the response and sends it back to Angular.
6. Angular updates the UI based on the response.

