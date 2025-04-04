# Vessel Performence System Overview

## Introduction
The VPS (Vessel Performance System) is a comprehensive application designed to track vessel performance, manage fleets, and analyze voyage data. The system includes multiple modules, authentication mechanisms, and role-based access controls.

## Authentication and Access Control
- Users can log in using username/password or Single Sign-On (SSO).
- Access is role-based, with permissions to different modules granted by the administrator.
- Users are assigned to vessel groups, which define the vessels they can access.

## Main Modules

**1. Tracking Screen (Landing Page)** <br>
**2. Passages** <br>
**3. EMS (Event Management System)** <br>
**4. Terms** <br>
**5. Reports** <br>
**6. Analytics** <br>
**7. Downloads** <br>
**8. Settings**

   ![image](https://github.com/user-attachments/assets/fb2fd68a-25ea-4ac4-a7ef-951dd290ef86)



## Tracking Screen
### Vessel Groups and Filters
- Users can be assigned to multiple vessel groups.
- Users can create custom vessel groups.
- Groups can be created at both user level and fleet level.
- Shows vessel count under each group.
- Admin-controlled access: Users must request admin approval to see a newly created group.
- Vessels are categorized into active and inactive.
- Users can filter vessels using:
  - Status (Active/Inactive)
  - Vessel Group
  - Vessel Name

    ![image](https://github.com/user-attachments/assets/21c123d4-7b7c-413d-8df5-83383bd24a33)



### Vessel Search & Display
- Users can search vessels beyond the selected vessel group.
- Selecting a vessel displays:
  - Voyage details (departure/arrival ports & dates)
  - Displays vessel positions on the map.
  - Key Performance  Indicator (KPI) (for single vessel selection)
    - Helps identify performance deviations (if a vessel is slower than expected).
    - Detects excessive fuel usage, optimizing costs.
    - Assesses weather impact on the voyage.
    - Ensures the vessel meets its contracted speed and efficiency.
- This data helps fleet managers and analysts make better decisions about route optimization, fuel efficiency, and ship maintenance.

  ![image](https://github.com/user-attachments/assets/6db1c2f1-9999-4891-805e-71dcd0eb7069)


### Visual Indicators on the Map
- **Circle icon** = Vessel at port
- **Triangle icon** = Vessel at sea
- **Direction of triangle** = Course of the vessel
- **Color coding** represents different vessel types.
- **Map Legends** provide additional details.

  ![image](https://github.com/user-attachments/assets/c7238e94-240f-46e7-b700-96af27865908)



## Passage Tracking
- Users can view entire voyage paths.
- Reports include:
  - **Departure report** (Lighter Green icon)
  - **Noon report** ( Green icon)
  - **Arrival report** (Red icon)
- Users can track multiple passages simultaneously.
- Weather overlays are provided for analysis.

 ![image](https://github.com/user-attachments/assets/14fa8155-0ecf-4d2d-a23d-53a6e2ab5e98)



## Weather & Position Data
- Stratum positions (GPS coordinates received via AIS)
- The Distance API calculates latitude and longitude for hourly positions.
- DTM processes weather and position data.
- It receives timestamps and GPS positions from Stratum/AIS data.
- Provides wind, wave, and current data for each position.
- DTM calculates estimated weather conditions for hourly intervals.
- Generates analyzed weather conditions based on vessel movement patterns.
- Each report's data is split into one-hour intervals for accurate readings.


  ![image](https://github.com/user-attachments/assets/13110749-3cc9-40c0-88aa-cb6b45e7da4e)


## Estimation Logic
- **Blue dots** = Actual GPS positions (Stratum/AIS data)
- If a vessel misses position updates, VPS estimates its location.
- VPS uses previous speed (SOG) and direction (COG) to calculate these missing positions.
- **Green Hollow circles** = Estimated positions based on voyage calculations
- Weather data is averaged over one-hour intervals.

### Conversions
- **Wind speed**: Nautical miles to Beaufort scale.
- **Wave height**: Meters to Douglas scale.

### Legend & Weather Data Display
- Wind, wave, and current data are displayed via color-coded overlays.
- The intensity of currents is shown via numerical values.

  ![image](https://github.com/user-attachments/assets/658a1bf1-1c15-45bd-8486-ad6d0ef5fef0)

- Analysts primarily use this data for TC performance claims.
- Generates Time Charter (TC) reports with weather-adjusted speeds.
- Weather overlays help analysts understand if bad weather is slowing down a vessel or increasing fuel consumption.

## Available Legends on VPS

### Currents
- Displayed using arrows indicating direction and speed.

## Waves
- Shows wave height, direction, and frequency.
- Indicated by numerical values and directional symbols.

## Wind
- Displays wind speed and direction using wind barbs (hockey stick symbols).

## Report Legend
- Categorizes different types of reports received (e.g., Noon Report, Departure Report, Arrival Report).

## Passage Weather Legend
- Provides weather conditions along the vessel's planned passage.
- Includes wind, waves, and current data at different timestamps.

## Tropic of Cancer, Equator, and Tropic of Capricorn
- Displays major latitude lines on the map for navigation reference.
- Helps in identifying tropical and non-tropical zones.

## ECA (Emission Control Area) Region
- Highlights areas with strict emission regulations.
- Used for compliance with environmental policies.

## High-Risk Area
- Marks zones with piracy threats or other navigational hazards.
- Helps vessels in route planning and security measures.

## Tropical and Non-Tropical Regions
- Distinguishes between regions with different weather conditions.
- Useful for predicting cyclone activity and temperature variations.

## Cursor and Depth Units
- Provides depth information based on cursor position on the map.
- Helps in assessing navigational depths for vessel safety.

## Vessel Type
- Identifies different vessel classifications.
- Useful for operational and regulatory considerations.

## Vessel Name
- Displays the vessel’s name for identification on the map.
- Helps in tracking and monitoring specific vessels.

## Conclusion
VPS tracks ships 24/7 with real-time data, estimates missing positions, analyzes weather impacts, optimizes routes for efficiency and cost savings, and ensures compliance with contractual performance.

