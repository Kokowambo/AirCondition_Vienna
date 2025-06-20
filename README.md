# AirCondition_Vienna

## Project Summary

This dataset documents all cafés located in Vienna's 1st district (Innere Stadt), with a specific focus on the availability of air conditioning. It aims to fill a critical data gap in OpenStreetMap (OSM), where only ~4% of cafés in this area had documented AC information prior to this work.

## Motivation

In Vienna’s city center, summer heat is intensified by dense surfaces and little greenery. Many people – especially older adults and vulnerable groups – seek relief in air-conditioned cafés. However, no reliable open dataset exists indicating which cafés actually provide air conditioning.

**Our motivation:** to expand existing OSM café data by manually adding missing values for air conditioning availability and related attributes.

## Data Source

Initial data collected via [Overpass Turbo](https://overpass-turbo.eu/) from OpenStreetMap using this query:

[out:json][timeout:25];
area["name"="1010 Wien"]->.searchArea;
(node"amenity"="cafe";);
out body;


- Data format: GeoJSON  
- Dataset filename: `NEW_CafeVienna.geojson`

## Data Structure

Each feature (café) contains:
- `name`: Name of the café
- `addr:street`: Street name
- `opening_hours`: Opening hours (OSM format)
- `website`: Website URL
- `air_conditioning`: Whether AC is available (`yes`/`no`/empty)

## Data Enrichment Workflow

- Missing `air_conditioning` values were completed by calling or researching each café individually.
- Additional missing values filled: street names, websites, opening hours
- Removed: duplicates and permanently closed locations

## Statistics

- Total cafés: 139  
- With air conditioning: 69  
- Without air conditioning: 43  
- No information: 8  
- Values added: 287  
- Missing values unresolved: 12

## Visualization

The dataset is visualized in a Jupyter Notebook using Folium with categorized markers (green = with AC, red = without, gray = unknown).

## License

This repository contains two distinct components with different licenses:

### Code and scripts

All scripts, notebooks and visualizations (e.g., Python, Jupyter, Folium) in this repository are licensed under the [MIT License](LICENSE).

### Dataset

The dataset is based on OpenStreetMap (OSM) data and follows the [Open Database License (ODbL) 1.0](https://opendatacommons.org/licenses/odbl/).  
Manually added attributes such as air_conditioning status are provided under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

If you use or share this dataset, please provide appropriate attribution to both OpenStreetMap and this project.


## Authors

Masterseminar “Places Of Interest and VGI”  
University of Vienna, Summer Term 2025
