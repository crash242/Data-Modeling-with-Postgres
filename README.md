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
