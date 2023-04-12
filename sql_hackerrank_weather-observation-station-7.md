**Question ([link](https://www.hackerrank.com/challenges/weather-observation-station-7))**

Query the list of *CITY* names ending with vowels (a, e, i, o, u) from **STATION**. Your result *cannot* contain duplicates.

**Input Format**

The **STATION** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where *LAT\_N* is the northern latitude and *LONG\_W* is the western longitude.

**My Solution**:

```sql
select distinct(city) from station
where city like '%a'
or city like '%i'
or city like '%e'
or city like '%o'
or city like '%u'
```
