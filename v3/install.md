---
title: Installation
nav_order: 1
layout: default
parent: v3
---

# Basic installation

## Prerequisites

* [NodeJS](https://nodejs.org/en/) 8 or newer
* Dedicated [MySQL database](mysql.html) version 5.7.6 or newer


## Installation

1. Start by cloning the repository and switching to the v3 branch:  
   ```
   git clone https://github.com/KartulUdus/PoracleJS.git --branch v3
   ```

2.  Either create a [Discord Bot](../discordbot.html), add it to your server and take note of your token for later.
    
    or
   
    create a [Telegram Bot](../telegrambot.html), create a group and add the bot to it and note your token for later.

3. Copy the config file (`cp .env.example .env`) and fill out the required options like database credentials and bottoken.

4. Install package requirements:
    ```
    npm install
    ```

5. Start Poracle:
    ```
    npm start
    ```

6. That's it, now proceed to [Enter some commands](commands.html).
