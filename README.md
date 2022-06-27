Discuss the purpose of this database in the context of the startup, Sparkify, and their analytical goals
# Data modeling with Postgres
## Purpose
The purpose of this database  is to establish a postgres database and etl pipeline for the Sparkify analytics team to understand and analyze what songs users are listening to using thier new app.  CUrrently data is stored in JSON files and the analytics team is unable to query the dataset. The database must be optimized to analytical queries

## Running scripts
To execute the script, follow these steps:
1. open command prompt
2. create the database and tables
    `python create_tables.py`
3. run the etl script:
    `python etl.py`

## Explanation of the files in the repository
Data is stored in JSON file for both song data and log data.  
### Song Data
Each file contains data about a song, and the artist. The files are partitioned, and stored in directories by the first three letters of each song's track ID.  Ex: `song_data/A/B/C/TRABCEI128F424C983.json`.

Sample Data: ```JSON {"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}```

### Log Data
Activity logs for the streaming app is partitioned and stored in directories by year and month. Ex: `log_data/2018/11/2018-11-12-events.json'

## Database schema design and ETL pipeline.
The databse uses a star schema which is optimized for analytical queries.
### Fact table
#### songplays
|field_name|type|
|---|---|
|songplay_id (PK)|SERIAL|
|start_time|timestamp (NOT NULL)|
|user_id|int (NOT NULL)|
|level|varchar|
|song_id|varchar|
|artist_id|varchar|
|session_id|int|
|location|varchar|
|user_agent|varchar

### Dimension Tables
#### users 
|field_name|type|
|---|---|
|user_id|int|
|first_name|varchar|
|last_name|varchar|
|gender|varchar|
|level|varchar
#### songs 
|field_name|type|
|---|---|
|song_id|varchar|
|title|varchar|
|artist_id|varchar|
|year|int|
|duration|float
#### artists 
|field_name|type|
|---|---|
|artist_id|varchar (NOT NULL)|
|name|varchar|
|location|varchar|
|latitude|float|
|longitude|float
#### time 
|field_name|type|
|---|---|
|start_time|timestamp|
|hour|int|
|day|int|
|week|int|
|month|int|
|year|int|
|weekday|int