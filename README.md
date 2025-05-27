Assignment No 1
1. Write a query to create a table employee with empno, ename, designation and salary.
2. Write a query to display the column name and data type of the table employee
3. Write a query to create a table from an existing table with all the fields.
4. Write a query to create table from an existing table with selected fields.
5. Write a query to create a new table from an existing table without any record.
6. Write a query to Alter the column empno number(4) to empno number(6).
7. Write a query to Alter the table employee with multiple columns (empno, ename).
8. Write a query to add a new column in employee table.
9. Write a query to add multiple columns in employee table.
10. Write a query to drop a column from an existing table employee.
11. Write a query to drop multiple columns from the employee table.
12. Write a query to rename table employee to emp 

Here are the Oracle-SQL queries for each of the above questions:

1. **Create table `employee`**

```sql
CREATE TABLE employee (
  empno       NUMBER(4),
  ename       VARCHAR2(100),
  designation VARCHAR2(100),
  salary      NUMBER(10,2)
);
```

2. **Display column names and data types of `employee`**

```sql
SELECT column_name,
       data_type
FROM   user_tab_columns
WHERE  table_name = 'EMPLOYEE';
```

3. **Create a new table (e.g. `emp_all`) from `employee` with all fields**

```sql
CREATE TABLE emp_all AS
SELECT *
FROM   employee;
```

4. **Create a new table (e.g. `emp_sel`) from `employee` with selected fields**

```sql
CREATE TABLE emp_sel AS
SELECT empno,
       ename,
       salary
FROM   employee;
```

5. **Create a new table (e.g. `emp_empty`) from `employee` without any records**

```sql
CREATE TABLE emp_empty AS
SELECT *
FROM   employee
WHERE  1 = 0;
```

6. **Alter column `empno` from `NUMBER(4)` to `NUMBER(6)`**

```sql
ALTER TABLE employee
  MODIFY (empno NUMBER(6));
```

7. **Alter multiple columns in one statement**
   *(e.g. change `empno` and `ename`)*

```sql
ALTER TABLE employee
  MODIFY (
    empno NUMBER(6),
    ename VARCHAR2(150)
  );
```

8. **Add a new column to `employee`**
   *(e.g. `hire_date` of type `DATE`)*

```sql
ALTER TABLE employee
  ADD (hire_date DATE);
```

9. **Add multiple new columns to `employee`**
   *(e.g. `deptno` and `manager_id`)*

```sql
ALTER TABLE employee
  ADD (
    deptno     NUMBER(2),
    manager_id NUMBER(6)
  );
```

10. **Drop a single column from `employee`**
    *(e.g. drop `designation`)*

```sql
ALTER TABLE employee
  DROP COLUMN designation;
```

11. **Drop multiple columns from `employee`**
    *(e.g. drop `designation` and `hire_date`)*

```sql
ALTER TABLE employee
  DROP (
    designation,
    hire_date
  );
```

12. **Rename table `employee` to `emp`**

```sql
ALTER TABLE employee
  RENAME TO emp;
```

1. Create a table employee with attributes emp_id, f_name, l_name, job_type, salary, dept,
commission, manager_id.
2. Make emp_id as the primary key of employee table.
3. Make f_name and salary NOT NULL type.
4. Add a column date_of_joining in the employee table.
5. Create a table department with attribute d_name, d_loc and HOD_id where d_name is
primary key.
6. Create a table location with attributes loc_id, city and contact_no.
7. Enhance the size of the ‘city’ attribute by 5, in the location table.
8. Delete the contact_no attribute from the location table.
9. Make the department attribute of the employee table its foreign key referencing the
department table.
10. Rename the city attribute to ‘address’ in the location table.
11. Rename the location table name to ‘loc’.
12. Insert the following rows in ‘loc’ table 

-- 1. Create table employee
CREATE TABLE employee (
  emp_id         NUMBER(6),
  f_name         VARCHAR2(50),
  l_name         VARCHAR2(50),
  job_type       VARCHAR2(100),
  salary         NUMBER(10,2),
  dept           VARCHAR2(30),
  commission     NUMBER(7,2),
  manager_id     NUMBER(6)
);

-- 2. Make emp_id the primary key

ALTER TABLE employee
  ADD CONSTRAINT pk_employee_empid PRIMARY KEY (emp_id);

-- 3. Make f_name and salary NOT NULL

ALTER TABLE employee
  MODIFY (
    f_name NOT NULL,
    salary NOT NULL
  );

-- 4. Add a column date_of_joining

ALTER TABLE employee
  ADD (date_of_joining DATE);

-- 5. Create table department, with d_name as primary key

CREATE TABLE department (
  d_name   VARCHAR2(30),
  d_loc    VARCHAR2(100),
  HOD_id   NUMBER(6),
  CONSTRAINT pk_department_dname PRIMARY KEY (d_name)
);

-- 6. Create table location

CREATE TABLE location (
  loc_id     NUMBER(4),
  city       VARCHAR2(50),
  contact_no VARCHAR2(15)
);

-- 7. Enhance size of city by 5 characters (from VARCHAR2(50) → VARCHAR2(55))


ALTER TABLE location
  MODIFY (city VARCHAR2(55));

-- 8. Delete the contact_no attribute
ALTER TABLE location
  DROP COLUMN contact_no;

-- 9. Make dept in employee a foreign key referencing department(d_name)

ALTER TABLE employee
  ADD CONSTRAINT fk_employee_dept
    FOREIGN KEY (dept)
    REFERENCES department(d_name);

-- 10. Rename city to address in location

ALTER TABLE location
  RENAME COLUMN city TO address;

-- 11. Rename table location to loc

ALTER TABLE location
  RENAME TO loc;

-- 12. Insert sample rows into loc (location) table

INSERT INTO loc (loc_id, address) VALUES (1, 'Mumbai');
INSERT INTO loc (loc_id, address) VALUES (2, 'Delhi');
INSERT INTO loc (loc_id, address) VALUES (3, 'Bengaluru');
INSERT INTO loc (loc_id, address) VALUES (4, 'Chennai');
INSERT INTO loc (loc_id, address) VALUES (5, 'Kolkata');

