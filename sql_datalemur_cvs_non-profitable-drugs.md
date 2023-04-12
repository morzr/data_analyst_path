**Question ([link](https://datalemur.com/questions/non-profitable-drugs))**

CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.
Write a query to find out which manufacturer is associated with the drugs that were not profitable and how much money CVS lost on these drugs. 
Output the manufacturer, number of drugs and total losses. Total losses should be in absolute value. Display the results with the highest losses on top.
If you like this question, try out [Pharmacy Analytics (Part 3)](https://datalemur.com/questions/total-drugs-sales)!

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
| 156 | 89514 | 3130097.00 | 3427421.73 | Biogen | Acyclovir |
| 25 | 222331 | 2753546.00 | 2974975.36 | AbbVie | Lamivudine and Zidovudine |
| 50 | 90484 | 2521023.73 | 2742445.90 | Eli Lilly | Dermasorb TA Complete Kit |
| 98 | 110746 | 813188.82 | 140422.87 | Biogen | Medi-Chord |

### Example Output:

| **manufacturer** | **drug\_count** | **total\_loss** |
| ------------ | ---------- | ---------- |
| Biogen | 1 | 297324.73 |
| AbbVie | 1 | 221429.36 |
| Eli Lilly | 1 | 221422.17 |

### Explanation:

The drugs in the first 3 rows of the **Example Input** table reported losses. Biogen's losses were the highest followed by AbbVie's and Eli Lilly's.
Medi-Chord drug by Biogen reported a profit, so it was excluded from the result.

**My Solution**:

```sql
SELECT manufacturer, COUNT(drug) AS drug_count, 
ABS(SUM(total_sales - cogs)) AS total_losses FROM pharmacy_sales 
WHERE total_sales - cogs <= 0
GROUP BY manufacturer
ORDER BY drug_count  DESC, total_losses DESC
```
