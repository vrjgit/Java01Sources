
# Postgress CheatSheet

Got it 👍
Below is a **consolidated PostgreSQL cheat sheet in TABLE format**, with **command → explanation → usage → examples**, so you can **revise fast and still understand deeply**.

This format is **interview-ready + day-to-day usable** for Spring Boot / JPA work.

---

# 🐘 PostgreSQL Comprehensive Cheat Sheet (Consolidated Table)

---

## 1️⃣ Database Management

| Command               | Explanation            | When to Use         | Example                   |
| --------------------- | ---------------------- | ------------------- | ------------------------- |
| `\l`                  | Lists all databases    | Verify DB existence | `\l`                      |
| `CREATE DATABASE db;` | Creates a new database | Project setup       | `CREATE DATABASE lms_db;` |
| `\c db`               | Connect to database    | Before querying     | `\c lms_db`               |
| `DROP DATABASE db;`   | Deletes database       | Cleanup             | `DROP DATABASE test_db;`  |

---

## 2️⃣ User & Role Management

| Command                                        | Explanation       | When to Use      | Example                                             |
| ---------------------------------------------- | ----------------- | ---------------- | --------------------------------------------------- |
| `\du`                                          | Lists users/roles | Security review  | `\du`                                               |
| `CREATE USER user WITH PASSWORD 'pwd';`        | Creates user      | Production setup | `CREATE USER viraj WITH PASSWORD '123';`            |
| `GRANT ALL PRIVILEGES ON DATABASE db TO user;` | Assign DB access  | Role control     | `GRANT ALL PRIVILEGES ON DATABASE lms_db TO viraj;` |

---

## 3️⃣ Table Operations

| Command             | Explanation    | When to Use   | Example                |
| ------------------- | -------------- | ------------- | ---------------------- |
| `\dt`               | Lists tables   | DB inspection | `\dt`                  |
| `CREATE TABLE`      | Creates table  | Schema design | See below              |
| `\d table`          | Describe table | Debugging     | `\d students`          |
| `DROP TABLE table;` | Deletes table  | Cleanup       | `DROP TABLE students;` |

### Example

```sql
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(150) UNIQUE
);
```

---

## 4️⃣ CRUD Operations (Daily Usage 🔥)

| Command  | Explanation | When to Use   | Example                                                           |
| -------- | ----------- | ------------- | ----------------------------------------------------------------- |
| `INSERT` | Add data    | Create record | `INSERT INTO students(name,email) VALUES('Viraj','v@gmail.com');` |
| `SELECT` | Fetch data  | Read records  | `SELECT * FROM students;`                                         |
| `UPDATE` | Modify data | Update record | `UPDATE students SET name='Amit' WHERE id=1;`                     |
| `DELETE` | Remove data | Delete record | `DELETE FROM students WHERE id=1;`                                |

---

## 5️⃣ Filtering & Conditions

| Command    | Explanation           | When to Use         | Example                                  |
| ---------- | --------------------- | ------------------- | ---------------------------------------- |
| `WHERE`    | Filter rows           | Conditional queries | `SELECT * FROM students WHERE age > 21;` |
| `AND / OR` | Combine conditions    | Complex filters     | `WHERE age>20 AND city='Pune'`           |
| `IN`       | Match multiple values | Multi-filter        | `WHERE id IN (1,2,3)`                    |
| `LIKE`     | Pattern match         | Search              | `WHERE name LIKE 'V%'`                   |

---

## 6️⃣ Constraints (Interview Favorite ⭐)

| Constraint    | Purpose                  | Example                                          |
| ------------- | ------------------------ | ------------------------------------------------ |
| `PRIMARY KEY` | Unique row identifier    | `id SERIAL PRIMARY KEY`                          |
| `FOREIGN KEY` | Relationship enforcement | `REFERENCES department(id)`                      |
| `UNIQUE`      | Prevent duplicates       | `email UNIQUE`                                   |
| `NOT NULL`    | Mandatory value          | `name VARCHAR(100) NOT NULL`                     |
| `CHECK`       | Custom rule              | `age INT CHECK(age>=18)`                         |
| `DEFAULT`     | Default value            | `created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP` |

---

## 7️⃣ Relationships (Joins)

| Join Type    | Meaning             | Example                                                          |
| ------------ | ------------------- | ---------------------------------------------------------------- |
| `INNER JOIN` | Matching rows only  | `SELECT e.name,d.name FROM emp e JOIN dept d ON e.dept_id=d.id;` |
| `LEFT JOIN`  | All left + matches  | `LEFT JOIN`                                                      |
| `RIGHT JOIN` | All right + matches | `RIGHT JOIN`                                                     |
| `FULL JOIN`  | All rows            | Rarely used                                                      |

---

## 8️⃣ Sorting & Pagination (Spring Boot Friendly)

| Command    | Explanation   | Example             |
| ---------- | ------------- | ------------------- |
| `ORDER BY` | Sort result   | `ORDER BY age DESC` |
| `LIMIT`    | Restrict rows | `LIMIT 10`          |
| `OFFSET`   | Skip rows     | `OFFSET 20`         |

```sql
SELECT * FROM students ORDER BY id LIMIT 5 OFFSET 10;
```

---

## 9️⃣ Aggregations & Grouping

| Function   | Purpose       | Example                          |
| ---------- | ------------- | -------------------------------- |
| `COUNT()`  | Total rows    | `SELECT COUNT(*) FROM students;` |
| `SUM()`    | Total         | `SELECT SUM(salary) FROM emp;`   |
| `AVG()`    | Average       | `SELECT AVG(age) FROM students;` |
| `GROUP BY` | Group rows    | `GROUP BY department_id`         |
| `HAVING`   | Filter groups | `HAVING COUNT(*) > 2`            |

---

## 🔟 Indexes (Performance 🔥)

| Command        | Explanation     | Example                                      |
| -------------- | --------------- | -------------------------------------------- |
| `CREATE INDEX` | Improves search | `CREATE INDEX idx_email ON students(email);` |
| `\di`          | List indexes    | `\di`                                        |

---

## 1️⃣1️⃣ Transactions (Critical Concept)

| Command    | Explanation       | Example     |
| ---------- | ----------------- | ----------- |
| `BEGIN`    | Start transaction | `BEGIN;`    |
| `COMMIT`   | Save changes      | `COMMIT;`   |
| `ROLLBACK` | Undo changes      | `ROLLBACK;` |

👉 Spring equivalent: `@Transactional`

---

## 1️⃣2️⃣ Schema Commands

| Command           | Explanation   | Example                          |
| ----------------- | ------------- | -------------------------------- |
| `\dn`             | List schemas  | `\dn`                            |
| `CREATE SCHEMA`   | Create schema | `CREATE SCHEMA lms_schema;`      |
| `SET search_path` | Use schema    | `SET search_path TO lms_schema;` |

---

## 1️⃣3️⃣ psql Meta Commands (Must Remember)

| Command    | Meaning        |
| ---------- | -------------- |
| `\l`       | List databases |
| `\c`       | Connect DB     |
| `\dt`      | List tables    |
| `\d table` | Describe table |
| `\du`      | List users     |
| `\q`       | Quit           |

---

## 🎯 One-Line Interview Summary

> PostgreSQL provides rich DDL, DML, indexing, and transaction support. In Spring Boot, these commands map directly to JPA operations, pagination, joins, and transactional consistency.

---

## 🚀 Want This Next?

I can:

* 📄 Convert this into a **GitHub README.md**
* 🧠 Create **interview questions from this table**
* 🔗 Map **each SQL command → Spring Data JPA method**
* 🐳 Add **PostgreSQL + Docker cheatsheet**

Just tell me 👍

