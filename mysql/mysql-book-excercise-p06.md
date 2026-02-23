1️⃣ **Create a new database**

2️⃣ **Design the tables exactly as shown in the diagram**

3️⃣ Add **Primary Keys**

4️⃣ Add **Foreign Key relationships**

There are **two separate database designs** in the image:

---

# ✅ FIRST DATABASE STRUCTURE

### Tables in First Design:

* item_types
* items
* cities
* customers
* orders
* order_items

---

## 🔹 Step 1: Create Database

```sql
CREATE DATABASE shop_db;
USE shop_db;
```

---

## 🔹 Step 2: Create Tables

### 1️⃣ item_types

```sql
CREATE TABLE item_types (
    item_type_id INT(11) PRIMARY KEY,
    name VARCHAR(50)
);
```

---

### 2️⃣ items

```sql
CREATE TABLE items (
    item_id INT(11) PRIMARY KEY,
    name VARCHAR(50),
    item_type_id INT(11),
    FOREIGN KEY (item_type_id) REFERENCES item_types(item_type_id)
);
```

---

### 3️⃣ cities

```sql
CREATE TABLE cities (
    city_id INT(11) PRIMARY KEY,
    name VARCHAR(50)
);
```

---

### 4️⃣ customers

```sql
CREATE TABLE customers (
    customer_id INT(11) PRIMARY KEY,
    name VARCHAR(50),
    birthday DATE,
    city_id INT(11),
    FOREIGN KEY (city_id) REFERENCES cities(city_id)
);
```

---

### 5️⃣ orders

```sql
CREATE TABLE orders (
    order_id INT(11) PRIMARY KEY,
    customer_id INT(11),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

---

### 6️⃣ order_items (Many-to-Many table)

```sql
CREATE TABLE order_items (
    order_id INT(11),
    item_id INT(11),
    PRIMARY KEY (order_id, item_id),
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (item_id) REFERENCES items(item_id)
);
```

---

# ✅ SECOND DATABASE STRUCTURE

### Tables in Second Design:

* subjects
* majors
* students
* results
* payments

---

## 🔹 Step 1: Create Database

```sql
CREATE DATABASE college_db;
USE college_db;
```

---

## 🔹 Step 2: Create Tables

---

### 1️⃣ subjects

```sql
CREATE TABLE subjects (
    subject_id INT(11) PRIMARY KEY,
    subject_name VARCHAR(50)
);
```

---

### 2️⃣ majors

```sql
CREATE TABLE majors (
    major_id INT(11) PRIMARY KEY,
    name VARCHAR(50)
);
```

---

### 3️⃣ students

```sql
CREATE TABLE students (
    student_id INT(11) PRIMARY KEY,
    student_number VARCHAR(20),
    student_name VARCHAR(50),
    major_id INT(11),
    FOREIGN KEY (major_id) REFERENCES majors(major_id)
);
```

---

### 4️⃣ results

```sql
CREATE TABLE results (
    result_id INT(11) PRIMARY KEY,
    subject_id INT(11),
    student_id INT(11),
    FOREIGN KEY (subject_id) REFERENCES subjects(subject_id),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

---

### 5️⃣ payments

```sql
CREATE TABLE payments (
    payment_id INT(11) PRIMARY KEY,
    payment_date DATE,
    payment_amount DECIMAL(10,2),
    student_id INT(11),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

---

# 🔥 Important Notes

* All `*_id` columns are **Primary Keys**
* Foreign keys are added exactly as shown in diagram
* `order_items` is a **junction table** (many-to-many relationship)
* `results` connects students and subjects

---
