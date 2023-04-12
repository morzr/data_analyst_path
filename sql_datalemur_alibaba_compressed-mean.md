**Question ([link](https://datalemur.com/questions/alibaba-compressed-mean))**

You are trying to find the mean number of items bought per order on Alibaba, rounded to 1 decimal place.
However, instead of doing analytics on all Alibaba orders, you have access to a summary table, which describes how many items were in an order (`item_count`), and the number of orders that had that many items (`order_occurrences`).

### `items_per_order` Table:

| Column Name | Type |
| ----------- | ---- |
| item\_count | integer |
| order\_occurrences | integer |

### `items_per_order` Example Input:

| item\_count | order\_occurrences |
| ---------- | ----------------- |
| 1 | 500 |
| 2 | 1000 |
| 3 | 800 |
| 4 | 1000 |

There are 500 orders with 1 item in each order; 1000 orders with 2 items in each order; 800 orders with 3 items in each order.

### Example Output:

| mean |
| ---- |
| 2.7 |

## Explanation

Let's calculate the arithmetic average:
Total items = `(1*500) + (2*1000) + (3*800) + (4*1000) = 8900`
Total orders = `500 + 1000 + 800 + 1000 = 3300`
Mean = `8900 / 3300 = 2.7`

**My Solution**:

```sql
SELECT ROUND(SUM(item_count::DECIMAL * order_occurrences) / SUM(order_occurrences), 1) AS mean
FROM items_per_order;
```
