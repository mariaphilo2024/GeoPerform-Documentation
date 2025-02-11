# GeoForms Application

## 1. Introduction
The GeoForms Application is designed to manage vessel-related data submissions, approvals, and ingestion into the VPS system. It allows users to create, approve, and track form submissions while ensuring accurate data flow. Additionally, automated processes, including bot-based submissions, enhance efficiency by reducing manual interventions.

There are two types of forms:
- **Veslink Forms:** Received via an external API.
- **GeoServe Forms:** Retrieved from the GeoForms Application.

## 2. GeoForms Application
The GeoForms Application is responsible for:
- Creating and managing vessel-and barge-specific forms.
- Facilitating form submissions from vessel and barge crews.
- Processing and storing submitted data securely.
- Integrating approved data with the VPS system.
- Automating data sharing with external systems like Veslink Forms.

### Main Sections:
- **Forms:** Includes Form Library, Template Library, Data Dictionary, and Submitted Forms.
- **Data Master:** Holds various master data.
- **User Settings:** Defines permissions and roles.

## 3. Data Dictionary (Field Creation)
Fields represent input elements within forms (e.g., Vessel Name, IMO Number, Barge Name, Registration Number). Each field includes:
- **Label:** Frontend display name.
- **Name:** Backend reference.
- **Type:** Text, dropdown, checkbox, etc.
- **Validation Rules:** Mandatory fields, unique constraints.

Certain fields, like "Report Time," may have different display names while retaining the same backend reference for consistency.

## 4. Form Library (Form Creation & Design)
- Forms are designed using a Form Designer by adding fields and sections.
- A new feature allows users to choose between creating a **Vessel Form** (IMO number) or a **Barge Form** (Registration number).
- Sections organize fields (e.g., General Details, Event Details).
- Fields can have conditional visibility, calculations, and warnings.
- Forms can include tables that allow multiple entries.
- Designed forms are previewed as HTML reports.

## 5. Template Library (Reusing Form Designs)
- Predefined form templates can be used to quickly create forms for multiple vessels.
- Instead of designing a new form from scratch, an existing template can be imported and modified.

## 6. Scaling & Cloning Forms
### Principle-Specific Form Creation:
- Within the Form section, there’s a **Principles** sub-tab.
- When creating a form for a vessel, all associated principles are listed.
- Users can design unique forms tailored to each principal's needs.

### Copying Form Templates Between Principles:
- To replicate a form template from one principal to another:
  - Select the desired principle.
  - Use the **Copy From** option to choose the source principal's form.
  - The form template is duplicated, allowing for further modifications as needed.

### Copying Data Between Principles:
- In the **View** section, there's a feature to copy data entries between principals.
- If data is entered under one principle, it can be copied to another using the **Copy** option.

## 7. Report Generation
Forms are converted into HTML reports, including:
- Noon Report
- Arrival Reports
- Departure Reports
- Bunker Reports
- Pump Log Reports

Certain reports include auto-calculations and validations for accuracy.

## 8. Form Creation and Assignment to Vessels
- A form is created in the GeoForms application.
- Each form is designed for a specific vessel or barge and is saved as an **HTML file**.
- The vessel or barge information is embedded in the HTML file, meaning a separate file is generated for each vessel.

## 9. Form Submission by Vessels and Barges
- The HTML file is emailed to the respective vessel or barge.
- The vessel crew downloads the HTML file, fills, and submits it.
- After submission, a popup appears showing:
  - **To:** and **CC:** email addresses.
  - Auto-generated subject line.
  - Email body (with form details in both plain text and encrypted format).
  - An "Open Mail" button (which might not work if the email body is too long, so a **Copy** option is also available).
- The crew copies the email content and manually sends it.

## 10. Data Processing in GeoForms Backend
### Email Reader Function:
- The backend service reads the email content.
- Only the encrypted data is used for system processing to prevent tampering.
- The decrypted data is stored as a JSON file in the GeoForms database.

### JSON Data Structure:
- Data is stored in key-value pairs (e.g., `"report_name": "Noon Report", "voyage_number": "123"`).
- Every field has a unique JSON key.

## 11. Form Review & Approval Process
- Analysts log in to review submitted forms.
- Forms are categorized by status:
  1. **Pending** – Form received but not yet reviewed.
  2. **Approved** – Data is correct and accepted.
  3. **Rejected** – Data is incorrect, vessel/barge must resubmit.
  4. **Resubmitted** – Analyst requested corrections; crew sent a revised version.
  5. **Open for Resubmit** – Previously approved form is under revision.
- Analysts use filters to find pending forms and process them.

## 12. Form Versions & Status Management
- Only the latest active form version can be approved or rejected.
- If a vessel/barge submits an older version, it still gets listed, but analysts cannot approve/reject it until the latest version is activated.
- Some vessels and barges may need to use older versions due to operational reasons.

## 13. Editing and Resubmission
- Analysts can edit a form before approval.
- If changes are needed after approval:
  - They open it for resubmission.
  - A new entry is created to track modifications.
  - This ensures that original submissions and modifications are both recorded.

## 14. Form Approval & Resubmission Process
- Once a form is approved in GeoForms, it is automatically ingested into the VPS system within **10 minutes**.
- VPS stores the latest approved data and overwrites older versions for the same report type and date.
- If incorrect data is found post-approval, the form is resubmitted and re-approved.
- VPS overwrites the latest approved data if a duplicate report exists.
- If an issue is found pre-approval, the form is rejected, requiring a new submission.
- Duplicate submissions from vessels are handled by keeping only the most recent approved version.

## 15. Bot Automation for Parallel Submission
- Some vessels and barges need to send reports to both **GeoForms** and **Veslink Forms**.
- Instead of manually filling both systems, a **Bot** extracts data from GeoForms and auto-fills Veslink Forms.
- The bot maps JSON keys to ensure correct data transfer.
- This ensures ingestion into both systems, reducing manual effort for vessel crews.

## 16. Data Management & Mapping (Principle-Based Mapping)
- Master tables store data on ports, suppliers, cargo grades, and principles.
- Different vessel principles (e.g., Exxon, Pacific Basin) require specific data.
- Instead of separate tables per principle, a **mapping table** links ports/cargo types to principles.

## Conclusion
GeoForms streamlines vessel and barge reporting, prevents errors, integrates with VPS, and automates external submissions.
