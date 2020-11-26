---
title: Analyzing nests
nav_order: 2
layout: default
parent: Understanding mechanics
---

# How Nest Watcher analyzes nests

When configuring Nest Watcher, it might be helpful to understand how it operates.

1. Get values needed for analyzation
  - If enabled, get the last nest migration:

      - Check [this](https://raw.githubusercontent.com/ccev/pogoinfo/info/last-nest-migration) for regular migrations
      - See [here](https://raw.githubusercontent.com/ccev/pogoinfo/info/events/all.json) if there's an event start/end between that time and right now If yes, use that.

  - Go through your areas.json and save it together with the appropiate settings in a list, to later iterate over
  - If enabled check [this](https://raw.githubusercontent.com/ccev/pogoinfo/info/events/active.json) for current event mons and save them as a list
  - Get Nesting species [from here](https://pogoapi.net/api/v1/nesting_pokemon.json) and subtract the event mon list from it
  - Connect to the DB and, if meganests are enabled, query the most common nest mon in your db and remove it from the nest list

2. For each area, do:
  - Get the OSM data file, if not existent, query the data from overpass-turbo (taking into account rate-limiting)

      - Overpass only allows for bbox-querying, if parks are outside of the given geofence, they're later being filtered out

  - Get area data. If not existent, use an empty dict
  - Delete nests within the area from the database
  - Save all nodes, ways and relations from osm in seperate lists
  - If less_queries is enabled, query all mons and spawns from the area
  - Go throgh all relations, generate polygons from them and save used ways in an extra list from the way-list. Then generate polygons from the ways. (The generating of polygons is pretty complicated and I wouldn't be able to easily explain it here)
  - Go through the area data and connect parks by merging the polygons and then removing the to-be-connected park from the list
  - Go through each park now and do:

      - If there was an error with the geometry calculation, skip
      - If the park polygon is not within the area polygon, skip
      - If the park ID a way and part of a relation, skip
      - If enabled, query Pokestops from the park polygon
      - Get Spawnpoints (if less_queries is enabled, go through the prequeried list, else grab them straight from the database)
      - If no Spawns/Stops exist, skip
      - If Spawns + Stops < min_spawnpoints (settings), skip
      - Get the most common mon and its count where the ID is in the generated nesting list and which spawned on the queried spawns/stops. (if less_queries, get them from the pregenerated list, else get them from the db)
      - Calculate mon_avg: (mon_amount / scan_hours_per_day)) * (24.00 / hours_since_change)
      - Calculate mon_ratio: mon_avg / (stops + spawns)
      - Now see if those values are higher than the filter configured in settings
      - Get name and center lat/lon of the park. If not existent in area_data, try to get the name from the OSM data and calculate the center using the polylabel algorithm for normal polygons. Or the simple centroid for multipolygons
      - Save the park details in GeoJSON format
      - Put the nest into the database
      - Save the park in a list
      
  - Convert the list into area_data format (sorted by mon_avg) and append data of nests that haven't been found this run, then save the area_data

3. Frontend features
  - Save the GeoJSON of all found parks according to the config
  - Send nests to Discord