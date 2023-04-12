**Question ([link](https://www.hackerrank.com/challenges/weather-observation-station-10))**

Query the list of *CITY* names from **STATION** that *do not end* with vowels. Your result cannot contain duplicates.

**Input Format**

The **STATION** table is described as follows:
![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where *LAT\_N* is the northern latitude and *LONG\_W* is the western longitude.

**My Solution**:

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '[aeiou]$'
```
