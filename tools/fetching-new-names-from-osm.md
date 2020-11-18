---
title: Fetching new names from OSM
nav_order: 2
layout: default
parent: Tools
---

# Fetching new names from OSM

## What it does

Since Pogo (and therefore Nest Watcher) use OpenStreetMap (OSM) data from early 2019 to determine nests, some of the parks with unknown names might have correct names already. This tool simply fetches current OSM data and updates area data.

Note that it will run through nests in your database and then write changes to the area_data file. So make sure your database is filled before running, and re-run the analyzer to have the changes reflect on your frontends.

## Running

Run `python3 tools.py` and choose the third `Update area_data using up-to-date OSM data` option by writing `3` in your terminal. Now, write the name of the area you want to update names in. The script will now let you approve each name pdate manually. You can either write `y` (yes) or `n` (no).