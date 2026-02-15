# Biliuhe Reservoir Flood Event Dataset

This repository contains a comprehensive dataset of flood events for the Biliuhe Reservoir basin, including rainfall-runoff data, station information, and spatial data (reservoir boundary and river network).

The dataset is suitable for hydrological modeling, flood forecasting, and reservoir operation studies.

## Dataset Structure

The repository is organized as follows:

- **`Flood_Events/`**: Contains CSV files for 26 historical flood events from 1984 to 2023.
  - Each file is named by the event date (e.g., `19840615.csv`).
  - Columns:
    - `time`: Timestamp (YYYY-MM-DD HH:MM:SS)
    - `prcp(mm/3h)`: Precipitation (mm per 3 hours)
    - `flow(m^3/s)`: Discharge/Flow (cubic meters per second)
    - `pet(mm/3h)`: Potential Evapotranspiration (mm per 3 hours)

- **`Stations_Info.csv`**: Metadata for hydro-meteorological stations in the basin.
  - `Station_Name`: Name of the station (Pinyin or English, e.g., Xiaoshipeng)
  - `Station_ID`: Unique identifier
  - `Station_Type`: Type of station (Rainfall Station or Hydrological Station)
  - `Longitude`: Longitude (WGS84)
  - `Latitude`: Latitude (WGS84)

- **`Reservoir_Shapefile/`**: ESRI Shapefile data for the Biliuhe Reservoir boundary.
  - Files: `Reservoir.shp`, `Reservoir.shx`, `Reservoir.dbf`, etc.

- **`River_Network/`**: ESRI Shapefile data for the Biliuhe river network (excluding downstream).
  - Files: `River_Network.shp`, `River_Network.shx`, `River_Network.dbf`, etc.

## Usage

This dataset is provided for research purposes. The data can be used to calibrate and validate hydrological models.

### Example (Python)

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load a flood event
df = pd.read_csv('Flood_Events/19840615.csv', parse_dates=['time'])

# Plot rainfall and flow
fig, ax1 = plt.subplots()

ax1.set_xlabel('Time')
ax1.set_ylabel('Flow (m^3/s)', color='blue')
ax1.plot(df['time'], df['flow(m^3/s)'], color='blue')
ax1.tick_params(axis='y', labelcolor='blue')

ax2 = ax1.twinx()
ax2.set_ylabel('Precipitation (mm)', color='red')
ax2.bar(df['time'], df['prcp(mm/3h)'], color='red', width=0.1)
ax2.tick_params(axis='y', labelcolor='red')
ax2.invert_yaxis()

plt.title('Flood Event: 1984-06-15')
plt.show()
```

## Citation

If you use this dataset in your research, please cite the following paper:

[To be added upon publication]

## License

This dataset is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
