# ETL Project: Chicago Divvy vs Taxi Usage
A merge of Divvy and Taxi data in Chicago, aggregated by route

### Meet the Team Members
- __haneenammouri__ and __jzefron__ : team Taxi 
- __Michele-Lodl__ and __sponre01__ : team Divvy
- __ayang2012__ : team cloud-based database set-up

### Meet the Database

We made a database that includes Divvy Bike and Taxi trip data in Chicago, for the 2017 fiscal year (09-2016 to 08-2017). The motivation for this database is that we could potentially answer useful questions about transportation usage based on routes.

__Jupyter Notebooks__
 - [Divvy Trip Information](https://github.com/sponre01/ETL_Chicago_Divvy_vs_Taxi/blob/master/Divvy_Trips.ipynb)
 - [Taxi Trip Information](https://github.com/sponre01/ETL_Chicago_Divvy_vs_Taxi/blob/master/Taxi_trips.ipynb)
 - [Divvy Station (Location) Information](https://github.com/sponre01/ETL_Chicago_Divvy_vs_Taxi/blob/master/Divvy_Stations.ipynb)
 - [Taxi Census Track (Location) Information](https://github.com/sponre01/ETL_Chicago_Divvy_vs_Taxi/blob/master/census_track_location.ipynb)

## Extract
#### _Divvy_
 - Divvy source data: https://www.divvybikes.com/system-data. The files to download are: "2016 Q3 & Q4 DATA", "2017 Q1 & Q2 DATA" and "2017 Q3 & Q4 DATA"
 - The original data sources were csv files
 - Note: original csvs are too large for github! Simply download and put in a "Resources" folder to re-create the notebooks
 #### _Taxi_
 - Taxi source data: https://data.cityofchicago.org/Transportation/Taxi-Trips/wrvz-psew#column-menu
 - Data was obtained via the API: https://dev.socrata.com/docs/app-tokens.html
 
 
 
 
 
## Transform
#### _Divvy_
 - The raw csv files were loaded into pandas dataframes and appended to one another to form two dataframes, one including trip information and one including station information.
 - The trip dataframe included columns called "from_station_id" and "to_station_id", so we created those corresponding columns in the station dataframe in order to use the data collections together in our final database. 
 - The data from Divvy was already fairly clean. There were a few columns that included mostly NaN values that were dropped in the Station dataframe. In the Trip dataframe, the "start time" and "end time" columns were dropped to lighten the load. These were deemed redundant for our needs, since we already have a "trip_duration" column.
 - The stations from one quarter to another didn't change much, but we wanted to make sure to capture all stations that were relevant over our defined time period, so after appending all files together, we dropped duplicate rows.
#### _Taxi_
- Information was extracted using cityof chicago API(app token).
- Create an account on Chicago Data portal (https://data.cityofchicago.org/signup).
- To obtain an app token, register an application in the Socrata profile. Once the application is made, click on App Tokens in the left-hand navigation bar. The application token will be visible.
- We changed what objects to get from database by adding info in this select file to lighten the load
- The number of rows was limited to 1 million lines for this excersie. Can either increase the rows or use the value offset to the get code.
- The data was cleaned up removing NaN and extra columns that were not needed for the DataFrame.
 



## Load
  - The final database is hosted by cloud.mongodb.com, so nobody needs to store this locally
  - We chose to use a non-relational database, mongo, over sql because because mysql has a risk of timing out when loading large datasets; mongo db is more forgiving
  - Our collections are: _Divvy_Stations_, _Divvy_Trips_, _Taxi_Trips_, _Census_Track_
