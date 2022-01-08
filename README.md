# Data Modeling with Cassandra
Udacity Project 2 of 6

# Sparkify Cassandra Database

An Apache Cassandra database sparkify for a music app, Sparkify. The purpose of the NoSQL database is to answer queries on song play data. 
The data model includes a table for each of the following queries:

    1. Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4
        query = "SELECT artist, song, length from songinfo_by_session_by_item WHERE sessionId=338 AND itemInSession=4"

    2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
        query = "SELECT artist, song, firstName, lastName FROM songinfo_by_user_by_session WHERE userId=10 AND sessionId=182"
    
    3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'
        query = "SELECT firstName, lastName FROM userinfo_by_song WHERE song='All Hands Against His Own'"

# Data pre-processing, ETL pipeline, and data modeling
The data are stored as a collection of csv files partitioned by date. (event_data)
The ETL pipeline and data modeling are written in a single jupyter notebook. (Project_1B_Project_Template.ipynb)

ETL copies data from the date-partitioned csv files to a single csv file event_datafile_new.csv which is used to populate the denormalized Cassandra tables optimised for the 3 queries above. 
The 3 tables in the model are named after the song play query they are created to solve:

    1. songinfo_by_session_by_item includes artist, song title and song length information for a given sessionId and itemInSessionId.

    2. songinfo_by_user_by_session includes artist, song and user for a given userId and sessionId.

    3. userinfo_by_song includes user names for a given song.
