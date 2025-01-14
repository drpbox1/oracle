# 实验一：分析SQL执行计划，执行SQL语句的优化指导

## 实验内容：
- 对Oracle12c中的HR人力资源管理系统中的表进行查询与分析。
- 首先运行和分析教材中的样例：本训练任务目的是查询两个部门('IT'和'Sales')的部门总人数和平均工资，以下两个查询的结果是一样的。但效率不相同。
- 设计自己的查询语句，并作相应的分析，查询语句不能太简单。

## 教材中的查询语句

查询1：

```SQL
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT'，'Sales')
GROUP BY department_name;
```
结果：  
![image](https://github.com/drpbox1/oracle/blob/master/test1/1.png)  
优化：  
![image](https://github.com/drpbox1/oracle/blob/master/test1/11.png)  

- 查询2：
```SQL
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
FROM hr.departments d，hr.employees e
WHERE d.department_id = e.department_id
GROUP BY department_name
HAVING d.department_name in ('IT'，'Sales');
```
结果：  
![image](https://github.com/drpbox1/oracle/blob/master/test1/2.png)  
优化：  
![image](https://github.com/drpbox1/oracle/blob/master/test1/22.png)  
自定义分析：  
![image](https://github.com/drpbox1/oracle/blob/master/test1/111.png)  
