**Question ([link](https://datalemur.com/questions/click-through-rate))**

Assume you have an events table on app analytics. Write a query to get the app’s click-through rate (CTR %) in 2022. Output the results in percentages rounded to 2 decimal places.
Notes:

* Percentage of click-through rate = 100.0 \* Number of clicks / Number of impressions
* To avoid integer division, you should multiply the click-through rate by 100.0, not 100.

### `events` Table:

| Column Name | Type |
| ----------- | ---- |
| app\_id | integer |
| event\_type | string |
| timestamp | datetime |

### `events` Example Input:

| app\_id | event\_type | timestamp |
| ------ | ---------- | --------- |
| 123 | impression | 07/18/2022 11:36:12 |
| 123 | impression | 07/18/2022 11:37:12 |
| 123 | click | 07/18/2022 11:37:42 |
| 234 | impression | 07/18/2022 14:15:12 |
| 234 | click | 07/18/2022 14:16:12 |

### Example Output:

| app\_id | ctr |
| ------ | --- |
| 123 | 50.00 |
| 234 | 100.00 |

### Explanation

App 123 has a CTR of 50.00% because this app receives 1 click out of the 2 impressions. Hence, it's 1/2 = 50.00%.

**My Solution**:

```sql
SELECT subq.app_id, ROUND(subq.clicks_number * 100.0 / subq.impressions_number, 2) as ctr FROM
(
  SELECT app_id, 
    COUNT(case event_type when 'impression' then 1 else null end) as impressions_number,
    COUNT(case event_type when 'click' then 1 else null end) as clicks_number
  FROM events
  WHERE timestamp BETWEEN '2022-01-01' AND '2023-01-01'
  GROUP BY app_id
) as subq
```
