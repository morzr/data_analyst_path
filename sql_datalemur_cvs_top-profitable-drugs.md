**Question ([link](https://datalemur.com/questions/top-profitable-drugs))**

CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.
Write a query to find the top 3 most profitable drugs sold, and how much profit they made. Assume that there are no ties in the profits. Display the result from the highest to the lowest total profit.
**Definition:**

* `cogs` stands for Cost of Goods Sold which is the direct cost associated with producing the drug.
* Total Profit = Total Sales - Cost of Goods Sold

If you like this question, try out [Pharmacy Analytics (Part 2)](https://datalemur.com/questions/non-profitable-drugs)!

### `pharmacy_sales` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| product\_id | integer |
| units\_sold | integer |
| total\_sales | decimal |
| cogs | decimal |
| manufacturer | varchar |
| drug | varchar |

### `pharmacy_sales` Example Input:

| **product\_id** | **units\_sold** | **total\_sales** | **cogs** | **manufacturer** | **drug** |
| ---------- | ---------- | ----------- | ---- | ------------ | ---- |
| 9 | 37410 | 293452.54 | 208876.01 | Eli Lilly | Zyprexa |
| 34 | 94698 | 600997.19 | 521182.16 | AstraZeneca | Surmontil |
| 61 | 77023 | 500101.61 | 419174.97 | Biogen | Varicose Relief |
| 136 | 144814 | 1084258 | 1006447.73 | Biogen | Burkhart |

### Example Output:

| **drug** | **total\_profit** |
| ---- | ------------ |
| Zyprexa | 84576.53 |
| Varicose Relief | 80926.64 |
| Surmontil | 79815.03 |

### Explanation:

Zyprexa made the most profit (of $84,576.53) followed by Varicose Relief (of $80,926.64) and Surmontil (of $79,815.3).

**My Solution**:

```sql
SELECT drug, (total_sales - cogs) AS total_profit FROM pharmacy_sales
GROUP BY drug, total_profit
ORDER BY total_profit DESC
LIMIT 3 ;
```
