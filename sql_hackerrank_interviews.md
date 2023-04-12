**Question ([link](https://www.hackerrank.com/challenges/interviews))**

Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the *contest\_id*, *hacker\_id*, *name*, and the sums of *total\_submissions*, *total\_accepted\_submissions*, *total\_views*, and *total\_unique\_views* for each contest sorted by *contest\_id*. Exclude the contest from the result if all four sums are 0.

**Note:** A specific contest can be used to screen candidates at more than one college, but each college only holds screening contest.

***

**Input Format**
The following tables hold interview data:

* *Contests:* The *contest\_id* is the id of the contest, *hacker\_id* is the id of the hacker who created the contest, and *name* is the name of the hacker.
 
    ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458517426-e017c3460e-ScreenShot2016-03-21at4.57.47AM.png)
* *Colleges:* The *college\_id* is the id of the college, and *contest\_id* is the id of the contest that Samantha used to screen the candidates.

     ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458517503-fd4aa63111-ScreenShot2016-03-21at4.57.56AM.png)
* *Challenges:* The *challenge\_id* is the id of the challenge that belongs to one of the contests whose contest\_id Samantha forgot, and *college\_id* is the id of the college where the challenge was given to candidates.

     ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458517661-a642f750ce-ScreenShot2016-03-21at4.58.04AM.png)
* *View\_Stats:* The *challenge\_id* is the id of the challenge, *total\_views* is the number of times the challenge was viewed by candidates, and *total\_unique\_views* is the number of times the challenge was viewed by unique candidates.

     ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458517983-b4302286a8-ScreenShot2016-03-21at4.58.15AM.png)
* *Submission\_Stats:* The *challenge\_id* is the id of the challenge, *total\_submissions* is the number of submissions for the challenge, and *total\_accepted\_submission* is the number of submissions that achieved full scores.

     ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458518090-80983c916a-ScreenShot2016-03-21at4.58.27AM.png)

***

**Sample Input**

*Contests* Table:

 ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458519044-d788f8a6ee-ScreenShot2016-03-21at4.58.39AM.png) 

*Colleges* Table:

![](https://s3.amazonaws.com/hr-challenge-images/19596/1458519098-912836d6ac-ScreenShot2016-03-21at4.59.22AM.png) 
 
*Challenges* Table:

 ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458519120-c531743caf-ScreenShot2016-03-21at4.59.32AM.png) 

*View\_Stats* Table:

 ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458519152-107a67866b-ScreenShot2016-03-21at4.59.43AM.png) 

*Submission\_Stats* Table:

 ![](https://s3.amazonaws.com/hr-challenge-images/19596/1458519173-091aba871a-ScreenShot2016-03-21at4.59.55AM.png)

**Sample Output**

```
66406 17973 Rose 111 39 156 56
66556 79153 Angela 0 0 11 10
94828 80275 Frank 150 38 41 15
```


**Explanation**

The contest 66406 is used in the college 11219. In this college 11219, challenges 18765 and 47127 are asked, so from the *view* and *submission* stats:

* Sum of total submissions = 27 + 56 + 28 = 111
* Sum of total accepted submissions = 10 + 18 + 11 = 39
* Sum of total views = 43 + 72 + 26 + 15 = 156
* Sum of total unique views = 10 + 13 + 19 + 14 = 56

Similarly, we can find the sums for contests and .

**My Solution**:

```sql
SELECT A.CONTEST_ID, A.HACKER_ID, A.NAME, 
        SUM(TOTAL_SUBMISSIONS) AS TOTAL_SUBMISSIONS, 
        SUM(TOTAL_ACCEPTED_SUBMISSIONS) AS TOTAL_ACCEPTED_SUBMISSIONS,
        SUM(TOTAL_VIEWS) AS TOTAL_VIEWS,
        SUM(TOTAL_UNIQUE_VIEWS) AS TOTAL_UNIQUE_VIEWS
FROM CONTESTS AS A
LEFT JOIN COLLEGES AS B
    ON A.CONTEST_ID = B.CONTEST_ID
LEFT JOIN CHALLENGES AS C
    ON B.COLLEGE_ID = C.COLLEGE_ID 
LEFT JOIN (SELECT CHALLENGE_ID, SUM(TOTAL_VIEWS) AS TOTAL_VIEWS, 
                  SUM(TOTAL_UNIQUE_VIEWS) AS TOTAL_UNIQUE_VIEWS
           FROM VIEW_STATS
           GROUP BY CHALLENGE_ID) AS D 
    ON C.CHALLENGE_ID = D.CHALLENGE_ID 
LEFT JOIN (SELECT CHALLENGE_ID, SUM(TOTAL_SUBMISSIONS) AS TOTAL_SUBMISSIONS, 
                  SUM(TOTAL_ACCEPTED_SUBMISSIONS) AS TOTAL_ACCEPTED_SUBMISSIONS
           FROM SUBMISSION_STATS
           GROUP BY CHALLENGE_ID) AS E
    ON C.CHALLENGE_ID = E.CHALLENGE_ID
GROUP BY A.CONTEST_ID, A.HACKER_ID, A.NAME
HAVING (TOTAL_SUBMISSIONS + TOTAL_ACCEPTED_SUBMISSIONS + TOTAL_VIEWS + TOTAL_UNIQUE_VIEWS) > 0 
ORDER BY A.CONTEST_ID;
```
