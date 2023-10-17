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
![image](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/043c5dd4-f3f2-4176-942e-f47186183a6f)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:

 select name,job from emp where  deptno=12 and job='manager';

### OUTPUT:
![d3(3)](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/17399b2e-840a-498d-97e8-393bc692b628)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
create view empv5 as select empno,name,job from emp where deptno=22;


### OUTPUT:
![d3(4)](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/01d318c1-b34d-4371-9643-6de2f179c3e4)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
create view empv30 as select empno,name,sal from emp where deptno=24;
`

### OUTPUT:
![d3(5](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/6ab5f93b-765d-4b0f-9036-07933d620c82)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
update emp set sal=sal*1.1 where job='clerk';

### OUTPUT:
![d3(6](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/829b5d96-bccb-4dd4-8003-6b35c30cb6d7)

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
![d3(7](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/8f35c15f-75d8-48d6-8b22-f2641c9ddbc7)


### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.

### QUERY:
select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
### OUTPUT:
![d3(8](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/d17b3d0e-fe4b-4c3f-ab78-a51535260c8b)


### Q9) Perform Natural join on both tables

### QUERY:
` select customer1.cusname as "Customer Name",customer1.city as "Customer City",salesperson.salesname AS "Salesman",salesperson.commission as "Commission" from salesperson inner join customer1 on salesperson.salesid=customer1.salesid where salesperson.commission>400;
### OUTPUT:
![d3(9](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/df49b919-ccd8-47d4-b14e-a2d10027c75e)


### Q10) Perform Left and right join on both tables

### QUERY:
`-- Left Join
select * from salesperson left join customer1 on salesperson.city=customer1.city;
### OUTPUT:
![d3(10](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/e197842f-7b0d-473c-8d14-f8b3ad8cfe54)
![d3(11](https://github.com/vidhyasrikachapalayam/EX-3-SubQueries-Views-and-Joins/assets/119477817/64853434-8d71-4da8-bcff-44b95cef15bb)
### Result:
Thus the dml command executed successfully.


