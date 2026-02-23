# 📘 Exercises: Table Relations

## 🔹 One-To-One Relationship

Create two tables as follows. Use appropriate data types.

---

## Table: Persons

| person_id | first_name | salary   | passport_id |
| --------- | ---------- | -------- | ----------- |
| 1         | Roberto    | 43300.00 | 102         |
| 2         | Tom        | 56100.00 | 103         |
| 3         | Yana       | 60200.00 | 101         |

---

## Table: Passports

| passport_id | passport_number |
| ----------- | --------------- |
| 101         | N34FG21B        |
| 102         | K65LO4R7        |
| 103         | ZE657QP2        |

---

### Instructions:

* Insert the data from the example above.
* Alter table persons and make person_id a primary key.
* Create a foreign key between persons and passports by using passport_id column.

---

# 🔹 One-To-Many Relationship

Create two tables as follows. Use appropriate data types.

---

## Table: Manufacturers

| manufacturer_id | name  | established_on |
| --------------- | ----- | -------------- |
| 1               | BMW   | 01/03/1916     |
| 2               | Tesla | 01/01/2003     |
| 3               | Lada  | 01/05/1966     |

---

## Table: Models

| model_id | name    | manufacturer_id |
| -------- | ------- | --------------- |
| 101      | X1      | 1               |
| 102      | i6      | 1               |
| 103      | Model S | 2               |
| 104      | Model X | 2               |
| 105      | Model 3 | 2               |
| 106      | Nova    | 3               |

---

### Instructions:

* Insert the data from the example above.
* Add primary keys and foreign keys.

---

# 🔹 Many-To-Many Relationship

Create three tables as follows. Use appropriate data types.

---

## Table: students

| student_id | Name |
| ---------- | ---- |
| 1          | Mila |
| 2          | Toni |
| 3          | Ron  |

---

## Table: exams

| exam_id | name       |
| ------- | ---------- |
| 101     | Spring MVC |
| 102     | Neo4j      |
| 103     | Oracle 11g |

---

## Table: students_exams

| student_id | exam_id |
| ---------- | ------- |
| 1          | 101     |
| 1          | 102     |
| 2          | 101     |
| 3          | 103     |
| 2          | 102     |
| 2          | 103     |

---

### Instructions:

* Insert the data from the example above.
* Add primary keys and foreign keys.
* Have in mind that table student_exams should have a composite primary key.

---

# 🔹 Self-Referencing Table

Create a single table as follows.

---

## Table: Teachers

| teacher_id | name   | manager_id |
| ---------- | ------ | ---------- |
| 101        | John   | NULL       |
| 102        | Maya   | 106        |
| 103        | Silvia | 106        |
| 104        | Ted    | 105        |
| 105        | Mark   | 101        |
| 106        | Greta  | 101        |

---

Below is the complete solution in **MySQL SQL** including:

1. ✅ Table Structures (DDL)
2. ✅ Insert Data
3. ✅ Questions
4. ✅ Answers (Queries)

Based exactly on your images.

---

# 🔹 PART 1 — ONE-TO-ONE RELATIONSHIP

## ✅ Table Structure

### 1️⃣ Passports Table

```sql
CREATE TABLE Passports (
    passport_id INT PRIMARY KEY,
    passport_number VARCHAR(20)
);
```

### 2️⃣ Persons Table

```sql
CREATE TABLE Persons (
    person_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    salary DECIMAL(10,2),
    passport_id INT UNIQUE,
    FOREIGN KEY (passport_id) REFERENCES Passports(passport_id)
);
```

---

## ✅ Insert Data

```sql
INSERT INTO Passports VALUES
(101, 'N34FG21B'),
(102, 'K65LO4R7'),
(103, 'ZE657QP2');

INSERT INTO Persons VALUES
(1, 'Roberto', 43300.00, 102),
(2, 'Tom', 56100.00, 103),
(3, 'Yana', 60200.00, 101);
```

---

# 🔹 PART 2 — ONE-TO-MANY RELATIONSHIP

## ✅ Table Structure

### 1️⃣ Manufacturers

```sql
CREATE TABLE Manufacturers (
    manufacturer_id INT PRIMARY KEY,
    name VARCHAR(50),
    established_on DATE
);
```

### 2️⃣ Models

```sql
CREATE TABLE Models (
    model_id INT PRIMARY KEY,
    name VARCHAR(50),
    manufacturer_id INT,
    FOREIGN KEY (manufacturer_id) REFERENCES Manufacturers(manufacturer_id)
);
```

---

## ✅ Insert Data

```sql
INSERT INTO Manufacturers VALUES
(1, 'BMW', '1916-03-01'),
(2, 'Tesla', '2003-01-01'),
(3, 'Lada', '1966-05-01');

INSERT INTO Models VALUES
(101, 'X1', 1),
(102, 'i6', 1),
(103, 'Model S', 2),
(104, 'Model X', 2),
(105, 'Model 3', 2),
(106, 'Nova', 3);
```

---

## ✅ Example Question

### Q1: Show all models with their manufacturer names.

```sql
SELECT m.model_id, m.name AS model_name, mf.name AS manufacturer_name
FROM Models m
JOIN Manufacturers mf
ON m.manufacturer_id = mf.manufacturer_id;
```

---

# 🔹 PART 3 — MANY-TO-MANY RELATIONSHIP

## ✅ Table Structure

### 1️⃣ Students

```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### 2️⃣ Exams

```sql
CREATE TABLE Exams (
    exam_id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### 3️⃣ Students_Exams (Composite Primary Key)

```sql
CREATE TABLE Students_Exams (
    student_id INT,
    exam_id INT,
    PRIMARY KEY (student_id, exam_id),
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (exam_id) REFERENCES Exams(exam_id)
);
```

---

## ✅ Insert Data

```sql
INSERT INTO Students VALUES
(1, 'Mila'),
(2, 'Toni'),
(3, 'Ron');

INSERT INTO Exams VALUES
(101, 'Spring MVC'),
(102, 'Neo4j'),
(103, 'Oracle 11g');

INSERT INTO Students_Exams VALUES
(1,101),
(1,102),
(2,101),
(3,103),
(2,102),
(2,103);
```

---

## ✅ Example Question

### Q2: Show student names with their exams.

```sql
SELECT s.name AS student_name, e.name AS exam_name
FROM Students s
JOIN Students_Exams se ON s.student_id = se.student_id
JOIN Exams e ON se.exam_id = e.exam_id;
```

---

# 🔹 PART 4 — SELF JOIN (Teachers Table)

## ✅ Table Structure

```sql
CREATE TABLE Teachers (
    teacher_id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT,
    FOREIGN KEY (manager_id) REFERENCES Teachers(teacher_id)
);
```

---

## ✅ Insert Data

```sql
INSERT INTO Teachers VALUES
(101, 'John', NULL),
(102, 'Maya', 106),
(103, 'Silvia', 106),
(104, 'Ted', 105),
(105, 'Mark', 101),
(106, 'Greta', 101);
```

---

## ✅ Example Question

### Q3: Show teachers with their manager names.

```sql
SELECT t1.name AS teacher,
       t2.name AS manager
FROM Teachers t1
LEFT JOIN Teachers t2
ON t1.manager_id = t2.teacher_id;
```

---

# 🔹 EXTRA QUESTIONS (From Page 6)

### Q: Fetch departments along with total salaries paid.

```sql
SELECT department, SUM(salary) AS total_salary
FROM Worker
GROUP BY department;
```

### Q: Fetch names of workers who earn the highest salary.

```sql
SELECT first_name
FROM Worker
WHERE salary = (SELECT MAX(salary) FROM Worker);
```

---

# ✅ What You Now Have

✔ One-to-One relationship (Persons ↔ Passports)

✔ One-to-Many relationship (Manufacturers → Models)

✔ Many-to-Many relationship (Students ↔ Exams)

✔ Self Join example (Teachers)

✔ All structures with proper PK & FK

✔ Insert statements

✔ Example queries

---
