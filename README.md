# Data-Modeling-using-Postgres
Creating a Postgres Star schema and ETL that loads raw data from json files.
This is the First project in the Udacity's data engineering course , it consists of creating a Database schema , and a Python ETL pipline that pulls raw data from json files.

Context : 


A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. 
The analytics team is particularly interested in understanding what songs users are listening to. 
Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.


Data:

song_data : all json files are nested in subdirectories under */data/song_data*. A sample of this files is:
```
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```
log_data : all json files are nested in subdirectories under */data/log_data*. A sample of a single row of each files is:

```
{"artist":"Slipknot","auth":"Logged In","firstName":"Aiden","gender":"M","itemInSession":0,"lastName":"Ramirez","length":192.57424,"level":"paid","location":"New York-Newark-Jersey City, NY-NJ-PA","method":"PUT","page":"NextSong","registration":1540283578796.0,"sessionId":19,"song":"Opium Of The People (Album Version)","status":200,"ts":1541639510796,"userAgent":"\"Mozilla\/5.0 (Windows NT 6.1) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"","userId":"20"}
```
Database Postgres Modeling : 


The schema used for this exercise is the Star Schema: 
There is one main fact table containing all the measures associated to each event (user song plays), 
and 4 dimentional tables, each with a primary key that is being referenced from the fact table.

On why to use a relational database for this case:
- The data types are structured (we know before-hand the sctructure of the jsons we need to analyze, and where and how to extract and transform each field)
- The amount of data we need to analyze is not big enough to require big data related solutions.
- Ability to use SQL that is more than enough for this kind of analysis
- Data needed to answer business questions can be modeled using simple ERD models
- We need to use JOINS for this scenario
