# Data Flow Diagram for GeoForms Application

- ![image](https://github.com/user-attachments/assets/dbd91984-f49a-4c50-a6ad-9ae0eae8fcf0)

## 1. External Entities
- **Vessel/Barge Crew**: Submits completed forms.
- **Analysts**: Review and approve submitted forms.
- **Veslink Forms**: External system receiving automated submissions.

## 2. Processes
- **Form Creation**: Back-office team creates and assigns forms to vessels/barge.
- **Form Submission**: Crew fills out and submits forms.
- **Data Processing**: Backend service reads incoming emails, decrypts data, and stores it.
- **Review & Approval**: Analysts review, approve, or reject submitted forms.
- **Data Integration**: Approved data is ingested into the VPS system and shared with Veslink Forms via automation.

## 3. Data Stores
- **GeoForms Database**: Stores submitted form data in JSON format.
- **VPS System**: Holds the latest approved data for analytics and decision-making.

