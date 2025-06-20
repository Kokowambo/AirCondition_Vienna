# AirCondition_Vienna

## Project Summary

This dataset documents all cafés located in Vienna's 1st district (Innere Stadt), with a specific focus on the availability of air conditioning. It aims to fill a critical data gap in OpenStreetMap (OSM), where only ~4% of cafés in this area had documented AC information prior to this work.

## Motivation

In Vienna’s city center, summer heat is intensified by dense surfaces and little greenery. Many people – especially older adults and vulnerable groups – seek relief in air-conditioned cafés. However, no reliable open dataset exists indicating which cafés actually provide air conditioning.

**Our motivation:** to expand existing OSM café data by manually adding missing values for air conditioning availability and related attributes.

## Data Source

Initial data collected via [Overpass Turbo](https://overpass-turbo.eu/) from OpenStreetMap using this query:

```overpass
[out:json][timeout:25];
area["name"="1010 Wien"]->.searchArea;
(node["amenity"="cafe"](area.searchArea););
out body;
```

- Data format: GeoJSON  
- Dataset filename: `NEW_CafeVienna.geojson`

## Data Structure

Each feature (café) contains:
- `name`: Name of the café
- `addr:street`: Street name
- `addr:housenumber`: House number
- `addr:city`: City
- `opening_hours`: Opening hours (OSM format)
- `website`: Website URL
- `air_conditioning`: Whether AC is available (`yes`, `no`, or empty)
- `source:ac`: Method of AC verification (`manual`, `web`, `phone`)
- `geometry`: WGS84 coordinates

For full documentation, see `metadata.txt`.

## Data Enrichment Workflow

- Missing `air_conditioning` values were completed by calling or researching each café individually.
- Additional missing values filled: street names, websites, opening hours.
- Removed: duplicates and permanently closed locations.
- Verified geometry and attribute consistency.

## Statistics

- Total cafés: 139  
- With air conditioning: 69  
- Without air conditioning: 43  
- No information: 8  
- Values manually added: 287  
- Missing values unresolved: 12

## FAIR Principles

The dataset follows FAIR data principles:
- **Findable**: Published on GitHub with structured metadata.
- **Accessible**: Shared in an open, human- and machine-readable format (GeoJSON).
- **Interoperable**: Uses OSM-compatible attribute schema and WGS84 coordinates.
- **Reusable**: Licensed openly (CC BY 4.0), with clear documentation and structure.

## Visualization

The dataset is visualized using a Jupyter Notebook with Folium.  
Categorized markers show:
- Green: with air conditioning
- Red: without air conditioning
- Gray: unknown status

Visual use cases:
- For tourists or residents during heat events
- For public health or climate adaptation planning
- For integration into apps or dashboards

## Scalability and Maintenance

The dataset and workflow can easily be applied to other Vienna districts:
- Replace `1010 Wien` with any other district in the Overpass query
- Follow the same research and enrichment steps

### Maintenance Strategy

- This is currently a one-time dataset.
- Periodic updates can be made through GitHub contributions (pull requests).
- A long-term goal is to integrate the added AC data into OpenStreetMap (e.g. via MapRoulette or direct tagging).
- The project structure encourages community-driven extensions.

## Legal and Ethical Considerations

- No personal data was collected.
- All research was conducted using publicly available information (websites, contact data).
- All sources are properly attributed.

## License

This repository contains two distinct components with different licenses:

### Code and scripts

All scripts, notebooks and visualizations (e.g., Python, Jupyter, Folium) in this repository are licensed under the [MIT License](LICENSE).

### Dataset

The dataset is based on OpenStreetMap (OSM) data and follows the [Open Database License (ODbL) 1.0](https://opendatacommons.org/licenses/odbl/).  
Manually added attributes such as air_conditioning status are provided under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

If you use or share this dataset, please provide appropriate attribution to both OpenStreetMap and this project.

## Repository Contents

- `NEW_CafeVienna.geojson` – Main dataset  
- `metadata.txt` – Full metadata with schema, source, and license info  
- `README.md` – Human-readable project overview  
- `LICENSE` – MIT license for code  
- `folium_visualization.ipynb` – Optional notebook for visualizing the data  
- `folium_maps/` – Folder for map exports (optional)

## Authors

Group 9 – Masterseminar “Places Of Interest and VGI”  
University of Vienna, Summer Term 2025

- Konrad Schmitz  
- Luis Fink  
- Stephan Guttenbrunner


