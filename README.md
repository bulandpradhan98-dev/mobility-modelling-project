# Citi Bike Mobility Modelling

This repository contains a five-stage mobility-modelling workflow based on 2025 Jersey City Citi Bike trip data. The work progresses from data cleaning and exploratory analysis through route generation, traffic-flow estimation, emissions modelling, and scenario testing.

## Project workflow

| Stage | Notebook | Main purpose |
| --- | --- | --- |
| 1 | `Task_1_Data_Exploration.ipynb` | Combine monthly trip files, assess data quality, clean the records, and explore temporal and spatial patterns. |
| 2 | `Task_2_Routing.ipynb` | Build the cycling network, match trip endpoints to network nodes, generate routes, and introduce route variability. |
| 3 | `Task_3_Traffic flows-revise1.ipynb` | Convert routed trajectories to network edges and estimate edge-level bicycle traffic flows. |
| 4 | `Task_4_Emission Modelling-Revise.ipynb` | Estimate road-segment emissions effects using traffic flow, speed, lane, and road-type attributes. |
| 5 | `Task_5_Scenario_Modelling.ipynb` | Model a high-impact corridor closure, reroute trips, and compare baseline and scenario outcomes. |

Earlier notebook versions are retained for traceability:

- `Task_3_Traffic flows.ipynb`
- `Task 4 Emission Modelling.ipynb`

## Data and generated outputs

- `citi_2025/` — monthly Citi Bike source files available in the working project.
- `citi_bike_2025_cleaned_consolidated.csv` and `citi_bike_2025_cleaned_consolidated_v2.csv` — consolidated and cleaned trip datasets.
- `task2_routed_trips.geojson` — routed trip trajectories.
- `routes_with_variability.geojson` / `.gpkg` — alternative-route outputs.
- `flow_data.gpkg` — edge-level traffic-flow results.
- `emissions_revised_road_segments.csv` / `.gpkg` — revised segment-level emissions results.

Large data and geospatial files are versioned with [Git LFS](https://git-lfs.com/). Clone the repository with Git LFS installed so these files are downloaded correctly.

## Environment

The notebooks use Python and Jupyter with the geospatial/scientific stack listed in `requirements.txt`. A typical setup is:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter lab
```

Some notebooks download OpenStreetMap network data through OSMnx, so those cells require an internet connection. Run the notebooks in numerical order because later stages consume outputs from earlier stages.

## Notes

- Jupyter checkpoints, request caches, virtual environments, and the local duplicate backup folder are intentionally excluded from version control.
- The February 2025 raw monthly CSV is not present in the current workspace; the consolidated datasets are retained as the authoritative cleaned inputs used by the analysis.
- Notebook outputs are kept so the analytical narrative, maps, and report-style results remain visible on GitHub.

## Data source

Trip records originate from the Citi Bike system data published by Lyft/Citi Bike. Consult the source data terms before redistributing or reusing the records.
