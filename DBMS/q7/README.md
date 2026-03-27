# Question 7

---

## Query 1 — Number of days remaining in current year

```sql id="y2t9bx"
SELECT DATEDIFF(
       MAKEDATE(YEAR(CURDATE()), 365 + IF(DAYOFYEAR(CONCAT(YEAR(CURDATE()),'-12-31'))=366,1,0)),
       CURDATE()
) AS Days_Remaining;
```

### Output (example)

```id="bqk7xn"
DAYS_REMAINING
--------------
279
```

---

## Query 2 — Highest, lowest salary and difference

```sql id="m3x1ra"
SELECT 
MAX(Sal) AS Highest_Salary,
MIN(Sal) AS Lowest_Salary,
MAX(Sal) - MIN(Sal) AS Difference
FROM Employee;
```

### Output

```id="6c4bqg"
HIGHEST_SALARY | LOWEST_SALARY | DIFFERENCE
-------------- | ------------- | ----------
5000           | 800           | 4200
```

---

## Query 3 — Employees with commission > 25% of salary

```sql id="dn3w8p"
SELECT *
FROM Employee
WHERE Comm > (0.25 * Sal);
```

### Output (sample)

```id="z7h3cu"
7499 | ALLEN | ... | 1600 | 300
...
```

---

## Query 4 — Display salary in dollar format

```sql id="4v6c1e"
SELECT Ename,
CONCAT('$', FORMAT(Sal,2)) AS Salary_In_Dollars
FROM Employee;
```

### Output (sample)

```id="fx3zbm"
ENAME | SALARY_IN_DOLLARS
------|-------------------
SMITH | $800.00
ALLEN | $1,600.00
...
```

---

## Query 5 — Matrix query (Job vs Dept with total)

```sql id="t5v9ao"
SELECT Job,
SUM(CASE WHEN DeptNo = 10 THEN Sal ELSE 0 END) AS Dept10,
SUM(CASE WHEN DeptNo = 20 THEN Sal ELSE 0 END) AS Dept20,
SUM(CASE WHEN DeptNo = 30 THEN Sal ELSE 0 END) AS Dept30,
SUM(Sal) AS Total_Salary
FROM Employee
GROUP BY Job;
```

### Output (sample)

```id="oqv8gi"
JOB      | DEPT10 | DEPT20 | DEPT30 | TOTAL_SALARY
---------|--------|--------|--------|--------------
CLERK    | 1300   | 1900   | 950    | 4150
MANAGER  | 2450   | 2975   | 2850   | 8275
...
```

---

## Query 6 — Employees count by hiring year

```sql id="z8h6pr"
SELECT 
COUNT(*) AS Total_Employees,
SUM(YEAR(HireDate)=1980) AS "1980",
SUM(YEAR(HireDate)=1981) AS "1981",
SUM(YEAR(HireDate)=1982) AS "1982",
SUM(YEAR(HireDate)=1983) AS "1983"
FROM Employee;
```

### Output (sample)

```id="yx3j1r"
TOTAL_EMPLOYEES | 1980 | 1981 | 1982 | 1983
----------------|------|------|------|------
14              | 1    | 10   | 2    | 1
```

---

## Query 7 — Last Sunday of any month

```sql id="7o4mdk"
SELECT DATE_SUB(
       LAST_DAY('2026-03-01'),
       INTERVAL (DAYOFWEEK(LAST_DAY('2026-03-01')) - 1) DAY
) AS Last_Sunday;
```

### Output (example)

```id="s8v4ax"
LAST_SUNDAY
------------
2026-03-29
```

---

## Query 8 — Department-wise employee count

```sql id="c3u6vw"
SELECT DeptNo, COUNT(*) AS Total_Employees
FROM Employee
GROUP BY DeptNo;
```

### Output (sample)

```id="l1q5eo"
DEPTNO | TOTAL_EMPLOYEES
------ | ----------------
10     | 3
20     | 5
30     | 6
```

---

## Query 9 — Job-wise employee count

```sql id="s9u1kt"
SELECT Job, COUNT(*) AS Total_Employees
FROM Employee
GROUP BY Job;
```

### Output (sample)

```id="b6a8tw"
JOB       | TOTAL_EMPLOYEES
----------|----------------
CLERK     | 4
MANAGER   | 3
SALESMAN  | 4
ANALYST   | 2
```

---

## Query 10 — Department-wise total salary

```sql id="5g2kpl"
SELECT DeptNo, SUM(Sal) AS Total_Salary
FROM Employee
GROUP BY DeptNo;
```

### Output (sample)

```id="o2i7wx"
DEPTNO | TOTAL_SALARY
------ | ------------
10     | 8750
20     | 10875
30     | 9400
```

---
