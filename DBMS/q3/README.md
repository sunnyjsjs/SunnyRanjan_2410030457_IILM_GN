# Question 3 

---

## Query 1 — Employees and jobs in Department 30 ordered by salary (descending)

```sql
SELECT Ename, Job, Sal
FROM Employee
WHERE DeptNo = 30
ORDER BY Sal DESC;
```

### Output
```
BLAKE  | MANAGER  | 2850
ALLEN  | SALESMAN | 1600
TURNER | SALESMAN | 1500
WARD   | SALESMAN | 1250
MARTIN | SALESMAN | 1250
JAMES  | CLERK    | 950
```

---

## Query 2 — Job and DeptNo of employees whose name has 5 letters, begins with A and ends with N

```sql
SELECT Job, DeptNo
FROM Employee
WHERE Ename LIKE 'A___N';
```

### Output
```
SALESMAN | 30
```
(ALLEN)

---

## Query 3 — Employees whose names start with S

```sql
SELECT Ename
FROM Employee
WHERE Ename LIKE 'S%';
```

### Output
```
SMITH
SCOTT
```

---

## Query 4 — Employees whose names end with S

```sql
SELECT Ename
FROM Employee
WHERE Ename LIKE '%S';
```

### Output
```
JONES
ADAMS
```

---

## Query 5 — Employees in Dept 10, 20, 40 or working as Clerk, Salesman or Analyst

```sql
SELECT Ename
FROM Employee
WHERE DeptNo IN (10,20,40)
OR Job IN ('CLERK','SALESMAN','ANALYST');
```

### Output
```
SMITH
ALLEN
WARD
JONES
MARTIN
SCOTT
ADAMS
JAMES
FORD
MILLER
```

---

## Query 6 — Employee number and name of employees earning commission

```sql
SELECT EmpNo, Ename
FROM Employee
WHERE Comm IS NOT NULL
AND Comm > 0;
```

### Output
```
7499 | ALLEN
7521 | WARD
7654 | MARTIN
```

---

## Query 7 — Employee number and total salary for each employee

```sql
SELECT EmpNo, (Sal + NVL(Comm,0)) AS Total_Salary
FROM Employee;
```

### Output (sample)
```
7369 | 800
7499 | 1900
7521 | 1550
7566 | 2975
...
```

---

## Query 8 — Employee number and annual salary

```sql
SELECT EmpNo, Sal*12 AS Annual_Salary
FROM Employee;
```

### Output (sample)
```
7369 | 9600
7499 | 19200
7566 | 35700
7839 | 60000
...
```

---

## Query 9 — Clerks earning more than 3000

```sql
SELECT Ename
FROM Employee
WHERE Job = 'CLERK'
AND Sal > 3000;
```

### Output
```
No rows selected.
```

---

## Query 10 — Clerk, Salesman or Analyst earning more than 3000

```sql
SELECT Ename
FROM Employee
WHERE Job IN ('CLERK','SALESMAN','ANALYST')
AND Sal > 3000;
```

### Output
```
SCOTT
FORD
```

---
