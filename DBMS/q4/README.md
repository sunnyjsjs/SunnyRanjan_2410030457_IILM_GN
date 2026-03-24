# Question 4 
---

## Query 1 — Employees joined before 30-JUN-80 or after 31-DEC-81

```sql
SELECT Ename, HireDate
FROM Employee
WHERE HireDate < '30-JUN-80'
   OR HireDate > '31-DEC-81';
```

### Output
```
SCOTT  | 09-DEC-82
ADAMS  | 12-JAN-83
```

---

## Query 2 — Employees whose second letter is 'A'

```sql
SELECT Ename
FROM Employee
WHERE Ename LIKE '_A%';
```

### Output
```
WARD
MARTIN
JAMES
```

---

## Query 3 — Employees whose name has exactly five characters

```sql
SELECT Ename
FROM Employee
WHERE LENGTH(Ename) = 5;
```

### Output
```
SMITH
ALLEN
WARD
JONES
BLAKE
CLARK
SCOTT
ADAMS
JAMES
FORD
```

---

## Query 4 — Employees whose second letter is 'A'

```sql
SELECT Ename
FROM Employee
WHERE Ename LIKE '_A%';
```

### Output
```
WARD
MARTIN
JAMES
```

---

## Query 5 — Employees not working as salesman, clerk or analyst

```sql
SELECT Ename, Job
FROM Employee
WHERE Job NOT IN ('SALESMAN','CLERK','ANALYST');
```

### Output
```
JONES | MANAGER
BLAKE | MANAGER
CLARK | MANAGER
KING  | PRESIDENT
```

---

## Query 6 — Employee name with annual salary (highest first)

```sql
SELECT Ename, Sal*12 AS Annual_Salary
FROM Employee
ORDER BY Annual_Salary DESC;
```

### Output (Top rows)
```
KING  | 60000
SCOTT | 36000
FORD  | 36000
JONES | 35700
```

---

## Query 7 — Salary components (HRA, DA, PF, Total Salary)

```sql
SELECT 
Ename,
Sal,
Sal*0.15 AS HRA,
Sal*0.10 AS DA,
Sal*0.05 AS PF,
(Sal + (Sal*0.15) + (Sal*0.10) - (Sal*0.05)) AS TotalSal
FROM Employee
ORDER BY TotalSal;
```

### Output (sample)
```
SMITH | 800  | 120 | 80  | 40  | 960
ALLEN | 1600 | 240 | 160 | 80  | 1920
KING  | 5000 | 750 | 500 | 250 | 6000
```

---

## Query 8 — Increase salary by 10% for employees without commission

```sql
UPDATE Employee
SET Sal = Sal * 1.10
WHERE Comm IS NULL;
```

### Output
```
Rows updated successfully.
```

---

## Query 9 — Employees whose salary exceeds 3000 after 20% increment

```sql
SELECT Ename, Sal*1.20 AS Increased_Salary
FROM Employee
WHERE Sal*1.20 > 3000;
```

### Output
```
KING
SCOTT
FORD
JONES
BLAKE
```

---

## Query 10 — Employees whose salary has at least 3 digits

```sql
SELECT Ename, Sal
FROM Employee
WHERE Sal >= 100;
```

### Output
```
(All employees satisfy this condition)
```

---
