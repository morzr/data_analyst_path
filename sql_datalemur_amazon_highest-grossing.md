**Question ([link](https://datalemur.com/questions/sql-highest-grossing))**

Assume you are given the table containing information on Amazon customers and their spending on products in various categories.
Identify the top two highest-grossing products within each category in 2022. Output the category, product, and total spend.

### `product_spend` Table:

| Column Name | Type |
| ----------- | ---- |
| category | string |
| product | string |
| user\_id | integer |
| spend | decimal |
| transaction\_date | timestamp |

### `product_spend` Example Input:

| category | product | user\_id | spend | transaction\_date |
| -------- | ------- | ------- | ----- | ---------------- |
| appliance | refrigerator | 165 | 246.00 | 12/26/2021 12:00:00 |
| appliance | refrigerator | 123 | 299.99 | 03/02/2022 12:00:00 |
| appliance | washing machine | 123 | 219.80 | 03/02/2022 12:00:00 |
| electronics | vacuum | 178 | 152.00 | 04/05/2022 12:00:00 |
| electronics | wireless headset | 156 | 249.90 | 07/08/2022 12:00:00 |
| electronics | vacuum | 145 | 189.00 | 07/15/2022 12:00:00 |

### Example Output:

| category | product | total\_spend |
| -------- | ------- | ----------- |
| appliance | refrigerator | 299.99 |
| appliance | washing machine | 219.80 |
| electronics | vacuum | 341.00 |
| electronics | wireless headset | 249.90 |


**My Solution**:

```sql
WITH product_category_spend AS (
SELECT 
  category, 
  product, 
  SUM(spend) AS total_spend 
FROM product_spend 
WHERE transaction_date >= '2022-01-01' 
  AND transaction_date <= '2022-12-31' 
GROUP BY category, product
),
top_spend AS (
SELECT *, 
  RANK() OVER (
    PARTITION BY category 
    ORDER BY total_spend DESC) AS ranking 
FROM product_category_spend)

SELECT category, product, total_spend 
FROM top_spend 
WHERE ranking <= 2 
ORDER BY category, ranking;
```
