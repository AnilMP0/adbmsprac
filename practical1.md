Practical-1 : DDL operations on Relational Schema 
Date- 23/01/23
Roll No.- L017

Creating database-
mysql> create database practical;
Query OK, 1 row affected (0.01 sec)
mysql> use practical;
Database changed

Creating salesman table-
mysql> create table salesman(salesman_id integer primary key,name text,city text,commission float);
Query OK, 0 rows affected (0.04 sec)
Inserting values into salesman tables-
mysql> insert into salesman values(5001,'james hooq','new york',0.15);
Query OK, 1 row affected (0.02 sec)
mysql> insert into salesman values(5002,'nail knite','paris',0.13);
Query OK, 1 row affected (0.01 sec)
mysql> insert into salesman values(5003,'pit alex','london',0.11);
Query OK, 1 row affected (0.01 sec)
mysql> insert into salesman values(5005,'pit alex','london',0.11);
Query OK, 1 row affected (0.00 sec)
mysql> insert into salesman values(5006,'mc lyon','paris',0.14);
Query OK, 1 row affected (0.00 sec)
mysql> insert into salesman values(5003,'lauson hen',0.12);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into salesman values(5003,'lauson hen',' ',0.12);
Query OK, 1 row affected (0.01 sec)
mysql> insert into salesman values(5007,'paul adam','rome',0.13);
Query OK, 1 row affected (0.01 sec)
Displaying salesman table-
mysql> select * from salesman;
+-------------+------------+----------+------------+
| salesman_id | name       | city     | commission |
+-------------+------------+----------+------------+
|        5001 | james hooq | new york |       0.15 |
|        5002 | nail knite | paris    |       0.13 |
|        5003 | lauson hen |          |       0.12 |
|        5005 | pit alex   | london   |       0.11 |
|        5006 | mc lyon    | paris    |       0.14 |
|        5007 | paul adam  | rome     |       0.13 |
+-------------+------------+----------+------------+
6 rows in set (0.00 sec)

Creating customer table-
mysql> CREATE TABLE customer (
    ->   customer_id INTEGER PRIMARY KEY,
    ->   cust_name TEXT NOT NULL,
    ->   city TEXT NOT NULL,
    ->   grade INTEGER,
    ->   salesman_id INTEGER
    -> );
Query OK, 0 rows affected (0.04 sec)

Inserting values into customer table-
mysql> INSERT INTO customer VALUES ( 3002, 'Nick Rimando' ,'New York',  100 ,5001);
Query OK, 1 row affected (0.01 sec)
mysql> INSERT INTO customer VALUES (3007, 'Brad Davis',  'New York' , 200, 5001);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO customer VALUES (3005, 'Graham Zusi', 'California' ,200 ,5002);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO customer VALUES (3008 ,'Julian Green', 'London' , 300, 5002);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO customer VALUES (3004, 'Fabian Johnson' ,'Paris' , 300, 5006);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO customer VALUES (3009, 'Geoff Cameron', 'Berlin',  100, 5003);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO customer VALUES (3003 ,'Jozy Altidor', 'Moscow', 200,  5007);
Query OK, 1 row affected (0.00 sec)

Displaying customer table-
mysql> select * from customer;
+-------------+----------------+------------+-------+-------------+
| customer_id | cust_name      | city       | grade | salesman_id |
+-------------+----------------+------------+-------+-------------+
|        3002 | Nick Rimando   | New York   |   100 |        5001 |
|        3003 | Jozy Altidor   | Moscow     |   200 |        5007 |
|        3004 | Fabian Johnson | Paris      |   300 |        5006 |
|        3005 | Graham Zusi    | California |   200 |        5002 |
|        3007 | Brad Davis     | New York   |   200 |        5001 |
|        3008 | Julian Green   | London     |   300 |        5002 |
|        3009 | Geoff Cameron  | Berlin     |   100 |        5003 |
+-------------+----------------+------------+-------+-------------+
7 rows in set (0.00 sec)

Creating orders table-
mysql> CREATE TABLE orders (
    ->   ord_no INTEGER PRIMARY KEY,
    ->   purch_amt INTEGER,
    ->   ord_date date,
    ->   customer_id INTEGER,
    ->   salesman_id INTEGER
    -> );
Query OK, 0 rows affected (0.03 sec)

Inserting values into orders table-
mysql> INSERT INTO orders VALUES (70001, 150.5, '2012-10-05', 3005, 5002);
Query OK, 1 row affected (0.01 sec)
mysql> INSERT INTO orders VALUES (70009, 270.65, '2012-09-10', 3001, 5005);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70002, 65.26 ,'2012-10-05' ,3002, 5001);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70004, 110.5, '2012-08-17', 3009, 5003);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70007, 948.5, '2012-09-10', 3005, 5002);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70005, 2400.6, '2012-07-27', 3007, 5001);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70008, 5760, '2012-09-10', 3002, 5001);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70010, 1983.43, '2012-10-10', 3004, 5006);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70003, 2480.4, '2012-10-10', 3009, 5003);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70012, 250.45, '2012-06-27', 3008, 5002);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70011, 75.29, '2012-08-17', 3003, 5007);
Query OK, 1 row affected (0.00 sec)
mysql> INSERT INTO orders VALUES (70013, 3045.6, '2012-04-25', 3002, 5001);
Query OK, 1 row affected (0.00 sec)

Displaying orders table-
mysql> select * from orders;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70001 |       151 | 2012-10-05 |        3005 |        5002 |
|  70002 |        65 | 2012-10-05 |        3002 |        5001 |
|  70003 |      2480 | 2012-10-10 |        3009 |        5003 |
|  70004 |       111 | 2012-08-17 |        3009 |        5003 |
|  70005 |      2401 | 2012-07-27 |        3007 |        5001 |
|  70007 |       949 | 2012-09-10 |        3005 |        5002 |
|  70008 |      5760 | 2012-09-10 |        3002 |        5001 |
|  70009 |       271 | 2012-09-10 |        3001 |        5005 |
|  70010 |      1983 | 2012-10-10 |        3004 |        5006 |
|  70011 |        75 | 2012-08-17 |        3003 |        5007 |
|  70012 |       250 | 2012-06-27 |        3008 |        5002 |
|  70013 |      3046 | 2012-04-25 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
12 rows in set (0.00 sec)

1,Display name and commission for all the salesmen. 
mysql> select name,commission from salesman;
+------------+------------+
| name       | commission |
+------------+------------+
| james hooq |       0.15 |
| nail knite |       0.13 |
| lauson hen |       0.12 |
| pit alex   |       0.11 |
| mc lyon    |       0.14 |
| paul adam  |       0.13 |
+------------+------------+
6 rows in set (0.00 sec)

2.Retrieve salesman id of all salesmen from orders table without any repeats. 
mysql> select distinct salesman_id from orders;
+-------------+
| salesman_id |
+-------------+
|        5002 |
|        5001 |
|        5003 |
|        5005 |
|        5006 |
|        5007 |
+-------------+
6 rows in set (0.01 sec)

3.Display names and city of salesman, who belongs to the city of Paris. 
mysql> select name,city from salesman where city='paris';
+------------+-------+
| name       | city  |
+------------+-------+
| nail knite | paris |
| mc lyon    | paris |
+------------+-------+
2 rows in set (0.00 sec)

4. Display all the information for those customers with a grade of 200. 
mysql> select * from customer where grade=200;
+-------------+--------------+------------+-------+-------------+
| customer_id | cust_name    | city       | grade | salesman_id |
+-------------+--------------+------------+-------+-------------+
|        3003 | Jozy Altidor | Moscow     |   200 |        5007 |
|        3005 | Graham Zusi  | California |   200 |        5002 |
|        3007 | Brad Davis   | New York   |   200 |        5001 |
+-------------+--------------+------------+-------+-------------+
3 rows in set (0.00 sec)

5. Display the order number, order date and the purchase amount for order(s) which will be delivered by the salesman with ID 5001
mysql> select ord_no,purch_amt,ord_date from orders where salesman_id=5001;
+--------+-----------+------------+
| ord_no | purch_amt | ord_date   |
+--------+-----------+------------+
|  70002 |        65 | 2012-10-05 |
|  70005 |      2401 | 2012-07-27 |
|  70008 |      5760 | 2012-09-10 |
|  70013 |      3046 | 2012-04-25 |
+--------+-----------+------------+
4 rows in set (0.00 sec)

11. Find the name and price of the cheapest item(s). 
mysql> select purch_amt from orders where purch_amt=(select min(purch_amt) from orders);
+-----------+
| purch_amt |
+-----------+
|        65 |
+-----------+
1 row in set (0.01 sec)

12. Display all the customers, who are either belongs to the city New York or not had a grade above 100. 
mysql> select * from customer where city='new york' or grade<100;
+-------------+--------------+----------+-------+-------------+
| customer_id | cust_name    | city     | grade | salesman_id |
+-------------+--------------+----------+-------+-------------+
|        3002 | Nick Rimando | New York |   100 |        5001 |
|        3007 | Brad Davis   | New York |   200 |        5001 |
+-------------+--------------+----------+-------+-------------+
2 rows in set (0.00 sec)

13. Find those salesmen with all information who gets the commission within a range of 0.12 and 0.14. 
mysql> select * from salesman where commission>0.12 and commission<0.14;
+-------------+------------+-------+------------+
| salesman_id | name       | city  | commission |
+-------------+------------+-------+------------+
|        5002 | nail knite | paris |       0.13 |
|        5007 | paul adam  | rome  |       0.13 |
+-------------+------------+-------+------------+
2 rows in set (0.00 sec)

14. Find all those customers with all information whose names are ending with the letter 'n'. 
mysql> select * from customer where name like '%n';
ERROR 1054 (42S22): Unknown column 'name' in 'where clause'
mysql> select * from customer where cust_name like '%n';
+-------------+----------------+--------+-------+-------------+
| customer_id | cust_name      | city   | grade | salesman_id |
+-------------+----------------+--------+-------+-------------+
|        3004 | Fabian Johnson | Paris  |   300 |        5006 |
|        3008 | Julian Green   | London |   300 |        5002 |
|        3009 | Geoff Cameron  | Berlin |   100 |        5003 |
+-------------+----------------+--------+-------+-------------+
3 rows in set (0.00 sec)

15. Find those salesmen with all information whose name containing the 1st character is 'N' and the 4th character is 'l' and rests may be any character. 
mysql> select * from salesman where name like 'n__i%';
Empty set (0.00 sec)

16. Find that customer with all information who does not get any grade except NULL. 
mysql> select * from customer where grade>0;
+-------------+----------------+------------+-------+-------------+
| customer_id | cust_name      | city       | grade | salesman_id |
+-------------+----------------+------------+-------+-------------+
|        3002 | Nick Rimando   | New York   |   100 |        5001 |
|        3003 | Jozy Altidor   | Moscow     |   200 |        5007 |
|        3004 | Fabian Johnson | Paris      |   300 |        5006 |
|        3005 | Graham Zusi    | California |   200 |        5002 |
|        3007 | Brad Davis     | New York   |   200 |        5001 |
|        3008 | Julian Green   | London     |   300 |        5002 |
|        3009 | Geoff Cameron  | Berlin     |   100 |        5003 |
+-------------+----------------+------------+-------+-------------+
7 rows in set (0.00 sec)

17. Find the total purchase amount of all orders. 
mysql> select sum(purch_amt) from orders;
+----------------+
| sum(purch_amt) |
+----------------+
|          17542 |
+----------------+
1 row in set (0.00 sec)

18. Find the number of salesman currently listing for all of their customers. 
mysql> select count(salesman_id) from orders;
+--------------------+
| count(salesman_id) |
+--------------------+
|                 12 |
+--------------------+
1 row in set (0.00 sec)

19. Find the highest grade for each of the cities of the customers. 
mysql> select city,max(grade) from customer group by city;
+------------+------------+
| city       | max(grade) |
+------------+------------+
| New York   |        200 |
| Moscow     |        200 |
| Paris      |        300 |
| California |        200 |
| London     |        300 |
| Berlin     |        100 |
+------------+------------+
6 rows in set (0.00 sec)

20. Find the highest purchase amount ordered by each customer with their ID and highest purchase amount. 
mysql> select customer_id,max(purch_amt) from orders group by customer_id;
+-------------+----------------+
| customer_id | max(purch_amt) |
+-------------+----------------+
|        3005 |            949 |
|        3002 |           5760 |
|        3009 |           2480 |
|        3007 |           2401 |
|        3001 |            271 |
|        3004 |           1983 |
|        3003 |             75 |
|        3008 |            250 |
+-------------+----------------+
8 rows in set (0.00 sec)

21. Find the highest purchase amount ordered by each customer on a particular date with their ID, order date and highest purchase amount. 
mysql> select customer_id,ord_date,max(purch_amt) from orders group by customer_id,ord_date;
+-------------+------------+----------------+
| customer_id | ord_date   | max(purch_amt) |
+-------------+------------+----------------+
|        3005 | 2012-10-05 |            151 |
|        3002 | 2012-10-05 |             65 |
|        3009 | 2012-10-10 |           2480 |
|        3009 | 2012-08-17 |            111 |
|        3007 | 2012-07-27 |           2401 |
|        3005 | 2012-09-10 |            949 |
|        3002 | 2012-09-10 |           5760 |
|        3001 | 2012-09-10 |            271 |
|        3004 | 2012-10-10 |           1983 |
|        3003 | 2012-08-17 |             75 |
|        3008 | 2012-06-27 |            250 |
|        3002 | 2012-04-25 |           3046 |
+-------------+------------+----------------+
12 rows in set (0.00 sec)

22. Find the highest purchase amount on a date '2012-08-17' for each salesman with their ID. 
mysql> select salesman_id,max(purch_amt) from orders where ord_date='2012-08-17' group by salesman_id;
+-------------+----------------+
| salesman_id | max(purch_amt) |
+-------------+----------------+
|        5003 |            111 |
|        5007 |             75 |
+-------------+----------------+
2 rows in set (0.00 sec)

23. Find the highest purchase amount with their customer ID and order date, for only those customers who have the highest purchase amount in a day is more than 2000. 
mysql> select customer_id,ord_date,purch_amt from orders where purch_amt>2000;
+-------------+------------+-----------+
| customer_id | ord_date   | purch_amt |
+-------------+------------+-----------+
|        3009 | 2012-10-10 |      2480 |
|        3007 | 2012-07-27 |      2401 |
|        3002 | 2012-09-10 |      5760 |
|        3002 | 2012-04-25 |      3046 |
+-------------+------------+-----------+
4 rows in set (0.00 sec)

24. Write a SQL statement that counts all orders for a date August 17th, 2012. 
mysql> select count(*) from orders where ord_date='2012-08-17';
+----------+
| count(*) |
+----------+
|        2 |
+----------+
1 row in set (0.00 sec)
