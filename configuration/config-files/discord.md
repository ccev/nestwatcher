---
title: discord.json
nav_order: 4
layout: default
parent: Config files
grand_parent: Configuration
---

# discord.json

This file is used to customize Discord messages. It's a JSON consisting of two parts. I call this the first and the second part.

#### Path

```
config/discord.json
```

### Example

```
[{
    "title": "Nests in {areaname}",
    "description": "{nest_entry}",
    "image": {
        "url": "{staticmap}"
    }
},
{
    "nest_entry": "{mon_emoji} {mon_name}{shiny} ({mon_avg}/hr): **{park_name}**\n",
    "sort_by": "mon_avg",
    "min_avg": 1,
    "ignore_unnamed": false
}]
```

## First part

The first part is a raw discord embed JSON. To see how such embed works, you can use a generator like [this one](https://leovoel.github.io/embed-visualizer/). Listed below are variables you can use within this embed, jst make sure to put them in `{}`.

- **Note for Bots**: The bot matches the title of the embed, when it's searching a message to edit. So make sure not to put a variable in it that changes on every run. Also, if you want multiple messages in one channel, you'll have to put `{areaname}` in the title.

### Variables

| Variable | Description |
|---|---|---|
| {nest_entry} | The nest entry defined in the second part. Recommended to be the only value for `"description"`. | 
| {areaname} | The name of the area the message summarizes nests of |
| {staticmap} | The Static Map (if used). Recommended to be the only value for `"image"-"url"`
| {current_time} | A timestamp of when the message was sent. Recommended to be the only value for `"timestamp`. |

## Second part

Options to customize in the second part:
- **nest_entry**: How a single nest will be displayed as
- **sort_by**: What value to sort nests after
  - Possible options: `mon_avg`, `mon_count`, `mon_ratio`, `mon_id`, `park_name`
- **min_avg**: If you want an additional filter for Discord messages
- **ignore_unnamed**: Whether or not to ignore unnamed parks

### Variables in nest_entry

| Variable | Description |
|---|---|---|
| {park_name} | Name of the park |
| {lat} / {lon} | Latitude and longitude (coordinates) of the park |
| {mon_id} | The nesting Mon's ID
| {mon_avg} | Average amount of nest spawns per hour
| {mon_count} | Total amount of nesting mon's found
| {mon_ratio} | Average chance for a spawnpoint to spawn a nesting mon
| {mon_emoji} | Icon of the nesting mon (as an emote) (only supported for bots)
| {type_emoji} | An emote that represents the nesting mon's type. If it has two, they will be seperated with a `/`
| shiny | An emote if the nestin mon is available in it shiny form