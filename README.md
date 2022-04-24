create database Emp_Record; 
use Emp_Record;
create table EmployeeDetails( EId int ,
FirstName varchar(50),
LastName varchar(50), 
salary int,
Joining_date datetime,
Department varchar(25), 
Gender varchar(15));

select*from EmployeeDetails;

Insert into EmployeeDetails
(EId,FirstName, LastName,Salary, Joining_Date, Department, Gender)
values(101,'Ansh',' Kumar',10000,'2013-02-12 11:16:28','IT','Male'), 
(102,'Chandan',' Kumar',22000,'2014-02-10 17:31:07','HR','Male'), 
(103,'Chhavi',' Kumari',13000,'2015-08-10 10:05:07','IT','Female'), 
(104,'Deepak',' Kumar',14000,'2013-02-12 09:00:07','Payroll','Male'),
(105,'Harshit',' Kumar',15000,'2014-02-10 09:31:07','HR','Male'),
(106,'Muskan',' Sagar',16000,'2014-02-10 11:16:28','HR','Female'),
(107,'Daksh',' Kumar',14000,'2013-02-01 09:00:07','Payroll','Male'),
(108,'Rahul',' Kumar',16000,'2013-01-01 09:00:07','Management','Male');

SELECT * FROM EmployeeDetails
WHERE FirstName LIKE '[a-p]%';

SELECT * FROM EmployeeDetails
WHERE Gender LIKE '__le';

SELECT * FROM EmployeeDetails
WHERE FirstName LIKE 'a____';

SELECT * FROM EmployeeDetails
WHERE FirstName LIKE 'Dee%ak';

SELECT DISTINCT Department FROM EmployeeDetails;

SELECT CONVERT(VARCHAR(20),Joining_date,106) Joining_date FROM EmployeeDetails;

SELECT CONVERT(VARCHAR(20),Joining_date,111) Joining_date FROM EmployeeDetails;

SELECT CONVERT(VARCHAR(20),Joining_date,108) Joining_date FROM EmployeeDetails;

SELECT YEAR (Joining_date) Joining_date  FROM EmployeeDetails;

SELECT FirstName, GETDATE() AS [Current Date], Joining_Date
,DATEDIFF(MM,Joining_Date,GETDATE()) AS TotalMonths FROM EmployeeDetails;

SELECT * FROM EmployeeDetails WHERE Year(Joining_Date)='2013';

SELECT * FROM EmployeeDetails WHERE Month(Joining_Date)='01';

SELECT * FROM EmployeeDetails WHERE Joining_Date BETWEEN '2013-01-01' AND '2013-12-01';

Select FirstName, 
  Case when Gender = 'Male' then 'M' when Gender = 'Female' then 'F' else 'Other' end
  as Gender from EmployeeDetails;


create table ProjectDetails(ProjectDetailsID int,
Employee_DetailID int,
ProjectName Varchar(25));
Insert into ProjectDetails
(ProjectDetailsID,Employee_DetailID, ProjectName)
values(1,101,'Task Track'), 
(2,102,'CLP'), 
(3,103,'Survey Management'), 
(4,104,'HR Management'), 
(5,105,'Task Track'), 
(6,106,'GRS'),
(7,107,'DDS'),
(8,108,'HR Management'),
(9,109,'GL Management');

SELECT FirstName,ProjectName FROM [EmployeeDetails] A INNER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID ORDER BY FirstName;

SELECT FirstName,ProjectName FROM [EmployeeDetails] A LEFT OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID ORDER BY FirstName;

SELECT FirstName, ISNULL(ProjectName,'-No Project Assigned') FROM [EmployeeDetails] A LEFT OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID ORDER BY FirstName;

SELECT FirstName,ProjectName FROM [EmployeeDetails] A RIGHT OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID ORDER BY FirstName;

SELECT FirstName,ProjectName FROM [EmployeeDetails] A FULL OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID ORDER BY FirstName;

SELECT FirstName, ISNULL(ProjectName,'-No Project Assigned') AS [ProjectName]
FROM [EmployeeDetails] A LEFT OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID
WHERE ProjectName IS NULL;

SELECT ProjectName FROM [EmployeeDetails] A RIGHT OUTER JOIN [ProjectDetails] B
ON A.EID = B.Employee_DetailID
WHERE FirstName IS NULL;

Select EID, FirstName, ProjectName
from [EmployeeDetails] E INNER JOIN [ProjectDetails] P
ON E.EID = P.Employee_DetailID
WHERE EID IN (SELECT Employee_DetailID FROM [ProjectDetails] 
GROUP BY Employee_DetailID HAVING COUNT(*) >1 );

Select FirstName, ProjectName from [EmployeeDetails] E INNER JOIN [ProjectDetails] P
ON E.EID = P.Employee_DetailID;
