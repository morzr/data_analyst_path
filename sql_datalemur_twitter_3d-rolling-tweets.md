**Question ([link](https://datalemur.com/questions/3d-rolling-tweets))**

Given a table of tweet data over a specified time period, calculate the 3-day rolling average of tweets for each user. Output the user ID, tweet date, and rolling averages rounded to 2 decimal places.
Notes:

* A rolling average, also known as a moving average or running mean is a time-series technique that examines trends in data over a specified period of time.
* In this case, we want to determine how the tweet count for each user changes over a 3-day period.

*Effective April 7th, 2023, the problem statement, solution and hints for this question have been revised.*

### `tweets` Table:

| Column Name | Type |
| ----------- | ---- |
| user\_id | integer |
| tweet\_date | timestamp |
| tweet\_count | integer |

### `tweets` Example Input:

| user\_id | tweet\_date | tweet\_count |
| ------- | ---------- | ----------- |
| 111 | 06/01/2022 00:00:00 | 2 |
| 111 | 06/02/2022 00:00:00 | 1 |
| 111 | 06/03/2022 00:00:00 | 3 |
| 111 | 06/04/2022 00:00:00 | 4 |
| 111 | 06/05/2022 00:00:00 | 5 |

### Example Output:

| user\_id | tweet\_date | rolling\_avg\_3d |
| ------- | ---------- | -------------- |
| 111 | 06/01/2022 00:00:00 | 2.00 |
| 111 | 06/02/2022 00:00:00 | 1.50 |
| 111 | 06/03/2022 00:00:00 | 2.00 |
| 111 | 06/04/2022 00:00:00 | 2.67 |
| 111 | 06/05/2022 00:00:00 | 4.00 |


**My Solution**:

```sql
WITH tweet_count AS (
  SELECT user_id,tweet_date, COUNT(tweet_id) AS tweet_num FROM tweets
  GROUP BY user_id,tweet_date
)
SELECT user_id, tweet_date, ROUND(AVG(tweet_num) OVER( PARTITION BY user_id order by tweet_date rows between 2 preceding AND current row
),2) AS rolling_avg_3d 
FROM tweet_count
```
