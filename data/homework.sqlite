Create table departments (
	dept_no varchar PRIMARY KEY,
	dept_name VARCHAR NOT NULL
);
select * from departments
Create table dept_emp (
	id serial primary key,
	emp_no int not null,
	foreign key (emp_no) references employees(emp_no),
	dept_no varchar not null,
	foreign key (dept_no) references departments(dept_no),
	from_date date NOT NULL,
	to_date date NOT NULL
);

select * from dept_emp
create table dept_manager (
	dept_no varchar not null,
	emp_no int not null,
	from_date DATE not null,
	to_date DATE not null
);
select * from dept_manager
create table employees (
	emp_no INT primary key,
	birth_date date not null,
	first_name varchar not null,
	last_name varchar not null,
	gender varchar not null,
	hire_date date not null
);

create table salaries (
	emp_no INT not null,
	foreign key (emp_no) references employees(emp_no),
	salary INT not null,
	from_date date not null,
	to_date date not null
);
 select * from salaries
create table titles (
	emp_no INT not null,
	foreign key (emp_no) references employees(emp_no),
	title varchar not null,
	from_date date not null,
	to_date date not null
);

Select * from departments
select * from dept_emp
select * from dept_manager
select * from employees
select * from salaries
select * from titles


--1. List the following details of each employee: employee number, last name, first name, gender, and salary.

select employees.emp_no, employees.last_name, employees.first_name, employees.gender, salaries.salary
from employees
left join salaries on employees.emp_no=salaries.emp_no

-- 2. List employees who were hired in 1986.

select first_name, last_name
from employees
where 
	hire_date >= '1986/01/01'
	and
	hire_date < '1987/01/01'

-- 3. List the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name, and start and end employment dates.
select dept_manager.dept_no, departments.dept_name, dept_manager.emp_no, employees.first_name, employees.last_name, dept_manager.from_date, dept_manager.to_date
from dept_manager
left join departments
on dept_manager.dept_no=departments.dept_no
left join employees
on dept_manager.emp_no=employees.emp_no

select * from dept_emp
-- 4. List the department of each employee with the following information: employee number, last name, first name, and department name.
create view employee_info as
select employees.emp_no, employees.last_name, employees.first_name, dept_emp.dept_no, departments.dept_name
from employees
left join dept_emp
on employees.emp_no=dept_emp.emp_no
left join departments
on dept_emp.dept_no=departments.dept_no

select * from employee_info

-- 5. List all employees whose first name is "Hercules" and last names begin with "B."

select *
from employees
where
	first_name = 'Hercules'
	and last_name like 'B%'

-- 6. List all employees in the Sales department, including their employee number, last name, first name, and department name.
select dept_name, emp_no, last_name, first_name
from employee_info
where dept_name = 'Sales'

-- 7. List all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.
select dept_name, emp_no, last_name, first_name
from employee_info
where 
	dept_name = 'Sales'
	or dept_name = 'Development'


-- 8. In descending order, list the frequency count of employee last names, i.e., how many employees share each last name.
select last_name, count(last_name) as "name_count"
from employees
group by last_name
order by "name_count" desc; 