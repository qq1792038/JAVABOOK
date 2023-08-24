[TOC]

# 什么是PostgreSQL?

PostgreSQL是一个功能强大的开源对象关系数据库管理系统(ORDBMS)。 用于安全地存储数据; 支持最佳做法，并允许在处理请求时检索它们。

PostgreSQL是跨平台的，可以在许多操作系统上运行，如Linux，FreeBSD，OS X，Solaris和Microsoft Windows等。

# PostgreSQL特点

PostgreSQL可在所有主要操作系统(即Linux，UNIX(AIX，BSD，HP-UX，SGI IRIX，Mac OS X，Solaris，Tru64)和Windows等)上运行。

PostgreSQL支持文本，图像，声音和视频，并包括用于C/C++，Java，Perl，Python，Ruby，Tcl和开放数据库连接(ODBC)的编程接口。

PostgreSQL支持SQL的许多功能，例如复杂SQL查询，SQL子选择，外键，触发器，视图，事务，多进程并发控制(MVCC)，流式复制(9.0)，热备(9.0))。

在PostgreSQL中，表可以设置为从“父”表继承其特征。

可以安装多个扩展以向PostgreSQL添加附加功能。

# PostgreSQL数据类型

**PostgreSQL主要有三种类型的数据类型：**

- 数值数据类型
- 字符串数据类型
- 日期/时间数据类型

## 数值数据类型

| 名称      | 描述                                   | 存储大小 | 范围                                                    |
| --------- | -------------------------------------- | -------- | ------------------------------------------------------- |
| smallint  | 存储整数，小范围                       | 2字节    | -32768至+32767                                          |
| integer   | 存储整数。使用这个类型可存储典型的整数 | 4字节    | -2147483648 至 +2147483647                              |
| bigint    | 存储整数，大范围。                     | 8字节    | -9223372036854775808 至 9223372036854775807             |
| decimal   | 用户指定的精度，精确                   | 变量     | 小数点前最多为131072个数字; 小数点后最多为16383个数字。 |
| numeric   | 用户指定的精度，精确                   | 变量     | 小数点前最多为131072个数字; 小数点后最多为16383个数字。 |
| real      | 可变精度，不精确                       | 4字节    | 6位数字精度                                             |
| double    | 可变精度，不精确                       | 8字节    | 15位数字精度                                            |
| serial    | 自动递增整数                           | 4字节    | 1 至 2147483647                                         |
| bigserial | 大的自动递增整数                       | 8字节    | 1 至 9223372036854775807                                |

## 字符串数据类型

| 数据类型                | 描述                                                         |
| ----------------------- | ------------------------------------------------------------ |
| char(size)              | 这里`size`是要存储的字符数。固定长度字符串，右边的空格填充到相等大小的字符。 |
| character(size)         | 这里`size`是要存储的字符数。 固定长度字符串。 右边的空格填充到相等大小的字符。 |
| varchar(size)           | 这里`size`是要存储的字符数。 可变长度字符串。                |
| character varying(size) | 这里`size`是要存储的字符数。 可变长度字符串。                |
| text                    | 可变长度字符串。                                             |

## 日期/时间数据类型

| 名称                          | 描述                   | 存储大小 | 最小值        | 最大值        | 解析度       |
| ----------------------------- | ---------------------- | -------- | ------------- | ------------- | ------------ |
| timestamp [ (p) ] [不带时区 ] | 日期和时间(无时区)     | 8字节    | 4713 bc       | 294276 ad     | 1微秒/14位数 |
| timestamp [ (p) ]带时区       | 包括日期和时间，带时区 | 8字节    | 4713 bc       | 294276 ad     |              |
| date                          | 日期(没有时间)         | 4字节    | 4713 bc       | 5874897 ad    | 1微秒/14位数 |
| time [ (p) ] [ 不带时区 ]     | 时间(无日期)           | 8字节    | 00:00:00      | 24:00:00      | 1微秒/14位数 |
| time [ (p) ] 带时区           | 仅限时间，带时区       | 12字节   | 00:00:00+1459 | 24:00:00-1459 | 1微秒/14位数 |
| interval [ fields ] [ (p) ]   | 时间间隔               | 12字节   | -178000000年  | 178000000年   | 1微秒/14位数 |

## 其它数据类型

**布尔类型**：

| 名称    | 描述                        | 存储大小 |
| ------- | --------------------------- | -------- |
| boolean | 它指定`true`或`false`的状态 | 1字节    |

**货币类型**

| 名称  | 描述     | 存储大小 | 范围                                           |
| ----- | -------- | -------- | ---------------------------------------------- |
| money | 货币金额 | 8字节    | -92233720368547758.08 至 +92233720368547758.07 |

**几何类型**：

| 名称    | 存储大小   | 表示                   | 描述                        |
| ------- | ---------- | ---------------------- | --------------------------- |
| point   | 16字节     | 在一个平面上的点       | (x,y)                       |
| line    | 32字节     | 无限线(未完全实现)     | ((x1,y1),(x2,y2))           |
| lseg    | 32字节     | 有限线段               | ((x1,y1),(x2,y2))           |
| box     | 32字节     | 矩形框                 | ((x1,y1),(x2,y2))           |
| path    | 16+16n字节 | 封闭路径(类似于多边形) | ((x1,y1),…)                 |
| polygon | 40+16n字节 | 多边形(类似于封闭路径) | ((x1,y1),…)                 |
| circle  | 24字节     | 圆                     | `<(x，y)，r>`(中心点和半径) |

# PostgreSQL创建/删除数据库

```sql
CREATE DATEBASE database_name;
DROP DATEBASE database_name;
```

# PostgreSQL 创建/删除数据表

```sql
# 创建
CREATE TABLE public.student2
(
  id integer NOT NULL,
  name character(100),
  subjects character(1),
  CONSTRAINT student2_pkey PRIMARY KEY (id)
)
WITH (
  OIDS=FALSE
);
ALTER TABLE public.student2
  OWNER TO postgres;
COMMENT ON TABLE public.student2
  IS '这是一个学生信息表2';
# 删除
DROP TABLE student2
```

# PostgreSQL 模式（架构）

```sql
# 创建
CREATE SCHEMA schema_name;
# 删除
DROP SCHEMA schema_name;
```

# 查询

## PostgreSQL 插入数据

**测试**：

创建数据表

```sql
CREATE TABLE public.employees
(
	id integer NOT NULL,
	name text NOT NULL,
	age integer NOt NUll,
	address character(50),
	salary real,
	CONSTRAINT employees_pkey PRIMARY KEY (id)
)
WITH (
	OIDS = FALSE
);
ALTER TABLE public.employees
	OWNER TO postgres;
```

![image-20230824113032209]([/image/image-20230824113032209.png](https://github.com/qq1792038/JAVABOOK/blob/main/PostgreSQL/image/image-20230824113032209.png))

插入数据

```sql
INSERT INTO employees( id, name, age, address, salary)
VALUES
(1, 'Maxsu', 25, '海口市人民大道2880号', 109990.00 ), 
(2, 'minsu', 25, '广州中山大道 ', 125000.00 ), 
(3, '李洋', 21, '北京市朝阳区', 185000.00),   
(4, 'Manisha', 24, 'Mumbai', 65000.00), 
(5, 'Larry', 21, 'Paris', 85000.00);
```

![image-20230824113503545](/image/image-20230824113503545.png)

## PostgreSQL 查询数据

```sql
# 检索所有字段
SELECT * FROM employees;
# 检索指定字段
SELECT id, name FROM employees;
```

## PostgreSQL 更新数据

```sql
# 更新id = 1的数据记录为age = 29, salary = 9800
UPDATE employees
SET age = 29, salary = 9800
WHERE id = 1;
```

![image-20230824114844713](/image/image-20230824114844713.png)

## PostgreSQL 删除数据

```sql
# 删除id = 1的数据记录
DELETE FROM public.employees
	WHERE id = 1;
```

## PostgreSQL ORDER BY 子句

**ASC按照字段升序排序**

```sql
SELECT * 
FROM employees
ORDER BY age ASC
```

![image-20230824115150420](/image/image-20230824115150420.png)

**DESC按照字段降序排序**

```sql
SELECT * 
FROM employees
ORDER BY age DESC
```

![image-20230824115331580](/image/image-20230824115331580.png)

**多列排序**

```sql
# 第一项排序优先，第一项相同时按照第二项排序。
SELECT * 
FROM employees
ORDER BY age, salary ASC
```

## PostgreSQL GROUP BY 分组 

```sql
SELECT name, sum(salary)
FROM employees
GROUP BY NAME;
```

![image-20230824120039538](/image/image-20230824120039538.png)

**如何减少冗余数据**

```sql
INSERT INTO EMPLOYEES VALUES (6, '李洋', 24, '深圳市福田区中山路', 135000);  
INSERT INTO EMPLOYEES VALUES (7, 'Manisha', 19, 'Noida', 125000);  
INSERT INTO EMPLOYEES VALUES (8, 'Larry', 45, 'Texas', 165000);
```

![image-20230824120153212](/image/image-20230824120153212.png)

**消除冗余**

```sql
SELECT name, sum(salary)
FROM employees
GROUP BY NAME;
```

![image-20230824120239299](/image/image-20230824120239299.png)

## PostgreSQL Having 子句

在PostgreSQL中，HAVING子句与GROUP BY子句组合使用，用于选择函数结果满足某些条件的特定行。

```sql
SELECT column1, column2  
FROM table1, table2  
WHERE [ conditions ]  
GROUP BY column1, column2  
HAVING [ conditions ]  
ORDER BY column1, column2
```

查询name数量小于2的记录。

```sql
SELECT name
FROM employees
GROUP BY name HAVING count(name) < 2;
```

![image-20230824132407553](/image/image-20230824132407553.png)

查询name字段值计数大于1的名称。

```sql
SELECT NAME,COUNT (NAME) 
FROM EMPLOYEES  
GROUP BY NAME HAVING COUNT (NAME) > 1;
```

![image-20230824132536591](/image/image-20230824132536591.png)

## PostgreSQL 条件查询

PostgreSQL条件用于从数据库获取更具体的结果。 它们通常与WHERE子句一起使用。 具有子句的条件就像双层过滤器。

以下是PostgreSQL条件的列表：

- AND 条件
- OR 条件
- AND & OR 条件
- NOT 条件
- LIKE 条件
- IN 条件
- NOT IN 条件
- BETWEEN 条件

### AND 条件

PostgreSQL AND条件与`WHERE`子句一起使用，以从表中的多个列中选择唯一的数据。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition]    
AND [search_condition];
```

查询所有id小于4并且薪水大于120000的员工数据信息：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE SALARY > 120000  
AND ID <= 4;
```

![image-20230824132850800](/image/image-20230824132850800.png)

### OR 条件

PostgreSQL OR条件与`WHERE`子句一起使用，以从表中的一列或多列列中选择唯一数据。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition]    
OR [search_condition];
```

查询名字是`minsu`或者地址为`Noida`员工信息：

```sql
SELECT *  
FROM  EMPLOYEES 
WHERE NAME = 'minsu'  
OR ADDRESS = 'Noida';
```

![image-20230824133148270](/image/image-20230824133148270.png)

### AND & OR 条件

PostgreSQL AND＆OR条件在仅一个查询中提供了`AND`和`OR`条件的优点。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition]  AND [search_condition]     
OR [search_condition];
```

查询名字的值为`minsu`和地址的值为’`Delhi`‘，或者ID值大于等`8`的记录信息：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE (NAME = 'minsu' AND ADDRESS = '广州中山大道')  
OR (ID>= 8);
```

![image-20230824133446074](/image/image-20230824133446074.png)

### NOT 条件

PostgreSQL NOT条件与WHERE子句一起使用以否定查询中的条件。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition] NOT [condition];
```

查询地址不为`NULL`的记录信息：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE address IS NOT NULL ;
```

查询年龄不是`21`和`24`的所有记录：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE age NOT IN(21,24) ;
```

![image-20230824133737604](/image/image-20230824133737604.png)

### LIKE条件

PostgreSQL LIKE条件与WHERE子句一起用于从指定条件满足`LIKE`条件的表中获取数据。

**语法**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition] LIKE [condition];
```

查询名字以`Ma`开头的数据记录：

```sql
SELECT *   
FROM EMPLOYEES   
WHERE NAME LIKE 'Ma%';
```

![image-20230824133909406](/image/image-20230824133909406.png)

查询名字以`su`结尾的数据记录，如下查询语句：

```sql
SELECT *   
FROM EMPLOYEES   
WHERE NAME LIKE '%su';
```

![image-20230824134004854](/image/image-20230824134004854.png)

查询地址中含有`大道`的数据记录，如下查询语句：

```sql
SELECT *   
FROM EMPLOYEES   
WHERE address LIKE '%大道%';
```

![image-20230824134035824](/image/image-20230824134035824.png)

### IN 条件

PostgreSQL IN条件与WHERE子句一起使用，从指定条件满足`IN`条件的表中获取数据。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition] IN [condition];
```

查询`employee`表中那些年龄为`19`，`21`的员工信息，执行以下查询：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE AGE IN (19, 21);
```

![image-20230824134133265](/image/image-20230824134133265.png)

### NOT IN条件

PostgreSQL NOT IN条件与WHERE子句一起使用，以从指定条件否定`IN`条件的表中获取数据。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition] NOT IN [condition];
```

查询那些年龄不是`19`，`25`的数据，执行以下查询：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE AGE NOT IN (19, 25);
```

![image-20230824134230361](/image/image-20230824134230361.png)

查询那些名字不是`minsu`，`李洋`的数据信息，执行以下查询：

```sql
SELECT *  
FROM EMPLOYEES  
WHERE name NOT IN ('李洋', 'minsu');
```

![image-20230824134354221](/image/image-20230824134354221.png)

### BETWEEN 条件

PostgreSQL BETWEEN条件与WHERE子句一起使用，以从两个指定条件之间的表中获取数据。

**语法：**

```sql
SELECT column1, column2, ..... columnN    
FROM table_name    
WHERE [search_condition] BETWEEN [condition];
```

查询`employees`表中年龄在`24`~`27`之间(含`24`，`27`)的数据信息，执行以下查询：

```sql
SELECT *   
FROM EMPLOYEES   
WHERE AGE BETWEEN 24 AND 27;
```

![image-20230824134454146](/image/image-20230824134454146.png)

# 连接

- 内连接(INNER JOIN)

- 左外连接(LEFT OUTER JOIN)

- 右外连接(RIGHT OUTER JOIN)

- 全连接(FULL OUTER JOIN)

- 跨连接(CROSS JOIN)

## PostgreSQL 连接（内连接）

### PostgreSQL INNER JOIN

PostgreSQL内部连接也被称为连接或简单连接。 这是最常见的连接类型。 此连接返回满足连接条件的多个表中的所有行。

![image-20230824134743688](/image/image-20230824134743688.png)

**语法：**

```sql
SELECT table1.columns, table2.columns  
FROM table1  
INNER JOIN table2  
ON table1.common_filed = table2.common_field;
```

创建`department`数据表

```sql
CREATE TABLE public.department
(
  id integer,
  dept text,
  fac_id integer
)
WITH (
  OIDS=FALSE
);
ALTER TABLE public.department
  OWNER TO postgres;

-- 插入数据
INSERT INTO department VALUES(1,'IT', 1);
INSERT INTO department VALUES(2,'Engineering', 2);
INSERT INTO department VALUES(3,'HR', 7);
```

查询连接两个表：

```sql
SELECT EMPLOYEES.ID, EMPLOYEES.NAME, DEPARTMENT.DEPT  
FROM EMPLOYEES   
INNER JOIN DEPARTMENT  
ON EMPLOYEES.ID = DEPARTMENT.ID;
```

![image-20230824135213011](/image/image-20230824135213011.png)

## PostgreSQL 左外连接

左外连接返回从“`ON`”条件中指定的左侧表中的所有行，只返回满足条件的另一个表中的行。
![image-20230824135309395](/image/image-20230824135309395.png)

**语法：**

```sql
SELECT table1.columns, table2.columns  
FROM table1  
LEFT OUTER JOIN table2  
ON table1.common_filed = table2.common_field;
```

左外连接

```sql
SELECT EMPLOYEES.ID, EMPLOYEES.NAME, DEPARTMENT.DEPT  
FROM EMPLOYEES 
LEFT OUTER JOIN DEPARTMENT  
ON EMPLOYEES.ID = DEPARTMENT.ID;
```

![image-20230824135348500](/image/image-20230824135348500.png)

左表(`EMPLOYEES`)全部列出来，而右表(`DEPARTMENT`)没有匹配上的项全留为空值。

## PostgreSQL 右外连接

右外连接返回从“`ON`”条件中指定的右侧表中的所有行，只返回满足条件的另一个表中的行。

![image-20230824135528222](/image/image-20230824135528222.png)

**语法：**

```sql
SELECT table1.columns, table2.columns  
FROM table1  
RIGHT OUTER JOIN table2  
ON table1.common_filed = table2.common_field;
```

```sql
INSERT INTO department VALUES(10,'Market', 10);

SELECT EMPLOYEES.ID, EMPLOYEES.NAME, DEPARTMENT.DEPT  
FROM EMPLOYEES 
RIGHT OUTER JOIN DEPARTMENT  
ON EMPLOYEES.ID = DEPARTMENT.ID;
```

![image-20230824135654561](/image/image-20230824135654561.png)

右表(`DEPARTMENT`)全部列出来，而左表(`EMPLOYEES`)没有匹配上的项全留为空值。

## PostgreSQL 全外连接

全外连接从左表和左表中返回所有行。 它将`NULL`置于不满足连接条件的位置。

**语法：**

```sql
SELECT table1.columns, table2.columns  
FROM table1  
FULL OUTER JOIN table2  
ON table1.common_filed = table2.common_field;
```

![image-20230824135802619](/image/image-20230824135802619.png)

全外连接：

```sql
SELECT EMPLOYEES.ID, EMPLOYEES.NAME, DEPARTMENT.DEPT  
FROM EMPLOYEES 
FULL OUTER JOIN DEPARTMENT  
ON EMPLOYEES.ID = DEPARTMENT.ID;
```



![image-20230824135910106](/image/image-20230824135910106.png)

左表(`EMPLOYEES`)和右表(`DEPARTMENT`)没有匹配上的项全留为空值。

## PostgreSQL 交叉连接（CROSS JOIN）

PostgreSQL跨连接(`CROSS JOIN`)将第一个表的每一行与第二个表的每一行相匹配。 它也被称为笛卡尔积。 如果`table1`具有“`x`”行，而`table2`具有“`y`”行，则所得到的表将具有(`x * y`)行。

**语法：**

```sql
SELECT coloums   
FROM table1   
CROSS JOIN table2
```

跨连接查询：

```sql
SELECT NAME, DEPT 
FROM EMPLOYEES  
CROSS JOIN DEPARTMENT;
```

![image-20230824140150622](/image/image-20230824140150622.png)

# PostgreSQL 函数（存储过程）

PostgreSQL函数也称为PostgreSQL存储过程。 PostgreSQL函数或存储过程是存储在数据库服务器上并可以使用SQL界面调用的一组SQL和过程语句(声明，分配，循环，控制流程等)。 它有助于您执行通常在数据库中的单个函数中进行多次查询和往返操作的操作。

您可以在许多语言(如SQL，PL/pgSQL，C，Python等)中创建PostgreSQL函数。

**语法：**

```sql
CREATE [OR REPLACE] FUNCTION function_name (arguments)   
RETURNS return_datatype AS $variable_name$  
  DECLARE  
    declaration;  
    [...]  
  BEGIN  
    < function_body >  
    [...]  
    RETURN { variable_name | value }  
  END; LANGUAGE plpgsql;
```

### 参数说明

- `function_name`：指定函数的名称。
- `[OR REPLACE]`：是可选的，它允许您修改/替换现有函数。
- `RETURN`：它指定要从函数返回的数据类型。它可以是基础，复合或域类型，或者也可以引用表列的类型。
- `function_body`：`function_body`包含可执行部分。
- `plpgsql`：它指定实现该函数的语言的名称。

在`EMPLOYEES`表上创建一个名为`total records()`的函数。
函数的定义如下：

```sql
CREATE OR REPLACE FUNCTION totalRecords ()  
RETURNS integer AS $total$  
declare  
    total integer;  
BEGIN  
   SELECT count(*) into total FROM EMPLOYEES;  
   RETURN total;  
END;  
$total$ LANGUAGE plpgsql;

# 调用函数并检查employees表中的记录
select totalRecords();
```

![image-20230824140730101](/image/image-20230824140730101.png)
