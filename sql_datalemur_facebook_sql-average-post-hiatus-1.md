**Question ([link](https://datalemur.com/questions/sql-average-post-hiatus-1))**

Given a table of Facebook posts, for each user who posted at least twice in 2021, write a query to find the number of days between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the days between each user's first and last post.
p.s. If you've read the [Ace the Data Science Interview](https://www.amazon.com/dp/0578973839?ref_=pe_3052080_397514860) and liked it, consider writing us a review?

### `posts` Table:

| Column Name | Type |
| ----------- | ---- |
| user\_id | integer |
| post\_id | integer |
| post\_date | timestamp |
| post\_content | text |

### `posts` Example Input:

| user\_id | post\_id | post\_date | post\_content |
| ------- | ------- | --------- | ------------ |
| 151652 | 599415 | 07/10/2021 12:00:00 | Need a hug |
| 661093 | 624356 | 07/29/2021 13:00:00 | Bed. Class 8-12. Work 12-3. Gym 3-5 or 6. Then class 6-10. Another day that's gonna fly by. I miss my girlfriend |
| 004239 | 784254 | 07/04/2021 11:00:00 | Happy 4th of July! |
| 661093 | 442560 | 07/08/2021 14:00:00 | Just going to cry myself to sleep after watching Marley and Me. |
| 151652 | 111766 | 07/12/2021 19:00:00 | I'm so done with covid - need travelling ASAP! |

### Example Output:

| user\_id | days\_between |
| ------- | ------------ |
| 151652 | 2 |
| 661093 | 21 |

The dataset you are querying against may have different input & output - **this is just an example**!

**My Solution**:

```sql
SELECT user_id, MAX(post_date::Date) - MIN(post_date::Date)AS days_between FROM posts
WHERE date_part('year', post_date::DATE) = 2021
 GROUP BY user_id
 HAVING COUNT(post_id) > 1;
```
