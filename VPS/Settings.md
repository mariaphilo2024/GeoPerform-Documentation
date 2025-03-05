**VPS Settings Document**

## **1. Overview**
The VPS settings page has been restructured and is now categorized into three main sections:
- **Master Pages**
- **User Settings**
- **Alert Settings**

Standard alerts are currently not in use. The settings page now contains **Data Master** and **User** configurations. The current version is displayed prominently on the settings page.

---

## **2. User Settings**
### **User Management**
- The user page allows for creating and managing users.
- Clicking the **Add User** button enables entering mandatory details such as:
  - First Name
  - Last Name
  - Email ID
  - Role
- Users can be activated or deactivated.

### **Role Management**
- The role management page displays existing roles.
- New roles can be created and assigned specific permissions.
- Users with specific roles can access selected reports.
- Each **sub-module** has permission definitions.

### **Permissions Structure**
Permissions are categorized as:
- **Read:** Allows users to view data.
- **Write:** Enables users to create entries (e.g., reports, passages).
- **Full:** Includes delete functionality along with Read & Write.
- **None:** No access to the specified feature.

---

## **3. Data Master**
### **Vessel Management**
#### **Vessel Master**
- Displays vessel details.
- Vessel categories include:
  - **Vessel Type** (Backend-defined, UI integration planned)
  - **Vessel Size** (User-defined in UI)
  - **Vessel Class** (User-defined in UI)
- Vessel types influence calculations in modules like **AER-CII Rating**.

#### **Vessel Groups**
- Allows categorization of vessels manually via dropdown.
- Users can create vessel groups by selecting vessels from a dropdown list.
- Admin have access to all vessels

### **Consumption Categories (Consumer Types)**
- Defines fuel consumption categories for passages.
- Includes both predefined and custom categories.
- **New Fuel Types require backend logic updates** in multiple reports and tracking screens.

### **Fuel Types and Dependencies**
- Adding a new fuel type requires updates in:
  - **Tracking Screen logic**
  - **Vessel Daily Details Report (VDD)**
  - **EUMRV grouping**
- Example: **LFO fuel type** was recently added but required manual backend mapping.
- Fuel type additions do not automatically integrate into system logic and require backend modifications.
- A proposed enhancement is to allow **FO(Fuel Oil) & GO(Gas Oil) category definition from the UI**.

### **Lube Oil Master**
- Recently introduced with five predefined categories.
- Only applicable to specific vessels.
- Master page includes options to:
  - View listings
  - Activate/deactivate categories
  - Add new oil types

### **Event Master**
- Defines vessel-reported events.
- Includes **Custom KPIs** such as:
  - Emission KPIs
  - Sea Cargo Charter Variables
  - Poseidon Constants
  - AER Constants
- Primarily used in the **EMS module** for calculations.

### **Port Master**
- Contains a database of **8,000–9,000 ports**.
- Individual ports can be added via the application.
- Bulk additions require backend updates.
- Ports impact **EUMRV logic, passage screen, arrival/departure records**.

---

## **4. EMS and Analytics Modules**
### **EMS Module**
- Includes:
  - **EUMRV**
  - **AER**
  - **Annual Vessel Reports**
- Some features require modification.

### **Analytics Module**
- Contains **Hull Management Calculators**.
- Allows users to input values and calculate **payback periods**.

---

## **5. Additional Features**
- **Password Change & Logout Functionality** available in the top navigation.
- **Tracking Screen, Passages, Reports, and Downloads** are all linked to settings.
- **Terms Module** is dependent on reports (e.g., Time Charter Report, Pool Performance Report).

---

## **6. Future Enhancements**
- **Incorporating Vessel Type selection in UI**.
- **Automating fuel category mapping within UI**.
- **Reactivating alert notifications**.
- **Expanding EMS & Analytics integration**.
- **Enhancing role-based access for report management**.

---

## **Conclusion**
- The settings page has been **restructured for efficiency**.
- **Fuel type dependency on backend logic** is a critical area for improvement.
- **EMS and Analytics modules** continue to evolve with additional calculations and features.
- **Future enhancements** focus on **automation, UI improvements, and system-wide optimizations**.
