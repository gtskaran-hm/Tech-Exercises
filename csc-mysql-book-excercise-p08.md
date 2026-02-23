**Student table** with columns:

* **id**
* **std_id**
* **Name**
* **marks**

From the image, the data looks approximately like this:

| id | std_id | Name     | marks |
| -- | ------ | -------- | ----- |
| 1  | 3      | Abhi     | 98    |
| 2  | 5      | Geethasi | 89    |
| 3  | 6      | Rahim    | 49    |
| 4  | 9      | Ram      | 60    |
| 5  | 1      | Rahul    | 87    |
| 6  | 1      | Rahul    | 96    |
| 7  | 1      | Rahul    | 96    |
| 8  | 9      | Ram      | 96    |
| 9  | 9      | Ram      | 96    |

---

## 1️⃣ Second Highest Marks

```sql
SELECT MAX(marks) 
FROM student 
WHERE marks < (SELECT MAX(marks) FROM student);
```

---

## 2️⃣ Find Duplicate Rows

To find duplicate records based on all columns:

```sql
SELECT id, std_id, name, marks, COUNT(*)
FROM student
GROUP BY id, std_id, name, marks
HAVING COUNT(*) > 1;
```

If checking duplicates by name and marks:

```sql
SELECT name, marks, COUNT(*)
FROM student
GROUP BY name, marks
HAVING COUNT(*) > 1;
```

---

## 3️⃣ Fetch First Record

```sql
SELECT * FROM student
ORDER BY id ASC
LIMIT 1;
```

(SQL Server)

```sql
SELECT TOP 1 * FROM student
ORDER BY id ASC;
```

---

## 4️⃣ Fetch Last Record

```sql
SELECT * FROM student
ORDER BY id DESC
LIMIT 1;
```

(SQL Server)

```sql
SELECT TOP 1 * FROM student
ORDER BY id DESC;
```

---

## 5️⃣ Display First 4 Records

```sql
SELECT * FROM student
ORDER BY id ASC
LIMIT 4;
```

---

## 6️⃣ Display Last 3 Records

```sql
SELECT * FROM student
ORDER BY id DESC
LIMIT 3;
```

---

## 7️⃣ Display Nth Record

Example: 5th record

```sql
SELECT * FROM student
ORDER BY id
LIMIT 1 OFFSET 4;
```

(SQL Server)

```sql
SELECT *
FROM (
    SELECT ROW_NUMBER() OVER (ORDER BY id) AS row_num, *
    FROM student
) t
WHERE row_num = 5;
```

---

## 8️⃣ Get 3 Highest Marks

```sql
SELECT DISTINCT marks
FROM student
ORDER BY marks DESC
LIMIT 3;
```

If you want full records:

```sql
SELECT *
FROM student
WHERE marks IN (
    SELECT DISTINCT marks
    FROM student
    ORDER BY marks DESC
    LIMIT 3
);
```

---

## 9️⃣ Display Odd Rows

```sql
SELECT *
FROM student
WHERE MOD(id, 2) = 1;
```

(SQL Server)

```sql
SELECT *
FROM student
WHERE id % 2 = 1;
```

---

## 🔟 Display Even Rows

```sql
SELECT *
FROM student
WHERE MOD(id, 2) = 0;
```

---

## 1️⃣1️⃣ Create Table With Same Structure

```sql
CREATE TABLE student_copy AS
SELECT * FROM student WHERE 1=0;
```

(SQL Server)

```sql
SELECT * INTO student_copy
FROM student
WHERE 1 = 0;
```

---

## 1️⃣2️⃣ Select Records Where Name = 'abhi geethasi'

If searching separately:

```sql
SELECT *
FROM student
WHERE name IN ('Abhi', 'Geethasi');
```

If searching combined string:

```sql
SELECT *
FROM student
WHERE name = 'abhi geethasi';
```

---

