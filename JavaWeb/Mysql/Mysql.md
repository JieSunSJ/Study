通过MySQL的客户端命令行，如何来连接服务器上部署的MySQL ：
```
mysql -h数据库服务器的IP地址 -P端口号 -u用户名 -p密码
```
数据库操作
查询所有数据库
```
show databases;
```
查询当前数据库
我们要操作某一个数据库，必须要切换到对应的数据库中。
```
select database();
```
创建数据库
```
create database [ if not exists ] 数据库名  [default charset utf8mb4];
```
```
-- 数据库不存在,则创建该数据库；如果存在则不创建
create database if not exists itcast; 
```
使用数据库
```
use 数据库名 ;
```
删除数据库
```
drop database [ if exists ] 数据库名 ;
```
数据库表操作
创建
```
create table  表名(
        字段1  字段1类型 [约束]  [comment  字段1注释 ],
        字段2  字段2类型 [约束]  [comment  字段2注释 ],
        ......
        字段n  字段n类型 [约束]  [comment  字段n注释 ] 
) [ comment  表注释 ] ;
```
约束
```
[05-Web后端基础(数据库)](https://heuqqdmbyk.feishu.cn/wiki/UmHJwg2cqi0kYUkOFDIcHGfvnld)
```
字段操作
分页查询
1. 起始索引从0开始。 计算公式 ：起始索引 = （查询页码 - 1）* 每页显示记录数
2. 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT
3. 如果查询的是第一页数据，起始索引可以省略，直接简写为 limit 条数
 案例1：从起始索引0开始查询员工数据, 每页展示5条记录
```
select id, username, password, name, gender, phone, salary, job, image, entry_date, create_time, update_time
from emp
limit 0 , 5; -- 从索引0开始，向后取5条记录
```
 案例2：查询 第1页 员工数据, 每页展示5条记录
```
select id, username, password, name, gender, phone, salary, job, image, entry_date, create_time, update_time
from emp
limit 5; -- 如果查询的是第1页数据，起始索引可以省略，直接简写为：limit 条数
```
 案例3：查询 第2页 员工数据, 每页展示5条记录
```
select id, username, password, name, gender, phone, salary, job, image, entry_date, create_time, update_time
from emp
limit 5 , 5; -- 从索引5开始，向后取5条记录
```
