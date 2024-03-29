# ETL pipleine using Amazon Redshift

### Background
A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.
As their data engineer, I am tasked with building an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to. I'll be able to test the database and ETL pipeline by running queries given to me by the analytics team from Sparkify and compare my results with their expected results.

### Project Description
In this project, I have used data warehouses and AWS to build an ETL pipeline for a database hosted on Redshift. I loaded data from S3 to staging tables on Redshift and execute SQL statements that create the analytics tables from these staging tables.

### Datasets
* [Song Data](s3://udacity-dend/song_data)
    The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID.
* [Log Data](s3://udacity-dend/log_json_path.json)
    The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings.

### Schema for Song Analysis
Using the song and event datasets, I have created a star schema optimized for queries on song play analysis. This includes the following tables.
##### Fact Table
1. **songplays** - records in event data associated with song plays i.e. records with page `NextSong`
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

##### Dimension Tables
2. **users** - users in the app
    - user_id, first_name, last_name, gender, level
3. **songs** - songs in music database
    - song_id, title, artist_id, year, duration
4. **artists** - artists in music database
    - artist_id, name, location, lattitude, longitude
5. **time** - timestamps of records in **songplays** broken down into specific units
    -  start_time, hour, day, week, month, year, weekday

### Project Template
The project template includes four files:

`create_table.py` -  is where I have created fact and dimension tables for the star schema in Redshift.

`etl.py` is where i have load data from S3 into staging tables on Redshift and then process that data into your analytics tables on Redshift.

`sql_queries.py` is where i have defined you SQL statements, which will be imported into the two other files above.
    
