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
