# oracle
教材中的查询语句
查询1
![image]()
SELECT d.department_name，count（e.job_id）as“部门总人数”，【】
avg（e.salary）as“平均工资
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT'，'Sales')
GROUP BY department_name;

查询2：
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
FROM hr.departments d，hr.employees e
WHERE d.department_id = e.department_id
GROUP BY department_name
HAVING d.department_name in ('IT'，'Sales');
   
   我认为查询一的语句是最优，因为代码中应该避免使用having子句，having只会在检索出所有记录之后才会对结果进行过滤，因此查询二代码会更慢
   
   
   我的代码：
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name exists ('IT'，'Sales')
GROUP BY department_name;
   
