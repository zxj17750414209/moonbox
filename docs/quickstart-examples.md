#### 系统初始化
step 1: 使用ROOT账号登录
```
bin/cli.sh -h master -P port -u ROOT -p 123456 [-r local]
```
step 2: 创建organization
```
create org org_test;
```
step 3: 在organization中创建管理员
```
create sa sally in org org_test identified by 123456
```
step 4: 退出ROOT账号
```
exit
```
至此, 系统初始化完成。系统拥有一个名为org_test的命名空间, 该空间下有一个名为sally的管理员和一个名为default的逻辑数据库。


#### 用户使用
- 使用sally登录
```
bin/cli.sh -h master -P port -u sally -p 123456
```
- 挂载数据源
```
mount database mb_mysql options(
    type 'mysql',
    url 'jdbc:mysql://host:port/database',
    user 'user',
    password 'password',
    driver 'com.mysql.jdbc.Driver'
)
```
- 列出所有数据库
```
show databases
```
- 列出以m开头的数据库
```
show databases like 'm%'
```
- 查看数据库信息
```
desc database mb_mysql
```
- 切换数据库
```
use mb_mysql
```
- 列出当前库下所有表
```
show tables
```
- 列出当前库下以m开头所有表
```
show tables like 'm%'
```
- 查看表结构
```
desc table_name
```
- 查看表信息
```
show create table table_name
```
- 对表进行查询
```
select * from table_name
```
- 查看SQL语句结果schema信息
```
show schema for select count(*) from table_name
```
- 创建视图
```
create view view_name as select count(*) from table_name
```
- 对视图进行查询
```
select * from view_name
```
- 查看表信息
```
show create table view_name
```
- 查看表结构
```
desc view_name
```
