**Question ([link](https://datalemur.com/questions/duplicate-job-listings))**

Assume you are given the table below that shows job postings for all companies on the LinkedIn platform. Write a query to get the number of companies that have posted duplicate job listings.
Clarification:

* Duplicate job listings refer to two jobs at the same company with the same title and description.

### `job_listings` Table:

| Column Name | Type |
| ----------- | ---- |
| job\_id | integer |
| company\_id | integer |
| title | string |
| description | string |

### `job_listings` Example Input:

| job\_id | company\_id | title | description |
| ------ | ---------- | ----- | ----------- |
| 248 | 827 | Business Analyst | Business analyst evaluates past and current business data with the primary goal of improving decision-making processes within organizations. |
| 149 | 845 | Business Analyst | Business analyst evaluates past and current business data with the primary goal of improving decision-making processes within organizations. |
| 945 | 345 | Data Analyst | Data analyst reviews data to identify key insights into a business's customers and ways the data can be used to solve problems. |
| 164 | 345 | Data Analyst | Data analyst reviews data to identify key insights into a business's customers and ways the data can be used to solve problems. |
| 172 | 244 | Data Engineer | Data engineer works in a variety of settings to build systems that collect, manage, and convert raw data into usable information for data scientists and business analysts to interpret. |

### Example Output:

| co\_w\_duplicate\_jobs |
| ------------------- |
| 1 |

### Explanation

Because job IDs 945 and 164 are at the same company (345), and the jobs have the same title and description, there is exactly one company with a duplicate job.
The dataset you are querying against may have different input & output - **this is just an example**!

**My Solution**:

```sql
SELECT COUNT(co_w_duplicate_jobs) FROM (
  SELECT company_id,title, description, COUNT(*) FROM job_listings
  GROUP BY  company_id,title, description
  HAVING COUNT(*) > 1) AS co_w_duplicate_jobs;
```