# Forms - Angular Application Documentation

## 1. Introduction

### 1.1 Purpose
This documentation outlines the architecture, functionality, and deployment of the Angular application used for form creation and management. The app is designed to handle dynamic forms and includes various interactive components such as rich text editing and mentions.

### 1.2 Scope
This document is intended for:
- Developers working on the codebase.
- QA teams for testing the features.
- DevOps teams responsible for deployment.
- Non-technical stakeholders for understanding the core features.

### 1.3 Document Structure
The document is structured as follows:
1. High-Level Architecture
2. Module Breakdown
3. Functional Flow
4. Testing & QA
5. Deployment & Maintenance
6. References & Resources

---

## 2. High-Level Architecture

### 2.1 Overall Design
This Angular 15 application follows a modular architecture, ensuring scalability and maintainability. The design is based on the Angular CLI structure, and it utilizes several libraries to manage UI components and data.

- **Framework Version:** Angular 15.x
- **Libraries Used:**
  - PrimeNG: For UI components like tables, dropdowns, and form controls.
  - Quill: Rich text editor for text-based form fields.
  - Angular Mentions: For tagging functionality within form fields.
  - JWT Authentication: Auth0 Angular JWT for token-based user authentication.
  - RxJS: For reactive programming and handling asynchronous data streams.

### Project Structure
```
src/
  app/
    components/
    services/
    models/
  environments/
    environment.ts
    environment.prod.ts
  assets/
    images/
    styles/
  index.html
  main.ts
  polyfills.ts
  styles.scss
angular.json
package.json
tsconfig.json
tsconfig.app.json
```

### 2.2 Module Organization
- **AppModule (app.module.ts):** The root module that bootstraps the application.
- **Feature Modules:**
  - `FormsModule`: Manages form-related functionality.
  - `DataMaster`: Manages the master data used in the application.
  - `AuthModule`: Handles authentication logic using JWT.
  - `UserSettings`: This feature is only available to the Admin role user.
- **Shared Modules:**
  - Shared components like headers, footers, and models are imported into other modules.
- **Third-Party Modules:**
  - PrimeNG: UI components library (tables, dropdowns, etc.).
  - Quill: Integrated for rich text editing.
  - Angular Mentions: Provides mention functionality in text fields.

### 2.3 Data Flow & Services
- **HttpClient Services:**
  - `ApiService`: Handles HTTP requests and API interactions.
  - `AuthService`: Manages authentication tokens and user login/logout.
- **Routing:**
The routing is defined in `app-routing.module.ts`, which includes lazy loading for feature modules.
```typescript
const routes: Routes = [
  { path: 'login', component: LoginComponent },
  { path: 'form-builder', component: FormBuilderComponent },
  { path: '', redirectTo: '/form-builder', pathMatch: 'full' }
];
```

---

## 3. Functional Documentation

### 3.1 Key Features / Use Cases
1. **Form Creation:**
   - Allows users to create dynamic forms by adding input fields, dropdowns, and text areas.
   - The form can be saved and reused.
2. **Rich Text Editing:**
   - Quill is used for rich text formatting, including bold, italics, and links.
3. **User Authentication:**
   - Uses Auth0 for handling JWT authentication.
4. **Form Management:**
   - Users can edit, delete, and manage forms.
5. **Mentions:**
   - Users can `@mention` others in the form fields using Angular Mentions.

### 3.2 Detailed Screens / Components
1. **FormBuilderComponent:**
   - Inputs: Form metadata like title, description.
   - Outputs: Emits an event to save the form.
   - Dependencies: FormService for saving form data.
2. **AuthComponent:**
   - Inputs: Username, password.
   - Outputs: Emits authentication status after login.

### 3.3 Interaction Flows
#### User Journey: Creating a Form
1. The user logs in through the `AuthComponent`.
2. The user is redirected to the `FormBuilderComponent`.
3. The user adds fields, configures settings, and clicks "Save".
4. The form data is sent to the API via `ApiService`.

---

## 4. Environment Configuration

### 4.1 Environment Files
The application uses multiple environment configurations, set in `angular.json` and `tsconfig.app.json`.

- **Development (`environment.ts`)**:
  - The API endpoint is set to the local dev server.
- **Production (`environment.prod.ts`)**:
  - Optimized for production with API pointing to the production server.

### 4.2 Build & Deployment
#### Build Configurations
The project supports multiple build configurations:
- **Development:** `ng serve --port 5010`
- **Production:** `ng build --configuration prod`
- **QA Environment:** `ng build --configuration qa`

Deployment scripts in `package.json`:
```json
{
  "scripts": {
    "start": "ng serve --port 5010",
    "build:prod": "ng build --configuration prod",
    "build:qa": "ng build --configuration qa"
  }
}
```

---

## 6. Deployment & Maintenance

### 6.1 Build & Release Process
1. **Local Development:**
   - Run `ng serve` to start the development server.
2. **Continuous Integration:**
   - Use GitHub Actions to trigger builds on new code pushes.
3. **Deployment:**
   - After a successful build, deploy the application to a cloud service (AWS, Azure, etc.) using a CI/CD pipeline.

---

## 7. References & Resources
- [Angular Documentation](https://angular.io/docs)
- [PrimeNG](https://primefaces.org/primeng)
- [Quill](https://quilljs.com/docs/quickstart)
- [Auth0 Angular JWT](https://github.com/auth0/angular2-jwt)

---

## 8. Future Enhancements & Roadmap
1. **Multi-language Support:** Implementing i18n for global audiences.
2. **Form Analytics:** Adding analytics and reporting for form usage and submissions.

![image](https://github.com/user-attachments/assets/60190ffb-b2db-4a66-86b9-e0a3fec7bb89)
