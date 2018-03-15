# Amplitude > Google Cloud Storage > Google BigQuery
Export your [Amplitude](https://amplitude.com/) data to [Google BigQuery](https://bigquery.cloud.google.com) for big data analysis.
This script will download all events & properties from the Amplitude
Export API, parse the data and prepare a data job for Google BigQuery
by storing the data for backup purposes in [Google Cloud Storage](https://cloud.google.com/storage/).

Read more about this integration [here](http://www.martijnscheijbeler.com/import-amplitude-into-google-bigquery/) on the blog of [Martijn Scheijbeler](http//www.martijnscheijbeler.com).

[![forthebadge](https://forthebadge.com/images/badges/fuck-it-ship-it.svg)](https://forthebadge.com)


## Features / Support
* Download data for a full day from Amplitude using the Export API
* Parse the data to match data types in Google BigQuery
* Export new parsed files for a load data job in Google BigQuery
* Store backup data in Google Cloud Storage
* Cleans up after use, all temporary files will be deleted.


## Quick start:
1. Clone this repository: `git clone git@github.com:MartijnSch/amplitude-bigquery.git`
2. Fill in your Amplitude Account ID: `ACCOUNT_ID`, you can find this in Amplitude under your account settings: Settings > Projects
3. Fill in your Amplitude API Key & Secret Key, you can find this in Amplitude under your account settings: Settings > Projects
4. [Create a new project on Google Cloud Platform](https://console.cloud.google.com/home/dashboard)
5. Add the Project ID to the script
6. Activate Google Cloud Storage and Google BigQuery + filled in your billing details
7. Create a bucket in Google Cloud storage with two folders: `export` & `import`
8. Load both schemas (`bigquery-schema-events.json` & `bigquery-schema-events-properties.json`) into Google BigQuery to create the tables
9. Adjust the Constant variables in `amplitude-bigquery.py`
10. Run the script via: `python amplitude-bigquery.py`
11. Look at the backup files in Google Cloud Storage and see the data in Google BigQuery


## BigQuery Schemas

To add the events and events properties to Google BigQuery you'll need to create the two tables. You'll find the JSON schema in the files in this repository, these are the Schema Text fields that you can also use.

![Create a new table in BigQuery](https://monosnap-m.s3.amazonaws.com/Google_BigQuery_2018-03-15_11-10-05.png)

*Events:* 
```
client_event_time:TIMESTAMP,ip_address:STRING,library:STRING,dma:STRING,user_creation_time:TIMESTAMP,insert_id:STRING,schema:INTEGER,processed_time:TIMESTAMP,client_upload_time:TIMESTAMP,app:INTEGER,user_id:STRING,city:STRING,event_type:STRING,device_carrier:STRING,location_lat:STRING,event_time:TIMESTAMP,platform:STRING,is_attribution_event:BOOLEAN,os_version:INTEGER,paying:BOOLEAN,amplitude_id:INTEGER,device_type:STRING,sample_rate:STRING,device_manufacturer:STRING,start_version:STRING,uuid:STRING,version_name:STRING,location_lng:STRING,server_upload_time:TIMESTAMP,event_id:INTEGER,device_id:STRING,device_family:STRING,os_name:STRING,adid:STRING,amplitude_event_type:STRING,device_brand:STRING,country:STRING,device_model:STRING,language:STRING,region:STRING,session_id:INTEGER,idfa:STRING
```

*Events Properties:*
```
property_type:STRING,insert_id:STRING,key:STRING,value:STRING
```

## History
#### March 20, 2018
* Initial Commit: Add the support for exporting Amplitude data to Google BigQuery.


## Want to contribute?
Contributions are welcome! There are just a few requested guidelines:

* Please create a feature branch for your changes and squash commits.
* Don't worry about updating the version, changelog, or minified version.
* Please respect the original syntax/formatting stuff.
* If proposing a new feature, it may be a good idea to create an issue first to discuss.


## Maintainer history
  * [Martijn Scheijbeler](https://github.com/martijnsch) (Current)