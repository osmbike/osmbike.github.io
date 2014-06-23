# BikeDistrict.org

* company consulting administration
* Milano only (other cities will be added)
* web app with
 * routing (3 cycle profiles)
 * bike sharing stations, shops, other cycle POIs
 * user profiles for customization
* native apps planned
* registered user rating suggested path to improve route
* analyse service usage to identify issues and trigger infrastructure improvements


# Map Rendering beyond Mapnik

* Mapserver.org
 * C++, Python bindings (and more), Apache module
 * WMS, WFS

* Geoserver
* comparison, missing features


# pgmapcss

* osm2pgsql database
* compile MapCSS style
* Python


# Lightning Map Tiles

* old workflow: mod_tile + tirex/renderd
* mod_tile: disk store (_not_ cache)
* Vector Tiles: see SOTM US 2013 Springmeyer
* z14 tile can contain z14+
 * z0-z14 vector tiles result in z0-z22 raster
 * from z23 you will see effect of feature simplification
* important modules: tilelive-bridge, tilelive-vector
 * no documentation available yet
* Andy Allan proprietary tools:
 * vtiler: converts data (.shp, PostGIS) to vector tiles using tilelive-vector, stores on disk
 * hailstorm: renders raster tiles from vector tiles
 * weatherman: find changes in PostGIS, call vtiler


# Rendering Maps with OpenGL

* talk covering lines and text (see also Mapbox blog)
* text: paper published by Valve, texture atlas
* label placement:
 * label should not vanish when zooming ("pops")
 * or change position ("jumps")
 * no panning/zooming history dependence
* browser version of mapbox-gl will be released in the future
* native first because of WWDC


# Tesselator's Delight

* WebGL intro
* using vector tiles (GeoJSON for dev)
* available on mapzen.com/vector, updated daily
* github.com/bcanoer/tangram
* greggman.github.io/...


# Label placement

* literature: "Thematic Carography" by E. Imhof
* shorter article: Imhof 1975, "Positioning names on Maps)
* ask Maxim Rylov (UHEI) if questions occur
* check out his thesis when published


# GeoGit

* github.com/opengeo/geogit
* OSM-specific commands (import, download data, etc.)
* can use Overpass API
* Java


# Imposm

* multi-CPU, memory efficient
* osm2pgsql planet import (normal mode): 22 GB RAM
* Imposm3:
 * Go
 * HyperlevelDB (Europe ~50GB, Planet ~90GB)
 * diff support production ready
 * doc missing for release


# Lightning talks

* discussions on changesets
 * GSoC14 project
 * commentsapi.dev.openstreetmap.org
* cycle.travel now available in Western Europe
* poichecker.de / github.com/sozialhelden/poichecker
* Disaster Mappers Heidelberg


# State of the License

* wiki.openstreetmap.org/State_of_the_License
* "Community Guidelines" document
* drop share-alike
 * biggest fear: company taking over community


# In/Outdoor Map for Android

* using mapsforge
* indoor data is XML (will change)
* manually select floor


# Keynote

* complex systems: local pertubation, cascade effect
* self-regulation vs. governance
* self-awareness


# Geocoding Session

## OpenCage

* geocoder.opencagedata.com (by Lokku)
* free tier available

## Mapzen

* OpenSource geocoders:
 * Nominatim (old architecture)
 * Pelias (new, accessible for developers, modular)
  * query: JSON/GeoJSON
  * auto-completion
  * ElasticSearch
  * mapzen.com/pelias
  * current data import: osm2pgsql -> redis -> ElasticSearch (written in Ruby)
  * new import: pbf -> ElasticSearch (written in NodeJS)
   * on github in branch "node"

## OSM Gazetteer

* ElasticSearch
* on Github


# Hack Day Session

## Osmium

* .opl format (object per line) for command line tools
* can read URLs
* npm install osmium
* Handler can be written in JS
* osmcode.org / github.com/osmium


## Overpass API

* new feature: print center (of the enclosing bbox)
* query old data (history): "attic data"
* augmented diffs: includes date
 * deleted: visible=false means actually deleted, visible=true means out of scope
* will be release as 0.7.50
* in future: feature branches which can be merged separately if required before release


## Carto

* github.com/gravitystorm/openstreetmap-carto (many open issues)
* install (non-production):
 * Tilemill 0.10
 * osm2pgsql + PostGIS (guide on switch2osm.org/loading-osm-data)
 * download additional shapefiles
* style has ~40 layers
* french fork: github.com/cquest/ carto-mml-fr (?)
* check out Harfbuzz
* style depends on stable releases only (Mapnik, Tilemill)
