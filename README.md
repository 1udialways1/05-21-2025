show databases;

use vit;

show tables;

select * from cont

where m_no between 1000 and 20000

and f_name not in ('hardhik','rohith');



#aggeration functions

select min(m_no) from cont;



select avg(m_no) from cont;



select count(m_no) from cont;



select max(m_no) from cont;



select sum(m_no) from cont;



create table shop(name varchar(20),p_id int primary key,Price int );

insert into shop values ('Power',1,50),('shampoo',2,340),('sunscreem',3,399),('wheypower',4,2000),('comb',5,10),('oil',6,39);

insert into shop values ('snaks',7,400),('pens',8,50),('scale',9,10),('groomimg set',10,4999);



select count(p_id) from shop;

select min(price) from shop;

select max(price) from shop;

select avg(price) from shop;



select * from shop where price=(select min(price) from shop);



#worker1

select * from worker;

INSERT INTO Worker 

	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES

		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),

		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),

		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),

		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),

		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),

		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),

		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),

		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');

create table worker1(WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,

	FIRST_NAME CHAR(25),

	LAST_NAME CHAR(25),

	SALARY INT(15),

	JOINING_DATE DATETIME,

	DEPARTMENT CHAR(25)

);

show tables;

INSERT INTO Worker1 

	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES

		(001, 'VAMIKA', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),

		(002, 'HARIKA', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),

		(003, 'VISHU', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),

		(004, 'AMIT', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),

		(005, 'VINNU', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),

		(006, 'ATTUL', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),

		(007, 'KOTALA', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),

		(008, 'GEETHU', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');



#TO CHECK HOW MANY DIFFERNET VALUES PRESENT IN A COLOUMN

select distinct(department) from worker1;



#UNION

select department from worker

union

select department from worker1;



#UNION ALL

select department from worker

union all

select department from worker1;



select worker_id,first_name from worker

where department='HR'

union 

select worker_id,first_name from worker1

where department='ADMIN';



#SQL CASE

Select First_name,Last_name,Salary,

CASE 

When salary >=500000 then 'Rich People'

when salary<500000 && salary>=100000 then 'MIDDLE CLASS'

when salary<100000 then 'POOR CLASS'

else 'DATA NOT FOUND'

END

as status_check_aspersalary

from worker;

 

#ORDERED BY

select * from worker where salary<1000000 order by salary;



select * from worker where salary<1000000 order by salary desc;



select * from worker where salary<1000000 order by first_name desc,last_name asc;



#LIKE CLAUSE

select * from worker where first_name LIKE '_i%l';

select * from worker where first_name LIKE '%a_a';

select * from worker where first_name LIKE '%i_a';

select * from worker where last_name LIKE '%i__h';

select * from worker where last_name LIKE 'V__m%';



SELECT * 

FROM worker 

WHERE first_name LIKE 'G__t%' AND first_name LIKE '__%ka';



#TO CREATE A VIEW

CREATE VIEW ADMIN_TEAM AS SELECT * FROM WORKER WHERE DEPARTMENT='HR' AND SALARY<100000;

SELECT * FROM ADMIN_TEAM;



#TO REPLACE A VIEW

CREATE OR REPLACE VIEW ADMIN_TEAM AS SELECT * FROM WORKER WHERE DEPARTMENT='HR' AND SALARY>100000;



#TO DROP A VIEW

DROP VIEW ADMIN_TEAM;
