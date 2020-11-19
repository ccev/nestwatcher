---
title: Additional steps
nav_order: 3
layout: default
parent: Getting Started
---

# Additional steps
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Tools

Nest Watcher comes with a few useful tools that help you with renaming parks. I highly recommend [to fetch new names from OSM](https://ccev.github.io/nestwatcher/tools/fetching-new-names.html) after you first got your parks written to the DB. Then, you can to easily [define details for all parks using Disocrd](https://ccev.github.io/nestwatcher/tools/fetching-new-names.html).

## Discord Notifications

After Nest Watcher analyzes your area for nests, it can send a customizable summary to Discord, either using a bot or webhooks. Below you can see the advantages of each option.

To customize the Summary message, use [discord.json](https://ccev.github.io/nestwatcher/configuration/config-files/discord.html)

#### Bot

Bot messages are edited on each run. Also, it will automatically generate one emote for every nesting Pokémon you can then use for a better overview on your message. The disadvantage here being the 2048 character limit.

If you want to use your own icons, make sure to set the icon_repo in your config before running the script.

To set up a bot:
- Get a bot token [here](https://discord.com/developers/applications) and put it in the config.ini (if you want, you can use the token of another bot)
- Your bot can only be in a maximum of 3 servers while you run the script for the first time, in order to have it create its own servers to host emotes in.
- In your settings.json, add a `"discord": 12346892` field. Replace the number with the Channel ID you want the message to be posted in. For additional help, refer to the [settings.json documentation](https://ccev.github.io/nestwatcher/configuration/config-files/settings.html)

#### Webhooks

If you want to send more nests to Discord, use Webhooks. On each run, enough messages will be sent to your endpoint, to fit all nests that have been found. This does not support mon emotes and might cause spam if you want to run the script often.

To set it up, just get a Webhook link for the channel you want the messages in and add it to the `settings.json` like this: `"discord": "https://discord.com/api/webhooks/123/abc"`. For additional help, refer to the [settings.json documentation](https://ccev.github.io/nestwatcher/configuration/config-files/settings.html)

#### Static Maps

Discord messages are able to display a Static Map of the area, showing the nesting species spread across the parks. The amount of sprites represents the hourly spawn average there.

To set it up, install [Flo's tileserver](https://github.com/123FLO321/SwiftTileserverCache/), copy `nests.json` to the `Templates/` folder in the tileserver directory and put the tileserver url in your [config.ini](https://ccev.github.io/nestwatcher/configuration/config-files/config.html).

Maps could look messy if your area is too big. If so, adjust the `"max_markers"` field in the [settings.json](https://ccev.github.io/nestwatcher/configuration/config-files/settings.html). If the limit is 1, the sprite will be placed at the configures center point of the parks.