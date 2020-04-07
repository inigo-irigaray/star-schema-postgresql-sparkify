# Sparkify Music App Log and Songs Relational Databases 

## Challenge

<p align=justify>A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.</p>

<p align=justify>They'd like a data engineer to create a PostgreSQL database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.</p>

## Project Description

### Data

<p align=justify>The first dataset is a subset of real data from the <a href=https://labrosa.ee.columbia.edu/millionsong/>Million Song Dataset</a>. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.</p>

<p align=justify>The second dataset consists of log files in JSON format generated by this <a href=https://github.com/Interana/eventsim>event simulator</a> based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations. The log files in the dataset you'll be working with are partitioned by year and month. </p>

### ERD

<p align=center><img src=https://github.com/inigo-irigaray/star-schema-postgresql-sparkify/blob/master/imgs/sparkify_schema.png> </a></p>

## Code Description

### ``sql_queries.py``

<p align=justify>The script specifies the SQL commands to DROP and CREATE the songplays, users, songs, artists and time tables in the relational database, as well as the INSERT command to fill in the data and a specific SELECT utility command to help in the processing of data for the songplays table.</p>

### ``create_tables.py``

<p align=justify>The script defines the functions to create the Sparkify relational database, create and drop the five tables aforementioned from the imported SQL commands in the previous script. It can be run as standalone to create empty tables or as part of the ETL pipeline in the following script.</p>

### ``etl.py``

<p align=justify>The script extracts, transforms and loads the data into the required tables in the Sparkify database from the song and log files in JSON format. It can additionally create the required tables and dataset if predetermined by the user with the --create_db argument in the command line.</p>

## Running the Code

### Option 1. Creating Databases and Tables from Scratch:

#### <p align=justify><b>1.A. Creating the Sparkify database and tables required from ``create_tables.py``first, and then extracting, transforming and loading the data from ``etl.py``: </b></p>

        $python3 create_tables.py
        $python3 etl.py
      
#### 1.B. Performing all actions directly from ``etl.py``:

        $python3 etl.py --create_db
        
### Option 2. Extracting, transforming and loading the data into the required existing tables and database:

        $pyhton3 etl.py
