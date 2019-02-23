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


# Extract 

- When: Analysis Timeframe: Fiscal Year 09-2016 to 08-2017

- What: Divvy Trips Data

- How (link): https://www.divvybikes.com/system-data

- How (cvs_files from the following zips located on link page above): 2016 Q3 & Q4 DATA; 2017 Q1 & Q2 DATA; 2017 Q3 & Q4 DATA


# ### Here is the web page screen shot


# ![image.png](attachment:image.png)

### Extract Coding Steps
- Import Dependencies and Setup. Use Pandas and Numpy libraries. 
- Read each Divvy Data File and store into Pandas DataFrame


### Transform coding steps 

- Read each Divvy Data File and store into Pandas DataFrame

- Combine Trips Divvy Data File and store into Pandas DataFrame

- Print dataframe to assess number of rows and gage general integrity of the data

- Assess the data and drop the columns that might not be relevant to final analysis.

- For this scenario (v. Taxis) we dropped the following: 'starttime','end_time','stoptime','start_time', 'gender','birthyear'



# Load

### Code to Load data 

- Upload the df into the Mongo Database. This is a way to store the data in a cloud. (If you receive and error, you may need to intall dnspython to connect.) 

- We are using a cloud-based database (hosted by cloud.mongodb.com) so nobody needs to store this locally

- Import pymongo allows to use python to connect to a Mongo DB database 

- Establish a connection to the database 

- Create a client connecting to the database. This allows data to be loaded from python into the database

- Establish a database in Mongo DB 

- Convert the Pandas DataFrame to a dictonary to be uploaded into Mongo DB

- Insert the data into the Mongo DB database




