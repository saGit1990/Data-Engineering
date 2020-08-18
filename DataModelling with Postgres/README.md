# Data Modelling with Postgres Project

## Over view of the project

### Introduction

Sparkify is a music streaming app start up company, they've been collecting data on user activity and songs on their music streaming app. The analytics team is particularly interested in understanding what songs users are listening too. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

### Goal

Sparkify wants a Postgres database with tables designed to optimize queries on song play analysis. The goal is to create a database and ETL pipeline to optimize queries to help Sparkify's analytics team.

## Files in the repository

### sql_queries.py

This file contain series of postgres commands for creating new tables and inserting data into those tables. Each table has its own primary key and this primary key is used to query information (select statement) about songs.

### create_tables.py

This files consist of following set of function that perform a particular set of tasks:

> create_database()
>> Creates and connects to the sparkifydb
>> Returns the connection and cursor to sparkifydb

> drop_tables()
>> Drops each table using the queries in sql_queries.py file.

> create_tables()
>> create new table using the queries in sql_queries.py file.

> main()
>> - Drops (if exists) and Creates the sparkify database. 
>> - Establishes connection with the sparkify database and gets cursor to it.  
>> - Drops all the tables.  
>> - Creates all tables needed.  
>> - Finally, closes the connection. 

### etl.py / etl.ipynb
> this notebook read the JSON logs files and perform some transformation so that data can be added to different tables

### test.ipynb
> This notebook is to check whether the operations we perfomr an etl.py is giving us the expected output.

## Database schema

Using the songs and log dataset, I have created a start schema, that inlcudes:
> one fact table - songplays
>> - songplays_id (PRIMARY KEY)
>> - start_time
>> - user_id  (FOREIGN KEY)
>> - level
>> - duration
>> - song_id (FOREIGN KEY)
>> - artist_id (FOREIGN KEY)
>> - location
>> - user_agent

> four dimension tables
>> users
>>> - user_id (PRIMARY KEY)
>>> - first_name
>>> - last_name
>>> - gender
>>> - level

>> songs
>>> - song_id (PRIMARY KEY)
>>> - title
>>> - artist_id
>>> - year
>>> - duration

>> artists
>>> - artist_id (PRIMARY KEY)
>>> - name
>>> - location
>>> - latitude
>>> - longitude

>> time
>>> - start_time (PRIMARY KEY)
>>> - hour
>>> - day
>>> - week
>>> - month
>>> - year
>>> - weekday

## How to run a the files?

On python terminal, run the following commands in order
> - python create_tables.py
> - python etl.py

