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

