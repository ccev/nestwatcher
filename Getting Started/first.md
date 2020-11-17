---
title: First time install
nav_order: 1
layout: default
parent: Getting Started
---

# First time install
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Preparing files
Clone the repo, install pip requirements and copy the config.
```bash
git clone https://github.com/M4d40/nestwatcher.git && cd nestwatcher
pip3 install -r requirements.txt
cp -r config_example config
```

## Set up your database
Steps to prepare your database will look different depending whether or not you have PMSF (and its manualdb) fully set up.

### No PMSF manuladb
```bash
mysql -u {USER} -p {PASS} {DBNAME} < sql/nests.sql
```
_If you're running RocketMAD, you'll have to replace `{DBNAME}` with your MAD DB name, else it's up to you what database to use_

### With PMSF manualdb
```bash
mysql -u {USER} -p {PASS} {MANUALDB} < sql/update.sql
```

## Configure the tool
Now `cd config` and fill out the files. For your first run, it's enough to focus on the DB credentials in `config.ini` and geofences in `areas.json`. You can do the rest later. If you need help filling them out, refer to #TODO

## Running
To run Nest Watcher, just run `python3 nests.py`. Since it's getting OSM data on its first run, you will have to wait a while for it to finish. (10+ minutes until it's fully done)

It should now be finding nests and write them to your database. Now, it's all working fine, but you might want Discord notifications or refine your results. For that, visit #TODO