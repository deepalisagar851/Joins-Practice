# Joins-Practice
create database Emp_Record;
use Emp_Record;
create table Employee_Details( EId int ,
FirstName varchar(50),
LastName varchar(50),
salary int, 
Joining_date date,
Department varchar(25),
Gender varchar(15));

select*from Employee_Details;

Insert into  Employee_Details(EId,FirstName, LastName,Salary, Joining_date, Department, Gender)
values(101,'Ansh',' Kumar',10000,'2013-02-12','IT','Male'),
(102,'Chandan',' Kumar',22000,'2014-02-10','HR','Male'),
(103,'Chhavi',' Kumari',13000,'2015-08-10','IT','Female'),
(104,'Deepak',' Kumar',14000,'2013-02-12','Payroll','Male'),
(107,'Harshit',' Kumar',15000,'2014-02-10','HR','Male'),
(108,'Muskan',' Sagar',16000,'2014-02-10','HR','Female');

create table Project_Details
(Project_DetailID int,Employee_DetailID int, ProjectName Varchar(25));
Insert into Project_Details(Project_DetailID,Employee_DetailID, ProjectName)
values(1,1,'Task Track'),
(2,1,'CLP'),
(3,1,'Survey Management'),
(4,2,'HR Management'),
(5,3,'Task Track'),
(6,3,'GRS'),
(7,3,'DDS'),
(8,4,'HR Management'),
(9,6,'GL Management');
