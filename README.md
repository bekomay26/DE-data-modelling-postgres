# Data Modelling with Postgres


## Overview

This project builds an ETL pipeline to create, fetch, process, and populate DB for the music streaming app Sparkify.
It has a Postgres database with tables designed to optimize queries on song play analysis.
It has a star schema - 1 fact table `songplay` and a few supporting tables. 

## Structure

The project contains the following elements:
* `create_tables.py` connect and creates the database and tables
* `sql_queries.py` contains the SQL queries for creating and inserting
* `etl.ipynb` and `test.ipynb` test the ETL pipeline
* `etl.py` defines the ETL pipeline
* `data/` contains song and log JSON files

## Schema

### Fact Table 
- **songplays** - records in log data associated with song plays i.e. records with page `NextSong`  
> songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

### Dimension Tables
- **users** - users in the app
> user_id, first_name, last_name, gender, level  
- **songs** - songs in music database
> song_id, title, artist_id, year, duration
- **artists** - artists in music database
> artist_id, name, location, latitude, longitude
- **time** - timestamps of records in songplays broken down into specific units
> start_time, hour, day, week, month, year, weekday

## Instructions

Open terminal and enter the following:

```
python3 create_tables.py
python3 etl.py
```


## Query Example

Test with the following queries:

```
# Connect to database
%load_ext sql
%sql postgresql://student:student@127.0.0.1/sparkifydb

# First 5 songs
%sql SELECT * FROM songs LIMIT 5;

# Count the number of artists
%sql SELECT COUNT(*) FROM artists;

# Count the number of song plays by user with id = 69
%sql SELECT COUNT(*) FROM songplays WHERE user_id = 69;

```