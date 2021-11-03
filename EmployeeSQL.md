create table employees(
	emp_no int not null,
	emp_title_id varchar not null,
	birth_date date not null,
	first_name varchar not null,
	last_name varchar not null,
	sex varchar not null,
	hire_date date not null,
	primary key (emp_no)
);
select * from male_employees;
create table departments(
	dept_no varchar not null,
	dept_name varchar not null,
	primary key (dept_no)
);
select * from departments;
create table dept_manager(
	dept_no varchar not null,
	emp_no int not null,
	primary key (dept_no,emp_no)
);
select * from dept_manager;
create table dept_emp(
	emp_no int not null,
	dept_no varchar not null,
	primary key (emp_no,dept_no)
);
select * from dept_emp;
create table salaries(
	emp_no int not null,
	salary int not null,
	primary key(emp_no)
);
select * from salaries;





select employees.emp_no,employees.last_name,employees.first_name,employees.sex,salaries.salary
from employees
left join salaries
on (employees.emp_no=salaries.emp_no);
select first_name,last_name,hire_date
from employees
where hire_date
between '1986-01-01' and '1986-12-31';
select dept_manager.dept_no, dept_manager.emp_no,employees.first_name,employees.last_name,departments.dept_name
from employees
inner join dept_manager
on (dept_manager.emp_no=employees.emp_no)
inner join departments
on (departments.dept_no = dept_manager.dept_no);
Select employees.emp_no,employees.last_name,employees.first_name,departments.dept_name
from employees
join dept_emp
on employees.emp_no = dept_emp.emp_no
Join departments
on dept_emp.dept_no = departments.dept_no;
select employees.first_name, employees.last_name, employees.sex
from employees
where first_name = 'Hercules' And Last_name Like 'B%';
select employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
from employees
join dept_emp
on employees.emp_no = dept_emp.emp_no
Join departments
on dept_emp.dept_no = departments.dept_no
where departments.dept_name = 'Sales';
select employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
from employees
Join dept_emp
ON  employees.emp_no = dept_emp.emp_no
Join departments
ON dept_emp.dept_no = departments.dept_no
where departments.dept_name = 'Sales' OR departments.dept_name = 'Development';
Select employees.last_name, Count(*)
From employees
Group By employees.last_name
Order BY Count (*) Desc;