# ✅ Table Name: **Worker**

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE | DEPARTMENT |
| --------- | ---------- | --------- | ------ | ------------ | ---------- |
| 001       | Monika     | Arora     | 100000 | 2014-02-20   | HR         |
| 002       | Niharika   | Verma     | 80000  | 2014-06-11   | Admin      |
| 003       | Vishal     | Singhal   | 300000 | 2014-02-20   | HR         |
| 004       | Amitabh    | Singh     | 500000 | 2014-02-20   | Admin      |
| 005       | Vivek      | Bhati     | 500000 | 2014-06-11   | Admin      |
| 006       | Vipul      | Diwan     | 200000 | 2014-06-11   | Account    |
| 007       | Satish     | Kumar     | 75000  | 2014-01-20   | Account    |
| 008       | Geetika    | Chauhan   | 90000  | 2014-04-11   | Admin      |

---

# ✅ Table Name: **Bonus**

| WORKER_REF_ID | BONUS_DATE | BONUS_AMOUNT |
| ------------- | ---------- | ------------ |
| 1             | 2016-02-20 | 5000         |
| 2             | 2016-06-11 | 3000         |
| 3             | 2016-02-20 | 4000         |
| 1             | 2016-02-20 | 4500         |
| 2             | 2016-06-11 | 3500         |

---

# ✅ Table Name: **Title**

| WORKER_REF_ID | WORKER_TITLE  | AFFECTED_FROM |
| ------------- | ------------- | ------------- |
| 1             | Manager       | 2016-02-20    |
| 2             | Executive     | 2016-06-11    |
| 8             | Executive     | 2016-06-11    |
| 5             | Manager       | 2016-06-11    |
| 4             | Asst. Manager | 2016-06-11    |
| 7             | Executive     | 2016-06-11    |
| 6             | Lead          | 2016-06-11    |
| 3             | Lead          | 2016-06-11    |

---

Three tables in your image: **Worker**, **Bonus**, and **Title**, followed by SQL practice questions (Q1–Q48). 
SQL queries standard MySQL syntax.

---
Here is the **DDL (CREATE TABLE statements)** based on the structure shown in your image, followed by the **complete list of all 48 questions** exactly as shown.

---

# ✅ DDL for Tables

### 🔹 1. Worker Table

```sql
CREATE TABLE Worker (
    WORKER_ID INT PRIMARY KEY,
    FIRST_NAME VARCHAR(25),
    LAST_NAME VARCHAR(25),
    SALARY INT,
    JOINING_DATE DATE,
    DEPARTMENT VARCHAR(25)
);
```

---

### 🔹 2. Bonus Table

```sql
CREATE TABLE Bonus (
    WORKER_REF_ID INT,
    BONUS_DATE DATE,
    BONUS_AMOUNT INT,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID)
);
```

---

### 🔹 3. Title Table

```sql
CREATE TABLE Title (
    WORKER_REF_ID INT,
    WORKER_TITLE VARCHAR(25),
    AFFECTED_FROM DATE,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID)
);
```

---

# ✅ Complete List of Questions (Q1–Q48)

### Page 1

**Q1.** Write an SQL Query to fetch "FIRST_NAME" from Worker table using alias name as `<WORKER_NAME>`.

**Q2.** Write an SQL Query to fetch "FIRST_NAME" from Worker table in upper case.

**Q3.** Write an SQL Query to fetch unique values of DEPARTMENT from Worker table.

**Q4.** Write an SQL Query to print the first three characters of FIRST_NAME from Worker table.

**Q5.** Write an SQL Query to find the position of the alphabet ('A') in the first name column 'Amitabh' from Worker table.

**Q6.** Write an SQL Query to print the FIRST_NAME from Worker table after removing white spaces from the right side.

**Q7.** Write an SQL Query to print the DEPARTMENT from Worker table after removing white spaces from the left side.

**Q8.** Write an SQL Query that fetches the unique values of DEPARTMENT from Worker table and prints its length.

**Q9.** Write an SQL Query to print the FIRST_NAME from Worker table after replacing 'A' with 'a'.

**Q10.** Write an SQL Query to print the FIRST_NAME and LAST_NAME from Worker table into a single column COMPLETE_NAME. A space char should separate them.

**Q11.** Write an SQL Query to print all Worker details from the Worker table order by FIRST_NAME ascending.

**Q12.** Write an SQL Query to print all Worker details from the Worker table order by FIRST_NAME ascending and DEPARTMENT descending.

**Q13.** Write an SQL Query to print details for workers with the first name as "Vipul" and "Satish" from Worker table.

**Q14.** Write an SQL Query to print details of workers excluding first names, "Vipul" and "Satish" from Worker table.

**Q15.** Write an SQL Query to print details of workers with DEPARTMENT name as "Admin".

**Q16.** Write an SQL Query to print details of the workers whose FIRST_NAME contains 'A'.

**Q17.** Write an SQL Query to print details of the workers whose FIRST_NAME ends with 'A'.

**Q18.** Write an SQL Query to print details of the workers whose FIRST_NAME ends with 'H' and contains six alphabets.

**Q19.** Write an SQL Query to print details of the workers whose SALARY lies between 100000 and 500000.

**Q20.** Write an SQL Query to print details of the workers who have joined in Feb 2014.

**Q21.** Write an SQL Query to fetch the count of employees working in the department 'Admin'.

**Q22.** Write an SQL Query to fetch worker names with salaries >= 50000 and <= 100000.

**Q23.** Write an SQL Query to fetch the no. of workers for each department in descending order.

**Q24.** Write an SQL Query to print details of the workers who are also Managers.

**Q25.** Write an SQL Query to fetch duplicate records having matching data in some fields of a table.

**Q26.** Write an SQL Query to show only odd rows from a table.

**Q27.** Write an SQL Query to show only even rows from a table.

**Q28.** Write an SQL Query to clone a new table from another table.

**Q29.** Write an SQL Query to fetch intersecting records of two tables.

**Q30.** Write an SQL Query to show records from one table that another table does not have.

**Q31.** Write an SQL Query to show the current date and time.

**Q32.** Write an SQL Query to show the top N (say 10) records of a table.

**Q33.** Write an SQL Query to determine the Nth (say N = 5) highest salary from a table.

**Q34.** Write an SQL Query to determine the 5th highest salary without using TOP or LIMIT method.

**Q35.** Write an SQL Query to fetch the list of employees with the same salary.

**Q36.** Write an SQL Query to show the second highest salary from a table.

**Q37.** Write an SQL Query to show one row twice in results from a table.

**Q38.** Write an SQL Query to fetch intersecting records of two tables.

**Q39.** Write an SQL Query to fetch the first 50% records from a table.

**Q40.** Write an SQL Query to fetch the departments that have less than five people in it.

**Q41.** Write an SQL Query to show all departments along with the number of people in there.

**Q42.** Write an SQL Query to show the last record from a table.

**Q43.** Write an SQL Query to fetch the first row of a table.

**Q44.** Write an SQL Query to fetch the last five records from a table.

**Q45.** Write an SQL Query to print the name of employees having the highest salary in each department.

**Q46.** Write an SQL Query to fetch three max salaries from a table.

**Q47.** Write an SQL Query to fetch three min salaries from a table.

**Q48.** Write an SQL Query to fetch Nth max salaries from a table.

**Q-49.** Write An SQL Query To Fetch Departments Along With The Total Salaries Paid For Each Of Them.

**Q-50.** Write An SQL Query To Fetch The Names Of Workers Who Earn The Highest Salary.

---

### ✅ Q1

```sql
SELECT FIRST_NAME AS WORKER_NAME 
FROM Worker;
```

### ✅ Q2

```sql
SELECT UPPER(FIRST_NAME) 
FROM Worker;
```

### ✅ Q3

```sql
SELECT DISTINCT DEPARTMENT 
FROM Worker;
```

### ✅ Q4

```sql
SELECT SUBSTRING(FIRST_NAME,1,3) 
FROM Worker;
```

### ✅ Q5

```sql
SELECT INSTR(FIRST_NAME,'A') 
FROM Worker 
WHERE FIRST_NAME='Amitabh';
```

### ✅ Q6

```sql
SELECT RTRIM(FIRST_NAME) 
FROM Worker;
```

### ✅ Q7

```sql
SELECT LTRIM(DEPARTMENT) 
FROM Worker;
```

### ✅ Q8

```sql
SELECT DISTINCT DEPARTMENT, LENGTH(DEPARTMENT) 
FROM Worker;
```

### ✅ Q9

```sql
SELECT REPLACE(FIRST_NAME,'A','a') 
FROM Worker;
```

### ✅ Q10

```sql
SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS COMPLETE_NAME 
FROM Worker;
```

### ✅ Q11

```sql
SELECT * 
FROM Worker 
ORDER BY FIRST_NAME ASC;
```

### ✅ Q12

```sql
SELECT * 
FROM Worker 
ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;
```

### ✅ Q13

```sql
SELECT * 
FROM Worker 
WHERE FIRST_NAME IN ('Vipul','Satish');
```

### ✅ Q14

```sql
SELECT * 
FROM Worker 
WHERE FIRST_NAME NOT IN ('Vipul','Satish');
```

### ✅ Q15

```sql
SELECT * 
FROM Worker 
WHERE DEPARTMENT='Admin';
```

### ✅ Q16

```sql
SELECT * 
FROM Worker 
WHERE FIRST_NAME LIKE '%A%';
```

### ✅ Q17

```sql
SELECT * 
FROM Worker 
WHERE FIRST_NAME LIKE '%A';
```

### ✅ Q18

```sql
SELECT * 
FROM Worker 
WHERE FIRST_NAME LIKE '_____H';
```

### ✅ Q19

```sql
SELECT * 
FROM Worker 
WHERE SALARY BETWEEN 100000 AND 500000;
```

### ✅ Q20

```sql
SELECT * 
FROM Worker 
WHERE YEAR(JOINING_DATE)=2014 
AND MONTH(JOINING_DATE)=2;
```

### ✅ Q21

```sql
SELECT COUNT(*) 
FROM Worker 
WHERE DEPARTMENT='Admin';
```

### ✅ Q22

```sql
SELECT FIRST_NAME, SALARY 
FROM Worker 
WHERE SALARY >= 50000 AND SALARY <= 100000;
```

---

## Page 5 Queries

### ✅ Q23

```sql
SELECT DEPARTMENT, COUNT(*) 
FROM Worker 
GROUP BY DEPARTMENT 
ORDER BY COUNT(*) DESC;
```

### ✅ Q24

```sql
SELECT W.* 
FROM Worker W
JOIN Title T 
ON W.WORKER_ID = T.WORKER_REF_ID
WHERE T.WORKER_TITLE='Manager';
```

### ✅ Q25

```sql
SELECT FIRST_NAME, COUNT(*) 
FROM Worker 
GROUP BY FIRST_NAME 
HAVING COUNT(*) > 1;
```

### ✅ Q26 (Odd rows)

```sql
SELECT * 
FROM Worker 
WHERE MOD(WORKER_ID,2)<>0;
```

### ✅ Q27 (Even rows)

```sql
SELECT * 
FROM Worker 
WHERE MOD(WORKER_ID,2)=0;
```

### ✅ Q28

```sql
CREATE TABLE Worker_Clone 
AS SELECT * FROM Worker;
```

### ✅ Q29

```sql
SELECT * FROM Worker
INTERSECT
SELECT * FROM Worker_Clone;
```

### ✅ Q30

```sql
SELECT * 
FROM Worker W
LEFT JOIN Bonus B 
ON W.WORKER_ID = B.WORKER_REF_ID
WHERE B.WORKER_REF_ID IS NULL;
```

### ✅ Q31

```sql
SELECT NOW();
```

### ✅ Q32

```sql
SELECT * 
FROM Worker 
LIMIT 10;
```

### ✅ Q33 (Nth highest salary – N=5 example)

```sql
SELECT DISTINCT SALARY 
FROM Worker W1
WHERE 5 = (
    SELECT COUNT(DISTINCT SALARY) 
    FROM Worker W2 
    WHERE W2.SALARY >= W1.SALARY
);
```

### ✅ Q34 (5th highest without LIMIT)

```sql
SELECT DISTINCT SALARY 
FROM Worker W1
WHERE 5 = (
    SELECT COUNT(DISTINCT SALARY) 
    FROM Worker W2 
    WHERE W2.SALARY >= W1.SALARY
);
```

### ✅ Q35

```sql
SELECT SALARY, COUNT(*) 
FROM Worker 
GROUP BY SALARY 
HAVING COUNT(*) > 1;
```

### ✅ Q36 (Second highest salary)

```sql
SELECT MAX(SALARY) 
FROM Worker 
WHERE SALARY < (SELECT MAX(SALARY) FROM Worker);
```

### ✅ Q37

```sql
SELECT * FROM Worker
UNION ALL
SELECT * FROM Worker WHERE WORKER_ID=1;
```

### ✅ Q38

```sql
SELECT W.WORKER_ID 
FROM Worker W
INNER JOIN Bonus B 
ON W.WORKER_ID = B.WORKER_REF_ID;
```

### ✅ Q39 (First 50%)

```sql
SELECT * 
FROM Worker 
LIMIT (SELECT COUNT(*)/2 FROM Worker);
```

### ✅ Q40

```sql
SELECT DEPARTMENT 
FROM Worker 
GROUP BY DEPARTMENT 
HAVING COUNT(*) < 5;
```

### ✅ Q41

```sql
SELECT DEPARTMENT, COUNT(*) AS TOTAL_EMPLOYEES
FROM Worker 
GROUP BY DEPARTMENT;
```

### ✅ Q42

```sql
SELECT * 
FROM Worker 
ORDER BY WORKER_ID DESC 
LIMIT 1;
```

### ✅ Q43

```sql
SELECT * 
FROM Worker 
ORDER BY WORKER_ID ASC 
LIMIT 1;
```

### ✅ Q44

```sql
SELECT * 
FROM Worker 
ORDER BY WORKER_ID DESC 
LIMIT 5;
```

### ✅ Q45

```sql
SELECT W.FIRST_NAME, W.SALARY, W.DEPARTMENT
FROM Worker W
WHERE SALARY = (
    SELECT MAX(SALARY)
    FROM Worker
    WHERE DEPARTMENT = W.DEPARTMENT
);
```

### ✅ Q46 (Top 3 salaries)

```sql
SELECT DISTINCT SALARY 
FROM Worker 
ORDER BY SALARY DESC 
LIMIT 3;
```

### ✅ Q47 (Lowest 3 salaries)

```sql
SELECT DISTINCT SALARY 
FROM Worker 
ORDER BY SALARY ASC 
LIMIT 3;
```

### ✅ Q48 (Nth max salary – generic)

```sql
SELECT DISTINCT SALARY 
FROM Worker W1
WHERE N = (
    SELECT COUNT(DISTINCT SALARY) 
    FROM Worker W2 
    WHERE W2.SALARY >= W1.SALARY
);
```

Using the **Worker, Bonus, and Title** tables given earlier, here are the answers for:

---

# ✅ Q49

**Write An SQL Query To Fetch Departments Along With The Total Salaries Paid For Each Of Them.**

### ✅ MySQL Query:

```sql
SELECT DEPARTMENT, SUM(SALARY) AS TOTAL_SALARY
FROM Worker
GROUP BY DEPARTMENT;
```

### 🔎 Explanation:

* `SUM(SALARY)` → Adds salaries department-wise
* `GROUP BY DEPARTMENT` → Groups records by department

### 📌 Output Based On Given Data:

| DEPARTMENT | TOTAL_SALARY |
| ---------- | ------------ |
| HR         | 400000       |
| Admin      | 670000       |
| Account    | 275000       |

---

# ✅ Q50

**Write An SQL Query To Fetch The Names Of Workers Who Earn The Highest Salary.**

### ✅ MySQL Query:

```sql
SELECT FIRST_NAME, LAST_NAME
FROM Worker
WHERE SALARY = (SELECT MAX(SALARY) FROM Worker);
```

### 🔎 Explanation:

* Subquery finds highest salary.
* Main query returns worker(s) having that salary.

### 📌 Output Based On Given Data:

| FIRST_NAME | LAST_NAME |
| ---------- | --------- |
| Amitabh    | Singh     |
| Vivek      | Bhati     |

(Both have salary = 500000)

---

