**Question ([link](https://datalemur.com/questions/second-day-confirmation))**

New TikTok users sign up with their emails and each user receives a text confirmation to activate their account. Assume you are given the below tables about emails and texts.
Write a query to display the ids of the users who did not confirm on the first day of sign-up, but confirmed on the second day.
Assumption:

* `action_date` is the date when the user activated their account and confirmed their sign-up through the text.

### `emails` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| email\_id | integer |
| user\_id | integer |
| signup\_date | datetime |

### `emails` Example Input:

| **email\_id** | **user\_id** | **signup\_date** |
| -------- | ------- | ----------- |
| 125 | 7771 | 06/14/2022 00:00:00 |
| 433 | 1052 | 07/09/2022 00:00:00 |

### `texts` Table:

| **Column Name** | **Type** |
| ----------- | ---- |
| text\_id | integer |
| email\_id | integer |
| signup\_action | string ('Confirmed', 'Not confirmed') |
| action\_date | datetime |

### `texts` Example Input:

| **text\_id** | **email\_id** | **signup\_action** | **action\_date** |
| ------- | -------- | ------------- | ----------- |
| 6878 | 125 | Confirmed | 06/14/2022 00:00:00 |
| 6997 | 433 | Not Confirmed | 07/09/2022 00:00:00 |
| 7000 | 433 | Confirmed | 07/10/2022 00:00:00 |

### Example Output:

| **user\_id** |
| ------- |
| 1052 |

### Explanation:

User 1052 is the only user who confirmed their sign up on the second day.

**My Solution**:

```sql
SELECT emails.user_id
FROM emails
inner JOIN texts
ON emails.email_id = texts.email_id
WHERE signup_action = 'Confirmed'
AND texts.action_date = emails.signup_date + INTERVAL '1 day'
```
