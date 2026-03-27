# Question 6

---

## Query 1 — Display empno, ename, deptno with department name

```sql
SELECT EmpNo, Ename,
CASE DeptNo
    WHEN 10 THEN 'ACCOUNTING'
    WHEN 20 THEN 'RESEARCH'
    WHEN 30 THEN 'SALES'
    WHEN 40 THEN 'OPERATIONS'
END AS Department_Name
FROM Employee;
```

### Output (sample)

```
EMPNO | ENAME | DEPARTMENT_NAME
----- | ----- | ----------------
7369  | SMITH | RESEARCH
7499  | ALLEN | SALES
...
```

---

## Query 2 — Display your age in days

```sql
SELECT DATEDIFF(CURDATE(), '2000-01-01') AS Age_In_Days;
```

### Output (example)

```
AGE_IN_DAYS
-----------
9500
```

---

## Query 3 — Display your age in months

```sql
SELECT TIMESTAMPDIFF(MONTH, '2000-01-01', CURDATE()) AS Age_In_Months;
```

### Output (example)

```
AGE_IN_MONTHS
--------------
312
```

---

## Query 4 — Display current date in full format

```sql
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS Full_Date;
```

### Output (example)

```
15th August Friday 1997
```

---

## Query 5 — Display formatted employee joining message

```sql
SELECT CONCAT(Ename, ' has joined the company on ',
DATE_FORMAT(HireDate, '%W %D %M %Y')) AS Message
FROM Employee;
```

### Output (sample)

```
SMITH has joined the company on Wednesday 17th December 1980
...
```

---

## Query 6 — Example formatted sentence

```sql
SELECT CONCAT('Scott has joined the company on ',
DATE_FORMAT('1990-08-13', '%W %D %M %Y')) AS Message;
```

### Output

```
Scott has joined the company on Wednesday 13th August 1990
```

---

## Query 7 — Nearest Saturday after current date

```sql
SELECT DATE_ADD(CURDATE(),
INTERVAL (7 - DAYOFWEEK(CURDATE()) + 7) % 7 DAY) AS Next_Saturday;
```

### Output (example)

```
NEXT_SATURDAY
--------------
2026-03-28
```

---

## Query 8 — Display current time

```sql
SELECT CURRENT_TIME() AS Current_Time;
```

### Output (example)

```
CURRENT_TIME
------------
14:35:20
```

---

## Query 9 — Date three months before current date

```sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS Three_Months_Before;
```

### Output (example)

```
THREE_MONTHS_BEFORE
-------------------
2025-12-27
```

---

## Query 10 — Employees who joined in December

```sql
SELECT *
FROM Employee
WHERE MONTH(HireDate) = 12;
```

### Output (sample)

```
7369 | SMITH | ... | 1980-12-17
...
```

---

## Query 11 — Employees whose first 2 chars of hire date match last 2 of salary

```sql
SELECT *
FROM Employee
WHERE LEFT(DATE_FORMAT(HireDate,'%d%m%y'),2) =
      RIGHT(Sal,2);
```

### Output (sample)

```
(No rows or matching rows)
```

---

## Query 12 — Employees whose 10% salary equals year of joining

```sql
SELECT *
FROM Employee
WHERE (Sal * 0.10) = YEAR(HireDate);
```

### Output (sample)

```
(No rows or matching rows)
```

---

## Query 13 — Employees who joined before 15th of the month

```sql
SELECT *
FROM Employee
WHERE DAY(HireDate) < 15;
```

### Output (sample)

```
7369 | SMITH | ...
...
```

---

## Query 14 — Employees who joined before 15th day (alternate)

```sql
SELECT *
FROM Employee
WHERE DAYOFMONTH(HireDate) < 15;
```

### Output (sample)

```
7499 | ALLEN | ...
...
```

---

## Query 15 — Employees whose joining date matches deptno

```sql
SELECT *
FROM Employee
WHERE DAY(HireDate) = DeptNo;
```

### Output (sample)

```
(No rows or matching rows)
```

---
