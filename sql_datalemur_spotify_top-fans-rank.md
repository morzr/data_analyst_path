**Question ([link](https://datalemur.com/questions/top-fans-rank))**

Assume there are three Spotify tables containing information about the artists, songs, and music charts. Write a query to determine the top 5 artists whose songs appear in the Top 10 of the `global_song_rank` table the highest number of times. From now on, we'll refer to this ranking number as "song appearances".
Output the top 5 artist names in ascending order along with their song appearances ranking (not the number of song appearances, but the rank of who has the most appearances). The order of the rank should take precedence.
For example, Ed Sheeran's songs appeared 5 times in Top 10 list of the global song rank table; this is the highest number of appearances, so he is ranked 1st. Bad Bunny's songs appeared in the list 4, so he comes in at a close 2nd.
Assumptions:

* If two artists' songs have the same number of appearances, the artists should have the same rank.
* The rank number should be continuous (1, 2, 2, 3, 4, 5) and not skipped (1, 2, 2, 4, 5).

### `artists` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| artist\_id | integer |
| artist\_name | varchar |

### `artists` Example Input:

| **artist\_id** | **artist\_name** |
| --------- | ----------- |
| 101 | Ed Sheeran |
| 120 | Drake |

### `songs` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| song\_id | integer |
| artist\_id | integer |

### `songs` Example Input:

| **song\_id** | **artist\_id** |
| ------- | --------- |
| 45202 | 101 |
| 19960 | 120 |

### `global_song_rank` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| day | integer (1-52) |
| song\_id | integer |
| rank | integer (1-1,000,000) |

### `global_song_rank` Example Input:

| **day** | **song\_id** | **rank** |
| --- | ------- | ---- |
| 1 | 45202 | 5 |
| 3 | 45202 | 2 |
| 1 | 19960 | 3 |
| 9 | 19960 | 15 |

### Example Output:

| **artist\_name** | **artist\_rank** |
| ----------- | ----------- |
| Ed Sheeran | 1 |
| Drake | 2 |

### Explanation

Ed Sheeran's song appeared twice in the Top 10 list of global song rank while Drake's song is only listed once. Therefore, Ed is ranked #1 and Drake is ranked #2.

**My Solution**:

```sql
WITH top_artists
AS ( 
-- Start of CTE
  SELECT 
    artist_id,
  	  DENSE_RANK() OVER (
      ORDER BY song_count DESC
  	  ) AS artist_rank
  FROM ( 
-- Start of subquery 
    SELECT 
      songs.artist_id,
      COUNT(songs.song_id) AS song_count
    FROM songs
  	JOIN global_song_rank
      ON songs.song_id = global_song_rank.song_id
  	WHERE global_song_rank.rank <= 10
  	GROUP BY songs.artist_id
-- End of subquery
  ) AS top_songs
) 
-- End of CTE

SELECT 
  artists.artist_name,
  top_artists.artist_rank
FROM top_artists
JOIN artists
  ON top_artists.artist_id = artists.artist_id
WHERE  top_artists.artist_rank <= 5
ORDER BY artist_rank, artist_name;
```
