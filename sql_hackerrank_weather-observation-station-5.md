**Question ([link](https://www.hackerrank.com/challenges/weather-observation-station-5))**

Query the two cities in **STATION** with the shortest and longest *CITY* names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The **STATION** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where **LAT\_N** is the northern latitude and **LONG\_W** is the western longitude.

**Sample Input**
For example, **CITY** has four entries: **DEF, ABC, PQRS** and **WXY**.

**Sample Output**

```
ABC 3
PQRS 4
```


**Explanation**
When ordered alphabetically, the **CITY** names are listed as **ABC, DEF, PQRS,** and **WXY**, with lengths and . The longest name is **PQRS**, but there are options for shortest named city. Choose **ABC**, because it comes first alphabetically.

**Note**
You can write two separate queries to get the desired output. It need not be a single query.

**My Solution**:

```sql
select city, length(city) from 
    (
        select city, 
        ROW_NUMBER() OVER (ORDER BY length(city) DESC, city ASC) as n1, 
        ROW_NUMBER() OVER (ORDER BY length(city) ASC, city ASC) as n2
        from station
    ) as station_with_row_numbers
where station_with_row_numbers.n1 = 1 OR station_with_row_numbers.n2 = 1
```
