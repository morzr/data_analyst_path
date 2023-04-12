**Question ([link](https://datalemur.com/questions/completed-trades))**

You are given the tables below containing information on Robinhood trades and users. Write a query to list the top three cities that have the most completed trade orders in descending order.
Output the city and number of orders.

### `trades` Table:

| Column Name | Type |
| ----------- | ---- |
| order\_id | integer |
| user\_id | integer |
| price | decimal |
| quantity | integer |
| status | string('Completed' ,'Cancelled') |
| timestamp | datetime |

### `trades` Example Input:

| order\_id | user\_id | price | quantity | status | timestamp |
| -------- | ------- | ----- | -------- | ------ | --------- |
| 100101 | 111 | 9.80 | 10 | Cancelled | 08/17/2022 12:00:00 |
| 100102 | 111 | 10.00 | 10 | Completed | 08/17/2022 12:00:00 |
| 100259 | 148 | 5.10 | 35 | Completed | 08/25/2022 12:00:00 |
| 100264 | 148 | 4.80 | 40 | Completed | 08/26/2022 12:00:00 |
| 100305 | 300 | 10.00 | 15 | Completed | 09/05/2022 12:00:00 |
| 100400 | 178 | 9.90 | 15 | Completed | 09/09/2022 12:00:00 |
| 100565 | 265 | 25.60 | 5 | Completed | 12/19/2022 12:00:00 |

### `users` Table:

| Column Name | Type |
| ----------- | ---- |
| user\_id | integer |
| city | string |
| email | string |
| signup\_date | datetime |

### `users` Example Input:

| user\_id | city | email | signup\_date |
| ------- | ---- | ----- | ----------- |
| 111 | San Francisco | [rrok10@gmail.com](mailto:rrok10@gmail.com) | 08/03/2021 12:00:00 |
| 148 | Boston | [sailor9820@gmail.com](mailto:sailor9820@gmail.com) | 08/20/2021 12:00:00 |
| 178 | San Francisco | [harrypotterfan182@gmail.com](mailto:harrypotterfan182@gmail.com) | 01/05/2022 12:00:00 |
| 265 | Denver | [shadower_@hotmail.com](mailto:shadower_@hotmail.com) | 02/26/2022 12:00:00 |
| 300 | San Francisco | [houstoncowboy1122@hotmail.com](mailto:houstoncowboy1122@hotmail.com) | 06/30/2022 12:00:00 |

### Example Output:

| city | total\_orders |
| ---- | ------------ |
| San Francisco | 3 |
| Boston | 2 |
| Denver | 1 |

### Explanation

In this example, San Francisco has first place with 3 orders, Boston has second place with 2 orders, and Denver has third place with 1 order.

**My Solution**:

```sql
SELECT user_id_to_city.city, count(*) FROM
  (SELECT trades.user_id , users.city FROM trades
  RIGHT JOIN users 
  ON users.user_id = trades.user_id
  WHERE trades.status LIKE 'Completed') AS user_id_to_city
  GROUP BY user_id_to_city.city
  ORDER BY COUNT(*) DESC
  LIMIT 3 
```
