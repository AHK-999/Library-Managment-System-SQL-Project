# Library Management System SQL Project

# Project Overiew
**Database:** LMS

This project demonstrates the implementation of a Library Management System using SQL. It includes creating and managing tables, performing CRUD operations, and executing advanced SQL queries. The goal is to showcase skills in database design, manipulation, and querying.

# Objectives
1) Set up the Library Management System Database: Create and populate the database with tables for branches, employees, members, books, issued status, and return status.
2) CRUD Operations: Perform Create, Read, Update, and Delete operations on the data.
3) CTAS (Create Table As Select): Utilize CTAS to create new tables based on query results.
4) Advanced SQL Queries: Develop complex queries to analyze and retrieve specific data.

# Project Structure

**1) Database Setup**
<img width="1307" height="824" alt="image" src="https://github.com/user-attachments/assets/201ee1de-a4ed-46c9-a13b-0f7d242cae3d" />

**Database Creation:** Created a database named LMS.
**Table Creation:** Created tables for branches, employees, members, books, issued status, and return status. Each table includes relevant columns and relationships.

```sql
CREATE DATABASE LMS;
```

```sql
--Branch Table
DROP TABLE IF EXISTS branch;
CREATE TABLE branch(
	branch_id VARCHAR(10) PRIMARY KEY,
	manager_id VARCHAR(10),
	branch_address VARCHAR(100),
	contact_no VARCHAR(20)
);
```

```sql
--Employees table
DROP TABLE IF EXISTS employees;
CREATE TABLE employees(
	emp_id VARCHAR(10) PRIMARY KEY,
	emp_name VARCHAR(50),
	position VARCHAR(50),
	salary NUMERIC(10,2),
	branch_id VARCHAR(10) --FK
);
```

```sql
--Members Table
DROP TABLE IF EXISTS members;
CREATE TABLE members(
	member_id VARCHAR(10) PRIMARY KEY,
	member_name VARCHAR(50),
	member_address VARCHAR(100),
	reg_date DATE
);
```

```sql
--Books table
DROP TABLE IF EXISTS books;
CREATE TABLE books(
	isbn VARCHAR(50) PRIMARY KEY,
	book_title VARCHAR(50),
	category VARCHAR(50),
	rental_price NUMERIC(10,2),
	status VARCHAR(10),
	author VARCHAR(50),
	publisher VARCHAR(50)
);
```

```sql
--Issued status table
DROP TABLE IF EXISTS issued_status;
CREATE TABLE issued_status(
	hoi VARCHAR(10) PRIMARY KEY,
	issued_member_id VARCHAR(10), --FK
	issued_book_name VARCHAR(50),
	issued_date DATE,
	issued_book_isbn VARCHAR(50), --FK
	issued_emp_id VARCHAR(10) --FK
);
```

```sql
--Returned table
DROP TABLE IF EXISTS return_status;
CREATE TABLE return_status(
	return_id VARCHAR(50) PRIMARY KEY,
	issued_id VARCHAR(50), --FK
	return_book_name VARCHAR(25),
	return_date DATE,
	return_book_isbn VARCHAR(50) --Foriegn Key
);
```

