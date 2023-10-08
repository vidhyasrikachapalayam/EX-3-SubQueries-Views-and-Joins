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
![d3(1](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/290a83fb-e73f-4afe-b005-d290d7506852)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
`SELECT ename, job, sal FROM emp WHERE sal = (SELECT MIN(sal) FROM emp);`

### OUTPUT:


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:

 select name,job from emp where  deptno=12 and job='manager';

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/b73b3be5-34d2-49a1-8f49-6954fce4005e)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
create view empv5 as select empno,name,job from emp where deptno=22;


### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/5ecfa3f9-d721-4c1a-b188-20afedf06b9b)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
create view empv30 as select empno,name,sal from emp where deptno=24;
`

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/7ef70314-9268-447b-bfc8-ec25022e41a3)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
update emp set sal=sal*1.1 where job='clerk';

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/131f9fca-ad86-4394-9c5c-815b8ca198df)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/4e4700df-464b-4829-85ea-f66e465dc6ca)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/86731a8b-570a-40da-8cca-681de0b54d4f)

## Create a Customer1 Table
```sql
create table customer1(cusid int(8),cusname char(20),city char(92),grade int(5),salesid int(27));
```
## Inserting Values to the Table
```sql
insert into customer1 (cusid,cusname,city,grade,salesid) values(100,'deepesh','chennai',5,121);

insert into customer1 (cusid,cusname,city,grade,salesid)values(102,'varsha','kanchipuram',5,122);

insert into customer1 (cusid,cusname,city,grade,salesid) values (103,'vidhya','chennai',5,122);

insert into customer1 (cusid,cusname,city,grade,salesid) values (104,'yuva','coimbatore',7,124);

insert into customer1 (cusid,cusname,city,grade,salesid) values (108,'prabha','kerala',4,125);
```
## Create a Salesperson1 table
```sql

create table salesperson (salesid int(2),city char(39),salesname char(20),commission int(5));
```
## Inserting Values to the Table
```sql
insert into salesperson(salesid,city,salesname,commission) values(1,'chennai','vijis',200);

insert into salesperson(salesid,city,salesname,commission) values(2,'puzhal','priya',400);

insert into salesperson(salesid,city,salesname,commission) values(3,'pondy','jeeva',500);

insert into salesperson(salesid,city,salesname,commission)values(4,'nungambakkam','anish',700)
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
`select salesperson.salesname AS "Salesman", customer1.cusname as "Customer Name", salesperson.city AS "City" from salesperson inner join customer1 on salesperson.city=customer1.city;

### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/bda2c8b9-36d7-4fdc-aada-4b45e3675b05)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.

### QUERY:
select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/9fab71d6-4926-45cc-a14c-f4e915737c01)

### Q9) Perform Natural join on both tables

### QUERY:
` select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/57496838-4974-40e7-8e50-8742f95b6c93)

### Q10) Perform Left and right join on both tables

### QUERY:
`-- Left Join
select * from salesperson left join customer1 on salesperson.city=customer1.city;
### OUTPUT:
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/af6f1c36-74fa-44ba-a208-7a5bfb1bb4e3)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/27e58da8-d845-402f-a850-f01e138ea285)
![image](https://github.com/Vijisdurai/EX-3-SubQueries-Views-and-Joins/assets/118343184/f3040739-6bdf-4542-9b34-9c2c63468054)
