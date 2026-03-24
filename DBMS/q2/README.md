# Question 2 

---

## Query 1 — List all distinct jobs in Employee

```sql
SELECT DISTINCT JOB
FROM Employee;
```

### Output
```
JOB
-----------
CLERK
SALESMAN
MANAGER
ANALYST
PRESIDENT
```

---

## Query 2 — List all information about employees in Department 30

```sql
SELECT *
FROM Employee
WHERE DeptNo = 30;
```

### Output
```
EMPNO | ENAME  | JOB      | SAL | DEPTNO
-----------------------------------------
7499  | ALLEN  | SALESMAN | 1600| 30
7521  | WARD   | SALESMAN | 1250| 30
7654  | MARTIN | SALESMAN | 1250| 30
7698  | BLAKE  | MANAGER  | 2850| 30
7844  | TURNER | SALESMAN | 1500| 30
7900  | JAMES  | CLERK    | 950 | 30
```

---

## Query 3 — Find department numbers with department names greater than 20

```sql
SELECT DeptNo, Dname
FROM Department
WHERE DeptNo > 20;
```

### Output
```
DEPTNO | DNAME
---------------
30     | SALES
40     | OPERATIONS
```

---

## Query 4 — Information about managers and clerks in Department 30

```sql
SELECT *
FROM Employee
WHERE DeptNo = 30
AND JOB IN ('MANAGER', 'CLERK');
```

### Output
```
7698 | BLAKE | MANAGER | 2850 | 30
7900 | JAMES | CLERK   | 950  | 30
```

---

## Query 5 — Employee name, employee number and department of all clerks

```sql
SELECT Ename, EmpNo, DeptNo
FROM Employee
WHERE JOB = 'CLERK';
```

### Output
```
ENAME  | EMPNO | DEPTNO
------------------------
SMITH  | 7369  | 20
ADAMS  | 7876  | 20
JAMES  | 7900  | 30
MILLER | 7934  | 10
```

---

## Query 6 — Find all managers not in Department 30

```sql
SELECT *
FROM Employee
WHERE JOB = 'MANAGER'
AND DeptNo <> 30;
```

### Output
```
7566 | JONES | MANAGER | 2975 | 20
7782 | CLARK | MANAGER | 2450 | 10
```

---

## Query 7 — Employees in Department 10 who are not managers or clerks

```sql
SELECT *
FROM Employee
WHERE DeptNo = 10
AND JOB NOT IN ('MANAGER', 'CLERK');
```

### Output
```
No rows selected.
```

---

## Query 8 — Employees and jobs earning between 1200 and 1400

```sql
SELECT Ename, JOB, SAL
FROM Employee
WHERE SAL BETWEEN 1200 AND 1400;
```

### Output
```
WARD   | SALESMAN | 1250
MARTIN | SALESMAN | 1250
MILLER | CLERK    | 1300
```

---

## Query 9 — Name and Department Number of clerks, analysts or salesmen

```sql
SELECT Ename, DeptNo
FROM Employee
WHERE JOB IN ('CLERK', 'ANALYST', 'SALESMAN');
```

### Output
```
SMITH  | 20
ALLEN  | 30
WARD   | 30
MARTIN | 30
TURNER | 30
ADAMS  | 20
JAMES  | 30
FORD   | 20
SCOTT  | 40
MILLER | 10
```

---

## Query 10 — Employees whose names begin with M

```sql
SELECT Ename, DeptNo
FROM Employee
WHERE Ename LIKE 'M%';
```

### Output
```
MARTIN | 30
MILLER | 10
```

---
