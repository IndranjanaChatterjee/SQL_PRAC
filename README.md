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
