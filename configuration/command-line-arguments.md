---
title: Command line arguments
nav_order: 3
layout: default
parent: Configuration
---

# Command line arguments

You can use arguments to define certain values when running Nest Watcher.

---

#### Argument
```
-nd
--nodelete
```
This would stop the script from deleting nests from the database.

---

#### Argument
```
-a [AREANAME]
--area [AREANAME]
```
To only analyze a specific area. Useful for testing.

---

#### Argument
```
-t [NUMBER]
--hours [NUMBER]
```
To specify a custom amount of hours since the last migration happened. Usually, the script will get this number automatically.

---

#### Argument
```
-c [PATH]
--config [PATH]
```
Used to define another config file, in case you don't want to use `config/config.ini`.

---

#### Argument
```
-ne
--noevents
```

If you don't want the script to ignore event Pokémon.