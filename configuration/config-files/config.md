---
title: config.ini
nav_order: 1
layout: default
parent: Config files
grand_parent: Configuration
---

# config.ini

The config file can be used to define general variables used in Nest Watcher.

#### Path

```
config/config.ini
```

## Options

#### Config

| Variable | Description | What to put in |
|---|---|---|
| auto_time | Whether or not to automatically get the last migration time. If you set this to false, you have to define the hours since change using the -t argument. | True/False |
| events | Whether or not to automatically remove event spawns from the nesting species list. | True/False |
| less_queries | If turned on, the script will query all Mons and Spawns from the database at once for each area. Else, it will query them for every nest, putting a lot of load on your database. Depending on your setup, one option will be faster than the other. I recommend just testing out both. | True/False |
| pokestop_pokemon | Whether or not to use less-reliable Pokestop Pokemon to determine nests. If on MAD, this option will forcebly set to False. | True/False |
| i_scan_berlin | If turned on, the most common nesting species in your whole area will be ignored from further analyzations. This is useful if you're living in a meganest (with Berlin being really the only one world-wide currently) | True/False | 

#### Scanner DB / Nest DB

Since options for both Scanner DB and Nest DB are practically the same, both sections are being combined here.

| Variable | Description | What to put in |
|---|---|---|
| scanner | The type of Scanner backend you're using | mad/rdm |
| custom_pokemon_table | If you happen to store pokemon data in another table than `pokemon`. Can also be set to e.g. `backupdb.pokemon_history`. Not available in the default config, must be added on your own. | table name 
| name | The name of the database | Text |
| password | The password used to access the database | Text |
| user | The username used to access the database | Text |
| host | The host of the database | IP |
| port | The port of the database | Number |

#### Geojson

Since Geojsons are only used in PMSF, you can ignore most of this section if you're not using that. Just make sure to put `geojson.json` as the value for `path`

| Variable | Description | What to put in |
|---|---|---|
| path | The path to save the Geojson in | Text |
| default_park_name | The name to use if there's no name set on OSM | Text |
| stroke | The polygon's stroke color | Hex color |
| stroke_width | The polygon's stroke width | Number |
| stroke_opacity | The polygon's stroke color opacity | Number |
| fill | The polygon's fill color | Hex color |
| fill_opacity | The polygon's fill color opacity | Number |

#### Discord

| Variable | Description | What to put in |
|---|---|---|
| token | The token of yor Discord bot | Text |
| language | The language to translate Pokemon names in | en/de/es/fr |
| tileserver_url | The URL to your Tileserver (if you have one). Don't forget the trailing slash | URL |
| icon_repo | The Icon Repo to use for the Pokemon emotes and on static maps | URL |