# Making Queens Roads Safer

## *An In-depth Analysis into Motor Vehicle Collisions From 2012-2022*

![nyc-gfa32626b6_1920](https://user-images.githubusercontent.com/122549893/234608948-b3a6ab58-901a-48b7-a9ca-9d43a4fed0e9.jpg)

**Author**: Orville Pagaduan

## Overview
## Business Problem
## Data
## Methods
### Cleaning and EDA
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
[NEWYORKMOTORCOLLISIONS.pdf](https://github.com/orvpagadua/New-York-City-Motor-Vehicle-Collisions/files/11581991/NEWYORKMOTORCOLLISIONS.pdf)

## Conclusions
## Next Steps

