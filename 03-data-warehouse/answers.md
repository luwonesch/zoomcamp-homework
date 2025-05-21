# Module 3: Data Warehouse

## ✅ Question 1

**How many records are in the green_tripdata_2019 table?**

**Answer**: `630,918`

**Query:**
```sql
SELECT COUNT(*) AS total_rows
FROM `data-engineering-course-460007.trips_data_all.green_tripdata_2019`;


## ✅ Question 2

**Which VendorID has the highest number of trips in January 2019?**  
**Answer**: `VendorID = 2`

**Query:**
```sql
SELECT
  VendorID,
  COUNT(*) AS num_trips
FROM `data-engineering-course-460007.trips_data_all.green_tripdata_2019`
GROUP BY VendorID
ORDER BY num_trips DESC;

## ✅ Question 3

**Which day had the largest number of trips in January 2019?**  
**Answer**: `2019-01-25` with `24,399` trips

**Query:**
```sql
SELECT
  DATE(lpep_pickup_datetime) AS trip_date,
  COUNT(*) AS num_trips
FROM `data-engineering-course-460007.trips_data_all.green_tripdata_2019`
GROUP BY trip_date
ORDER BY num_trips DESC
LIMIT 1;

## ✅ Question 4

**What is the number of distinct PULocationID values in January 2019?**  
**Answer**: `256`

**Query:**
```sql
SELECT
  COUNT(DISTINCT PULocationID) AS num_unique_pulocation_ids
FROM `data-engineering-course-460007.trips_data_all.green_tripdata_2019`
WHERE DATE(lpep_pickup_datetime) BETWEEN '2019-01-01' AND '2019-01-31';

## ✅ Question 5

**What is the busiest hour of the day for pickups in January 2019?**  
**Answer**: `18:00 (6 PM)` with `43,597` trips

**Query:**
```sql
SELECT
  EXTRACT(HOUR FROM lpep_pickup_datetime) AS pickup_hour,
  COUNT(*) AS num_trips
FROM `data-engineering-course-460007.trips_data_all.green_tripdata_2019`
GROUP BY pickup_hour
ORDER BY num_trips DESC
LIMIT 1;

