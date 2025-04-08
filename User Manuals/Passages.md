# Passage Module User Manual 📘

## Introduction
The Passage Module helps manage vessel passages, track voyage details, and generate reports.

## Accessing the Passage Module
1. From the sidebar, select **Passages**.

<br>

   ![image](https://github.com/user-attachments/assets/ff6d4f7e-f6c0-4886-b618-70b20d2bfcdb)

   <br>

3. The module consists of multiple sections for efficient navigation.

## Passage Layout
The Passage Module is divided into the following sections:
- **Filter Section** – Filter passages by vessel, date range, and status.
- **Passage Table** – Displays details of available passages.
- **Reports Section** – Provides detailed voyage and report data.
- **Action Buttons** – Create, edit, and audit passages or reports.

  ![image](https://github.com/user-attachments/assets/0f2fe594-2b6b-4980-88c5-f7ba9ea9604a)

<br>

## Viewing Passages
1. Select a vessel from the **Vessel Name** dropdown.
2. Choose **Active/InActive** status and select the date range.
3. Once a vessel is selected, the **Show Passages** button will be enabled.

   ![image](https://github.com/user-attachments/assets/e177936c-226b-4ee9-82cc-bf38c0e456d2)

   <br>

3. Click **Show Passages** to display existing passages for the vessel.

   ![image](https://github.com/user-attachments/assets/1ce193a6-d7bc-45f5-9dc4-20c3ff8477da)

   <br>

5. Select any passage and click **Passage Audit** to view its approval status and details on who approved it and when.

   ![image](https://github.com/user-attachments/assets/d8270332-d1e7-42f5-b78d-9d729e0104a9)

   <br>


## Creating a New Passage
1. Click on **Create Passage**.
2. Enter the required passage details.
3. Click **Save** to store the new passage.

 ### Passage Table Fields

- **Voyage Number** – Unique identifier for the voyage.
- **Load Condition** – Indicates whether the vessel is **Ballast** (sailing without cargo) or **Laden** (carrying cargo).
- **Departure Port** – Name of the port where the vessel departed.
- **Start Of Sea Passage (UTC)** – Date and UTC time of departure.
- **Departure Time Zone** – Time zone of the departure port.
- **Arrival Port** – Name of the port where the vessel arrived.
- **End Of Sea Passage (UTC)** – Date and UTC time of arrival.
- **Arrival Time Zone** – Time zone of the arrival port.


   ![image](https://github.com/user-attachments/assets/5a54c302-4f53-4762-bd81-27be242e9324)


   <br>


## Editing Reports
1. In the **Report Section**, select any report.
2. The related action buttons will be enabled.
3. Click the necessary button to edit or update the report.

## Managing Bunker Consumption
1. To view **Bunker Consumption**, select **Bunker Consumptions & ROB**.
2. You can **create, edit, and delete** fuel consumption and bunkers details.

   ### Fuel Table Fields

- **Fuel Type** – Name of the fuel type.  
- **Category** – Category of the fuel.  
- **Units** – Measurement unit used for the fuel (e.g., metric tons, liters).  
- **Consumed** – Total amount of fuel consumed in the given unit.  


   ![image](https://github.com/user-attachments/assets/c738a736-c93f-4409-921f-c18ff58c7afe)

   <br>


## Managing Lube Oil Consumption
1. Navigate to **Lube Oil Consumption & ROB**.
2. Enter **Lube Oil Consumption** details and save them.

## Report Section has 2 Tabs
1. **General** – Displays vessel position, speed, distance, and related details.

### Sea Passage Report Fields 


- **Type**: Select the type of report (e.g., Start of Sea Passage).
- **Voyage Number**: Unique identifier for the voyage.
- **Date / Time (Local)**: Date and time of the report in local time.
- **Time Zone Offset**: Offset from UTC for the current location.
- **Latitude**: Latitude coordinate in degrees, minutes, and direction (N/S).
- **Longitude**: Longitude coordinate in degrees, minutes, and direction (E/W).
- **COG (Course Over Ground)**: The actual course of the vessel over the ground.
- **SOG (Speed Over Ground)**: The vessel’s speed relative to the ground (knots).
- **Ordered Speed**: The speed the vessel is instructed to maintain (knots).
- **Steaming Hours**: Total number of hours the vessel has been in motion.
- **Distance to Go**: Remaining distance to the destination (nautical miles).
- **Daily Distance**: Distance covered in the last 24 hours (nautical miles).
- **Distance Through Water**: Distance traveled through water, considering current effects (nautical miles).
- **Engine Distance**: Distance covered based on engine performance (nautical miles).
- **Slip (%)**: Percentage of slip calculated based on propeller efficiency.
- **Average RPM**: Average revolutions per minute of the engine.
- **Average KW**: Average power output in kilowatts (BHP - Brake Horse Power).
- **Fwd Draft**: Forward draft measurement (depth of the vessel at the bow).
- **Aft Draft**: Aft draft measurement (depth of the vessel at the stern).
- **Cargo Temp**: Temperature of the cargo.
- **Port**: Select the nearest port or last port of call.

---




   ![image](https://github.com/user-attachments/assets/c44233de-162f-4355-9b06-4d8b47312193)

   <br>

3. **Weather** – Shows information on wind, wave, and current directions and heights.

# Sea Passage Report - Weather Section

## Fields and Descriptions

| Field Name             | Description |
|------------------------|-------------|
| **Date / Time (Local)** | The local date and time when the report is created. |
| **Time Zone Offset**   | The time zone offset from UTC for the current location. |
| **Voyage Number**      | Unique identifier for the ongoing voyage. |
| **Wind**              | The wind speed measured in Beaufort scale (BF). |
| **Wind Direction**    | The direction from which the wind is coming (e.g., North, South). |
| **Sea Height**        | The height of the waves at sea, measured in meters (m). |
| **Sea Direction**     | The direction in which the sea waves are moving. |
| **Swell Height**      | The height of the swell waves, measured in meters (m). |
| **Swell Direction**   | The direction of the swell waves. |
| **Sea Water Temp**    | The temperature of the seawater, measured in degrees Celsius (°C). |
| **Air Temp**          | The temperature of the air at the reporting location, measured in degrees Celsius (°C). |
| **Atmospheric Pressure** | The atmospheric pressure at sea level, measured in kilopascals (kPa). |




   ![image](https://github.com/user-attachments/assets/9e25036c-0b8b-491c-b64b-da3e1bf33acf)


   <br>


This user manual provides guidance on efficiently using the Passage Module to manage vessel voyages and reports.

