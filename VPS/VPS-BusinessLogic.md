# 🚢 VPS Business Logic Overview  
The VPS business logic is designed to process vessel performance data, generate insights, and improve operational efficiency through structured processing and analysis.  

---

## 1. **Data Ingestion and Processing**  
### ✅ **Email Reader Service**  
- Receives vessel data (e.g., Noon Report, Arrival Report) via email.  
- Extracts key information using parsing and data extraction logic.  
- Validates the extracted data (e.g., check for missing fields, incorrect formats).  
- Sends the cleaned data to the VPS database.  

### ✅ **GeoForms Ingestion Engine**  
- Receives structured data from GeoForms.  
- Maps JSON keys to predefined database fields.  
- Validates the data using business rules (e.g., vessel type, IMO number).  
- Handles calculated fields (e.g., fuel consumption per mile).  
- Stores processed data in the VPS database.  

---

## 2. **Validation Rules**  
### 🚦 **Data Integrity**  
- Check for duplicate records.  
- Ensure active IMO number exists.  
- Ensure vessel data matches known vessel profiles.  

### 📏 **Data Type Validation**  
- Confirm numeric values for speed, fuel consumption, etc.  
- Ensure dates and timestamps are in the correct format.  

### 🔎 **Conditional Logic**  
- If `vessel type = "Tanker"`, then allow only certain fuel types.  
- If `vessel status = "In Port"`, skip speed and course data.  

---

## 3. **Performance Calculation**  
### 🛠️ **Fuel Efficiency**  
- Calculate fuel consumption per mile.  
- Compare with historical data for similar vessels.  

### 🌊 **Weather Impact**  
- Adjust performance calculations based on weather data.  
- Example: Increase expected fuel consumption during rough seas.  

### 📉 **Performance Deviation**  
- Identify outliers and performance drops.  
- Generate alerts if vessel performance deviates from the baseline.  

---

## 4. **Data Enrichment and Transformation**  
### 🔄 **AIS Data Matching**  
- Match vessel location (from AIS) with performance data.  
- Combine weather data and performance data to improve accuracy.  

### 💡 **Derived Fields**  
Create new fields based on calculations:  
- **Fuel per mile** = Total fuel consumption ÷ Distance traveled  
- **Average speed** = Total distance ÷ Total travel time  

---

## 5. **Reporting and Insights**  
### 📊 **Analytics Engine**  
- Queries processed data from VPS database.  
- Generates structured reports (e.g., weekly/monthly performance).  
- Identifies improvement areas (e.g., high fuel consumption).  

### 👨‍💻 **Frontend (UI)**  
- Displays insights to the user.  
- Accepts user feedback for refining analysis.  

---

## 6. **Feedback and Continuous Improvement**  
### 🔄 **Feedback Loop**  
- User feedback is collected via the frontend.  
- Feedback is stored in the VPS database.  
- Business rules are updated based on performance insights and user input.  

---

## ✅ **Business Logic Highlights**  
✔️ Real-time validation and data correction.  
✔️ Adaptive performance calculation based on environmental factors.  
✔️ Predictive insights for operational improvements.  
✔️ Integration of multiple data sources for holistic insights.  

---

This business logic ensures that the VPS can handle complex data structures, process them accurately, and provide actionable insights to vessel operators and analysts. 🚀  
