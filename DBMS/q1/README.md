

# Question 1 

---

## Query 1 — Create Employee_master table using Employee table

```sql
CREATE TABLE Employee_master AS
SELECT * FROM Employee;
```

---

## Query 2 — Delete all records whose DeptNo is 10

```sql
DELETE FROM Employee_master
WHERE DeptNo = 10;
```

---

## Query 3 — Update salary by 10% for DeptNo 20

```sql
UPDATE Employee_master
SET SAL = SAL * 1.10
WHERE DeptNo = 20;
```

---

## Query 4 — Alter SAL column size to (10,2)

```sql
ALTER TABLE Employee_master
MODIFY SAL NUMBER(10,2);
```

---

## Query 5 — Drop Employee_master table

```sql
DROP TABLE Employee_master;
```
