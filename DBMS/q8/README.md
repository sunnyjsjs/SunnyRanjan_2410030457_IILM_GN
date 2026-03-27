# Question 8

---

## Query 1 — Display all employees with their department name

```sql
SELECT E.Ename, D.Dname
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo;
```

### Output (sample)

```
ENAME | DNAME
------|-------
SMITH | RESEARCH
ALLEN | SALES
...
```

---

## Query 2 — Employees whose manager is JONES (with manager name)

```sql
SELECT E.Ename AS Employee, M.Ename AS Manager
FROM Employee E
JOIN Employee M ON E.Mgr = M.EmpNo
WHERE M.Ename = 'JONES';
```

### Output (sample)

```
EMPLOYEE | MANAGER
---------|--------
SCOTT    | JONES
FORD     | JONES
...
```

---

## Query 3 — Employee details with dept, manager, and grade

```sql
SELECT 
E.Ename, 
E.Job, 
D.Dname, 
M.Ename AS Manager, 
S.Grade
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo
LEFT JOIN Employee M ON E.Mgr = M.EmpNo
JOIN SalGrade S ON E.Sal BETWEEN S.LosAL AND S.HiSal
ORDER BY D.Dname;
```

### Output (sample)

```
ENAME | JOB     | DNAME    | MANAGER | GRADE
------|---------|----------|---------|------
SMITH | CLERK   | RESEARCH | FORD    | 1
...
```

---

## Query 4 — Employees except clerks with job, grade, dept (sorted by salary desc)

```sql
SELECT 
E.Ename, 
E.Job, 
S.Grade, 
D.Dname, 
E.Sal
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo
JOIN SalGrade S ON E.Sal BETWEEN S.LosAL AND S.HiSal
WHERE E.Job <> 'CLERK'
ORDER BY E.Sal DESC;
```

### Output (sample)

```
ENAME | JOB     | GRADE | DNAME | SAL
------|---------|-------|-------|-----
KING  | MANAGER | 5     | ADMIN | 5000
...
```

---

## Query 5 — Employee name, job, and manager (including no manager)

```sql
SELECT 
E.Ename, 
E.Job, 
IFNULL(M.Ename, 'No Manager') AS Manager
FROM Employee E
LEFT JOIN Employee M ON E.Mgr = M.EmpNo;
```

### Output (sample)

```
ENAME | JOB     | MANAGER
------|---------|---------
KING  | MANAGER | No Manager
SMITH | CLERK   | FORD
...
```

---

## Query 6 — Employees earning 36000/year OR not clerks

```sql
SELECT 
E.Ename, 
E.Job, 
(E.Sal * 12) AS Annual_Salary,
E.DeptNo, 
D.Dname, 
S.Grade
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo
JOIN SalGrade S ON E.Sal BETWEEN S.LosAL AND S.HiSal
WHERE (E.Sal * 12) = 36000 OR E.Job <> 'CLERK';
```

### Output (sample)

```
ENAME | JOB | ANNUAL_SALARY | DEPTNO | DNAME | GRADE
...
```

---

## Query 7 — Employees earning 30000/year AND not clerks

```sql
SELECT 
E.Ename, 
E.Job, 
(E.Sal * 12) AS Annual_Salary,
E.DeptNo, 
D.Dname, 
S.Grade
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo
JOIN SalGrade S ON E.Sal BETWEEN S.LosAL AND S.HiSal
WHERE (E.Sal * 12) = 30000 AND E.Job <> 'CLERK';
```

### Output (sample)

```
(No rows or matching rows)
```

---

## Query 8 — Employee and manager details (with ‘No Manager’)

```sql
SELECT 
E.EmpNo AS Emp_No,
E.Ename AS Employee,
IFNULL(M.EmpNo, '---') AS Mgr_No,
IFNULL(M.Ename, 'No Manager') AS Manager
FROM Employee E
LEFT JOIN Employee M ON E.Mgr = M.EmpNo;
```

### Output (sample)

```
EMP_NO | EMPLOYEE | MGR_NO | MANAGER
-------|----------|--------|---------
7839   | KING     | ---    | No Manager
7369   | SMITH    | 7902   | FORD
...
```

---

## Query 9 — Department name, dept no, and total salary

```sql
SELECT 
D.Dname, 
D.DeptNo, 
SUM(E.Sal) AS Total_Salary
FROM Department D
JOIN Employee E ON D.DeptNo = E.DeptNo
GROUP BY D.DeptNo, D.Dname;
```

### Output (sample)

```
DNAME   | DEPTNO | TOTAL_SALARY
--------|--------|--------------
SALES   | 30     | 9400
...
```

---

## Query 10 — Employee number, name, and department location

```sql
SELECT 
E.EmpNo, 
E.Ename, 
D.Loc
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo;
```

### Output (sample)

```
EMPNO | ENAME | LOC
------|-------|------
7369  | SMITH | DALLAS
...
```

---

## Query 11 — Employee name and department name

```sql
SELECT 
E.Ename, 
D.Dname
FROM Employee E
JOIN Department D ON E.DeptNo = D.DeptNo;
```

### Output (sample)

```
ENAME | DNAME
------|-------
SMITH | RESEARCH
ALLEN | SALES
...
```

---
