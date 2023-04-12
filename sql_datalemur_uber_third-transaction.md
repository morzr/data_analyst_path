**Question ([link](https://datalemur.com/questions/sql-third-transaction))**

Assume you are given the table below on Uber transactions made by users. Write a query to obtain the third transaction of every user. Output the user id, spend and transaction date.

### `transactions` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| user\_id | integer |
| spend | decimal |
| transaction\_date | timestamp |

### `transactions` Example Input:

| **user\_id** | **spend** | **transaction\_date** |
| ------- | ----- | ---------------- |
| 111 | 100.50 | 01/08/2022 12:00:00 |
| 111 | 55.00 | 01/10/2022 12:00:00 |
| 121 | 36.00 | 01/18/2022 12:00:00 |
| 145 | 24.99 | 01/26/2022 12:00:00 |
| 111 | 89.60 | 02/05/2022 12:00:00 |

### Example Output:

| **user\_id** | **spend** | **transaction\_date** |
| ------- | ----- | ---------------- |
| 111 | 89.60 | 02/05/2022 12:00:00 |


**My Solution**:

```sql
SELECT n2.user_id, n2.spend, n2.transaction_date FROM
(
  SELECT user_id, spend, transaction_date,
  ROW_NUMBER () OVER ( PARTITION BY user_id ORDER BY transaction_date ASC)  as n
  FROM transactions
) as n2
where n2.n = 3
```
