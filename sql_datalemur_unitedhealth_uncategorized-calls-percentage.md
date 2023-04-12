**Question ([link](https://datalemur.com/questions/uncategorized-calls-percentage))**

UnitedHealth Group has a program called Advocate4Me, which allows members to call an advocate and receive support for their health care needs – whether that's behavioural, clinical, well-being, health care financing, benefits, claims or pharmacy help.
Calls to the Advocate4Me call centre are categorised, but sometimes they can't fit neatly into a category. These uncategorised calls are labelled “n/a”, or are just empty (when a support agent enters nothing into the category field).
Write a query to find the percentage of calls that cannot be categorised. Round your answer to 1 decimal place.

### `callers` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| policy\_holder\_id | integer |
| case\_id | varchar |
| call\_category | varchar |
| call\_received | timestamp |
| call\_duration\_secs | integer |
| original\_order | integer |

### `callers` Example Input:

| **policy\_holder\_id** | **case\_id** | **call\_category** | **call\_received** | **call\_duration\_secs** | **original\_order** |
| ---------------- | ------- | ------------- | ------------- | ------------------ | -------------- |
| 52481621 | a94c-2213-4ba5-812d |  | 01/17/2022 19:37:00 | 286 | 161 |
| 51435044 | f0b5-0eb0-4c49-b21e | n/a | 01/18/2022 2:46:00 | 208 | 225 |
| 52082925 | 289b-d7e8-4527-bdf5 | benefits | 01/18/2022 3:01:00 | 291 | 352 |
| 54624612 | 62c2-d9a3-44d2-9065 | IT\_support | 01/19/2022 0:27:00 | 273 | 358 |
| 54624612 | 9f57-164b-4a36-934e | claims | 01/19/2022 6:33:00 | 157 | 362 |

### Example Output:

| **call\_percentage** |
| --------------- |
| 40.0 |

### Explanation:

A total of 5 calls were registered. Out of which 2 calls were not categorised. That makes 40.0% (2/5 x 100.0) of the calls uncategorised.

**My Solution**:

```sql
SELECT 
  ROUND(100.0 * COUNT(case_id) FILTER (WHERE call_category IS NULL OR call_category = 'n/a')
  / COUNT(case_id),1) AS total_calls
  FROM callers
```
