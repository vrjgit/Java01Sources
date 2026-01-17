# MySQl Cheatsheet 
Great 👍
Here’s a **MySQL Commands Cheat Sheet**, **structured exactly like the PostgreSQL one**, but adapted to **MySQL syntax, tools, and real-world Spring Boot usage**.

This is **consolidated, interview-ready, and practical**.

---

# 🐬 MySQL Comprehensive Cheat Sheet (Consolidated Table)

---

## 1️⃣ Database Management

| Command               | Explanation         | When to Use         | Example                   |
| --------------------- | ------------------- | ------------------- | ------------------------- |
| `SHOW DATABASES;`     | Lists all databases | Verify DB existence | `SHOW DATABASES;`         |
| `CREATE DATABASE db;` | Creates a database  | Project setup       | `CREATE DATABASE lms_db;` |
| `USE db;`             | Select database     | Before queries      | `USE lms_db;`             |
| `DROP DATABASE db;`   | Deletes database    | Cleanup             | `DROP DATABASE test_db;`  |

---

## 2️⃣ User & Privileges Management (Enterprise 🔥)

| Command                        | Explanation       | When to Use      | Example                                                |
| ------------------------------ | ----------------- | ---------------- | ------------------------------------------------------ |
| `SELECT user FROM mysql.user;` | Lists users       | Security review  | `SELECT user FROM mysql.user;`                         |
| `CREATE USER`                  | Create DB user    | Production setup | `CREATE USER 'viraj'@'localhost' IDENTIFIED BY '123';` |
| `GRANT`                        | Assign privileges | Access control   | `GRANT ALL ON lms_db.* TO 'viraj'@'localhost';`        |
| `FLUSH PRIVILEGES;`            | Apply changes     | After GRANT      | `FLUSH PRIVILEGES;`                                    |

---

## 3️⃣ Table Operations

| Command             | Explanation     | When to Use   | Example                |
| ------------------- | --------------- | ------------- | ---------------------- |
| `SHOW TABLES;`      | Lists tables    | Inspect DB    | `SHOW TABLES;`         |
| `CREATE TABLE`      | Create table    | Schema design | See below              |
| `DESCRIBE table;`   | Table structure | Debugging     | `DESCRIBE students;`   |
| `DROP TABLE table;` | Delete table    | Cleanup       | `DROP TABLE students;` |

### Example

```sql
CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(150) UNIQUE
);
```

---

## 4️⃣ CRUD Operations (Daily Usage 🔥)

| Command  | Explanation | When to Use   | Example                                                           |
| -------- | ----------- | ------------- | ----------------------------------------------------------------- |
| `INSERT` | Add row     | Create record | `INSERT INTO students(name,email) VALUES('Viraj','v@gmail.com');` |
| `SELECT` | Fetch data  | Read records  | `SELECT * FROM students;`                                         |
| `UPDATE` | Modify row  | Update record | `UPDATE students SET name='Amit' WHERE id=1;`                     |
| `DELETE` | Remove row  | Delete record | `DELETE FROM students WHERE id=1;`                                |

---

## 5️⃣ Filtering & Conditions

| Command    | Explanation        | When to Use         | Example                                  |
| ---------- | ------------------ | ------------------- | ---------------------------------------- |
| `WHERE`    | Filter rows        | Conditional queries | `SELECT * FROM students WHERE age > 21;` |
| `AND / OR` | Combine conditions | Complex filters     | `WHERE age>20 AND city='Pune'`           |
| `IN`       | Match values       | Multi-select        | `WHERE id IN (1,2,3)`                    |
| `LIKE`     | Pattern search     | Text search         | `WHERE name LIKE 'V%'`                   |
| `BETWEEN`  | Range filter       | Date/number range   | `WHERE age BETWEEN 18 AND 30`            |

---

## 6️⃣ Constraints (Very Important ⭐)

| Constraint    | Purpose               | Example                                          |
| ------------- | --------------------- | ------------------------------------------------ |
| `PRIMARY KEY` | Unique identifier     | `id INT PRIMARY KEY`                             |
| `FOREIGN KEY` | Relationship          | `REFERENCES department(id)`                      |
| `UNIQUE`      | Prevent duplicates    | `email UNIQUE`                                   |
| `NOT NULL`    | Mandatory value       | `name VARCHAR(100) NOT NULL`                     |
| `CHECK`       | Validation (MySQL 8+) | `CHECK (age >= 18)`                              |
| `DEFAULT`     | Default value         | `created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP` |

---

## 7️⃣ Relationships & Joins

| Join Type    | Meaning             | Example                                                          |
| ------------ | ------------------- | ---------------------------------------------------------------- |
| `INNER JOIN` | Matching rows       | `SELECT e.name,d.name FROM emp e JOIN dept d ON e.dept_id=d.id;` |
| `LEFT JOIN`  | All left + matches  | `LEFT JOIN dept d ON ...`                                        |
| `RIGHT JOIN` | All right + matches | `RIGHT JOIN dept d ON ...`                                       |
| `CROSS JOIN` | Cartesian product   | Rarely used                                                      |

---

## 8️⃣ Sorting & Pagination (Spring Boot Friendly)

| Command    | Explanation  | Example             |
| ---------- | ------------ | ------------------- |
| `ORDER BY` | Sort results | `ORDER BY age DESC` |
| `LIMIT`    | Limit rows   | `LIMIT 10`          |
| `OFFSET`   | Skip rows    | `OFFSET 20`         |

```sql
SELECT * FROM students ORDER BY id LIMIT 5 OFFSET 10;
```

---

## 9️⃣ Aggregate Functions & Grouping

| Function   | Purpose       | Example                          |
| ---------- | ------------- | -------------------------------- |
| `COUNT()`  | Count rows    | `SELECT COUNT(*) FROM students;` |
| `SUM()`    | Total         | `SELECT SUM(salary) FROM emp;`   |
| `AVG()`    | Average       | `SELECT AVG(age) FROM students;` |
| `GROUP BY` | Group rows    | `GROUP BY department_id`         |
| `HAVING`   | Filter groups | `HAVING COUNT(*) > 2`            |

---

## 🔟 Indexes (Performance 🔥)

| Command        | Explanation    | Example                                      |
| -------------- | -------------- | -------------------------------------------- |
| `CREATE INDEX` | Improve lookup | `CREATE INDEX idx_email ON students(email);` |
| `SHOW INDEX`   | View indexes   | `SHOW INDEX FROM students;`                  |
| `DROP INDEX`   | Remove index   | `DROP INDEX idx_email ON students;`          |

---

## 1️⃣1️⃣ Transactions (ACID 🔥)

| Command              | Explanation       | Example              |
| -------------------- | ----------------- | -------------------- |
| `START TRANSACTION;` | Begin transaction | `START TRANSACTION;` |
| `COMMIT;`            | Save changes      | `COMMIT;`            |
| `ROLLBACK;`          | Undo changes      | `ROLLBACK;`          |

👉 Spring Boot equivalent: `@Transactional`

---

## 1️⃣2️⃣ Engine & Charset (Production-Level)

| Command         | Explanation     | Example                   |
| --------------- | --------------- | ------------------------- |
| `SHOW ENGINES;` | List engines    | `SHOW ENGINES;`           |
| `ENGINE=InnoDB` | Supports FK, TX | `ENGINE=InnoDB`           |
| `CHARSET`       | Encoding        | `DEFAULT CHARSET=utf8mb4` |

```sql
CREATE TABLE courses (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(100)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

---

## 1️⃣3️⃣ MySQL Utility Commands

| Command           | Meaning         |
| ----------------- | --------------- |
| `SHOW DATABASES;` | List DBs        |
| `USE db;`         | Select DB       |
| `SHOW TABLES;`    | List tables     |
| `DESCRIBE table;` | Table structure |
| `EXIT;`           | Quit MySQL      |

---

## 🎯 Interview One-Line Summary

> MySQL supports transactional DDL/DML using InnoDB, indexing for performance, and SQL features like joins, grouping, and pagination, which directly map to Spring Data JPA operations.

---

## 🚀 What I Can Do Next (Useful for You)

* 🔗 **Side-by-side MySQL vs PostgreSQL table**
* 🧠 **Map MySQL SQL → Spring Data JPA methods**
* 📄 **Convert this into a GitHub README.md**
* 🐳 **MySQL + Docker + Spring Boot setup cheat sheet**

Just tell me 👍
