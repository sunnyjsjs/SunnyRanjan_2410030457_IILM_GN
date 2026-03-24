# Question 5 
---

## Query 1 — Total number of employees

```sql
SELECT COUNT(*) AS Total_Employees
FROM Employee;
```

### Output
```
TOTAL_EMPLOYEES
---------------
14
```

---

## Query 2 — Total salary paid to all employees

```sql
SELECT SUM(Sal) AS Total_Salary
FROM Employee;
```

### Output
```
TOTAL_SALARY
------------
29025
```

---

## Query 3 — Maximum salary

```sql
SELECT MAX(Sal) AS Maximum_Salary
FROM Employee;
```

### Output
```
MAXIMUM_SALARY
--------------
5000
```

---

## Query 4 — Minimum salary

```sql
SELECT MIN(Sal) AS Minimum_Salary
FROM Employee;
```

### Output
```
MINIMUM_SALARY
--------------
800
```

---

## Query 5 — Average salary

```sql
SELECT AVG(Sal) AS Average_Salary
FROM Employee;
```

### Output
```
AVERAGE_SALARY
--------------
2073.21
```

---

## Query 6 — Maximum salary paid to clerks

```sql
SELECT MAX(Sal)
FROM Employee
WHERE Job = 'CLERK';
```

### Output
```
1300
```

---

## Query 7 — Maximum salary in Department 20

```sql
SELECT MAX(Sal)
FROM Employee
WHERE DeptNo = 20;
```

### Output
```
3000
```

---

## Query 8 — Minimum salary paid to salesman

```sql
SELECT MIN(Sal)
FROM Employee
WHERE Job = 'SALESMAN';
```

### Output
```
1250
```

---

## Query 9 — Average salary of managers

```sql
SELECT AVG(Sal)
FROM Employee
WHERE Job = 'MANAGER';
```

### Output
```
2758.33
```

---

## Query 10 — Total salary of analysts in Department 40

```sql
SELECT SUM(Sal)
FROM Employee
WHERE Job = 'ANALYST'
AND DeptNo = 40;
```

### Output
```
3000
```

---

## Query 11 — Employee names in uppercase

```sql
SELECT UPPER(Ename)
FROM Employee;
```

### Output (sample)
```
SMITH
ALLEN
WARD
...
```

---

## Query 12 — Employee names in lowercase

```sql
SELECT LOWER(Ename)
FROM Employee;
```

### Output (sample)
```
smith
allen
ward
...
```

---

## Query 13 — Employee names in proper case

```sql
SELECT INITCAP(Ename)
FROM Employee;
```

### Output (sample)
```
Smith
Allen
Ward
...
```

---

## Query 14 — Length of your name

```sql
SELECT LENGTH('YOUR_NAME') AS Name_Length
FROM Dual;
```

### Output (example)
```
NAME_LENGTH
-----------
8
```

---

## Query 15 — Length of all employee names

```sql
SELECT Ename, LENGTH(Ename) AS Name_Length
FROM Employee;
```

### Output (sample)
```
SMITH  | 5
ALLEN  | 5
WARD   | 4
MARTIN | 6
...
```

---
