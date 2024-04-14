1. Total number of employees
 Code: 
select count(*) from emp;
2.  Total number of departments
Code:
select count(*) from dept;
3. All the employees
Code:
 select * from emp;
4. All the Departments
Code: select * from dept;
5. Total salary paid for all employees
Code:
select sum(sal)
from emp;
6. Total commission paid to all the employees
Code:
select sum(comm)
from emp;
7.  Which job title of the employees get commission paid
Code:
select job, comm
from emp
where comm >0
group by job, comm;
8. System date
Code:
select sysdate as system_date from dual;
9. Average salary paid for each employee
Code:
select avg(sal) 
from emp;
10. How many employees are their in each department
Code:
select d.dname as dept_name, count(e.empno) as count
from dept d
left join emp e on d.deptno = e.deptno
group by d.dname;
11.Total salary of the employees in each department
Code:
select d.deptno, d.dname, sum(e.sal) as tot_sal
from dept d
inner join emp e on d.deptno = e.deptno
group by d.deptno, d.dname;
12.How many employees are there under each job title
Code:
 select job, count(empno) as num_of_emp
from emp
group by job;
13.Average salary paid for each job title
Code:
 select job, avg(sal) as avg_salary
from emp
group by job;
14. Hireday,month,and year for each employee
Code:
 select ename, to_char(hiredate, 'dd') as hire_day,
    to_char(hiredate, 'mm') as hire_month,
    to_char(hiredate, 'yyyy') as hire_year
from emp;
15.Sort the employee department wise
Code:
select  e.ename, e.deptno,
d.dname as dept_name, d.loc as dept_loc
from emp e
full outer join dept d on e.deptno = d.deptno
order by d.dname;
16.Sort the employees based on their job titles
Code:
select ename,job from emp
order by job;
17. Sort the employee based on descending order of their salaries
Code:
select ename,sal from emp
order by sal desc;
18.Sort the employee ascending order of their department and descending order of their salary
Code:
select e.ename, e.job, e.deptno, d.dname
from emp e
full outer join dept d on e.deptno = d.deptno
order by e.deptno asc, e.sal desc;
19.How many employees have their names with 6 characters
Code:
 select count(*)
from emp
where length(ename) = 6;
20.Maximum and Minimum salary paid
Code:
select max(sal) as max_sal,
    min(sal) as min_sal
from emp;
21.Maximum, minimum, average and sum of salary paid under each department
Code:
 select d.deptno,
       d.dname as dept_name,
       max(e.sal) as max_sal,
       min(e.sal) as min_sal,
       avg(e.sal) as avg_sal,
       sum(e.sal) as tot_sal
from dept d
 full outer join emp e on d.deptno = e.deptno
group by d.deptno, d.dname;
22. Sort the employee based on their hiredate
Code:
select ename, job , hiredate
    from emp
order by hiredate;
23. Employee who joined latest
Code:
select ename,hiredate
from emp
where hiredate = (select max(hiredate)
    from emp);
24. Who is the oldest employee in the organization based on their hiredate
Code:
select ename,hiredate
from emp
where hiredate = (select min(hiredate)
    from emp);
25. Sort the employee based on their hire year(descending) and department (ascending)
Code:
select e.ename, e.hiredate, d.dname
from emp e
join dept d on e.deptno = d.deptno
order by (e.hiredate) desc, d.dname asc;
26.Employees who get salaries greater than or equal to the average salary of the employees
Code:
select empno, ename, sal
from emp
where sal >= (select avg(sal) from emp);
27.Employees who get salaries less than or equal to the average salary of the employees
Code:
select empno, ename,sal
from emp
where sal <= (select avg(sal) from emp);
28.Employees get salaries between 2000 & 4000
Code:
select e.* from emp e
  full outer join dept d on e.deptno = d.deptno
where e.sal between 2000 and 4000;

29.Which employees get the highest and lowest salary
Code:
select empno, ename, sal
from em
    where 
sal = (select max(sal) from emp)
    or 
sal = (select min(sal) from emp);

30.We need to celebrate the joining month of the employees. We plan to buy a gift for each of them. How many gifts do I need to buy for next month
Code:
select count (*) as num_employees
from emp
where extract (month from hiredate) = extract (month from current_date);


