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


```
INSERT ALL
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    1,
    'ARUN',
    'KHAN',
    'MANAGER',
    90000,
    NULL,
    'PRODUCTION',
    NULL,
    TO_DATE('04-JAN-1998','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    2,
    'BARUN',
    'KUMAR',
    'MANAGER',
    80000,
    NULL,
    'MARKETING',
    NULL,
    TO_DATE('09-FEB-1998','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    3,
    'CHITRA',
    'KAPOOR',
    'ENGINEER',
    60000,
    NULL,
    'PRODUCTION',
    1,
    TO_DATE('08-JAN-1998','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    4,
    'DHEERAJ',
    'MISHRA',
    'MANAGER',
    75000,
    NULL,
    'SALES',
    4,
    TO_DATE('27-DEC-2001','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    5,
    'EMMA',
    'DUTT',
    'ENGINEER',
    55000,
    NULL,
    'PRODUCTION',
    1,
    TO_DATE('20-MAR-2002','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    6,
    'FLOKI',
    'DUTT',
    'ACCOUNTANT',
    70000,
    NULL,
    'ACCOUNTS',
    6,
    TO_DATE('16-JUL-2000','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    7,
    'DHEERAJ',
    'KUMAR',
    'CLERK',
    40000,
    NULL,
    'ACCOUNTS',
    6,
    TO_DATE('01-JUL-2016','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    8,
    'SAUL',
    'GOOD',
    'ENGINEER',
    60000,
    NULL,
    'R&D',
    NULL,
    TO_DATE('06-SEP-2014','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    9,
    'MOU',
    'BHAT',
    'CLERK',
    30000,
    NULL,
    'SALES',
    4,
    TO_DATE('08-MAR-2015','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    10,
    'SUNNY',
    'DEOL',
    'SALESMAN',
    20000,
    10000,
    'MARKETING',
    2,
    TO_DATE('31-MAR-2001','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    11,
    'BOBBY',
    'DEOL',
    'ENGINEER',
    35000,
    NULL,
    'R&D',
    8,
    TO_DATE('17-OCT-2017','DD-MON-YYYY')
  )
  INTO EMPLOYEE (
    EMP_ID,
    F_NAME,
    L_NAME,
    JOB_TYPE,
    SALARY,
    COMMISSION,
    DEPT,
    MANAGER_ID,
    DATE_OF_JOINING
  ) VALUES (
    12,
    'AAMIR',
    'KHAN',
    'SALESMAN',
    15000,
    5000,
    'MARKETING',
    2,
    TO_DATE('11-JAN-2013','DD-MON-YYYY')
  )
SELECT * FROM DUAL;
```

17. Show the values of departmental table.
18. Select the department names and their locations.
19. Show the employees f_name , l_name , salary and the salary after 1000rs. Bonus.
20. Show the employees annual salary with a 1000rs. Yearly bonus and the annual salary
with a 100rs. Monthly bonus.
21. Show f_name as NAME and annual salary as ANNSAL from the employee table.
22. Show the l_name as LasT AND 100rs. Incremented salary as NewSal.
23. Show the emp_id, f_name, l_name, job_type of the employee getting highest salary.
24. Show the emp_id, f_name, l_name, job_type of the employee getting minimum salary.
25. Show the average salary of employees in the employee table

Here are the correct and simplest Oracle SQL queries for questions 17 to 25:

---

**17. SHOW THE VALUES OF DEPARTMENTAL TABLE.**

```sql
SELECT * FROM DEPARTMENT;
```

---

**18. SELECT THE DEPARTMENT NAMES AND THEIR LOCATIONS.**

```sql
SELECT D_NAME, D_LOC FROM DEPARTMENT;
```

---

**19. SHOW THE EMPLOYEES F\_NAME, L\_NAME, SALARY AND THE SALARY AFTER 1000RS. BONUS.**

```sql
SELECT F_NAME, L_NAME, SALARY, SALARY + 1000 AS BONUS_SALARY FROM EMPLOYEE;
```

---

**20. SHOW THE EMPLOYEES ANNUAL SALARY WITH A 1000RS. YEARLY BONUS AND THE ANNUAL SALARY WITH A 100RS. MONTHLY BONUS.**

```sql
SELECT 
  F_NAME, 
  L_NAME, 
  (SALARY * 12) + 1000 AS YEARLY_BONUS_SALARY,
  (SALARY * 12) + (100 * 12) AS MONTHLY_BONUS_SALARY 
FROM EMPLOYEE;
```

---

**21. SHOW F\_NAME AS NAME AND ANNUAL SALARY AS ANNSAL FROM THE EMPLOYEE TABLE.**

```sql
SELECT F_NAME AS NAME, SALARY * 12 AS ANNSAL FROM EMPLOYEE;
```

---

**22. SHOW THE L\_NAME AS LAST AND 100RS. INCREMENTED SALARY AS NEWSAL.**

```sql
SELECT L_NAME AS LAST, SALARY + 100 AS NEWSAL FROM EMPLOYEE;
```

---

**23. SHOW THE EMP\_ID, F\_NAME, L\_NAME, JOB\_TYPE OF THE EMPLOYEE GETTING HIGHEST SALARY.**

```sql
SELECT EMP_ID, F_NAME, L_NAME, JOB_TYPE
FROM EMPLOYEE
WHERE SALARY = (SELECT MAX(SALARY) FROM EMPLOYEE);
```

---

**24. SHOW THE EMP\_ID, F\_NAME, L\_NAME, JOB\_TYPE OF THE EMPLOYEE GETTING MINIMUM SALARY.**

```sql
SELECT EMP_ID, F_NAME, L_NAME, JOB_TYPE
FROM EMPLOYEE
WHERE SALARY = (SELECT MIN(SALARY) FROM EMPLOYEE);
```

---

**25. SHOW THE AVERAGE SALARY OF EMPLOYEES IN THE EMPLOYEE TABLE.**

```sql
SELECT AVG(SALARY) AS AVERAGE_SALARY FROM EMPLOYEE;
```

---

26. Consider the Insurance database given below. The primary keys are underlined and the data types are specified:
PERSON (driver-id: string, name: string, address: string)
CAR (Regno:string,model:string,year:int)
ACCIDENT (report-number:int,date:date,location:string)
OWNS (driver-id:string,regno:string)
PARTICIPATED (driver-id:string,regno:string,report-number:int,damage-amount:int)
i. Create the above tables by properly specifying the primary keys and the foreign keys
ii. Enter atleast five tuples for each relation
iii. Demonstrate how you a. Update the damage amount for the car with a specific regno in accident with report number 12 to 25000 b. Add a new accident to the databaseiv. Find the total number of people who owned cars that were involved in accidents in
2006.
v. Find the number of accidents in which cars belonging to a specific model were
involved. 

```sql
-- =============================================
-- i.  CREATE TABLES WITH PRIMARY & FOREIGN KEYS
-- =============================================

CREATE TABLE PERSON (
  DRIVER_ID   VARCHAR2(20),
  NAME        VARCHAR2(100),
  ADDRESS     VARCHAR2(200),
  CONSTRAINT PK_PERSON        PRIMARY KEY (DRIVER_ID)
);

CREATE TABLE CAR (
  REGNO       VARCHAR2(20),
  MODEL       VARCHAR2(50),
  YEAR        NUMBER(4),
  CONSTRAINT PK_CAR           PRIMARY KEY (REGNO)
);

CREATE TABLE ACCIDENT (
  REPORT_NUMBER  NUMBER(6),
  ACC_DATE       DATE,
  LOCATION       VARCHAR2(100),
  CONSTRAINT PK_ACCIDENT      PRIMARY KEY (REPORT_NUMBER)
);

CREATE TABLE OWNS (
  DRIVER_ID   VARCHAR2(20),
  REGNO       VARCHAR2(20),
  CONSTRAINT PK_OWNS          PRIMARY KEY (DRIVER_ID, REGNO),
  CONSTRAINT FK_OWNS_PERSON   FOREIGN KEY (DRIVER_ID) REFERENCES PERSON(DRIVER_ID),
  CONSTRAINT FK_OWNS_CAR      FOREIGN KEY (REGNO)   REFERENCES CAR(REGNO)
);

CREATE TABLE PARTICIPATED (
  DRIVER_ID      VARCHAR2(20),
  REGNO          VARCHAR2(20),
  REPORT_NUMBER  NUMBER(6),
  DAMAGE_AMOUNT  NUMBER(10,2),
  CONSTRAINT PK_PARTIC         PRIMARY KEY (DRIVER_ID, REGNO, REPORT_NUMBER),
  CONSTRAINT FK_PARTIC_PERSON  FOREIGN KEY (DRIVER_ID)      REFERENCES PERSON(DRIVER_ID),
  CONSTRAINT FK_PARTIC_CAR     FOREIGN KEY (REGNO)          REFERENCES CAR(REGNO),
  CONSTRAINT FK_PARTIC_ACC     FOREIGN KEY (REPORT_NUMBER)  REFERENCES ACCIDENT(REPORT_NUMBER)
);

-- =============================================
-- ii. INSERT AT LEAST FIVE TUPLES INTO EACH TABLE
-- =============================================

-- PERSON
INSERT ALL
  INTO PERSON (DRIVER_ID, NAME, ADDRESS) VALUES ('D001','ALICE SMITH',   '123 OAK ST')
  INTO PERSON (DRIVER_ID, NAME, ADDRESS) VALUES ('D002','BOB JONES',     '456 PINE AVE')
  INTO PERSON (DRIVER_ID, NAME, ADDRESS) VALUES ('D003','CARLA GARCIA',  '789 MAPLE RD')
  INTO PERSON (DRIVER_ID, NAME, ADDRESS) VALUES ('D004','DAVID LEE',     '321 CEDAR BLVD')
  INTO PERSON (DRIVER_ID, NAME, ADDRESS) VALUES ('D005','EMILY PATEL',   '654 SPRUCE LN')
SELECT * FROM DUAL;

-- CAR
INSERT ALL
  INTO CAR (REGNO, MODEL, YEAR) VALUES ('XYZ123','CIVIC',    2005)
  INTO CAR (REGNO, MODEL, YEAR) VALUES ('ABC999','COROLLA',  2006)
  INTO CAR (REGNO, MODEL, YEAR) VALUES ('JKL456','CAMRY',    2007)
  INTO CAR (REGNO, MODEL, YEAR) VALUES ('QWE789','ACCORD',   2006)
  INTO CAR (REGNO, MODEL, YEAR) VALUES ('RTY321','MALIBU',   2008)
SELECT * FROM DUAL;

-- ACCIDENT
INSERT ALL
  INTO ACCIDENT (REPORT_NUMBER, ACC_DATE,    LOCATION) VALUES (10, TO_DATE('15-MAR-2006','DD-MON-YYYY'),'NOIDA')
  INTO ACCIDENT (REPORT_NUMBER, ACC_DATE,    LOCATION) VALUES (11, TO_DATE('20-JUL-2006','DD-MON-YYYY'),'DELHI')
  INTO ACCIDENT (REPORT_NUMBER, ACC_DATE,    LOCATION) VALUES (12, TO_DATE('05-SEP-2007','DD-MON-YYYY'),'MUMBAI')
  INTO ACCIDENT (REPORT_NUMBER, ACC_DATE,    LOCATION) VALUES (13, TO_DATE('12-DEC-2006','DD-MON-YYYY'),'BENGALURU')
  INTO ACCIDENT (REPORT_NUMBER, ACC_DATE,    LOCATION) VALUES (14, TO_DATE('01-JAN-2008','DD-MON-YYYY'),'CHENNAI')
SELECT * FROM DUAL;

-- OWNS
INSERT ALL
  INTO OWNS (DRIVER_ID, REGNO) VALUES ('D001','XYZ123')
  INTO OWNS (DRIVER_ID, REGNO) VALUES ('D002','ABC999')
  INTO OWNS (DRIVER_ID, REGNO) VALUES ('D003','JKL456')
  INTO OWNS (DRIVER_ID, REGNO) VALUES ('D004','QWE789')
  INTO OWNS (DRIVER_ID, REGNO) VALUES ('D005','RTY321')
SELECT * FROM DUAL;

-- PARTICIPATED
INSERT ALL
  INTO PARTICIPATED (DRIVER_ID, REGNO, REPORT_NUMBER, DAMAGE_AMOUNT) VALUES ('D001','XYZ123',10, 5000)
  INTO PARTICIPATED (DRIVER_ID, REGNO, REPORT_NUMBER, DAMAGE_AMOUNT) VALUES ('D002','ABC999',11, 7500)
  INTO PARTICIPATED (DRIVER_ID, REGNO, REPORT_NUMBER, DAMAGE_AMOUNT) VALUES ('D003','JKL456',12,12000)
  INTO PARTICIPATED (DRIVER_ID, REGNO, REPORT_NUMBER, DAMAGE_AMOUNT) VALUES ('D004','QWE789',13, 3000)
  INTO PARTICIPATED (DRIVER_ID, REGNO, REPORT_NUMBER, DAMAGE_AMOUNT) VALUES ('D005','RTY321',14, 9500)
SELECT * FROM DUAL;

-- =============================================
-- iii.a UPDATE DAMAGE_AMOUNT FOR REGNO 'JKL456' & REPORT_NUMBER 12
-- =============================================

UPDATE PARTICIPATED
   SET DAMAGE_AMOUNT = 25000
 WHERE REGNO         = 'JKL456'
   AND REPORT_NUMBER = 12;

-- =============================================
-- iii.b ADD A NEW ACCIDENT (REPORT_NUMBER 15)
-- =============================================

INSERT INTO ACCIDENT (REPORT_NUMBER, ACC_DATE, LOCATION)
VALUES (15, TO_DATE('22-FEB-2009','DD-MON-YYYY'), 'HYDERABAD');

-- =============================================
-- iv.  TOTAL NUMBER OF PEOPLE WHO OWNED CARS INVOLVED IN ACCIDENTS IN 2006
-- =============================================

SELECT COUNT(DISTINCT o.DRIVER_ID) AS TOTAL_OWNERS_2006
FROM   OWNS o
  JOIN PARTICIPATED p
    ON o.DRIVER_ID = p.DRIVER_ID
   AND o.REGNO     = p.REGNO
  JOIN ACCIDENT a
    ON p.REPORT_NUMBER = a.REPORT_NUMBER
WHERE  EXTRACT(YEAR FROM a.ACC_DATE) = 2006;

-- =============================================
-- v.   NUMBER OF ACCIDENTS INVOLVING CARS OF A SPECIFIC MODEL (e.g. 'CIVIC')
-- =============================================

SELECT COUNT(DISTINCT p.REPORT_NUMBER) AS ACCIDENT_COUNT_FOR_MODEL
FROM   PARTICIPATED p
  JOIN CAR c
    ON p.REGNO = c.REGNO
WHERE  c.MODEL = 'CIVIC';
```

4. Show the different department names from department table
5. Show the employee names who works in ‘Sales’
6. Show the employee names who gets salary of more than 50000 per month
7. Show the details of the employee whose manager id is not 1
8. Show the employee details whose salary ranges between 40000 and 70000
9. Show the details of the employees who works under the manager having id 1, 6 and 8
10. Select the f_name and salary of those employees whose last name starts with ‘K’
11. Select the f_name and salary of those employees whose last name starts with ‘K’ and
ends with ‘R’
12. Show the details of those employees where 3rd letter of l_name is ‘o’
13. Select the details of those employees who works as an engineer with monthly salary
more than 50000 
```
-- 4. SHOW THE DIFFERENT DEPARTMENT NAMES FROM DEPARTMENT TABLE
SELECT DISTINCT D_NAME
FROM DEPARTMENT;

-- 5. SHOW THE EMPLOYEE NAMES WHO WORKS IN ‘SALES’
SELECT F_NAME || ' ' || L_NAME AS EMPLOYEE_NAME
FROM EMPLOYEE
WHERE DEPT = 'SALES';

-- 6. SHOW THE EMPLOYEE NAMES WHO GETS SALARY OF MORE THAN 50000 PER MONTH
SELECT F_NAME || ' ' || L_NAME AS EMPLOYEE_NAME, SALARY
FROM EMPLOYEE
WHERE SALARY > 50000;

-- 7. SHOW THE DETAILS OF THE EMPLOYEE WHOSE MANAGER ID IS NOT 1
SELECT *
FROM EMPLOYEE
WHERE MANAGER_ID != 1;

-- 8. SHOW THE EMPLOYEE DETAILS WHOSE SALARY RANGES BETWEEN 40000 AND 70000
SELECT *
FROM EMPLOYEE
WHERE SALARY BETWEEN 40000 AND 70000;

-- 9. SHOW THE DETAILS OF THE EMPLOYEES WHO WORKS UNDER THE MANAGER HAVING ID 1, 6 AND 8
SELECT *
FROM EMPLOYEE
WHERE MANAGER_ID IN (1, 6, 8);

-- 10. SELECT THE F_NAME AND SALARY OF THOSE EMPLOYEES WHOSE LAST NAME STARTS WITH ‘K’
SELECT F_NAME, SALARY
FROM EMPLOYEE
WHERE L_NAME LIKE 'K%';

-- 11. SELECT THE F_NAME AND SALARY OF THOSE EMPLOYEES WHOSE LAST NAME STARTS WITH ‘K’ AND ENDS WITH ‘R’
SELECT F_NAME, SALARY
FROM EMPLOYEE
WHERE L_NAME LIKE 'K%R';

-- 12. SHOW THE DETAILS OF THOSE EMPLOYEES WHERE 3RD LETTER OF L_NAME IS ‘O’
SELECT *
FROM EMPLOYEE
WHERE SUBSTR(L_NAME, 3, 1) = 'O';

-- 13. SELECT THE DETAILS OF THOSE EMPLOYEES WHO WORKS AS AN ENGINEER WITH MONTHLY SALARY MORE THAN 50000
SELECT *
FROM EMPLOYEE
WHERE JOB_TYPE = 'ENGINEER'
  AND SALARY > 50000;
```


14. Select the employees whose department is ‘Production’ or monthly salary is more than
60000 per month.
15. Find the minimum salary, maximum salary, total salary, average salary of the
employees who work in ‘Sales’ department
16. Find the employee l_name that is first and f_name that is last if they are arranged in an
order
17. Find the number of employees working in each department
18. Find the number of departments from employee table
19. Find the average commission of the employees.
20. Find the average salaries of the employees department wise
21. Find the sum of salary of different job_type according to different departments
22. Find the department name and average salaries of those departments whose average
salary is greater than 40000
23. Find the department name and maximum salaries of those departments whose
maximum salary is greater than 55000
24. Display the job_type and total monthly salary for each job_type where total payroll is
exceeding 100000
25. Display the name of the department having maximum average salary

14. **SELECT EMPLOYEES WHOSE DEPARTMENT IS ‘PRODUCTION’ OR MONTHLY SALARY IS MORE THAN 60000**

```sql
SELECT *
FROM EMPLOYEE
WHERE DEPT = 'PRODUCTION'
   OR SALARY > 60000;
```

15. **MINIMUM, MAXIMUM, TOTAL & AVERAGE SALARY OF EMPLOYEES IN ‘SALES’**

```sql
SELECT 
  MIN(SALARY)   AS MIN_SALARY,
  MAX(SALARY)   AS MAX_SALARY,
  SUM(SALARY)   AS TOTAL_SALARY,
  AVG(SALARY)   AS AVG_SALARY
FROM EMPLOYEE
WHERE DEPT = 'SALES';
```

16. **FIRST LAST-NAME AND LAST FIRST-NAME IN ORDER**
    *(lexicographically first L\_NAME, lexicographically last F\_NAME)*

```sql
SELECT 
  MIN(L_NAME) AS FIRST_LNAME,
  MAX(F_NAME) AS LAST_FNAME
FROM EMPLOYEE;
```

17. **NUMBER OF EMPLOYEES WORKING IN EACH DEPARTMENT**

```sql
SELECT 
  DEPT,
  COUNT(*) AS EMP_COUNT
FROM EMPLOYEE
GROUP BY DEPT;
```

18. **NUMBER OF DISTINCT DEPARTMENTS IN EMPLOYEE TABLE**

```sql
SELECT 
  COUNT(DISTINCT DEPT) AS DEPT_COUNT
FROM EMPLOYEE;
```

19. **AVERAGE COMMISSION OF ALL EMPLOYEES**

```sql
SELECT 
  AVG(COMMISSION) AS AVG_COMMISSION
FROM EMPLOYEE;
```

20. **AVERAGE SALARY DEPARTMENT-WISE**

```sql
SELECT 
  DEPT,
  AVG(SALARY) AS AVG_SALARY
FROM EMPLOYEE
GROUP BY DEPT;
```

21. **SUM OF SALARY BY JOB\_TYPE WITHIN EACH DEPARTMENT**

```sql
SELECT 
  DEPT,
  JOB_TYPE,
  SUM(SALARY) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPT, JOB_TYPE;
```

22. **DEPT AND AVG SALARY FOR THOSE DEPTS WITH AVG\_SALARY > 40000**

```sql
SELECT 
  DEPT,
  AVG(SALARY) AS AVG_SALARY
FROM EMPLOYEE
GROUP BY DEPT
HAVING AVG(SALARY) > 40000;
```

23. **DEPT AND MAX SALARY FOR THOSE DEPTS WITH MAX\_SALARY > 55000**

```sql
SELECT 
  DEPT,
  MAX(SALARY) AS MAX_SALARY
FROM EMPLOYEE
GROUP BY DEPT
HAVING MAX(SALARY) > 55000;
```

24. **JOB\_TYPE AND TOTAL PAYROLL WHERE TOTAL PAYROLL > 100000**

```sql
SELECT 
  JOB_TYPE,
  SUM(SALARY) AS TOTAL_PAYROLL
FROM EMPLOYEE
GROUP BY JOB_TYPE
HAVING SUM(SALARY) > 100000;
```

25. **DEPARTMENT WITH THE MAXIMUM AVERAGE SALARY**

```sql
SELECT DEPT
FROM   EMPLOYEE
GROUP BY DEPT
HAVING AVG(SALARY) = (
  SELECT MAX(avg_sal)
  FROM (
    SELECT AVG(SALARY) AS avg_sal
    FROM   EMPLOYEE
    GROUP BY DEPT
  )
);
```



