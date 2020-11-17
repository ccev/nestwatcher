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

## Get the nest DB
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