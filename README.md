
1. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id.

/// create table countries (country_id int,
			country_name varchar(255),
			region_id int
			);


2. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists.



3. Write a SQL statement to create the structure of a table dup_countries similar to countries.

/// create table dup_countries LIKE countries; ///

4. Write a SQL statement to create a duplicate copy of countries table including structure and data by name dup_countries.

/// create table dup_countries select * from countries; ///

5. Write a SQL statement to create a table countries set a constraint NOT NULL (all the fields should be not null).

/// create table countryies (country_id int not null, country_name varchar(255) not null, region_id int not null);

6. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.

/// create table jobs (job_id int,
		       job_title varchar(255), 
		       min_salary int, 	
		       max_salary int
 		       chech(max_salary<=25000)
		       );

 
7. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table.

/// create table countries (country_id int,
			    country_name varchar(255),
			    check(country_name in("Italy","India","China")),
			    region_id int
			   );
 

8. Write a SQL statement to create a table named job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.

/// create table job_history (employee_id int, 
		              start_date date,
			      end_date date,
            		      check (end_date like '--/--/----'), 
			      job_id int, 
			      department_id int
			     );


9. Write a SQL statement to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.

/// create table countries (country_id int,
			country_name varchar(255),
			region_id int,
			unique(country_id)	
			);


10. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

/// create table jobs (job_id int,
		   job_title varchar(255) not null default " ",
		   min_salary int dafault 8000,
		   max_salary int dafault null
		  );


11. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.

/// create table countries (country_id int unique primary key,
			    country_name varchar(30),
			    region_id int
			   );



12. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.

/// create table countries (country_id int unique auto_incremented,
			    country_name varchar(30),
			    region_id int
			   );


13. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.

create table countries (country_id int unique,
			country_name varchar(30),
			region_id int,
			primary key (country_id, region_id)
			);


14. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.

Here is the structure of the table jobs;

create table job_history (employee_id int primary key,
		          start_date date,
		          end_date date,
            		  check (end_date like '--/--/----'), 
			  job_id int foreign key, 
			  department_id int,
		          foreign key (job_id) references jobs(job_id)
		          )ENGINE=InnoDB;
			  


| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |



15. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.

Assume the structure of departments table below.

create table employees (employee_id int primary key,
			first_name varchar(30),
			last_name varchar(30),
			email varchar(40),
			phone_number int,
			hire_date date,
			job_id int,
			salary int,
			commision int,
			manager_id int,
			department_id int,
			foreign key (department_id, manager_id),
			REFERENCES (department_id, manager_id)
			)engine=innoBB;


| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |


16. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

"A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference dev.mysql.com

Assume that the structure of two tables departments and jobs.


create table employees (employee_id int primary key,
			first_name varchar(30),
			last_name varchar(30),
			email varchar(40),
			phone_number int,
			hire_date date,
			job_id int,
			salary int,
			commision int,
			manager_id int,
			department_id int,
			foreign key (department_id),
			REFERENCES department(department_id),
			foreign key (job_id),
			REFERENCES jobs(job_id)	
			)engine=innoBB;


| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |



17. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```

create teble employees (employee_id int primary key,
			first_name varchar(30), 
			last_name varchar(30), 
			job_id int, 
			salary int,
			foreign key (job_id),
			references jobs(job_id),
			);engine innoDB



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |


18. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```

create table employees(employee_id int primary key, 
		       first_name varchar(30), 
		       last_name varchar(30), 
		       job_id int, 
		       salary int,
		       foreign key (job_id),
		       references jobs(job_id),
		       ON DELETE CASCADE ON UPDATE RESTRICT
		       );engine innoDB



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |


19. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```

cteate table eployees (employee_id int primary key,
		       first_name varchar(30), 
		       last_name varchar(30),
		       job_id int,
		       salary int,
	               foreign key (job_id),
		       references jobs(job_id),
		       ON DELETE set null,
		       ON UPDATE set null
		       );engine innoDB
		       


| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

20. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.



Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```

cteate table eployees (employee_id int primary key,
		       first_name varchar(30), 
		       last_name varchar(30),
		       job_id int,
		       salary int,
	               foreign key (job_id),
		       references jobs(job_id),
		       ON DELETE no action,
		       ON UPDATE no action
		       );engine innoDB
		       





| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |


