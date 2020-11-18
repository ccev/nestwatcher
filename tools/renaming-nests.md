---
title: Renaming Nests
nav_order: 1
layout: default
parent: Tools
---

# Renaming Nests using Discord

## Requirements
- Needs a set Discord token in the config
- The Discord bot needs "Manage Messages" permission
- Highly recommended: A set Tileserver URL

## What it does

![](https://images-ext-2.discordapp.net/external/TI0z-v7fm18OQ3-L0ZkZ20ZmgHXQLRGbt2kfRFvS_Fg/http/g.recordit.co/TpnelqNRli.gif)

The Script lets your Discord bot go through each of your nests one-by-one, allowing you to set a new name or change its center coordinates. Each message shows the name, center coordinates, an OpenStreetMap link, a Google Maps link and a Static Map (if enabled) of the nest, making it easy to determine which nest you're currently editing.

Note that it will run through nests in your database and then write changes to the area_data file. So make sure your database is filled before running, and re-run the analyzer to have the changes reflect on your frontends.

## Running

Run `python3 tools.py` and choose the first `Update area_data using Discord` option by writing `1` in your terminal. Now, write the name of the area you want to edit nests in. Finally, go to a channel your bot has access to and say `start`. The bot will give you instructions on how to control it and then start the process.