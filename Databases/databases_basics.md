### Databases

the are mainly 2 types of databases sql and nosql databases

the most comman databases are

- MySql  -> sql database
- MongoDB -> nosql databases


# SQL

sql databases are tabular or can also be said Relational databases.
- they store data in the form of tables i.e rows and colums

for example thier is a database named persons

it consists of table information    

name	 age	salary		location	grade

anil	45	20000		newyork
suraj	52	80000		newyork		
max	10			newyork		a
rohan	15			newyork		b
rohan	16			newyork		c

this is called a table so it is called a tabular database.

in this database we have records of persons their age salary location and grades
the persons who are working have a salary and the persons who are studing have grades
but the working persons doesnt have grade entry and the students doesnt have a salary entry
so they are nill. to avoid such things we use a nosql database.

# NoSql

it stores data in the form of docs or pages format their can be different formats of the doc. it set of info is stored as a seperete doc.

e.g. 
name 	anil
age	45
location newyork
salary 20000

this entry is stored in a single doc
many such docs makes a collection.

example of sql databases :

mysql
postgre sql
ms sql server

example of nosql databases :

mongo DB
Amazon DynamoDB
Cassandra


# Mysql commands

- wget <url>  -> to download rpm package of mysql server
- rpm -ivh  -> to add rpm to repo
- yum install mysql-server - to install the mysql server
- services mysql start
- service mysql status - to know satus
cat /var/log/mysql.log - for log and for temperory password

mysql -u root -p'password' - to login as -u user root and -p for password withoutspace

SET PASSWORD = 'PASS';  - TO change password
ALTER USER 'root@localhost' IDENTIFIED BY 'pass'; - TO CHANGE PASSWORD OF A USER

Database Commands

SHOW DATABASES  - to show all the databases available
CREATE DATABASES database_name;  - to create new database
USE database_name; - to use a particular database
CREATE TABLE table_name ( 
Name varchar (255);
age INT;
location varchar (255);
);			- to create a table in databse

INSERT INTO table_name VALUES ("jhon.Doe ",45,"newyork");  - to insert values in a table
SELECT* FROM Persons; - to select the table
SHOW TABLES; - to view tables
CREATE USER 'JHON'@'localhost' IDENTIFIED BY 'pass';  - to create a user with localhost and pasword
CREATE USER 'JHON'@'172.162.0.1' IDENTIFIED BY 'pass'; - to create a user with ip for remote acess with password
CREATE USER 'JHON'@'%' IDENTIFIED BY 'PASS'; - to create a user with global acess

# PERMISSIONS

GRANT SELECT ON database_name.table_name TO 'user'@'%'; - granting select privilages of a table in a database to user
GRANT SELECT,UPDATE ON database_name.table_name TO 'user'@'%'; - granting select and update privilages of a table in a database to a user
GRANT SELECT,UPDATE ON database_name.* to 'USER'@'%'; - granting select and update privilages of all thr tables in a database to the user
GRANT ALL PRIVILAGES ON *.* TO 'USER'@'%'; - granting all privilages to the full databse to a user
SHOW GRANTS FOR 'user'@'localhost'; - show all the permissions to jhon has on localhost


## MongoDB

- it is a nosql databse
- it stores data in a DOC
- Mongo shell is a java script interface
- it uses json files to store data

## commands

yum install mongodb-org   -> to install mongodb
systemctl start mongod  -> to start mongodb
systemctl status mongod  -> to see status of mongodb
cat /var/log/mongodb/mongodb.log  -> to view logs of mongod
/ect/mongod.conf  -> to view the confifuration file of mongodb

## connect

mongo		- it is used to get into the command line of mongodb
showdb  	- it shows all the db available on server
use db_name - create and uses a db
db - it shows which db is used
db.createcollection ("name")	- it is used to create collection
show collection		- it shows all the collection in th db
db.collection-name.insert({
"name":"jhon"
"age":4,
"loction":"newyork"
"salary":5000
})			- it is used to entry data in a collection
db.persons.find() - to find and filter data

