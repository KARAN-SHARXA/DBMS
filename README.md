# DBMS – Chapter 1: Database Theory (Detailed Notes + Interview Prep)

---

## 1. Importance of Data

Data is the raw material every application, business decision, and system is built on. Before any software can be useful, it needs a reliable way to store, organize, and retrieve data. This is the foundation for why databases exist at all — without structured data, applications would have no memory, no history, and no way to serve consistent information to users.

**Why it matters:** Every modern system — from a simple to-do app to a large-scale MERN stack application — depends on data being stored correctly and retrieved efficiently. As a developer, understanding *why* data matters helps you design better schemas and APIs.

---

## 2. What are Databases?

> A **Database** is a shared collection of logically related data (and a description of that data), designed to meet the information needs of an organization.

Key roles a database plays:

- **Data Storage** – Stores large volumes of structured data so it's searchable and retrievable.
- **Data Analysis** – Enables complex querying, reporting, and insight generation (this is where data analytics ties in directly).
- **Record Keeping** – Maintains critical records like financial transactions, customer data, inventory.
- **Web Applications** – Powers dynamic content and user management in web apps (e.g., MongoDB in a MERN stack).

**In short:** A database isn't just "a place to dump data" — it's a structured, queryable system that other software depends on.

---

## 3. Properties of an Ideal Database

A well-designed database should have these five properties:

| Property | Meaning |
|---|---|
| **Integrity** | Data must remain accurate and consistent (no corruption or contradictory records) |
| **Availability** | Data should be accessible whenever needed, with minimal downtime |
| **Security** | Only authorized users/processes can access or modify data |
| **Independent of Application** | The database structure shouldn't be tightly coupled to one specific application — it should be reusable |
| **Concurrency** | Multiple users should be able to access/modify data simultaneously without conflicts |

**Memory tip:** Think **I-A-S-I-C** — Integrity, Availability, Security, Independence, Concurrency.

---

## 4. Types of Databases

| Type | Description | Examples |
|---|---|---|
| **Relational (SQL)** | Organizes data into tables with rows and columns using a relational model | MySQL, PostgreSQL |
| **NoSQL** | Handles large amounts of unstructured/semi-structured data (documents, images, video) | MongoDB |
| **Column Databases** | Stores data in columns instead of rows — great for analytics/data warehousing | Amazon Redshift, Google BigQuery |
| **Graph Databases** | Stores/queries graph-structured data (relationships-heavy data) | Neo4j, Amazon Neptune |
| **Key-Value Databases** | Stores data as simple key-value pairs — great for caching | Redis, Amazon DynamoDB |

**Choosing between them** usually depends on:
- Structure of your data (structured vs. unstructured)
- Read/write speed requirements
- Relationship complexity between entities
- Scale (horizontal vs vertical scaling needs)

*As a MERN stack developer, you'll mostly work with MongoDB (NoSQL/document-based), but understanding relational databases is essential since many real-world systems still use SQL, and interviewers expect you to compare both confidently.*

---

## 5. Relational Databases (Deep Dive)

Relational (SQL) databases organize data into **tables (relations)**, where:
- Each **row** = a record (tuple)
- Each **column** = an attribute (field)

They rely on a well-defined schema, use **SQL** for querying, and enforce relationships between tables using **keys** (discussed in Section 8). They're ideal when data integrity, complex relationships, and transactions (ACID properties) matter most — e.g., banking systems, e-commerce order management.

---

## 6. What is a DBMS?

> A **Database Management System (DBMS)** is software that provides the interfaces and tools needed to store, organize, and manage data in a database.

It acts as a **middleman** between:
- The **raw database** (physical storage of data)
- The **applications/users** who need to access that data

Instead of applications directly manipulating raw files, they interact with the DBMS, which handles the complexity of storage, retrieval, and integrity behind the scenes.

**Examples of DBMS:** MySQL, PostgreSQL, Oracle, MongoDB (technically an NoSQL DBMS), SQL Server.

---

## 7. Core Functionalities of a DBMS

| Function | What it does |
|---|---|
| **Data Management** | Store, retrieve, and modify data |
| **Integrity** | Maintains accuracy and consistency of data |
| **Concurrency** | Allows simultaneous access by multiple users without conflicts |
| **Transaction Management** | Ensures a modification either fully succeeds or doesn't happen at all (atomicity) |
| **Security** | Restricts access to authorized users only |
| **Utilities** | Supports import/export, user management, backup, and logging |

**Interview tip:** This maps closely to the **ACID properties** (Atomicity, Consistency, Isolation, Durability) — if asked "how does a DBMS ensure reliable transactions," ACID is the answer they're looking for, and it stems directly from "Transaction Management" above.

---

## 8. Database Keys (Very Important for Interviews)

A **key** is an attribute (or set of attributes) that uniquely identifies a row (tuple) in a table. Keys ensure data integrity and define relationships between tables.

**Sample table used for reference:**

| Roll No | Name | Branch | |
|---|---|---|---|
| 1 | Nitish Singh | CSE | nitish@gmail.com |
| 2 | Ankit Sharma | EEE | ankit@gmail.com |
| 3 | Neha Verma | ME | neha@gmail.com |

### Types of Keys

1. **Super Key** – Any combination of columns that uniquely identifies a row. (E.g., {Roll No}, {Roll No, Name}, {Email} — all qualify, even with redundant columns.)

2. **Candidate Key** – A *minimal* super key — no redundant attributes. It's the smallest possible set of columns that still uniquely identifies a row. (E.g., {Roll No} alone, or {Email} alone.)

3. **Primary Key** – The candidate key chosen to be the main unique identifier for a table. Only **one** primary key per table, and it **cannot be NULL**. (E.g., Roll No.)

4. **Alternate Key** – Any candidate key that was *not* chosen as the primary key. (E.g., if Roll No is the primary key, Email becomes an alternate key.)

5. **Composite Key** – A primary key made up of **two or more** attributes, used when no single column is sufficient to uniquely identify a row.

6. **Surrogate Key** – An artificially generated key (like an auto-increment ID) with no business meaning, used purely for uniqueness.

7. **Foreign Key** – A primary key from one table used in another table to establish a relationship between the two tables.

**Interview one-liner:** "Primary key uniquely identifies a row within its own table; a foreign key references the primary key of another table to build relationships."

---

## 9. Cardinality of Relationships

**Cardinality** defines how many instances of one entity relate to instances of another entity in a relationship.

The three main types:

| Cardinality | Meaning | Example |
|---|---|---|
| **One-to-One (1:1)** | One record in Entity A relates to exactly one in Entity B | Person → Driving License Number |
| **One-to-Many (1:N)** | One record in Entity A relates to many in Entity B | Student → College Branch, Restaurant → Menu |
| **Many-to-Many (M:N)** | Many records in Entity A relate to many in Entity B | Students → Courses, Restaurants → Orders |

**Interview tip:** Be ready to give real-world examples and explain how Many-to-Many relationships are implemented in relational databases (using a **junction/bridge table**).

---

## 10. Drawbacks of Databases

| Drawback | Explanation |
|---|---|
| **Complexity** | Setting up and maintaining a database is time-consuming, especially at scale |
| **Cost** | Hardware, software, and skilled personnel add up |
| **Scalability** | Performance can degrade as data volume grows |
| **Data Integrity** | Hard to maintain consistency with many concurrent users |
| **Security** | Constant risk of unauthorized access/cyberattacks |
| **Data Migration** | Moving/upgrading databases is complex and risky |
| **Flexibility** | Rigid schema structures make adapting to new data types difficult |

---

## Quick Recap Table

| Topic | One-Line Summary |
|---|---|
| Data | The raw material every system depends on |
| Database | A structured, shared, logically related collection of data |
| Ideal Properties | Integrity, Availability, Security, Independence, Concurrency |
| Types | Relational, NoSQL, Column, Graph, Key-Value |
| DBMS | Software middleman between database and applications |
| Core Functions | Manage, protect, and control access/consistency of data |
| Keys | Super, Candidate, Primary, Alternate, Composite, Surrogate, Foreign |
| Cardinality | 1:1, 1:N, M:N relationships between entities |
| Drawbacks | Complexity, cost, scalability, integrity, security, migration, flexibility |

---
# DBMS – Chapter 2: SQL DDL Commands (Detailed Notes + Code Examples)

---

## 1. What is SQL?

> **SQL (Structured Query Language)** is a programming language used for managing and manipulating data in relational databases.

It lets you **insert, update, retrieve, and delete** data in a database. SQL is the standard way applications, websites, and businesses communicate with and control their databases.

---

## 2. Types of SQL Commands

SQL commands are grouped into categories based on what they do:

| Category | Full Form | Purpose | Example Commands |
|---|---|---|---|
| **DDL** | Data Definition Language | Defines/modifies structure of database objects | `CREATE`, `DROP`, `ALTER`, `TRUNCATE` |
| **DML** | Data Manipulation Language | Manipulates the actual data | `INSERT`, `UPDATE`, `DELETE` |
| **DQL** | Data Query Language | Queries/retrieves data | `SELECT` |
| **DCL** | Data Control Language | Controls access/permissions | `GRANT`, `REVOKE` |
| **TCL** | Transaction Control Language | Manages transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

This chapter focuses on **DDL** — commands that define and modify the structure of databases and tables (not the data inside them).

---

## 3. DDL Commands for Databases

```sql
-- CREATE a new database
CREATE DATABASE school;

-- DROP (permanently delete) a database
DROP DATABASE school;
```

| Command | Purpose |
|---|---|
| `CREATE` | Creates a new database |
| `DROP` | Deletes an entire database permanently, including all its tables |

---

## 4. DDL Commands for Tables

```sql
-- CREATE a table
CREATE TABLE students (
    roll_no INT,
    name VARCHAR(50),
    branch VARCHAR(20)
);

-- TRUNCATE removes all rows but keeps the table structure
TRUNCATE TABLE students;

-- DROP removes the table structure entirely
DROP TABLE students;
```

| Command | Purpose |
|---|---|
| `CREATE` | Creates a new table with defined columns |
| `TRUNCATE` | Deletes **all data** from a table instantly, but keeps the table itself (structure remains, faster than DELETE, can't be rolled back) |
| `DROP` | Deletes the table **and** its structure completely |

**Interview tip:** `TRUNCATE` vs `DELETE` vs `DROP` is a classic interview question:
- `DELETE` — removes rows one by one (can use `WHERE`, can be rolled back, slower)
- `TRUNCATE` — removes all rows at once, resets identity, faster, minimal logging
- `DROP` — removes the entire table structure + data, table no longer exists

---

## 5. Data Integrity

> **Data integrity** refers to the accuracy, completeness, and consistency of data stored in a database. It ensures data is protected from errors, corruption, or unauthorized changes.

Three key methods used to ensure data integrity:

1. **Constraints** – Rules that data must satisfy before being inserted/updated/deleted.
2. **Transactions** – A group of database operations treated as a single unit of work (all succeed or all fail).
3. **Normalization** – A design technique that reduces data redundancy by organizing data into separate related tables.

---

## 6. Constraints in MySQL (with Simple Code Examples)

> **Constraints** are rules or conditions applied to table columns to enforce data integrity and prevent inconsistent or corrupted data.

### 1. NOT NULL
**Definition:** Ensures a column cannot store a NULL (empty) value.
```sql
CREATE TABLE students (
    roll_no INT NOT NULL,
    name VARCHAR(50) NOT NULL
);
```

### 2. UNIQUE
**Definition:** Ensures all values in a column (or combination of columns) are different from each other.
```sql
CREATE TABLE students (
    email VARCHAR(100) UNIQUE
);

-- UNIQUE on a combination of columns (composite unique constraint)
CREATE TABLE enrollments (
    student_id INT,
    course_id INT,
    UNIQUE (student_id, course_id)
);
```

### 3. PRIMARY KEY
**Definition:** Uniquely identifies each row in a table. It combines `NOT NULL` + `UNIQUE`, and a table can have only one primary key.
```sql
CREATE TABLE students (
    roll_no INT PRIMARY KEY,
    name VARCHAR(50)
);
```

### 4. AUTO_INCREMENT
**Definition:** Automatically generates a unique number for a column every time a new row is inserted (commonly used with primary keys).
```sql
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50)
);
```

### 5. CHECK
**Definition:** Ensures values in a column satisfy a specific condition.
```sql
CREATE TABLE students (
    age INT CHECK (age >= 18)
);
```

### 6. DEFAULT
**Definition:** Sets a default value for a column when no value is provided during insert.
```sql
CREATE TABLE students (
    country VARCHAR(50) DEFAULT 'India'
);
```

### 7. FOREIGN KEY
**Definition:** Links a column in one table to the primary key of another table, enforcing a relationship between the two tables.
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(roll_no)
);
```

---

## 7. Referential Actions (Used with FOREIGN KEY)

Referential actions define **what happens to child rows when the referenced parent row is updated or deleted.**

### 1. RESTRICT
**Definition:** Prevents deletion/update of the parent row if matching child rows exist.
```sql
FOREIGN KEY (student_id) REFERENCES students(roll_no)
ON DELETE RESTRICT
ON UPDATE RESTRICT;
```

### 2. CASCADE
**Definition:** Automatically deletes/updates the matching child rows when the parent row is deleted/updated.
```sql
FOREIGN KEY (student_id) REFERENCES students(roll_no)
ON DELETE CASCADE
ON UPDATE CASCADE;
```

### 3. SET NULL
**Definition:** Sets the child row's foreign key column to NULL when the parent row is deleted/updated.
```sql
FOREIGN KEY (student_id) REFERENCES students(roll_no)
ON DELETE SET NULL
ON UPDATE SET NULL;
```

### 4. SET DEFAULT
**Definition:** Sets the child row's foreign key column to its default value when the parent row is deleted/updated.
```sql
FOREIGN KEY (student_id) REFERENCES students(roll_no)
ON DELETE SET DEFAULT
ON UPDATE SET DEFAULT;
```

**Interview tip:** `CASCADE` is the most commonly asked about — it's used when child data should not exist without its parent (e.g., deleting a `user` should delete all their `orders`).

---

## 8. ALTER TABLE Command

> The `ALTER TABLE` statement modifies the structure of an existing table — without needing to drop and recreate it.

### Add a column
```sql
ALTER TABLE students
ADD COLUMN email VARCHAR(100);
```

### Delete (drop) a column
```sql
ALTER TABLE students
DROP COLUMN email;
```

### Modify a column
```sql
ALTER TABLE students
MODIFY COLUMN name VARCHAR(100);
```

---

## 9. Editing and Deleting Constraints

Constraints themselves can also be added, edited, or removed after a table is created using `ALTER TABLE`.

### Add a constraint
```sql
ALTER TABLE students
ADD CONSTRAINT chk_age CHECK (age >= 18);
```

### Delete a constraint
```sql
-- Dropping a CHECK constraint
ALTER TABLE students
DROP CONSTRAINT chk_age;

-- Dropping a PRIMARY KEY
ALTER TABLE students
DROP PRIMARY KEY;
```

### Edit a constraint
MySQL doesn't allow directly "editing" a constraint — you **drop it and add a new one** with the updated rule:
```sql
ALTER TABLE students
DROP CONSTRAINT chk_age;

ALTER TABLE students
ADD CONSTRAINT chk_age CHECK (age >= 21);
```

---

## Quick Recap Table

| Concept | One-Line Summary |
|---|---|
| SQL | Language for managing/manipulating relational database data |
| DDL | Commands that define/modify structure (`CREATE`, `DROP`, `ALTER`, `TRUNCATE`) |
| Data Integrity | Accuracy + consistency of data, ensured via constraints, transactions, normalization |
| NOT NULL | Column can't be empty |
| UNIQUE | No duplicate values allowed |
| PRIMARY KEY | Unique + Not Null identifier for each row |
| AUTO_INCREMENT | Auto-generates sequential unique values |
| CHECK | Value must satisfy a condition |
| DEFAULT | Fallback value if none provided |
| FOREIGN KEY | Links a column to another table's primary key |
| RESTRICT | Blocks delete/update if child rows exist |
| CASCADE | Auto delete/update child rows with parent |
| SET NULL | Sets child's FK to NULL on parent delete/update |
| SET DEFAULT | Sets child's FK to default value on parent delete/update |
| ALTER TABLE | Modify existing table structure (add/drop/modify columns & constraints) |

---

## Interview Q&A Practice

**Q1: What's the difference between DDL and DML?**
DDL defines/modifies the *structure* of database objects (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`), while DML manipulates the *data* inside those objects (`INSERT`, `UPDATE`, `DELETE`).

**Q2: DELETE vs TRUNCATE vs DROP — what's the difference?**
`DELETE` removes specific rows (can use `WHERE`, is logged, can be rolled back). `TRUNCATE` removes all rows instantly but keeps the table structure. `DROP` removes the entire table, including its structure, permanently.

**Q3: What does the PRIMARY KEY constraint actually enforce?**
It enforces both `NOT NULL` and `UNIQUE` simultaneously, and there can only be one primary key per table.

**Q4: What's the difference between UNIQUE and PRIMARY KEY?**
A table can have multiple `UNIQUE` columns but only one `PRIMARY KEY`. Also, `UNIQUE` columns can technically hold one NULL value (in most databases), while `PRIMARY KEY` cannot hold NULL at all.

**Q5: Explain ON DELETE CASCADE with a real-world example.**
If a `users` table has related rows in an `orders` table via a foreign key, `ON DELETE CASCADE` means deleting a user automatically deletes all their associated orders — keeping the database free of orphaned records.

**Q6: How do you add a new column to an existing table without losing existing data?**
Use `ALTER TABLE table_name ADD COLUMN column_name datatype;` — this adds the column without affecting existing rows (new column will be NULL or default for existing rows).

**Q7: Can you directly modify a CHECK constraint's condition?**
No — in MySQL you must drop the existing constraint and add a new one with the updated condition.

**Q8: Why use AUTO_INCREMENT with PRIMARY KEY?**
It automatically generates a unique, sequential value for each new row, removing the need to manually assign unique IDs and reducing the risk of duplicate key errors.

**Q9: What is referential integrity, and how do FOREIGN KEY constraints help maintain it?**
Referential integrity ensures relationships between tables stay valid — a foreign key value must always match an existing primary key value in the referenced table (or be NULL, if allowed), preventing "orphan" records.

**Q10: When would you choose SET NULL over CASCADE for a foreign key?**
Use `SET NULL` when the child record should still exist even after the parent is deleted (e.g., an order shouldn't be deleted just because a customer's account is removed — instead its `customer_id` becomes NULL). Use `CASCADE` when the child record has no meaning without its parent.

---

*Since you're building MERN stack projects, note that MongoDB doesn't enforce these constraints natively the way SQL does — you'd implement similar validation logic (required fields, unique indexes, default values) at the schema level using Mongoose.*



# DBMS / SQL Notes — Database & Query Basics

Based on the SQL script covering: database/table creation, constraints, `INSERT`, `SELECT`, aliasing, computed columns, and `DISTINCT`.

---

## 1. Database & Table Creation

```sql
CREATE DATABASE dbms;

CREATE TABLE users(
    user_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);
```

**Key concepts:**
| Term | Meaning |
|---|---|
| `PRIMARY KEY` | Uniquely identifies each row; implicitly `NOT NULL` + `UNIQUE`. Only one per table. |
| `AUTO_INCREMENT` | Auto-generates the next integer value when you insert `NULL`/omit the column. MySQL-specific (Postgres uses `SERIAL`/`IDENTITY`). |
| `NOT NULL` | Column must always have a value. |
| `UNIQUE` | No two rows can share the same value in that column (unlike primary key, a table can have many `UNIQUE` columns, and `UNIQUE` allows one `NULL` in most DBs). |
| `VARCHAR(255)` | Variable-length string, max 255 chars. |

**Note on your script:** `NOt null` and similar mixed-case keywords work fine — SQL keywords are **case-insensitive**. Only string/identifier values (like table names on some OS/DBs) can be case-sensitive.

---

## 2. Inserting Data

```sql
INSERT INTO dbms.users(user_id, name, email, password)
VALUE (NULL, 'karan sharma', 'karansharma@gmail.com', '1234');

INSERT INTO dbms.users VALUE (NULL, 'ankit', 'ankit@gmail.com', '33333');

INSERT INTO dbms.users(user_id, name, email, password) VALUE
(NULL, 'karan sharma', 'karansharma1@gmail.com', '12342'),
(NULL, 'karan sharma', 'karansharma12@gmail.com', '12342');
```

**Key concepts:**
- `VALUE` and `VALUES` are both accepted by MySQL (`VALUES` is the standard/preferred keyword).
- Passing `NULL` for `user_id` lets `AUTO_INCREMENT` generate the next number automatically.
- The last statement shows a **multi-row insert** — inserting several rows in a single statement (more efficient than multiple separate `INSERT`s).
- Duplicate `name` values ('karan sharma' appears 3 times) are allowed because `name` has no `UNIQUE` constraint — only `email` does.
- ⚠️ If you tried to insert a duplicate **email**, this would throw a `Duplicate entry` error due to the `UNIQUE` constraint.

---

## 3. Basic SELECT Queries

```sql
SELECT * FROM dbms.users;
SELECT model, price, rating FROM dbms.smartphones;
```

- `SELECT *` → returns all columns (fine for exploration, avoid in production code — explicit columns are faster and safer).
- `SELECT col1, col2` → returns only specified columns, in the order listed.

```sql
SELECT * FROM dbms.smartphones WHERE 1;
```

- `WHERE 1` is a condition that always evaluates to **true**, so this behaves identically to `SELECT * FROM smartphones` (no rows filtered out). It's commonly used as a placeholder in dynamically-built queries (e.g., in app code where more `AND` conditions get appended later).

---

## 4. Aliasing (`AS`)

```sql
SELECT model AS n, price AS p FROM dbms.smartphones;
SELECT model, 'smartphones' AS 'type' FROM dbms.smartphones;
```

- `AS` renames a column (or expression) in the **output only** — it doesn't change the actual column name in the table.
- Alias names with spaces or reserved words need quotes/backticks: `` `type` `` or `'type'` (MySQL is lenient with quotes here, but backticks `` ` `` are the standard way to quote identifiers in MySQL).
- A literal string like `'smartphones'` can be selected as a constant column — useful for tagging rows when combining results from multiple tables (e.g., with `UNION`).

---

## 5. Computed / Derived Columns

```sql
SELECT model,
  SQRT(resolution_height * resolution_height + resolution_width * resolution_width) / screen_size AS 'ppi'
FROM dbms.smartphones;

SELECT model, rating/10 FROM dbms.smartphones;
```

- SQL lets you compute new values on the fly using arithmetic operators (`+ - * /`) and functions (`SQRT()`, etc.) directly in the `SELECT` clause.
- This example calculates **PPI (pixels per inch)** using the Pythagorean theorem: diagonal resolution in pixels ÷ screen size in inches.
- `rating/10` — normalizes a rating (e.g., out of 100) down to a 0–10 scale. Note: no alias is given here, so the output column name will be the raw expression, e.g. `rating/10`.

---

## 6. DISTINCT

```sql
SELECT DISTINCT(brand_name) AS 'ALL_BRAND' FROM dbms.smartphones;
SELECT processor_brand FROM dbms.smartphones;
SELECT DISTINCT(processor_brand) AS 'processor' FROM dbms.smartphones;
```

- `DISTINCT` removes duplicate rows from the result set, keeping only unique values.
- ⚠️ Common misconception: `DISTINCT(col)` looks like a function call, but the parentheses are **not required** — `DISTINCT` is a keyword, not a function. `SELECT DISTINCT brand_name` works identically.
- Without `DISTINCT`, `SELECT processor_brand` returns one row per record (including repeats).

---

## Interview Questions & Answers

### Beginner Level

**Q1. What is the difference between `PRIMARY KEY` and `UNIQUE`?**
A: Both enforce uniqueness, but a table can have only one `PRIMARY KEY` (which is also automatically `NOT NULL`), while it can have multiple `UNIQUE` columns, and most databases allow `NULL` in a `UNIQUE` column (though only one `NULL` per column typically, depending on the DB).

**Q2. What does `AUTO_INCREMENT` do, and what happens if you insert an explicit value for that column?**
A: It automatically assigns the next sequential integer when the column is left as `NULL`/omitted. If you insert an explicit value, MySQL uses that value instead, and the auto-increment counter updates to continue from the highest value used.

**Q3. What's the difference between `WHERE 1` and no `WHERE` clause at all?**
A: Functionally identical — both return all rows. `WHERE 1` is often used as a base condition in dynamically constructed queries so additional `AND` conditions can be appended programmatically without worrying about whether it's the "first" condition.

**Q4. Does `SELECT DISTINCT(col)` treat `DISTINCT` as a function?**
A: No — despite the parentheses, `DISTINCT` is a keyword modifying the whole `SELECT`, not a function applied to one column. `SELECT DISTINCT(a), b` still returns distinct rows based on the combination of `a` and `b`, not just distinct `a` values.

**Q5. What is the purpose of column aliasing with `AS`?**
A: To give a column or expression a more readable/custom name in the query's output, without altering the underlying table's schema.

### Intermediate Level

**Q6. If you run `SELECT DISTINCT(a), b FROM table`, does it return distinct values of `a` only, or distinct combinations of `a` and `b`?**
A: Distinct combinations of `(a, b)` — a common trap, since the parentheses make it look like `DISTINCT` only applies to `a`.

**Q7. Why might multi-row `INSERT` statements be preferred over multiple single-row inserts?**
A: They reduce the number of round-trips to the database and the number of transaction/log operations, making bulk inserts significantly faster.

**Q8. What error would occur if you tried to insert a user with an email that already exists in the table?**
A: A duplicate-key/unique-constraint violation error (e.g., MySQL's `Error 1062: Duplicate entry '...' for key 'email'`), because `email` has a `UNIQUE` constraint.

**Q9. How would you calculate PPI (pixels per inch) for a phone screen using SQL, given resolution height, width, and screen size?**
A: `SQRT(height^2 + width^2) / screen_size` — compute the diagonal resolution using the Pythagorean theorem, then divide by the physical diagonal screen size.

**Q10. What's the difference between `VALUE` and `VALUES` in an `INSERT` statement?**
A: In MySQL, both work as aliases of each other, but `VALUES` is the ANSI SQL-standard keyword and is the more portable/recommended choice.

### Slightly Advanced

**Q11. Why is `SELECT *` discouraged in production code?**
A: It fetches all columns even if unneeded (wasting bandwidth/memory), can break if the table schema changes (e.g., column order or new columns), and makes queries harder to optimize since the database can't use covering indexes as effectively.

**Q12. Can a `UNIQUE` column contain more than one `NULL` value?**
A: Depends on the DBMS. MySQL and SQL Server allow multiple `NULL`s in a `UNIQUE` column (since `NULL` isn't considered equal to another `NULL`), while some databases like Oracle behave differently under certain configurations.

**Q13. What's the difference between filtering with `WHERE` and computing a value in `SELECT`?**
A: `WHERE` filters which *rows* are returned based on a condition; a computed expression in `SELECT` doesn't filter rows — it transforms/derives a new value per row that's already included in the result.

**Q14. If `screen_size` is `0` or `NULL` for a row, what happens to the PPI calculation?**
A: Dividing by `0` typically returns `NULL` in MySQL (not an error, since MySQL by default doesn't throw a divide-by-zero exception), and dividing by `NULL` also returns `NULL`, since any arithmetic operation involving `NULL` yields `NULL`.

---

*Tip: Try rewriting Q6–Q14 as your own practice queries against the `smartphones`/`users` tables to reinforce these concepts.*



# Day 3 – SQL Notes (WHERE, Filtering, UPDATE, DELETE)

Table used: `dbms.smartphones`

---

## 1. Basic `WHERE` filtering

Filter rows using a condition on a column.

```sql
SELECT * FROM dbms.smartphones
WHERE brand_name = 'samsung';
```

```sql
SELECT * FROM dbms.smartphones
WHERE price > 50000;
```

**Note:** String values (`'samsung'`) go in single quotes; numbers don't.

---

## 2. `BETWEEN`

Used to filter values within a range (inclusive on both ends).

```sql
-- Old way (avoid — more verbose)
SELECT * FROM dbms.smartphones
WHERE price > 10000 AND price < 20000;

-- Better way using BETWEEN
SELECT * FROM dbms.smartphones
WHERE price BETWEEN 10000 AND 20000;
```

⚠️ `BETWEEN 10000 AND 20000` includes **both** 10000 and 20000 (inclusive), while `price > 10000 AND price < 20000` **excludes** the boundary values. They are not exactly the same!

---

## 3. Combining conditions with `AND`

All conditions must be true.

```sql
SELECT * FROM dbms.smartphones
WHERE price < 25000 
  AND rating > 80 
  AND processor_brand = 'snapdragon';
```

```sql
SELECT * FROM dbms.smartphones
WHERE brand_name = 'samsung' 
  AND ram_capacity > 8;
```

```sql
SELECT * FROM dbms.smartphones
WHERE brand_name = 'samsung' 
  AND processor_brand = 'snapdragon';
```

---

## 4. `DISTINCT`

Removes duplicate values from the result — useful to see unique categories.

```sql
SELECT DISTINCT(brand_name) FROM dbms.smartphones
WHERE price > 50000;
```

Returns the **unique list of brands** that have at least one phone priced above 50000 (not all matching rows).

---

## 5. `OR` vs `IN`

Both do the same thing, but `IN` is cleaner when checking a column against multiple possible values.

```sql
-- Using OR (long form)
SELECT * FROM dbms.smartphones
WHERE processor_brand = 'snapdragon' 
   OR processor_brand = 'exynos' 
   OR processor_brand = 'bionic';
```

```sql
-- Using IN (short form, same logic for 2 values)
SELECT * FROM dbms.smartphones
WHERE processor_brand IN ('snapdragon', 'exynos');
```

✅ `IN` is preferred for readability when checking multiple values of the **same column**.

---

## 6. `NOT IN`

Opposite of `IN` — excludes the listed values.

```sql
SELECT * FROM dbms.smartphones
WHERE processor_brand NOT IN ('snapdragon', 'exynos');
```

Returns all rows **except** those with snapdragon or exynos processors.

---

## 7. `UPDATE`

Modifies existing rows that match a condition.

```sql
UPDATE dbms.smartphones
SET processor_brand = 'dimensity'
WHERE processor_brand = 'mediatek';
```

Then verify the change:

```sql
SELECT * FROM dbms.smartphones
WHERE processor_brand = 'mediatek';   -- should return 0 rows now
```

⚠️ **Always run a `SELECT` with the same `WHERE` clause first** to confirm which rows will be affected before running `UPDATE` or `DELETE`. Without a `WHERE` clause, `UPDATE` changes **every row** in the table.

---

## 8. `DELETE`

Removes rows permanently that match a condition.

```sql
-- Step 1: Check what will be deleted
SELECT * FROM dbms.smartphones
WHERE price > 200000;

-- Step 2: Delete those rows
DELETE FROM dbms.smartphones
WHERE price > 200000;

-- Step 3: Confirm deletion
SELECT * FROM dbms.smartphones
WHERE price > 200000;   -- should return 0 rows
```

⚠️ **Danger:** `DELETE FROM table_name;` (no `WHERE`) deletes **all rows** in the table. Always double-check the `WHERE` clause before running `DELETE`.

---

## 🔑 Key Takeaways

| Concept | Purpose |
|---|---|
| `WHERE` | Filters rows based on condition(s) |
| `BETWEEN a AND b` | Range filter (inclusive) |
| `AND` / `OR` | Combine multiple conditions |
| `IN` / `NOT IN` | Match/exclude a column against a list of values |
| `DISTINCT` | Get unique values from a column |
| `UPDATE ... SET ... WHERE` | Modify existing rows |
| `DELETE FROM ... WHERE` | Remove rows |

**Golden Rule:** Before `UPDATE` or `DELETE`, always `SELECT` with the same `WHERE` clause first to preview affected rows.


# Day 4 – SQL Notes (Aggregate Functions)

Table used: `dbms.smartphones`

Aggregate functions operate on a **set of rows** and return a **single summary value**.

---

## 1. `MAX()` — highest value

```sql
SELECT MAX(price) FROM dbms.smartphones;
```

Returns the single highest price in the whole table.

```sql
SELECT MAX(price) FROM dbms.smartphones
WHERE brand_name = 'samsung';
```

Returns the highest price **only among Samsung phones** (combine with `WHERE` to scope the aggregate).

⚠️ Watch spelling — `'smasung'` won't match anything and will silently return `NULL`. SQL doesn't autocorrect string values.

---

## 2. `MIN()` — lowest value

```sql
SELECT MIN(ram_capacity) FROM dbms.smartphones;
```

Returns the smallest RAM capacity across all rows.

---

## 3. `AVG()` — average value

```sql
SELECT AVG(rating) FROM dbms.smartphones
WHERE brand_name = 'apple';
```

Returns the average rating of Apple phones only. `AVG` ignores `NULL` values automatically (doesn't count them in the denominator).

---

## 4. `SUM()` — total value

```sql
SELECT SUM(price) FROM dbms.smartphones;
```

Adds up the `price` column across all rows — total combined value of every phone in the table.

---

## 5. `COUNT(*)` — count rows

```sql
SELECT COUNT(*) FROM dbms.smartphones 
WHERE brand_name = 'oneplus';
```

Counts how many rows match the condition (i.e., how many OnePlus phones exist), including rows with `NULL` in any column.

---

## 6. `COUNT(DISTINCT ...)` — count unique values

```sql
SELECT COUNT(DISTINCT(brand_name)) FROM dbms.smartphones;
```

Counts how many **unique** brand names exist in the table — not the number of rows, just the number of distinct brands.

---

## 🔑 Key Takeaways

| Function | Purpose |
|---|---|
| `MAX(col)` | Highest value in a column |
| `MIN(col)` | Lowest value in a column |
| `AVG(col)` | Average of a column (ignores `NULL`) |
| `SUM(col)` | Total of a column |
| `COUNT(*)` | Number of rows matching condition |
| `COUNT(DISTINCT col)` | Number of unique values in a column |

**Notes:**
- Aggregate functions can be combined with `WHERE` to scope the calculation to specific rows before aggregating.
- `COUNT(*)` counts rows; `COUNT(column)` counts non-`NULL` values in that column — these can differ if there are `NULL`s.
- A typo in a string filter (e.g. `'smasung'` instead of `'samsung'`) won't error — it just matches zero rows, so aggregates like `MAX`/`AVG`/`SUM` return `NULL`. Always double check spelling in `WHERE` conditions.
# SQL Notes — Sorting Data (`ORDER BY` + `LIMIT`)

**Table used:** `dbms.smartphones`
**Topic of the day:** Sorting rows, picking top-N results, and combining sort with filters.

---

## 1. Sort by a single column, get top N

```sql
SELECT model, screen_size
FROM dbms.smartphones
WHERE brand_name = 'samsung'
ORDER BY screen_size DESC
LIMIT 5;
```

**What it does:** Filters to Samsung phones, sorts by `screen_size` largest → smallest, keeps only the top 5.

**Key idea:** `WHERE` always runs before `ORDER BY` and `LIMIT`. So the engine filters first, *then* sorts, *then* trims the result.

---

## 2. Sort by a computed (derived) column

```sql
SELECT model, num_front_cameras + num_rear_cameras AS total_cameras
FROM dbms.smartphones
ORDER BY total_cameras DESC;
```

**What it does:** Creates a new column `total_cameras` on the fly by adding two existing columns, then sorts by it.

**Key idea:** Once you give a computed column an alias (`AS total_cameras`), you can refer to that alias directly in `ORDER BY` — no need to repeat the whole expression. This only works because `ORDER BY` is evaluated *after* the `SELECT` list is built.

---

## 3. `LIMIT` with an offset — skipping rows

```sql
SELECT model, battery_capacity
FROM dbms.smartphones
ORDER BY battery_capacity DESC
LIMIT 2, 1;
```

**What it does:** Gets the **3rd highest** battery capacity phone.

**Key idea — the syntax that trips people up:**
```
LIMIT offset, count
```
- `offset = 2` → skip the first 2 rows (rank 1 and rank 2)
- `count = 1` → return just 1 row after skipping

So this returns the row at **rank 3**, not row "2 to 1". Equivalent, more readable version (standard SQL style):
```sql
LIMIT 1 OFFSET 2;
```
Both do the same thing — MySQL supports either form.

---

## 4. Sort ascending to find the "worst"/minimum

```sql
SELECT model, rating
FROM dbms.smartphones
WHERE brand_name = 'apple'
ORDER BY rating ASC
LIMIT 1;
```

**What it does:** Among Apple phones, finds the one with the **lowest** rating.

**Key idea:** `ASC` is actually the default (you could drop it and get the same result), but writing it explicitly makes intent clear — especially useful when reading old queries later.

---

## 5. Multi-column sort

```sql
SELECT *
FROM dbms.smartphones
ORDER BY brand_name ASC, price ASC;
```

**What it does:** Sorts all rows first by `brand_name` alphabetically, and *within* each brand, sorts by `price` ascending.

**Key idea:** In multi-column `ORDER BY`, the first column is the primary sort key; every column after it only matters for breaking ties within the previous column's groups. Order of columns in the clause = priority of sorting.

---

## Quick Reference Table

| Concept | Syntax | Notes |
|---|---|---|
| Sort descending | `ORDER BY col DESC` | Largest/latest first |
| Sort ascending | `ORDER BY col ASC` | Default if omitted |
| Top N rows | `LIMIT N` | After sorting |
| Skip + take (pagination) | `LIMIT offset, count` | offset is 0-indexed |
| Sort by alias | `ORDER BY alias_name` | Alias must be defined in SELECT |
| Multi-column sort | `ORDER BY col1, col2` | col2 breaks ties in col1 |
| Filter before sort | `WHERE ... ORDER BY ...` | Execution order: WHERE → ORDER BY → LIMIT |

---

## Execution Order Cheat Sheet (important!)

SQL doesn't run top-to-bottom the way it's written. Actual logical order:

```
FROM  →  WHERE  →  SELECT  →  ORDER BY  →  LIMIT
```

This is why you can use a `SELECT` alias inside `ORDER BY`, but **not** inside `WHERE` (since `WHERE` runs before `SELECT` builds the alias).

---

## Practice Ideas for Next Session
- Try `ORDER BY` with a `CASE WHEN` for custom sort order (e.g., force a specific brand to always appear first).
- Combine `GROUP BY` + `ORDER BY` (e.g., average rating per brand, sorted highest to lowest).
- Explore `ORDER BY` with `NULL` values — where do NULLs land by default in MySQL?
