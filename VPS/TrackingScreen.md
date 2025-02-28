# VPS Vessel Performance System Overview

## Introduction
The VPS (Vessel Performance System) is a comprehensive application designed to track vessel performance, manage fleets, and analyze voyage data. The system includes multiple modules, authentication mechanisms, and role-based access controls.

## Authentication and Access Control
- Users can log in using username/password or Single Sign-On (SSO).
- Access is role-based, with permissions to different modules granted by the administrator.
- Users are assigned to vessel groups, which define the vessels they can access.

## Main Modules
1. Tracking Screen (Landing Page)
2. Passages
3. EMS (Event Management System)
4. Terms
5. Reports
6. Analytics
7. Downloads
8. Settings

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
  - Key Performance Analytics (KPA) (for single vessel selection)
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

  ![image](https://github.com/user-attachments/assets/5fa7b14d-01fd-4989-ab62-ecf77fb003e7)


## Passage Tracking
- Users can view entire voyage paths.
- Reports include:
  - **Departure report** (Green icon)
  - **Noon report** (Lighter green icon)
  - **Arrival report** (Red icon)
- Users can track multiple passages simultaneously.
- Weather overlays are provided for analysis.

## Weather & Position Data
- Stratum positions (GPS coordinates received via AIS)
- DTM processes weather and position data.
- It receives timestamps and GPS positions from Stratum/AIS data.
- Provides wind, wave, and current data for each position.
- DTM calculates estimated weather conditions for hourly intervals.
- Generates analyzed weather conditions based on vessel movement patterns.
- Each report's data is split into one-hour intervals for accurate readings.
- The Distance API calculates latitude and longitude for hourly positions.

## Estimation Logic
- **Blue dots** = Actual GPS positions (Stratum/AIS data)
- **Green Hollow circles** = Estimated positions based on voyage calculations
- Weather data is averaged over one-hour intervals.

### Conversions
- **Wind speed**: Nautical miles to Beaufort scale.
- **Wave height**: Meters to Douglas scale.

### Legend & Weather Data Display
- Wind, wave, and current data are displayed via color-coded overlays.
- The intensity of currents is shown via numerical values.
- Analysts primarily use this data for TC performance claims.

## Settings Module
- User roles & permissions
- Master data management:
  - Vessel types, vessel classes, fuel types
- User-specific settings
- None/Read/Write/Full access controls

## Conclusion
The VPS system is a powerful vessel tracking and performance management tool. It provides real-time tracking, weather analysis, and voyage insights. Future enhancements will focus on automation, usability, and predictive analytics to further optimize maritime operations.

