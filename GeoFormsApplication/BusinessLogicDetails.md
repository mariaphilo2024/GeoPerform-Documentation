# Business Logic Details in GeoForms Application

GeoForms enforces several critical business rules to ensure data accuracy, regulatory compliance, and seamless integration with VPS and external platforms like Veslink. Below are the key business logic implementations:

## 1. Form Creation & Assignment Rules
- Forms must be assigned to specific vessels or barges based on IMO number or registration number.
- Each vessel or barge can only have one active form version per report type (e.g., Noon Report, Bunker Report).
- Forms can be copied between principals (operators) but must be revalidated before use.

## 2. Submission & Data Validation Rules
- Forms must be submitted in the latest active version; older versions are flagged for review.
- Each form has predefined mandatory fields (e.g., IMO number, report time, fuel type).
- If mandatory fields are missing or incorrect, the form is rejected and requires resubmission.
- Encrypted email submissions ensure data integrity; only decrypted data is stored.

## 3. Approval & Review Process
- Only approved forms are ingested into VPS; rejected forms require correction.
- Analysts can edit submitted data before approval, but changes are logged for auditing.
- Once approved, the form cannot be edited directly—instead, it must be opened for resubmission.

## 4. Version Control & Status Management
- If a vessel submits an older form version, it is listed but cannot be approved until the latest version is activated.
- Forms go through the following statuses:
  - **Pending** – Awaiting analyst review.
  - **Approved** – Data verified and sent to VPS.
  - **Rejected** – Errors found, requiring vessel resubmission.
  - **Resubmitted** – Vessel corrected data and resubmitted.
  - **Open for Resubmit** – Previously approved form is being modified.

## 5. Automated Data Ingestion to VPS
- Only forms with a valid IMO number and correct mapping fields are ingested.
- Approved data is transferred to VPS within 10 minutes of approval.
- VPS automatically overwrites previous records if a new submission for the same report type and date exists.
- If ingestion fails due to missing IMO or incorrect mapping, an email alert is triggered.

## 6. Duplicate Submission Handling
- If a vessel sends duplicate reports for the same date and report type, only the latest approved version is retained.
- If a previous report needs correction, it must be opened for resubmission instead of submitting a duplicate.

## 7. Bot Automation for Veslink Integration
- If a vessel is required to submit reports to both GeoForms and Veslink, a bot automates this process.
- The bot extracts approved data from GeoForms and maps it to Veslink’s format.
- If the bot fails due to incorrect mapping, an email alert is sent for manual intervention.

## 8. Data Dictionary & Field Mapping Rules
- Each form field has a unique JSON key, ensuring standardized data mapping.
- Certain fields (e.g., fuel type, port name) must match values from the Master Data tables.
- Conditional fields (e.g., cargo type appearing only if the vessel is carrying cargo) follow visibility and calculation rules.

## 9. Report Generation & Audit Trail
- Approved forms are converted into structured HTML reports (e.g., Noon Reports, Arrival Reports).
- All user actions (form submissions, approvals, rejections, modifications) are logged in an audit trail.

## 10. Error Handling & Alerts
- If a vessel submits an invalid form, it is immediately flagged and an email alert is sent.
- If ingestion to VPS fails, the system retries three times before sending an alert.
- Analysts receive automated notifications for pending reviews.

## Conclusion
These business rules ensure that GeoForms maintains data accuracy, regulatory compliance, and seamless vessel reporting while automating processes for efficiency.

