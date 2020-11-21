---
title: settings.json
nav_order: 3
layout: default
parent: Config files
grand_parent: Configuration
---

# settings.json

Settings are used to define specific values for certain areas. This includes options to filter out nests, as well as Discord settings.

There's one entry called `DEFAULT` you can use to set options that will be used for all areas. To overwrite those values for certain areas, you can add new entries like in the example below. Just make sure that it always has the `"area"` key that matched a name from your `areas.json`.

#### Path

```
config/settings.json
```

### Example

```
[
    {
        "area": "DEFAULT",
        "min_pokemon": 9,
        "min_spawnpoints": 2,
        "min_average": 0.5,
        "min_ratio": 0,
        "scan_hours_per_day": 24,
        "max_markers": 30,
        "discord": null
    },
    {
        "area": "Berlin",
        "min_pokemon": 10,
        "min_average": 1,
        "max_markers": 1,
        "discord": 502074808662622208
    },
    {
        "area": "New York",
        "discord": "https://discord.com/api/webhooks/2786185391351/hblec87EH29nwmB82skjw18MEmdhd8ndD1L"
    }
]
```

### Options

| Variable | Description | What to put in |
|---|---|---|
| area | Required. Used to connect the entry to an area from areas.json. | Area name |
| min_pokemon | Total amount of Mons in a park for it to qualify as a nest. Basically lets you define a minimum samplesize to avoid false-positives. | Number
| min_spawnpoints | Total amount of spawnpoints a park needs to qualify. Probably the best way to sort out parks that are too small for your likings. | Number
| min_average | The minimum amount of average nest spawns per hour a park needs to qualify. Another good way to sort out small nests. | Number
| min_ratio | The average chance for a spawnpoint to have a nesting mon. This should always be 0.25. However, due to different reasons, the ratio value will rarely be close to 0.25. so I don't recommend using it in most cases. | Number
| scan_hours_per_days | The hours you scan this area per day. Used in the calculation for the hourly average. | Number
| max_markers | The maximum amount of markers per nest on a Static Map. If set to 1, the marker will be at the set center point. | Number
| discord | Either a Channel ID (if you want to use a bot) or a Webhook URL of a Discord channel. Make sure the ID is not put in `""`, but the Webhook URL is. | Channel ID/Webhook URL