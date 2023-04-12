**Question ([link](https://www.hackerrank.com/challenges/weather-observation-station-3))**

Query a list of **CITY** names from **STATION** for cities that have an even **ID** number. Print the results in any order, but exclude duplicates from the answer.
The **STATION** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where **LAT\_N** is the northern latitude and **LONG\_W** is the western longitude.

**My Solution**:

```sql
select distinct(CITY) from STATION 
where ID % 2 = 0
```
