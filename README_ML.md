# ETL_Chicago_Divvy_vs_Taxi
A merge of Divvy and Taxi data in Chicago, aggregated by route


Focus on fiscal year: 09-2016 to 08-2017
- Divvy data source: https://www.divvybikes.com/system-data
- Taxi data source: https://data.cityofchicago.org/Transportation/Taxi-Trips/wrvz-psew#column-menu


The Jupyter Notebook File currently has the data for the date range listed above. 

There are 10 CSV files across three zips package. 
The zip packages contain two sets of data: stations and trips. 
- Divvy_Trips_2016_Q3Q4.zip
- Divvy_Trips_2017_Q3Q4.zip
- Divvy_Trips_2017_Q1Q2.zip

# This notebook is for the trips data only. 

To combine trip data with stations, add a column to stations that is "from_station_id" and is a duplicate of "id" in the stations csv. 



