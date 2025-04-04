# Tracking Screen Module

The Tracking Screen module provides a real-time view of vessel locations, tracking data, and voyage statuses.

## Accessing the Tracking Screen

1. Open the VPS application.
2. From the left-side menu, select **Tracking Screen**.

## Tracking Screen Layout

- **Left Panel** – Displays filters and vessel information.
- **Right Panel** – Interactive map showing vessel routes and status.

  ![image](https://github.com/user-attachments/assets/77411a39-0cab-442f-a637-e69d81ff7404)


### 1.1 Filtering Options

You can filter the vessel list based on the following options:

| **Filter**          | **Description** |
|---------------------|----------------|
| **All**            | Displays all vessels (active and inactive). |
| **Active**         | Displays only active voyages. |
| **Inactive**       | Displays only inactive voyages. |
| **Vessel Group**   | Select a vessel group from the dropdown (e.g., "Demo Group"). |
| **Vessel**         | Select a specific vessel from the list. |
| **Departure Date Range** | Set the start and end date of the voyage to filter results. |

### Actions

- **Load** – Click to apply the filter and display voyage details.
- **Show on Map** – Displays the vessel's route on the map.
- **Clear** – Resets all filters and selections.

When a vessel group is selected and **Load** is clicked, it shows the location of the vessel on the map.

## Visual Indicators on the Map

- **Circle icon** = Vessel at port
- **Triangle icon** = Vessel at sea
- **Direction of triangle** = Course of the vessel
- **Color coding** represents different vessel types.
- **Map Legends** provide additional details. 

## Key Performance Indicator (KPI) (Available for Single Vessel Selection)

| **KPI**              | **Description** |
|----------------------|----------------|
| **Ordered Speed**    | The speed that the vessel is instructed to maintain as per the shipowner, operator, or charterer. |
| **Performed Speed**  | The actual speed at which the vessel is sailing, considering real-time conditions. It may differ from the ordered speed due to weather, currents, engine performance, or operational adjustments. |
| **Distance Covered** | Total distance covered. |
| **ME Consumption**   | Main Engine fuel consumption. |
| **AUX Consumption**  | Auxiliary Engine fuel consumption. |
| **Total FO Consumed** | Total Fuel Oil consumed. |
| **Total GO Consumed** | Total Gas Oil consumed. |

![image](https://github.com/user-attachments/assets/3e824716-9d18-48b9-8a9d-a4fc5eca2f41)


## Passage Screen

1. Once a single vessel is selected, under that, select **Passages** (users can track multiple passages simultaneously).
2. Click **Show on Map** to display the passages on the map.

### Indicators

- **Blue dots** = Actual GPS positions (Stratum/AIS data).
- **Green Hollow circles** = Estimated positions based on voyage calculations.
- **Weather data** is averaged over one-hour intervals.

  ![image](https://github.com/user-attachments/assets/9ce3a707-f9b9-4af8-b6af-f019f13ad90a)


## Available Legends on the Map

### Currents
- Displayed using arrows indicating direction and speed.

### Waves
- Shows wave height, direction, and frequency.
- Indicated by numerical values and directional symbols.

### Wind
- Displays wind speed and direction using wind barbs (hockey stick symbols).

### Report Legend
- Categorizes different types of reports received (e.g., Noon Report, Departure Report, Arrival Report).

### Passage Weather Legend
- Provides weather conditions along the vessel's planned passage.
- Includes wind, waves, and current data at different timestamps.

### Tropic of Cancer, Equator, and Tropic of Capricorn
- Displays major latitude lines on the map for navigation reference.
- Helps in identifying tropical and non-tropical zones.

### ECA (Emission Control Area) Region
- Highlights areas with strict emission regulations.
- Used for compliance with environmental policies.

### High-Risk Area
- Marks zones with piracy threats or other navigational hazards.
- Helps vessels in route planning and security measures.

### Tropical and Non-Tropical Regions
- Distinguishes between regions with different weather conditions.
- Useful for predicting cyclone activity and temperature variations.

### Cursor and Depth Units
- Provides depth information based on cursor position on the map.
- Helps in assessing navigational depths for vessel safety.

### Vessel Type
- Identifies different vessel classifications.
- Useful for operational and regulatory considerations.

### Vessel Name
- Displays the vessel’s name for identification on the map.
- Helps in tracking and monitoring specific vessels.
