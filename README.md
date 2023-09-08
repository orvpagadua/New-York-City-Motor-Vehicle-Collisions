<img width="1132" alt="image" src="https://github.com/orvpagadua/New-York-City-Motor-Vehicle-Collisions/assets/122549893/94e5ad5b-69f9-442f-b1d8-d5f0ffaef613"># Making Queens Roads Safer

## *An In-depth Analysis into Motor Vehicle Collisions From 2012-2022*

![nyc-gfa32626b6_1920](https://user-images.githubusercontent.com/122549893/234608948-b3a6ab58-901a-48b7-a9ca-9d43a4fed0e9.jpg)

**Author**: Orville Pagaduan

## About the Dataset
Dataset Source: NYC Open Data - Motor Vehicle Collisions - Crashes
The foundation of our analysis lies in the extensive dataset obtained from NYC Open Data - specifically, the "Motor Vehicle Collisions - Crashes" dataset. This invaluable resource provides a comprehensive understanding of motor vehicle collision events within the five boroughs of New York City.
Dataset Details:
Each row in the dataset represents a unique crash event.
The data encompasses information from all police-reported motor vehicle collisions in NYC.
The dataset relies on the completion of the official police report form known as "MV104-AN," which is mandatory for collisions resulting in injuries, fatalities, or property damage exceeding $1000.
Data Quality and Updates:
It's important to note that the data is considered preliminary and may be subject to change. This can occur when the "MV-104AN" forms are updated to reflect revised crash details.
For the most accurate and up-to-date statistics on traffic fatalities, we recommend referring to the NYPD Motor Vehicle Collisions page, which is updated on a weekly basis. Additionally, Vision Zero View provides monthly updates on relevant data.
This dataset forms the cornerstone of our analysis, enabling us to identify trends, patterns, and contributing factors in motor vehicle collisions over the past decade. The quality and accuracy of this data are crucial in our mission to make NYC roads safer.
As we progress through this presentation, we will delve deeper into the insights and knowledge that this dataset offers, allowing us to make informed recommendations and work collectively toward a safer urban environment.

## Approach

THE PROBLEM -Have a good understanding of the problem statement - "How to reduce deaths and accidents in Brooklyn" based on 2012 - 2022 data.
PREP THE DATA - Got clarity of dataset, performed data cleaning (Duplicate entries, Null Values etc.) and exploratory data analysis using SQL queries 
DEEP DIVE - Prepped data & analyzed top collision causes. Carried out time series analysis & fatality analysis on different categories of road users 
INSIGHTS - Results were presented in a dashboard using PowerBI to allow stakeholders interact with the data and get more insights .
RECOMMENDATIONS - Provided recommendations based on insights obtained from the deep-dive for implementation. 


# SQL QUERIES

#### Obtaining `Earliest Date` in dataset
```
SELECT MIN(timestamp) 
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
LIMIT 10
```

#### Obtaining `Latest Date` in dataset
```
SELECT MAX (timestamp) 
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
LIMIT 10
```

#### Obtaining the `Total` number of rows in entire dataset
```
SELECT COUNT (*)
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
LIMIT 10
```

#### Checking for Duplicate Values based on Primary key
```
SELECT unique_key, COUNT (unique_key) 
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
GROUP BY unique_key
HAVING COUNT (unique_key)>1
LIMIT 10
```

#### Obtaining Total Number of in Dataset from 2012 to 2022 for New York
```
SELECT COUNT(*)
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
WHERE TIMESTAMP >='2012-01-01' AND TIMESTAMP <= '2022-12-31' 
LIMIT 1000
```

#### Obtain Total Number of in Dataset from 2012 to 2022 for Queens
```
SELECT COUNT(*)
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
WHERE borough ='QUEENS' AND TIMESTAMP >='2012-01-01' AND TIMESTAMP <= '2022-12-31' 
LIMIT 1000
```

#### Top Contributing Factors to `Collisions` for `New York` from 2012 to 2023
```
SELECT contributing_factor_vehicle_1, COUNT(contributing_factor_vehicle_1) AS COUNT
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
WHERE TIMESTAMP >='2012-01-01' AND TIMESTAMP <= '2022-12-31'
GROUP BY contributing_factor_vehicle_1
ORDER BY COUNT DESC 
LIMIT 1000
```

#### Top Contributing Factors to `Collisions` for `Queens` from 2012 to 2023
```
SELECT contributing_factor_vehicle_1, COUNT(contributing_factor_vehicle_1) AS COUNT
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
WHERE borough ='QUEENS' AND TIMESTAMP >='2012-01-01' AND TIMESTAMP <= '2022-12-31'
GROUP BY contributing_factor_vehicle_1
ORDER BY COUNT DESC 
LIMIT 1000
```

#### DOWNLODING THE RAW DATA FOR EXPORT TO POWERBI
```
SELECT *
FROM `bigquery-public-data-368005.nypd_motor_vehicle_collisions.nypd_mv_collisions`
WHERE TIMESTAMP >='2012-01-01' AND TIMESTAMP <= '2022-12-31' 
```

## Final Dashboard
<img width="1410" alt="image" src="https://github.com/orvpagadua/New-York-City-Motor-Vehicle-Collisions/assets/122549893/d256154a-dab6-4623-8e41-cdd6c7545b3a">


