## 📘 Given Tables

### **Table: EmployeeDetails**

| EmpId | FullName     | ManagerId | DateOfJoining |
| ----- | ------------ | --------- | ------------- |
| 121   | John Snow    | 321       | 01/31/2014    |
| 321   | Walter White | 986       | 01/30/2015    |
| 421   | KuldeepRana  | 876       | 27/11/2016    |

---

### **Table: EmployeeSalary**

| EmpId | Project | Salary |
| ----- | ------- | ------ |
| 121   | P1      | 8000   |
| 321   | P2      | 1000   |
| 421   | P1      | 12000  |

---

## 1️⃣ Count of employees working in project 'P1'

```sql
SELECT COUNT(*) 
FROM EmployeeSalary
WHERE Project = 'P1';
```

---

## 2️⃣ Employee names with salary > 5000 and <= 10000

```sql
SELECT ed.FullName
FROM EmployeeDetails ed
JOIN EmployeeSalary es 
ON ed.EmpId = es.EmpId
WHERE es.Salary > 5000 
AND es.Salary <= 10000;
```

---

## 3️⃣ Project-wise employee count (descending order)

```sql
SELECT Project, COUNT(*) AS TotalEmployees
FROM EmployeeSalary
GROUP BY Project
ORDER BY TotalEmployees DESC;
```

---

## 4️⃣ Fetch only first name (string before space)

```sql
SELECT SUBSTRING_INDEX(FullName, ' ', 1) AS FirstName
FROM EmployeeDetails;
```

(SQL Server)

```sql
SELECT LEFT(FullName, CHARINDEX(' ', FullName + ' ') - 1) AS FirstName
FROM EmployeeDetails;
```

---

## 5️⃣ Employee names and salary (include employees without salary record)

```sql
SELECT ed.FullName, es.Salary
FROM EmployeeDetails ed
LEFT JOIN EmployeeSalary es
ON ed.EmpId = es.EmpId;
```

---

## 6️⃣ Employees who are also managers

```sql
SELECT *
FROM EmployeeDetails
WHERE EmpId IN (
    SELECT DISTINCT ManagerId 
    FROM EmployeeDetails
);
```

---

## 7️⃣ Employees who have salary record

```sql
SELECT ed.*
FROM EmployeeDetails ed
JOIN EmployeeSalary es
ON ed.EmpId = es.EmpId;
```

---

## 8️⃣ Fetch duplicate records from a table

Example (duplicates by EmpId):

```sql
SELECT EmpId, COUNT(*)
FROM EmployeeDetails
GROUP BY EmpId
HAVING COUNT(*) > 1;
```

---

## 9️⃣ Remove duplicates without temporary table

```sql
DELETE ed1
FROM EmployeeDetails ed1
INNER JOIN EmployeeDetails ed2
WHERE ed1.EmpId > ed2.EmpId
AND ed1.FullName = ed2.FullName;
```

---

## 🔟 Fetch only odd rows

```sql
SELECT *
FROM EmployeeDetails
WHERE EmpId % 2 = 1;
```

---

## 1️⃣1️⃣ Fetch only even rows

```sql
SELECT *
FROM EmployeeDetails
WHERE EmpId % 2 = 0;
```

---

## 1️⃣2️⃣ Create new table with data and structure copied

```sql
CREATE TABLE NewEmployee
AS SELECT * FROM EmployeeDetails;
```

(SQL Server)

```sql
SELECT * INTO NewEmployee
FROM EmployeeDetails;
```

---

## 1️⃣3️⃣ Create empty table with same structure

```sql
CREATE TABLE NewEmployee
AS SELECT * FROM EmployeeDetails WHERE 1=0;
```

---

## 1️⃣4️⃣ Fetch common records between two tables

```sql
SELECT ed.EmpId
FROM EmployeeDetails ed
INNER JOIN EmployeeSalary es
ON ed.EmpId = es.EmpId;
```

---

## 1️⃣5️⃣ Records present in one table but not in another

```sql
SELECT *
FROM EmployeeDetails ed
WHERE NOT EXISTS (
    SELECT 1 
    FROM EmployeeSalary es
    WHERE ed.EmpId = es.EmpId
);
```

---

## 1️⃣6️⃣ Find current date-time

(MySQL)

```sql
SELECT NOW();
```

(SQL Server)

```sql
SELECT GETDATE();
```

---

## 1️⃣7️⃣ Employees who joined in Year 2016

```sql
SELECT *
FROM EmployeeDetails
WHERE YEAR(DateOfJoining) = 2016;
```

---
