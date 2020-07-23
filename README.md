# Purpose

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app.

Their analytics team is very much interested in knowing the music taste of their users which is hard for them as they do not have currently an easy way of querying their data residing in a directory of JSON logs on user activity on the app and directory with JSON metadata on the songs in their app.

The company wants a data engineer to make a Postgres database in order to make queries on song play analysis.

As the data is in the form of JSON files (song and log datasets), a star schema is created in this project for sparkify in order to run optimised queries on the tables made.

# Star Schema
In the star schema, we have a ``Fact Table `` called as ``songplays`` and various ``dimension Tables`` such as ``users``, ``songs``, ``àrtists`` and ``time``

## Fact Table
* songplays -  records in log data associated with song plays
    * Columns - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

## Dimension Table
* users - users in the app
    * Columns - user_id, first_name, last_name, gender, level
* songs - songs in music database
    * Columns - song_id, title, artist_id, year, duration
* artists - artists in music database
    * Columns - artist_id, name, location, latitude, longitude
* time - timestamp of records in songplays broken down into specific units
    * Columns - start_time, hour, day, week, month, year, weekday

# ETL pipeline 

The ETL pipeline consists of creation of fact table and various dimension tables.
* ``songs`` table is created by extracting the data from ```data/song_data``` folder
* ``artists`` table is created by extracting the data from ```data/song_data``` folder
* ``time`` table is created by extracting the data from ```data/log_data``` folder
* ``users`` - table is created by extracting the data from ```data/log_data``` folder
*  ``songplays`` - table is created from dimensions table and the data from ```data/log_data``` folder

# How to get Started

Please follow the below steps in order to get the project running:
* Make sure the project consists of the following files:
    * ``etl.ipynb`` - This is jupyter workbook to create the pipeline
    * ``create_tables.py`` - Script to initiate the database connection and create tables and drop tables.
    * ``etl.py`` - Script defining the complete ETL pipeline.
    * ``sql_queries.py`` -  It contains create and insert statements for the database.
    * ``data`` - Folder contains the data files to be processed
    * ``test.ipynb`` - Jupyter workbook to check the creation of database and tables and addition of data inside the tables.
* when all the files are in place, now we are ready to run the project as:
    * First run ``create_tables.py`` script in order to drop and create the database and tables.
    * Now run the ``etl.py`` script in order to extract the data from song and log dataset and inserting them in the facts and dimensions table.
