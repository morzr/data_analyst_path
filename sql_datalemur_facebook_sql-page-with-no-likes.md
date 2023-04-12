**Question ([link](https://datalemur.com/questions/sql-page-with-no-likes))**

Assume you are given the tables below about Facebook **pages** and **page likes**. Write a query to return the page IDs of all the Facebook pages that don't have any likes. The output should be in ascending order.

### `pages` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| page\_id | integer |
| page\_name | varchar |

### `pages` Example Input:

| **page\_id** | **page\_name** |
| ------- | --------- |
| 20001 | SQL Solutions |
| 20045 | Brain Exercises |
| 20701 | Tips for Data Analysts |

### `page_likes` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| user\_id | integer |
| page\_id | integer |
| liked\_date | datetime |

### `page_likes` Example Input:

| **user\_id** | **page\_id** | **liked\_date** |
| ------- | ------- | ---------- |
| 111 | 20001 | 04/08/2022 00:00:00 |
| 121 | 20045 | 03/12/2022 00:00:00 |
| 156 | 20001 | 07/25/2022 00:00:00 |

### Example Output:

| **page\_id** |
| ------- |
| 20701 |

Explanation: The page with ID 20701 has no likes.
The dataset you are querying against may have different input & output - **this is just an example**!

**My Solution**:

```sql
SELECT pages.page_id FROM pages
LEFT outer JOIN page_likes
ON page_likes.page_id = pages.page_id
WHERE page_likes.page_id is NULL
```
