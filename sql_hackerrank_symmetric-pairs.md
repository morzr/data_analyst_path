**Question ([link](https://www.hackerrank.com/challenges/symmetric-pairs/problem?isFullScreen=true))**

You are given a table, *Functions*, containing two columns: *X* and *Y*.

![](https://s3.amazonaws.com/hr-challenge-images/12892/1443818798-51909e977d-1.png)

Two pairs *(X1, Y1)* and *(X2, Y2)* are said to be *symmetric* *pairs* if *X1 = Y2* and *X2 = Y1*.
Write a query to output all such *symmetric* *pairs* in ascending order by the value of *X*. List the rows such that *X1 ≤ Y1*.

**Sample Input**

![](https://s3.amazonaws.com/hr-challenge-images/12892/1443818693-b384c24e35-2.png)

**Sample Output**

```
20 20
20 21
22 23
```


**My Solution**:

```sql
SELECT f1.X, f1.Y
FROM Functions f1, Functions f2
WHERE f1.X <= f1.Y
AND f1.X = f2.Y
AND f2.X = f1.Y
GROUP BY f1.X, f1.Y
HAVING count(CASE WHEN f1.X=f1.Y THEN f1.X END)>2
OR count(CASE WHEN f1.X<f1.Y THEN f1.X END)=1
ORDER BY f1.X, f1.Y;
```
