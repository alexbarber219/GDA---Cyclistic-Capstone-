# GDA - Cyclistic-Capstone -
Cyclistic Case Study - Capstone, Google Data Analytics (May 2025)

Related Course: Google Data Analytics: Complete a Case Study

### Abstract

I, the acting Junior Data Analyst, will simulate a situation where a fictional company (Cyclistic) has requested a number of imporant business questions be answered. I will follow the steps of Data Analysis taught in the Google Data Analytics Course (Ask, Prepare, Process, Analyze, Share, and Act) to answer said questions.

* Data used in this study was sourced from https://divvy-tripdata.s3.amazonaws.com/index.html on 14/5/25
* Data visualisations were made in Tableau Public

### Brief

In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs. Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical data to identify trends.

## Ask
### Task

I have been assigned the following question by Moreno: How do annual members and casual riders use Cyclistic bikes differently?

* Business Task: to come up with pathway suggestions that will convert more casual riders to members going forward

## Prepare

* Data was provided via DIVVY and the City of Chicago, and made available to us via Data License Agreement
* Data was collected on 1st party basis indicating high integrity

12 csv files were collected with the naming convention of YYYYMM-divvy-tripdata spanning dates from May 2024 - April 2025, covering a 1 year period. As such, each file contained a month of data, with all files containing the following column names; ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.

### Data Shortcomings/Problems

No information was provided on the distance a rider had ridden during a trip; a rider could've riden the most direct route between their start and finish stations, or made multiple stops along the way. Also, many rows of blank data were found, suggesting a potential data collection error.

## Process

### Exploring the Data

Copies were made of each csv file before any edits were made. From early observations of each file, it was decided that station names and id's would not be useful in the analysis, consequently they (start_station_name, start_station_id, end_station_name, end_station_id) were removed from all csv files. The following columns were added to each file having exrtracted the information from the data already within each table; ride_length, day_of_week, month, start_time.

All csv files were the uploaded into SQLite for analysis. Excel was used for brief edits and not analysis due to the millions of rows of data that the combined files contained.

Once uploaded, all 12 files were combined into one table titled 'combined_bike'.

### Data Assesment

* The total number of rows of the 'combined_bike' table were checked = 5,735,884 rows

* The number of NULL values in all columns were counted; end_lat and end_lng both had 6399 NULL values, so both of they and thier coresponding 'start' columns were removed.

* Ride_id was used to check for duplicates; 220 were found, and consequently removed

* The number of each rideable_type were counted; classic_bike = 2,533,829  electric_bike = 3,057,718  electric_scooter = 144,337

* The distinct types of rider were checked in the member_casual column; only 'casual' and 'member' were found

### Data Cleaning

A new table title 'combined_bike_cleaned' was created from 'combined_bike' including the following columns; ride_id, rideable_type, member_casual, ride_length, day_of_week, and month. To provide a more accurate picture, bike trips shorter than 1 minute and longer than 1 day were removed from this new table (132,899 rows).

## Analyze/Share

* To create visualisations, the 'combined_bike_cleaned' table was exported from SQLite as a csv file and then uploaded into Tableau Public

To begin, the difference between 'Casual' and 'Member' types were displayed:

![total riders](https://github.com/user-attachments/assets/d2e5a50b-faf1-4fa8-b7af-e6bf15ad2f13)

As can be seen, 'member' riders make up a significantly larger portion of the people using Cyclistic bikes during the assesment period.

Following this, the number of trips over each week day, month, and start time over the assesment period were analyzed.

For each of the following visualisations, data is split by member and casual, with casual always as blue and member always displayed as orange.

![membercasual](https://github.com/user-attachments/assets/fa93dc8c-258c-4b6b-b0cc-84b95fd5b980)

![day_of_week](https://github.com/user-attachments/assets/9819f2a9-24d0-4780-ad07-f33359f55bd1)

![month](https://github.com/user-attachments/assets/2eebde78-af0f-416f-85f3-36fcd7094e6c)

![start_time](https://github.com/user-attachments/assets/f3849e11-009e-4dc4-96f5-635f1d1f94b8)
