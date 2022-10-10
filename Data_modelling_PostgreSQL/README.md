# Sparkify PostgreSQL DB ETL

## Project summary
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

In particular the data, in JSON format, are nested in subdirectories in `data/song_data` and `data/log_data`.
The schema implemented in the project is the so called *star schema*, composed of one fact table (`songplays`) and 4 dimention tables (`users`,
`songs`, `artists` and `time`). The fact table contains all the measures associated to each event (which user is listening to which song). The dimention tables have a primary key that is being referenced from the fact table.

The goal of the project is to create a PostgreSQL database with tables designed to optimize queries on song play analysis.
The script, create_tables.py, runs in the terminal without errors. The script successfully connects to the Sparkify database, drops any tables if they exist, and creates the tables.

## Description of the files in the repository
The repostory contains:
- **data** folder, where all JSON data file are
- **sql_queries.py** script, that contains all the sql queries to create tables, insert the data into them and drop the tables.
- **create_tables.py** script, that connects to the Sparkify database, drops and creates tables. This file should be run before running ETL scripts.
- **test.ipynb** notebook, that displays the first few rows of each table to let you check your database. It contains also a *sanity check*.
- **etl.ipynb** notebook, that connects to the Sparkify database, reads and processes data from a single file in song_data and log_data and loads them into the tables.
- **etl.py** script, that connects to the Sparkify database, reads and processes files from song_data and log_data and loads them into the five tables.

## How to run the Python scripts / passages followed to develop the project
1) Completed DROP, CREATE and INSERT query in **sql_queries.py**
2) Run in terminal 

    `` python create_tables.py 
    ``

3) Run `test.ipynb` notebook to verify that all tables were created correctly.
4) Completed `etl.ipynb` notebook to insert the data from a single file in song_data and log_data into tables.
5) Run `test.ipynb` notebook to verify that all the entries were inserted correctly.
6) Completed `etl.py` and run it in terminal  

    `` python etl.py 
    ``

7) Run once again `test.ipynb` to check the tables and run (and passed) the *sanity check*

