**VPS Report Generation and Business Context**

### **Report Generation Mechanisms**
Currently, there are two mechanisms for generating reports in VPS:
1. **Direct Download:** Once the user clicks "Generate," a loader appears, and the report gets directly downloaded in the browser.
2. **Queued Download:** When "Generate" is clicked, the report request is placed in a queue. The report moves to the download space, where its status updates once it is ready. Users can download it anytime and refer to previous reports. If an error occurs, it is displayed in the remarks section.

   ![image](https://github.com/user-attachments/assets/a3d49d3a-76ce-4258-a4b9-4c94e2831e88)

<br>

### **Available Reports**
Reports can be downloaded in multiple formats (PDF/Excel). Different types of reports include:
- **Bunker Intake Report**
- **EOV (End of Voyage) Report**
- **Event Report**
- **Passage Performance Report**
- **Various TC Reports**
- **Different VDD Reports**

### **Report Selection and Filters**
Users select the type of report and apply relevant filters, which vary based on the selected report. For example:
- **Bunker Intake Report:** Filters include status, vessel, vessel group, and date range.
- **Voyage TC Performance Report:** Filters include a specific vessel, date range, and defined terms and conditions.
- **Event Report:** Allows selecting a vessel group along with a date range.
- **VDD Report:** Requires only a date range as it applies to each vessel individually.

### **Report Structure and Output Formats**
- **VDD Report:** Output in **Excel** format.
- **TC Report:** Output in **PDF** format.
- **Event Report:** Contains event data extracted from GeoForms or Veslink forms and outputs in **Excel**.
- **Bunker Report:** Includes data such as fuel type, quantity, viscosity, and density, derived from bunkering forms submitted by ships.

### **Business Context of Reports**
Each report serves a specific business function. For instance:
- **Bunker Report:**
  - Helps monitor fuel consumption and efficiency over a defined period.
  - Displays details such as fuel quantity, type, port of bunkering, and viscosity.
  - Data is extracted from bunkering forms submitted by vessels.
- **Event Report:**
  - Summarizes vessel events recorded in Veslink or GeoForms.
  - Helps analyze operational patterns over a three to six-month period.
- **Voyage TC Performance Report:**
  - Assesses time-chartered vessel performance based on voyage data.
  - Filters vessels based on predefined terms and conditions.

### **Report Recipients and Usage**
- **Fleet Managers:** Use reports to track vessel fuel consumption, bunkering trends, and operational performance.
- **Operations Team:** Monitors events and performance-related KPIs.
- **Chartering Teams:** Uses TC performance reports to analyze vessel profitability.
- **Regulatory Compliance Teams:** Utilize reports for compliance with environmental regulations.

---

### **EMS and Analytics Modules**

#### **EMS Module**
The EMS (Environmental Management System) module includes:
- **EUMRV (EU Monitoring, Reporting, and Verification)**
- **AER (Annual Efficiency Ratio)**
- **Annual Vessel Reports**
- Some features require modification to meet compliance and reporting requirements.

#### **Analytics Module**
- **Hull Management Calculators:** Helps users calculate payback periods for various efficiency improvements.
- Allows users to input values and analyze the economic feasibility of operational changes.

### **Settings Page**
- Includes configuration options for reports and user preferences.
- Provides control over report accessibility and visibility.

This document provides a comprehensive overview of the VPS report generation mechanisms, business context, and related modules.
