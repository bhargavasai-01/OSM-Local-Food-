# OSM Local Food Producers – County Level Extraction
This project extracts local food producers, markets, farms, and processors**
from OpenStreetMap (OSM) for a specific U.S. county, using the
Overpass API and GeoPandas
The output is a clean, county-clipped GeoJSON file ready for use in QGIS
or further spatial analysis.

 Features
- County-based spatial filtering using official county boundaries
- OSM data extraction via Overpass API
- Supports nodes and ways (using centroids)
- Clean GeoJSON output
- CRS-safe workflow (EPSG:4326)
- QGIS-ready visualization

Project Structure
.venv
data/
├── raw/
│   └── boundaries
      └── osm
      └── usda
└── processed/
    └── osm_producers.geojson
     └── county_boundary.geojson
scripts/
└── extract_osm_producers.py

Requirements
Python 3.9+
GeoPandas
Requests
Shapely
Fiona

Install dependencies:
pip install geopandas requests shapely fiona pyproj

Loads a county boundary GeoJSON
Reprojects boundary to EPSG:4326
Extracts bounding box for Overpass query

Queries OSM for:
Farms
Markets
Food producers
Processors

Model
Converts results to GeoDataFrame
Spatially filters features inside the county
Exports GeoJSON


Usage
python scripts/extract_osm_producers.py
Output file:
data/processed/osm_producers.geojson

🗺 Visualizing in QGIS
Open QGIS
Drag osm_producers.geojson into the map
Set project CRS to EPSG:3857 or EPSG:3083
Use Identify Features to inspect attributes

Output Fields
osm_id
name
shop
amenity
craft
industrial
products
organic
delivery
website
phone
geometry
GEOID

Notes
Overpass queries use bounding boxes for performance
Final spatial filtering ensures county-only results
Large counties may require query simplification

Future Enhancements
Polygon-based Overpass queries
Multi-county batch processing
Data classification by producer type
Web map integration
CLI arguments
