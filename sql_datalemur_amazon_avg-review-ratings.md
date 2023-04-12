**Question ([link](https://datalemur.com/questions/sql-avg-review-ratings))**

The output should include the month in numerical value, product id, and average star rating rounded to two decimal places. Sort the output based on month followed by the product id.
P.S. If you've read the [Ace the Data Science Interview](https://amzn.to/3kF79Fx), and liked it, consider writing us a review?

### `reviews` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| review\_id | integer |
| user\_id | integer |
| submit\_date | datetime |
| product\_id | integer |
| stars | integer (1-5) |

### `reviews` Example Input:

| **review\_id** | **user\_id** | **submit\_date** | **product\_id** | **stars** |
| --------- | ------- | ----------- | ---------- | ----- |
| 6171 | 123 | 06/08/2022 00:00:00 | 50001 | 4 |
| 7802 | 265 | 06/10/2022 00:00:00 | 69852 | 4 |
| 5293 | 362 | 06/18/2022 00:00:00 | 50001 | 3 |
| 6352 | 192 | 07/26/2022 00:00:00 | 69852 | 3 |
| 4517 | 981 | 07/05/2022 00:00:00 | 69852 | 2 |

### Example Output:

| **mth** | **product** | **avg\_stars** |
| --- | ------- | --------- |
| 6 | 50001 | 3.50 |
| 6 | 69852 | 4.00 |
| 7 | 69852 | 2.50 |

### Explanation

In June (month #6), product 50001 had two ratings - 4 and 3, resulting in an average star rating of 3.5.

**My Solution**:

```sql
SELECT  EXTRACT(MONTH FROM submit_date) AS Month, product_id, ROUND(AVG(stars),2) FROM reviews
GROUP BY Month,product_id
ORDER BY Month, product_id 
```
