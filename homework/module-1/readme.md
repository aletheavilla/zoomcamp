# Module 1 Homework
## Answers
1. 24.3.1
2. localhost:5432
3. 104,802; 198,924; 109,603; 27,678; 35,189
4. 2019-10-31
5. East Harlem North, East Harlem South, Morningside Heights
6. JFK Airport
7. terraform init, terraform apply -auto-approve, terraform destroy

# SQL Queries
Question 3
```
SELECT COUNT(lpep_pickup_datetime)
FROM taxi_db.green_taxi
WHERE trip_distance <= 1 -- vary based on the distance params
```
Question 4
```
SELECT *
FROM taxi_db.green_taxi
ORDER BY trip_distance DESC
```
Question 5
```
SELECT 
    PULocationID,
    SUM(total_amount) as cum_total_amount
FROM taxi_db.green_taxi as t
INNER JOIN taxi_db.taxi_zone as z
    ON t.PULocationID = z.LocationID
WHERE
    lpep_pickup_datetime >= '2019-10-18' 
    AND lpep_pickup_datetime < '2019-10-18' 
GROUP BY PULocationID
ORDER BY cum_total_amount DESC
```
Question 6
```
SELECT 
    DOLocationID,
    MAX(tip_amount) as max_tip
FROM taxi_db.green_taxi as t
INNER JOIN taxi_db.taxi_zone as z
    ON t.DOLocationID = z.LocationID
WHERE
    lpep_pickup_datetime >= '2019-10-01' 
    AND lpep_pickup_datetime < '2019-11-01' 
GROUP BY DOLocationID
ORDER BY max_tip DESC
```