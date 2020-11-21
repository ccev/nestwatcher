---
title: areas.json
nav_order: 2
layout: default
parent: Config files
grand_parent: Configuration
---

# areas.json

This file defines the areas you want to analyze nests in. Each area listed will be used. It's using the same format as Poracle, Discordopole and all the other Watchers, so if you're using on of those tools, you can copy it from there. Below is another methos you can use to make geofences.

Note that capitalization is important everywhere you type in the areaname.

#### Path

```
config/areas.json
```

### Example

```json
[
    {
        "name": "Tokyo",
        "path": [
            [
                139.57271575927734,
                35.71557676488898
            ],
            [
                139.5754623413086,
                35.61153436353458
            ],
            [
                 139.74094390869138,
                 35.62046556900037
            ],
            [
                 139.82093811035156,
                35.67988848691441
            ],
            [
                 139.7739028930664,
                35.754871141690366
            ],
            [
                 139.70661163330078,
                 35.775485962767995
            ],
            [
                 139.57271575927734,
                 35.71557676488898
            ]
        ]
    },
    {
        "name": "Busan",
        "path": [
            [
                128.90533447265625,
                35.068221159859256
            ],
            [
                 129.38323974609375,
                35.21645362659458
            ],
            [
                129.06463623046875,
                35.46961797120201
            ],
            [
                 128.90533447265625,
                35.068221159859256
            ]
        ]
    }
]

```

### How to generate a JSON in this format

Since poracle.world is not around anymore, the best option I know of would be to go to <http://geojson.io/>, draw a polygon and copy the part after `"coordinates"` on the right side, then bring that in the right format.