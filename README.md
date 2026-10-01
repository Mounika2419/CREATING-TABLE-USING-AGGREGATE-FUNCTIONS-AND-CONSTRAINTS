# Bank Database SQL

## 1. Introduction

This SQL program creates a `bank` table and demonstrates different SQL operations such as:

* Creating a table
* Primary Key
* Inserting records
* Displaying records
* `WHERE` condition
* `COUNT()`
* Selecting specific columns
* `SUM()`
* `LIKE`
* `MAX()`
* `MIN()`
* `AVG()`

---

## 2. Create Bank Table

```sql
CREATE TABLE bank(
    bank_id INT PRIMARY KEY,
    cust_name VARCHAR(20),
    bank_name VARCHAR(30),
    amount DECIMAL(5,2),
    transaction INT
);
```

This creates a table named `bank`.

| Column        | Data Type    | Purpose                 |
| ------------- | ------------ | ----------------------- |
| `bank_id`     | INT          | Unique bank/customer ID |
| `cust_name`   | VARCHAR(20)  | Customer name           |
| `bank_name`   | VARCHAR(30)  | Bank name               |
| `amount`      | DECIMAL(5,2) | Transaction amount      |
| `transaction` | INT          | Transaction value       |

### Primary Key

```sql
bank_id INT PRIMARY KEY
```

`bank_id` uniquely identifies every row in the table.

---

## 3. Describe the Table

```sql
DESC bank;
```

`DESC` displays the structure of the `bank` table.

It shows the column names, data types, key information, NULL information, and default values.

---

## 4. Insert Records

```sql
INSERT INTO bank VALUES(1,'anil','sbi',200.00,25);
INSERT INTO bank VALUES(2,'ramu','union',300.00,25);
INSERT INTO bank VALUES(3,'raju','union',400.00,25);
INSERT INTO bank VALUES(4,'ravi','andhra',500.00,23);
INSERT INTO bank VALUES(5,'amala','canara',600.00,15);
```

These commands insert five records into the `bank` table.

### Table Data

| bank_id | cust_name | bank_name | amount | transaction |
| ------: | --------- | --------- | -----: | ----------: |
|       1 | anil      | sbi       | 200.00 |          25 |
|       2 | ramu      | union     | 300.00 |          25 |
|       3 | raju      | union     | 400.00 |          25 |
|       4 | ravi      | andhra    | 500.00 |          23 |
|       5 | amala     | canara    | 600.00 |          15 |

---

# 5. Display All Records

```sql
SELECT * FROM bank;
```

`SELECT *` displays **all columns and all rows** from the table.

---

# 6. WHERE Clause

```sql
SELECT * FROM bank WHERE transaction > 20;
```

The `WHERE` clause filters records based on a condition.

Here, only records where `transaction` is greater than `20` are displayed.

### Result

| bank_id | cust_name | bank_name | amount | transaction |
| ------: | --------- | --------- | -----: | ----------: |
|       1 | anil      | sbi       | 200.00 |          25 |
|       2 | ramu      | union     | 300.00 |          25 |
|       3 | raju      | union     | 400.00 |          25 |
|       4 | ravi      | andhra    | 500.00 |          23 |

`amala` is not displayed because her transaction value is `15`.

---

# 7. COUNT() Function

```sql
SELECT COUNT(8) FROM bank;
```

`COUNT()` is an aggregate function used to count rows.

Since `8` is a non-NULL constant, `COUNT(8)` counts every row.

### Result

```text
5
```

### Better and clearer version

```sql
SELECT COUNT(*) FROM bank;
```

This is generally preferred when the intention is simply to count all rows.

---

# 8. Selecting Specific Columns

```sql
SELECT cust_name, amount FROM bank;
```

This displays only the `cust_name` and `amount` columns.

### Result

| cust_name | amount |
| --------- | -----: |
| anil      | 200.00 |
| ramu      | 300.00 |
| raju      | 400.00 |
| ravi      | 500.00 |
| amala     | 600.00 |

---

# 9. WHERE with Text

```sql
SELECT cust_name FROM bank
WHERE bank_name = 'union';
```

This displays customers whose bank name is `union`.

### Result

| cust_name |
| --------- |
| ramu      |
| raju      |

---

# 10. SUM() Function

```sql
SELECT SUM(amount) FROM bank;
```

`SUM()` calculates the total of a numeric column.

Calculation:

```text
200 + 300 + 400 + 500 + 600 = 2000
```

### Result

```text
2000.00
```

---

# 11. LIKE Operator

The `LIKE` operator is used for **pattern matching**.

## Customers whose names start with `r`

```sql
SELECT * FROM bank
WHERE cust_name LIKE 'r%';
```

`r%` means:

> Starts with `r` followed by any number of characters.

### Result

| bank_id | cust_name | bank_name | amount | transaction |
| ------: | --------- | --------- | -----: | ----------: |
|       2 | ramu      | union     | 300.00 |          25 |
|       3 | raju      | union     | 400.00 |          25 |
|       4 | ravi      | andhra    | 500.00 |          23 |

---

## Customers whose names start with `a`

```sql
SELECT * FROM bank
WHERE cust_name LIKE 'a%';
```

### Result

| bank_id | cust_name | bank_name | amount | transaction |
| ------: | --------- | --------- | -----: | ----------: |
|       1 | anil      | sbi       | 200.00 |          25 |
|       5 | amala     | canara    | 600.00 |          15 |

---

# 12. MAX() Function

```sql
SELECT MAX(amount) FROM bank;
```

`MAX()` returns the highest value.

The amounts are:

```text
200, 300, 400, 500, 600
```

### Result

```text
600.00
```

---

# 13. MIN() Function

```sql
SELECT MIN(amount) FROM bank;
```

`MIN()` returns the smallest value.

### Result

```text
200.00
```

---

# 14. AVG() Function

```sql
SELECT AVG(amount) FROM bank;
```

`AVG()` calculates the average value.

Calculation:

```text
(200 + 300 + 400 + 500 + 600) / 5
= 2000 / 5
= 400
```

### Result

```text
400.00
```

---

# 15. Aggregate Functions Used

Your program uses four important aggregate functions:

| Function  | Purpose             | Result |
| --------- | ------------------- | -----: |
| `COUNT()` | Counts rows         |      5 |
| `SUM()`   | Calculates total    |   2000 |
| `MAX()`   | Finds highest value |    600 |
| `MIN()`   | Finds lowest value  |    200 |
| `AVG()`   | Calculates average  |    400 |

---

# 16. Important SQL Concepts

### PRIMARY KEY

```sql
bank_id INT PRIMARY KEY
```

Uniquely identifies each record.

### WHERE

```sql
WHERE transaction > 20
```

Filters records according to a condition.

### LIKE

```sql
cust_name LIKE 'r%'
```

Searches for values matching a pattern.

### `*`

```sql
SELECT * FROM bank;
```

Means all columns.

### Aggregate Functions

Functions such as:

```sql
COUNT()
SUM()
MAX()
MIN()
AVG()
```

perform calculations on multiple rows and return a single result.

---

# 17. Complete SQL Program

```sql
CREATE TABLE bank(
    bank_id INT PRIMARY KEY,
    cust_name VARCHAR(20),
    bank_name VARCHAR(30),
    amount DECIMAL(5,2),
    transaction INT
);

DESC bank;

INSERT INTO bank VALUES(1,'anil','sbi',200.00,25);
INSERT INTO bank VALUES(2,'ramu','union',300.00,25);
INSERT INTO bank VALUES(3,'raju','union',400.00,25);
INSERT INTO bank VALUES(4,'ravi','andhra',500.00,23);
INSERT INTO bank VALUES(5,'amala','canara',600.00,15);

SELECT * FROM bank;

SELECT * FROM bank
WHERE transaction > 20;

SELECT COUNT(*) FROM bank;

SELECT cust_name, amount
FROM bank;

SELECT cust_name
FROM bank
WHERE bank_name = 'union';

SELECT SUM(amount)
FROM bank;

SELECT *
FROM bank
WHERE cust_name LIKE 'r%';

SELECT *
FROM bank
WHERE cust_name LIKE 'a%';

SELECT MAX(amount)
FROM bank;

SELECT MIN(amount)
FROM bank;

SELECT AVG(amount)
FROM bank;
```

---

# 18. Summary

This program demonstrates the basic SQL concepts of **table creation, primary keys, data insertion, filtering, pattern matching, column selection, and aggregate functions**.

The most important commands to remember are:

```text
CREATE TABLE  → Creates a table
INSERT        → Adds records
SELECT        → Retrieves records
WHERE         → Filters records
LIKE          → Pattern matching
COUNT()       → Counts records
SUM()         → Total
MAX()         → Highest value
MIN()         → Lowest value
AVG()         → Average
```
