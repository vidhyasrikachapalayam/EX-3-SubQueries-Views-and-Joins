# EX 3 SubQueries, Views and Joins 


## Create employee Table
```sql
create table emp (empno int(10) primary key,name char(30),job char(30),sal int(10),deptno int(8));
```
## Insert the values
```sql
insert into emp(empno,name,job,sal,deptno) valuse(1201,'ashok','manager',1350,21);

insert into emp(empno,name,job,sal,deptno) valuse(1202,'seetha','clerk',1351,22);

insert into emp(empno,name,job,sal,deptno) valuse(1203,'priya','manager',1352,23);

insert into emp(empno,name,job,sal,deptno) valuse(1204,'varsha','clerk',1353,23);

insert into emp(empno,name,job,sal,deptno) valuse(1205,'jeeva','salesman',135422);

insert into emp(empno,name,job,sal,deptno) valuse(1206,'prabha','accountant',1350,24);


```

## Create department table
```sql
create table dept(deptno int(5) primary key,deptname char(30),loc char(40));
```
## Insert the values in the department table
```sql
insert into dept (deptno,deptname,loc) values (1,'research','mumbai');

insert into dept (deptno,deptname,loc) values (2,'manufacture','chennai');

insert into dept (deptno,deptname,loc) values (3,'accounting','hyderabad');

insert into dept (deptno,deptname,loc) values (4,'marketing','delhi');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
`create view minimum as select name,job,sal from emp where sal =(select min(sal) from emp);`

### OUTPUT:


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
`SELECT ename, job, sal FROM emp WHERE sal = (SELECT MIN(sal) FROM emp);`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/a1905da6-3702-4cea-9399-e734c1177c31)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
`SELECT e.ename, e.job FROM emp e, dept d WHERE e.deptno = 10 AND e.job IN (SELECT job FROM emp WHERE deptno = (SELECT deptno FROM dept WHERE dname = 'SALES'));`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/b73b3be5-34d2-49a1-8f49-6954fce4005e)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
`CREATE VIEW empv5 AS SELECT empno, ename, job FROM emp WHERE deptno = 10;`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/5ecfa3f9-d721-4c1a-b188-20afedf06b9b)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
`CREATE VIEW empv30 AS SELECT empno, ename, sal FROM emp WHERE deptno = 30;
SELECT * FROM empv30;
`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/7ef70314-9268-447b-bfc8-ec25022e41a3)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
`UPDATE emp SET sal = sal * 1.10 WHERE empno IN (SELECT empno FROM empv5 WHERE job = 'CLERK');
SELECT * FROM emp;`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/131f9fca-ad86-4394-9c5c-815b8ca198df)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/4e4700df-464b-4829-85ea-f66e465dc6ca)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/86731a8b-570a-40da-8cca-681de0b54d4f)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
`SELECT S.name AS Salesman, C.cust_name, C.city FROM Salesman1 S ,Customer1 C where S.city = C.city;`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/bda2c8b9-36d7-4fdc-aada-4b45e3675b05)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.

### QUERY:
`SELECT c.cust_name AS CustomerName, c.city AS CustomerCity, s.name AS Salesman, s.commission FROM Salesman1 s JOIN Customer1 c ON s.salesman_id = c.salesman_id WHERE s.commission > 0.13;`
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/9fab71d6-4926-45cc-a14c-f4e915737c01)

### Q9) Perform Natural join on both tables

### QUERY:
`SELECT * FROM Salesman1 NATURAL JOIN Customer1;`
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/57496838-4974-40e7-8e50-8742f95b6c93)

### Q10) Perform Left and right join on both tables

### QUERY:
`-- Left Join
SELECT * FROM Customer1 LEFT JOIN Salesman1 ON Customer1.salesman_id = Salesman1.salesman_id;`
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/af6f1c36-74fa-44ba-a208-7a5bfb1bb4e3)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/27e58da8-d845-402f-a850-f01e138ea285)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/f3040739-6bdf-4542-9b34-9c2c63468054)
