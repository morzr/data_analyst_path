**Question ([link](https://datalemur.com/questions/time-spent-snaps))**

Assume you are given the tables below containing information on Snapchat users, their ages, and their time spent sending and opening snaps. Write a query to obtain a breakdown of the time spent sending vs. opening snaps (as a percentage of **total time spent** on these activities) for each age group.
Output the age bucket and percentage of sending and opening snaps. Round the percentage to 2 decimal places.
Notes:

* You should calculate these percentages:
    * time sending / (time sending + time opening)
    * time opening / (time sending + time opening)
* To avoid integer division in percentages, multiply by 100.0 and not 100.

### `activities` Table:

| Column Name | Type |
| ----------- | ---- |
| activity\_id | integer |
| user\_id | integer |
| activity\_type | string ('send', 'open', 'chat') |
| time\_spent | float |
| activity\_date | datetime |

### `activities` Example Input:

| activity\_id | user\_id | activity\_type | time\_spent | activity\_date |
| ----------- | ------- | ------------- | ---------- | ------------- |
| 7274 | 123 | open | 4.50 | 06/22/2022 12:00:00 |
| 2425 | 123 | send | 3.50 | 06/22/2022 12:00:00 |
| 1413 | 456 | send | 5.67 | 06/23/2022 12:00:00 |
| 1414 | 789 | chat | 11.00 | 06/25/2022 12:00:00 |
| 2536 | 456 | open | 3.00 | 06/25/2022 12:00:00 |

### `age_breakdown` Table:

| Column Name | Type |
| ----------- | ---- |
| user\_id | integer |
| age\_bucket | string ('21-25', '26-30', '31-25') |

### `age_breakdown` Example Input:

| user\_id | age\_bucket |
| ------- | ---------- |
| 123 | 31-35 |
| 456 | 26-30 |
| 789 | 21-25 |

### Example Output:

| age\_bucket | send\_perc | open\_perc |
| ---------- | --------- | --------- |
| 26-30 | 65.40 | 34.60 |
| 31-35 | 43.75 | 56.25 |

### Explanation

For the age bucket 26-30, the time spent sending snaps was 5.67 and opening 3. The percent of time sending snaps was 5.67/(5.67+3)=65.4%, and the percent of time opening snaps was 3/(5.67+3)=34.6%.

**My Solution**:

```sql
SELECT 
  age.age_bucket, 
  ROUND(100.0 * 
    SUM(activities.time_spent) FILTER  (WHERE activities.activity_type = 'send')/
      SUM(activities.time_spent),2) AS send_perc, 
  ROUND(100.0 * 
    SUM(activities.time_spent) FILTER (WHERE activities.activity_type = 'open')/
      SUM(activities.time_spent),2) AS open_perc
FROM activities
INNER JOIN age_breakdown AS age 
  ON activities.user_id = age.user_id 
WHERE activities.activity_type IN ('send', 'open') 
GROUP BY age.age_bucket;
```
