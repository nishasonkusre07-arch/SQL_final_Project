# 🎓🏫📚 University Database Management System 💻✨

## 📌✨🌈 Project Overview

The **University Database Management System** 🎓 is a MySQL project designed to manage and analyse university information. It contains student, course, instructor, enrollment, and department records.

This project demonstrates database creation 🗄️, table creation 📋, CRUD operations ✍️, filtering 🔎, joins 🔗, aggregate functions 📊, subqueries 🧠, date functions 📅, window functions 🪟, and conditional logic using SQL 💻.

## 🎯🚀💡 Project Objectives

- Create and manage a university database.
- Store student, course, instructor, enrollment, and department details.
- Perform INSERT, SELECT, UPDATE, and DELETE operations.
- Retrieve information using JOINs and subqueries.
- Analyse records using aggregate functions.
- Apply date, string, and window functions.
- Categorize students using the `CASE` statement.

## 🛠️💻⚙️ Technologies Used

- 🗄️ **Database:** MySQL
- 💻 **Query Language:** SQL
- 🧰 **Tools:** MySQL Workbench / VS Code with a MySQL extension
- 📊 **Project Type:** Database Management and SQL Practice

## 🗃️📂🧩 Database Information

**Database name:** `university_db`

The database contains five main tables 📚🗂️:

### 1. 👩‍🎓🧑‍🎓 Students

| Column | Data type | Description |
|---|---|---|
| `StudentID` | INT (Primary Key) | Unique student ID |
| `FirstName` | VARCHAR(50) | Student's first name |
| `LastName` | VARCHAR(50) | Student's last name |
| `Email` | VARCHAR(100) | Student's email address |
| `BirthDate` | DATE | Student's date of birth |
| `EnrollmentDate` | DATE | Date the student enrolled |

### 2. 📚📝 Courses

| Column | Data type | Description |
|---|---|---|
| `CourseID` | INT (Primary Key) | Unique course ID |
| `CourseName` | VARCHAR(100) | Name of the course |
| `DepartmentID` | INT | Department offering the course |
| `Credits` | INT | Course credit value |

### 3. 🧑‍🏫👨‍🏫 Instructors

| Column | Data type | Description |
|---|---|---|
| `InstructorID` | INT (Primary Key) | Unique instructor ID |
| `FirstName` | VARCHAR(50) | Instructor's first name |
| `LastName` | VARCHAR(50) | Instructor's last name |
| `Email` | VARCHAR(100) | Instructor's email address |
| `DepartmentID` | INT | Instructor's department ID |
| `Salary` | DECIMAL(10,2) | Instructor salary; added later using `ALTER TABLE` |

### 4. 📝📖 Enrollments

| Column | Data type | Description |
|---|---|---|
| `EnrollmentID` | INT (Primary Key) | Unique enrollment ID |
| `StudentID` | INT | Student ID |
| `CourseID` | INT | Course ID |
| `EnrollmentDate` | DATE | Enrollment date |

### 5. 🏢🏛️ Departments

| Column | Data type | Description |
|---|---|---|
| `DepartmentID` | INT (Primary Key) | Unique department ID |
| `DepartmentName` | VARCHAR(100) | Department name |

## 🔗🧩📌 Database Relationships

- 👩‍🎓 A student can have multiple enrollment records.
- 📚 A course can have multiple enrollment records.
- 🔗 The `Enrollments` table connects `Students` and `Courses`.
- 🏢 Courses and instructors are associated with departments through `DepartmentID` in the project queries.

> **Note:** The supplied SQL defines primary keys, but it does not declare foreign-key constraints on `Enrollments.StudentID`, `Enrollments.CourseID`, or the department columns.

## 📋📊🧠 Project Tasks and SQL Concepts

| Section | SQL concept | Purpose |
|---|---|---|
| Database setup | `DROP DATABASE`, `CREATE DATABASE`, `USE` | Creates and selects the university database |
| Table creation | `CREATE TABLE` | Creates five tables |
| Sample data | `INSERT INTO` | Adds sample records |
| View records | `SELECT *` | Displays all table records |
| CRUD | `INSERT`, `SELECT`, `UPDATE`, `DELETE` | Performs basic data operations on all tables |
| Student filtering | `WHERE` | Finds students enrolled after 2022 |
| Course filtering | `JOIN`, `WHERE`, `LIMIT` | Finds Mathematics courses, limited to five |
| Group analysis | `GROUP BY`, `HAVING`, `COUNT()` | Counts students per course when the count is above five |
| Both courses | `IN`, `GROUP BY`, `HAVING` | Finds students enrolled in both SQL and Data Structures |
| Either course | `IN`, `DISTINCT` | Finds students enrolled in SQL or Data Structures |
| Average credits | `AVG()` | Calculates average course credits |
| Maximum salary | `ALTER TABLE`, `UPDATE`, `MAX()`, `JOIN` | Adds salary data and finds the maximum Computer Science instructor salary |
| Department analysis | `COUNT()`, `DISTINCT`, `GROUP BY` | Counts students in each department |
| Student-course details | `INNER JOIN` | Displays students with their enrolled courses |
| All students | `LEFT JOIN` | Displays all students, including those without an enrollment |
| Subquery | Nested query, `HAVING` | Finds students enrolled in courses with more than ten students |
| Date analysis | `YEAR()` | Extracts the enrollment year |
| Name formatting | `CONCAT()` | Combines instructor first and last names |
| Window function | `SUM() OVER()` | Calculates a running total of course enrollment counts |
| Conditional logic | `CASE`, `TIMESTAMPDIFF()` | Labels students as Senior or Junior |

## ▶️⚙️🖥️ How to Run the Project

1. Install and open MySQL Workbench or another MySQL-compatible SQL editor.
2. Connect to your MySQL server.
3. Open the SQL project file.
4. Run the database setup statements:
   ```sql
   DROP DATABASE IF EXISTS university_db;
   CREATE DATABASE university_db;
   USE university_db;
   ```
5. Create the five tables and insert their sample records.
6. Run the remaining queries in order.
7. View the output after executing each query.

> ⚠️ **Important:** `DROP DATABASE IF EXISTS university_db;` deletes the existing `university_db` database and all its tables before recreating it. Back up any data you need before running this statement.

## ⚠️🛠️🔍 Important SQL Corrections Before Running

The pasted script contains a few issues that should be corrected for a successful run:

1. **Instructor INSERT:** The `Instructors` table initially has five columns, but the CRUD example inserts six values:
   ```sql
   INSERT INTO Instructors
   VALUES (11, 'Harsh', 'Shah', 'harsh@gmail.com', 1, 70000);
   ```
   Either insert only the five existing columns, or add the `Salary` column before this INSERT and provide an explicit column list.

2. **Department UPDATE:** The statement is missing a `WHERE` clause and a semicolon. To update only department 11, use:
   ```sql
   UPDATE Departments
   SET DepartmentName = 'Artificial Intelligence and ML'
   WHERE DepartmentID = 11;
   ```

3. **Course count condition:** The sample data has only one enrollment per course, so the query using `HAVING COUNT(e.StudentID) > 5` will return no rows with the supplied records.

4. **Both SQL and Data Structures:** The supplied enrollment data does not show any student enrolled in both courses, so that query will return no rows.

5. **More than ten students:** The supplied data has only ten enrollment records, so the subquery for courses with more than ten students will return no rows.

6. **Foreign keys:** The script currently does not define foreign-key constraints for the student/course enrollment links. Add them if you want MySQL to enforce those relationships.

## 💡📚🏆 Key SQL Skills Practised

- 🗄️ Database and table creation
- 🔑 Primary keys and relational database concepts
- ✍️ CRUD operations
- 🔎 Filtering and sorting
- 🔗 INNER JOIN and LEFT JOIN
- 🧠 Subqueries
- 📊 Aggregate functions: `COUNT()`, `AVG()`, `MAX()`
- 🗂️ `GROUP BY` and `HAVING`
- 📅 Date functions: `YEAR()` and `TIMESTAMPDIFF()`
- 🔤 String function: `CONCAT()`
- 🪟 Window functions: `SUM() OVER()`
- ⚖️ Conditional statements using `CASE`
- 🛠️ Table modification using `ALTER TABLE`

## 🌟🎓🚀 Learning Outcomes

By completing this project, you practise how to 🚀:

- 🗂️ Organize university information into separate database tables.
- ✍️ Perform basic data management operations.
- 🔗 Retrieve related information from multiple tables.
- 📊 Summarize and analyse records using aggregate functions.
- 🧠 Use subqueries and window functions for data analysis.
- ⚖️ Apply conditional logic to classify student records.

## connect with me:

  Linkedin : www.linkedin.com/in/nisha-sonkusre-283526415
  g-mail : nishasonkusre07@gmail.com

---

🎉💙🚀 *Created with passion for SQL learning and practice — University Database Management System.*

🌐 **Explore • Learn • Practise • Improve** 📚💻
