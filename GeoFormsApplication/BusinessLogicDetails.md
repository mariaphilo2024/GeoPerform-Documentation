# Business Logic Details in GeoForms

GeoForms is designed to handle vessel form submissions, validate data, and process it for structured storage in VPS. Below are the key business rules and logic implemented in the system.

## 1. Form Creation & Data Dictionary Rules
### 1.1 Form Structure & Field Definitions
Forms are composed of multiple fields stored in the Data Dictionary.
Each field has:
- **Label** (Frontend name)
- **Name** (Backend reference)
- **Type** (Text, Dropdown, Number, Date, Boolean, etc.)
- **Validation rules** (Required, Min/Max value, Regex, etc.)
- **Default values** (Pre-populated based on vessel/barge type)
- **Field mappings** ensure consistency across all forms.
### 1.2 Conditional Fields & Visibility Rules
Fields can be displayed/hidden based on conditions.
#### Example:
- If **Fuel Type** = "HFO", show **Sulfur Percentage** Field.
### 1.3 Auto-Populated Fields
Certain fields are automatically filled based on vessel data.
#### Example:
- **IMO or Registration Number** is fetched from the database when a vessel/barge name is entered.

## 2. Form Submission & Approval Rules
### 2.1 Submission Workflow
- Forms are filled offline and submitted via email.
- An **Email Reader Service** extracts JSON data from the email attachments.
- The system verifies whether the form matches a valid template.
### 2.2 Approval & Rejection Rules
Submitted forms go through an approval process.
- Only **approved forms** are eligible for ingestion into VPS.
- A form is **rejected** if:
  - Required fields are missing.
  - IMO/Registration number does not exist in VPS.
  - Data format is incorrect.
  - Duplicate entries are detected.
### 2.3 Resubmission & Correction
If a form is rejected:
- An **error message** is logged.
- The user receives an email with the **reason for rejection**.
- The corrected form can be **resubmitted**.

## 3. Data Ingestion & Mapping Rules
### 3.1 Data Extraction & Transformation
- JSON data from GeoForms is transformed into structured VPS tables.
- **Mapping profiles:**
  - `geoforms` → Noon Report, Arrival Report, Departure Report, Bunker Report.
  - `geoformspumplog` → Pump performance data.
### 3.2 Field Mapping & Validations
Fields from JSON are mapped to VPS database fields.
- If a **required field** is missing, an **error is logged**, and the **form is rejected**.
### 3.3 Multi-Table Data Processing
Some data is split across multiple VPS tables

## 4. Scheduled Processing & Automation
### 4.1 Background Processing Rules
A **scheduler** runs every **5 minutes** to process **approved forms**.
Checks for:
- New forms that need ingestion.
- Resubmitted forms requiring reprocessing.
- Ingestion failures that need retries.
### 4.2 Duplicate & Conflict Handling
Before ingestion, the system checks if a similar record already exists.
- If a **duplicate** is found:
  - The **record is skipped** to prevent redundancy.
  - A **log entry** is created for reference.

## 5. Error Handling & Notifications
### 5.1 Logging & Alert Mechanism
All ingestion failures are logged with **error codes**.
### 5.2 Email Alerts & Notifications
- If **ingestion fails**, an **email alert** is sent to admins.
- Uses:
  - **Graph API** (Production)
  - **SMTP** (QA & Testing)
### 5.3 Retry Mechanism
If an ingestion attempt **fails**:
- The form is **queued for retry**.

## 6. Vessel-Specific Rules & Scalability
### 6.1 Vessel-Specific Configurations
Forms can have **different rules** based on **vessel/Barge type**.
### 6.2 Auto-Generated Tables for Vessels/Barges
Some tables **auto-populate** based on vessel/Barge specifications.
  
## Conclusion
The business logic in GeoForms ensures **structured data processing, accurate validation, and seamless ingestion** into VPS. The system enforces strict rules to **maintain data integrity, workflow efficiency, and error handling**. 🚀

