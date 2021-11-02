# MYSQL Queries

### Refer url link
      https://tutorial.techaltum.com/sql-queries-for-practice.html

### Table Name:- Employee
		
      Empid	EmpName	Department	      ContactNo	EmailId	      EmpHeadId
      101	Isha	      E-101	            1234567890	isha@gmail.com	      105
      102	Priya 	E-104	            1234567890	priya@yahoo.com	      103
      103	Neha	      E-101	            1234567890	neha@gmail.com	      101
      104	Rahul	      E-102	            1234567890	rahul@yahoo.com	      105
      105	Abhishek	E-101	            1234567890	abhishek@gmail.com	102

      Schema:-
      create table employee(empid int primary key,empname varchar(100), department varchar(50),contactno bigint, emaildid varchar(100), empheadid int)

### Table :- EmpDept

            DeptId	DeptName	      Dept_off	DeptHead
            E-101	       HR	            Monday	105
            E-102	       Development	Tuesday	101
            E-103      	Hous Keeping	Saturday	103
            E-104	      Sales	            Sunday	104
            E-105	      Purchage	      Tuesday	104

            Schema:-
            create table empdept(deptid varchar(50) primary key,deptname varchar(100), dept_off varchar(100), depthead int foreign key references employee(empid))

### Table :- EmpSalary

            EmpId	Salary	IsPermanent
            101	2000	      Yes
            102	10000	      Yes
            103	5000	      No
            104	1900	      Yes
            105	2300	      Yes

            Schema:-
            create table empsalary(empid int foreign key references employee(empid), salary bigint, ispermanent varchar(3))

### Table :- Project

            ProjectId	Duration
            p-1	      23
            p-2	      15
            p-3	      45
            p-4	      2
            p-5	      30

            Schema:-
            create table project(projectid varchar(50) primary key, duration int)
 
 ### Table :- Country
             cid	cname
            c-1	India
            c-2	USA
            c-3	China
            c-4	Pakistan
            c-5	Russia

            Schema:-
            create table country(cid varchar(50) primary key, cname varchar(100))
            
            
            
### Table :- ClientTable

            ClientId	ClientName	cid
            cl-1	      ABC Group	c-1
            cl-2	      PQR	c-1
            cl-3	      XYZ	c-2
            cl-4	      tech altum	c-3
            cl-5	      mnp	c-5

            Schema:-
            create table clienttable(clientid varchar(50) primary key, clientname varchar(100), cid varchar(50) references country(cid))
            
### Table :- EmpProject

            EmpId	ProjectId	ClientID	StartYear	EndYear
            101	p-1   	Cl-1	2010	2010
            102	p-2   	Cl-2	2010	2012
            103	p-1   	Cl-3	2013	
            104	p-4   	Cl-1	2014	2015
            105	p-4   	Cl-5	2015	

            Schema:-
            create table empproject(empid int foreign key references employee(empid), projectid varchar(50) foreign key references project(projectid), clientid varchar(50) foreign key references clienttable(clientid),startyear int, endyear int)

========

Queries:-
Simple Queries
### 1.   Select the detail of the employee whose name start with P.

		select * from employee where empname like 'p%'
		output:-
		query 1 output
![image](https://user-images.githubusercontent.com/53860717/139909162-79bc57ef-226e-4f00-9e3b-afd7b920ef10.png)
		
		
### 2.   How many permanent candidate take salary more than 5000.

		select count(salary) as count from empsalary where ispermanent='yes' and salary>5000
		output:-
		query 2 output
![image](https://user-images.githubusercontent.com/53860717/139909237-65b73f27-3ec7-4376-a6ec-5bd97d8131de.png)
		
		
### 3.   Select the detail of employee whose emailId is in gmail.

		select * from employee where emaildid like '%@gmail.com'
		output:-
		query 3 output
![image](https://user-images.githubusercontent.com/53860717/139909333-96d4cceb-016a-4eb4-ae42-e09e6fca5c28.png)


### 4.   Select the details of the employee who work either for department E-104 or E-102.

		select * from employee where department='E-102' or department='E-104'

		or

		select * from employee where department in ('E-102','E-104')
		output:-
		query 4 output
![image](https://user-images.githubusercontent.com/53860717/139909428-c74be959-e98a-47db-93e3-d3c349efa5c8.png)



### 5.   What is the department name for DeptID E-102?

		select deptname from empdept where deptid ='E-102'
		output:-
		query 5 output
![image](https://user-images.githubusercontent.com/53860717/139909526-024766c7-aaae-443c-adc9-79d3ec2f2421.png)



### 6.  What is total salarythat is paid to permanent employees?

		select sum(salary) as salary from empsalary where ispermanent='yes'
		output:-
		query 6 output

![image](https://user-images.githubusercontent.com/53860717/139909602-9ebb46b4-faba-40af-b567-c83e11a25bf3.png)


### 7.  List name of all employees whose name ends with a.

		select * from employee where empname like '%a'
		output:-
		query 7 output

![image](https://user-images.githubusercontent.com/53860717/139909673-07f69bd4-6f86-42d1-bd09-7c17b3f1d45c.png)


### 8.  List the number of department of employees in each project.

		select count(empid) as employee, projectid from empproject group by projectid
		output:-
		query 8 output
![image](https://user-images.githubusercontent.com/53860717/139909746-e3d0faff-ae9e-42b1-86e9-536903dbb85d.png)
		
### 9.  How many project started in year 2010.

		select count(projectid) as project from empproject where startyear=2010
		output:-
		query 9 output
![image](https://user-images.githubusercontent.com/53860717/139909831-22217787-1027-465f-bc66-09b7ce5286e0.png)



### 10.  How many project started and finished in the same year.

		select count(projectid) as project from empproject where startyear=endyear
		output:-
		query 10 output
![image](https://user-images.githubusercontent.com/53860717/139909911-34be3276-bf41-4934-ae48-19cbdf8856ae.png)


### 11.  select the name of the employee whose name's 3rd charactor is 'h'.

		select * from employee where empname like '__h%'
		output:-
		query 11 output
![image](https://user-images.githubusercontent.com/53860717/139909988-07055c4f-47da-491c-8303-8b817df3d0c4.png)
 		

 
## Nested Queries
### 1.   Select the department name of the company which is assigned to the employee whose employee id is grater 103.

		select deptname from empdept where deptid in (select department from employee where empid>103)
		output:-
		nested query 1 output
![image](https://user-images.githubusercontent.com/53860717/139910077-8b51c507-ca44-4726-92f1-8e51e8a0bbfc.png)


### 2.   Select the name of the employee who is working under Abhishek.

		select empname from employee where empheadid =(select empid from employee where empname='abhishek') 
		output:-
		nested query 2 output
![image](https://user-images.githubusercontent.com/53860717/139910129-d4e3db17-8dd9-4697-9319-2d3fe9d0f3ab.png)



### 3.   Select the name of the employee who is department head of HR.

		select empname from employee where empid =(select depthead from empdept where deptname='hr')
		output:-
		nested query 2 output
![image](https://user-images.githubusercontent.com/53860717/139910189-0f59a3d3-4645-4bbf-a943-debc617a8e5f.png)
		
		
### 4.   Select the name of the employee head who is permanent.

		select empname from employee where empid in(select empheadid from employee) and empid in(select empid from empsalary where ispermanent='yes')
		output:-
		nested query 4 output
![image](https://user-images.githubusercontent.com/53860717/139910257-9782826d-e33f-42ee-9c69-d01b3f22452b.png)
		
		
### 5.   Select the name and email of the Dept Head who is not Permanent.
		
		select empname, emaildid from employee where empid in(select depthead from empdept ) and empid in(select empid from empsalary where ispermanent='no')
		output:-
		nested query 5 output
![image](https://user-images.githubusercontent.com/53860717/139910315-af13bc14-60d0-46bb-89fb-794273c5e946.png)

		
### 6.   Select the employee whose department off is monday
		
		select * from employee where department in(select deptid from empdept where dept_off='monday')
		output:-
		nested query 6 output
![image](https://user-images.githubusercontent.com/53860717/139910396-ec0cc468-1141-4866-9453-b58bd826547d.png)
		
		

 
### 7.   select the indian clinets details.
		
		select * from clienttable where cid in(select cid from country where cname='india')
		output:-
		nested query 7 output
![image](https://user-images.githubusercontent.com/53860717/139910500-5543333e-5751-4e0a-892a-9e86449fb091.png)
		
		
### 8.   select the details of all employee working in development department.
		
            select * from employee where department in(select deptid from empdept where deptname='development')
            output:-
            nested query 8 output
	    
	    
![image](https://user-images.githubusercontent.com/53860717/139910568-e4cf9c0d-5c2f-4d76-a1e2-22e3f6b108e2.png)


		
