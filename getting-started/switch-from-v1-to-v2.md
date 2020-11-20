---
title: Switching from v1 to v2
nav_order: 2
layout: default
parent: Getting Started
---

# Switching from v1 (PMSFnestScript) to v2 (Nest Watcher)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Preparing files
To flawlessly update your nest script, clone Nest Watcher in a new directory and follow below steps. There's an integrated script that converts your config and area data to the new formats.

#### Clone, install pip requirements and copy the config

```bash
git clone https://github.com/M4d40/nestwatcher.git && cd nestwatcher
pip3 install -r requirements.txt
cp -r config_example config
```

## Setting up the database
Since you most lieklay already have a working nest database, you'll need to update it like this:

```bash
mysql -u {USER} -p {PASS} {DBNAME} < sql/update.sql
```

## Converting config files
By running `python3 tools.py` you can run a few tools, that make your life easier. For now, the important thing here is the Config converter. To access it, write `2` and then `1`. Now confirm and write the path to the old script. After it's done, you should see updated area data files in `data/area_data` and an updated config. Since not all options are supported, here's a list of the supported ones.

#### Supported config options
```ini
[Config]
pokestop_pokemon = x

[Scanner DB]
scanner = x
name = x
user = x
password = x
host = x
port = x

[Nest DB]
name = x
user = x
password = x
host = x
port = x

[Geojson]
path = x
default_park_name = x
stroke = x
stroke_width = x
stroke_opacity = x
fill = x
fill_opacity = x

[Discord]
language = x
```

## Configure the tool
There's a bunch of new config files to discover, for now I recommend focusing on `areas.json` and do the rest later. For help filling it in, [look here.](https://ccev.github.io/nestwatcher/configuration/config-files/areas.html)

## Running
To start Nest Watcher, just do `python3 nests.py`. Since it's getting OSM data on its first run, you will have to wait a while for it to finish. (10+ minutes until it's fully done)

It should now be finding nests and write them to your database. Now, it's all working fine, but you might want Discord notifications or refine your results. For that, visit [Additional steps](https://ccev.github.io/nestwatcher/getting-started/additional-steps.html)