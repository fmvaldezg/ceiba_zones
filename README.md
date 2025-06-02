# CEIBA zones map

This repository contains data and files to build an interactive webmap allowing users to enter a street address and identify whether the location is inside the benefits zone.

## Primary Purpose
The application is a **zone checker tool for Philadelphia** that allows users to search for addresses and determine which geographic zones they fall within.

### Files

- data
  - ASEZ.geojson
  - ASEZ_horn.geojson
  - ASEZ_original.geojson
  - JUNIATA.geojson
  - PTSSD.geojson
  - SCI.geojson
- index.html

```bash
├── data
│   ├── ASEZ.geojson
│   ├── ASEZ_horn.geojson
│   ├── ASEZ_original.geojson
│   ├── JUNIATA.geojson
│   ├── PTSSD.geojson
│   └── SCI.geojson
├── .gitattributes
├── .gitignore
├── LICENSE
├── README.md
└── index.html
```

## Data

The `data` folder contains six files representing the benefit zones. 

| Zone name                             | file                  | source                                                                                                                                  |
|---------------------------------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| American Street Empowerment Zone      | ASEZ.geojson          | https://www.phila.gov/programs/neighborhood-funding-stream/                                                                             |
| American Street Empowerment Zone      | ASEZ_horn.geojson     | https://www.phila.gov/programs/neighborhood-funding-stream/                                                                             |
| American Street Empowerment Zone      | ASEZ_original.geojson | https://www.phila.gov/programs/neighborhood-funding-stream/                                                                             |
| Juniata (zipcodes)                    | JUNIATA.geojson       | https://data.census.gov/map/1400000US42101019000,42101019100/ACSST5Y2023/S0101?layer=VT_2023_140_00_PY_D1&loc=40.0091,-75.1069,z12.9280 |
| Penn Treaty Special Services District | PTSSD.geojson         | https://penntreatyssd.org/                                                                                                              |
| Sustainable Communities Initiative    | SCI.geojson           | https://www.lisc.org/philly/where-we-work/                                                                                              |


## The map

The file `index.html` contains the code that generates the webmap at [https://felipevaldez.com/ceiba_zones/](https://felipevaldez.com/ceiba_zones/).

It uses **MapLibre GL JS** to create an interactive web mapping application along with **Turf.js** for spatial analysis.

### Key Functions of MapLibre GL JS:

**1. Interactive Base Map**
- Renders an OpenStreetMap-based raster tile layer
- Provides pan, zoom, and navigation controls
- Restricts the map view to Philadelphia boundaries

**2. Geographic Zone Visualization** 
- Displays 4 colored polygon zones overlaid on the map:
  - ASEZ (green) `#1b9e77`
  - ASEZ cuerno/horn (pink) `#e7298a`
  - PTSSD (orange) `#d95f02`
  - JUNIATA (purple) `#7570b3`
- Makes zones clickable with popup information

**3. Address Geocoding Integration**
- Integrates with MapLibre GL Geocoder plugin
- Converts address searches into map coordinates
- Places markers at searched locations
- Automatically zooms to search results

**4. User Interface Controls**
- Provides a reset button to return to default map view
- Shows zone check results in a sidebar panel
- Handles user interactions like clicks and searches

### Key Functions of Turf.js:

**1. Spatial Analysis**
- Performs point-in-polygon analysis to determine if searched addresses fall within any of the defined zones
- Updates a results panel showing "Yes/No" for each zone
- Uses `queryRenderedFeatures()` to detect spatial relationships

## Updating the map



