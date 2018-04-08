#SQL--结构化查询语言

## 1. 基本介绍

  ### 1.1 **文件系统的三个缺陷**

> 1. 数据冗余，由于文件之间缺乏联系，导致每个应用程序都有对应的文件。
> 2. 不一致性，往往由数据冗余造成
> 3. 数据联系弱，这是由于文件之间相互独立，缺乏联系造成的

###1.2 **数据库阶段数据管理具有以下特点**

> 1. 采用数据模型表示复杂的数据结构。**使得数据冗余明显减少，实现了数据共享**。
>
> 2. 有较高的独立性。数据的逻辑结构与物理结构之间的区别可以很大用户，用户以简单的逻辑结构操作数据而无需考虑数据的物理结构。数据库的结构分为**用户的局部逻辑结构**、**数据库的整体逻辑结构**和**物理结构**三级。
>
> 3. 数据库系统为用户提供了方便的用户接口。
>
> 4. 数据库系统提供以下四方面的数据控制功能：
>
>    (1) 数据库的并发控制
>
>    (2) 数据库的恢复
>
>    (3) 数据的完整性
>
>    (4) 数据的安全性
>
> 5. 增加了系统的灵活性

###1.3 **基本术语**

> 1. 数据库：DB
> 2. 数据库管理系统: DBMS
> 3. 数据库系统: DBS

###1.4 ***SQL 能做什么？***

- SQL 面向数据库执行查询
- SQL 可从数据库取回数据
- SQL 可在数据库中插入新的记录
- SQL 可更新数据库中的数据
- SQL 可从数据库删除记录
- SQL 可创建新数据库
- SQL 可在数据库中创建新表
- SQL 可在数据库中创建存储过程
- SQL 可在数据库中创建视图
- SQL 可以设置表、存储过程和视图的权限

###1.5 ***在您的网站中使用 SQL***

要创建发布数据库中数据的网站，您需要以下要素：

- RDBMS 数据库程序（比如 MS Access, SQL Server, MySQL）
- 服务器端脚本语言（比如 PHP 或 ASP）
- SQL
- HTML / CSS

###1.6 ***RDBMS***

RDBMS 指的是关系型数据库管理系统。

RDBMS 是 SQL 的基础，同样也是所有现代数据库系统的基础，比如 MS SQL Server, IBM DB2, Oracle, MySQL 以及 Microsoft Access。

RDBMS 中的数据存储在被称为**表（tables）**的数据库对象中。

**表是相关的数据项的集合，它由列和行组成。**

### 1.7 数据描述

**在数据处理中，数据描述将涉及到不同的范畴：**

####1.概念设计中的数据描述 

> 1. 实体：一个具体或者是抽象的对象，如学生、借书、比赛。
> 2. 实体集：性质相同的同类实体的集合
> 3. 属性：实体有很多特性，每个特性都称为属性，如学生的姓名。
> 4. 实体标识符：能唯一标识实体的属性与属性集。有时也称为关键码，简称键。如学生的学号。

#### 2. 逻辑设计中的数据描述

> 1. 字段：标记实体属性的命名单位称为字段，或**数据项**。如：学生的学号等字段。
> 2. 记录：字段的有序集合称为记录。用一个记录完整的描述一个实体，如一个学生记录：学号、姓名、年龄、性别。
> 3. 文件：同一类集合称为文件。
> 4. 关键码：能唯一确定**文件**中每个**记录**的**字段或字段集**。

### 1.8 数据联系的描述

联系时实体间的相互关系。

> 1. 一元联系
> 2. 二元联系：一对多，多对一，多对多
> 3. 三元联系

### 1.9 数据模型

模型是对现实世界的抽象，能表示实体类型及实体间联系的模型称为数据模型。

#### 1. 实体联系模型（ER）

ER模型直接从现实世界中抽象出实体类型及实体间联系，然后用实体联系图表示数据模型

ER图的四个基本成分:

>1. 矩形框：表示实体类型（问题放入对象）
>2. 菱形框：表示联系类型（实体间联系）
>3. 椭圆形框：表示实体类型或联系类型的属性
>4. 连线：实体与属性之间，联系与属性之间用直线连接，并在直线端部标注联系的类型（1:1,1:N或M:N）
>5. 确定实体类型的键：在ER图中属于键的属性名下画一个横线

[例图](https://img-blog.csdn.net/20161019203344282)

####2. 层次模型

用树形（层次）结构表示实体类型及实体间联系的数据类型称为层次模型

#### 3. 网状模型

用有向图表示实体类型及实体间联系的数据模型称为网状模型。

#### 4. 关系模型

用二维表格表示实体集，用关键码表示实体集间联系的数据模型称为关系模型

#### 5. 面向对象模型

### 1.10 数据库管理员(DBA)

DBA的主要职责是：

1. 定义模型
2. 定义内模型
3. 与用户的联络。包括定义外模型、应用程序的设计、提供技术培训等专业服务
4. 定义安全性规则，对用户访问数据库授权
5. 定义完整性原则，监督数据库的运行
6. 数据库的转储与恢复



## 2. 关系运算

###2.1关系数据模型 

**域(Domain)**是值的集合，如：学生的性别域{男，女}

给定一组域D1,D2,D3,...Dn上的**笛卡尔积**定义为集合：

```
D1×D2×...Dn = {(d1,d2,...dn) | di 属于Di, i = 1,2,3...,n}
```

**关键码和表之间的联系：**

> 1. 超键：在一个关系中，能**唯一标识**元组或属性集称为关系的超键
> 2. 候选键：如果一个属性集能**唯一标识**元组，且又**不含有多余的属性**，那么此属性集称为关系的候选键
> 3. 主键：若一个关系中有多个候选键，则**选择一个候选键**作为**关系的主键**。包含在**任何一个候选键**中的属性称为**主属性**，其他的属性称为**非主属性**。
> 4. 外键：若一个关系R中含有另一个关系S的**主键**所对应的**属性组F**，则称F为R的外键，并称关系S为参照关系，关系R为依赖关系

### 2.2 关系模型的完整性规则

关系模型的完整性规则是对数据的约束，关系模型提供了三类完整性规则：**实体完整性规则，参照完整性规则，用户定义完整性规则**。其中实体完整性规则和参照完整性规则是关系模型**必须满足的完整性的约束条件**，称为**关系完整性规则**。

1. 实体完整性规则：关系中元组的**主键值不能为空**

2. 参照完整性规则：如果**属性集K**是关系模型**R1的主键**，K也是关系模型**R2的外键**，那么在R2的关系中，K的取值只允许两种可能：或者为空，或者等于R1关系中的某个主键值

   **使用注意：**

   > 1. **外键和相应的主键可以不同名，只要定义在相同值域上即可**
   > 2. R1和R2也可以是同一个关系模型，表示了同一个关系中不同元组之间的联系
   > 3. 外键值是否允许为空，应视具体问题而定，若外键是该模型主键中的成分时，则外键值不允许为空，否则允许为空

3. 用户定义完整性规则：反映出某一项具体应用所涉及的数据必须满足的语义要求，如学生成绩应该>=0。

### 2.3 关系代数

####1. 关系代数的基本操作

1. 并(Union)：　R∪S

   关系R和关系S具有相同的n个属性，且相应的属性取自同一个域，可以将其进行并运算，结果仍为n元关系。并运算要求两个属性的性质必须一致，并且运算的结果要**消除重复的元组**。

2. 差(Difference): R－S

   关系R和关系S具有相同的n个属性，且相应的属性取自同一个域，可以将其进行差运算，结果仍为n元关系。结果为属于R而不属于S的所有元组组成。

3. 笛卡儿积(Cartesian Product): R×S

   设关系R和S的元数分别为r和s。定义R和S的笛卡儿积R×S是一个(r+s)元的元组集合，每个元组的前r个分量(属性值)来自R的一个元组，后s个分量是S的一个元组，记为R×S。

4. 投影(Projection): πi,j(R)

   这个操作是对一个关系进行**垂直分割**，消除某些列，并重新安排的顺序，再扇区重复元组。

   如，πi,j(R)操作是只留下那个R表的i,j两行，再去重

5. 选择(Selection): σb>’4’ (R) 

   这个操作是对一个关系进行**水平分割**，b>'4'是选择的行应该要满足的条件。

#### 2. 关系代数的组合操作

1. 交(Intersection): R∩S

   设关系R和关系S具有相同的元数n，且相应的属性取自同一个域，则关系R和关系S的交由既属于关系R又属于关系S的元组组成，其结果仍为n元的关系。关系的交可以由关系的差来表示:R∩S = R - (R - S)或R∩S = S - (S - R)

2. **联接（Join）**：

   联接操作可将两个关系连在一起，形成一个新的关系，是**笛卡儿积和选择操作**的组合，分为θ联接和F联接两种。

   > 1. **θ**联接：**θ**联接是从关系R和S的笛卡儿积中选取属性值满足某个**θ**操作的元组，记为：
   >
   >    ![image](https://images2015.cnblogs.com/blog/872539/201610/872539-20161020123151935-261097945.png)
   >
   >    当θ为等号时称为等值联接
   >
   >    其值相当于：σ(RXS)　及先进行笛卡儿积操作X，再进行选择操作σ
   >
   > 2. F联接：与θ操作类似，只是最终结果需要满足F公式

3. 自然联接(Natural Join)：　R⋈S

   自然联接是一种特殊的等值联接，它要求两个关系中进行比较的分量必须是相同的属性组，并要在结果中把重复的属性去掉。

   和等值联接唯一的区别就是：去除了多余的属性，及选择时的属性有两组，去除S中的那一组即可

   其相当于：先进行笛卡儿积X，再进行选择操作σ，最后进行投影操作π（删除多余属性）

4. 除(Division): R÷S 

## 3. SQL语法

###3.1 数据库表

一个数据库通常包含一个或多个表。每个表由一个名字标识（例如“客户”或者“订单”）。表包含带有数据的记录（行）。

下面的例子是一个名为 "Persons" 的表：

| Id   | LastName | FirstName | Address        | City     |
| ---- | -------- | --------- | -------------- | -------- |
| 1    | Adams    | John      | Oxford Street  | London   |
| 2    | Bush     | George    | Fifth Avenue   | New York |
| 3    | Carter   | Thomas    | Changan Street | Beijing  |

上面的表包含三条记录（每一条对应一个人）和五个列（Id、姓、名、地址和城市）。

###3.2 SQL 语句

####1. 例子

您需要在数据库上执行的大部分工作都由 SQL 语句完成。

下面的语句从表中选取 LastName 列的数据：

```
SELECT LastName FROM Persons
```

结果集类似这样：

| LastName |
| -------- |
| Adams    |
| Bush     |
| Carter   |

####2. ***重要事项: 一定要记住，SQL 对大小写不敏感！***

####3. ***SQL 语句后面的分号？***

某些数据库系统要求在每条 SQL 命令的末端使用分号。在我们的教程中不使用分号。

分号是在数据库系统中分隔每条 SQL 语句的标准方法，这样就可以在对服务器的相同请求中执行一条以上的语句。

如果您使用的是 MS Access 和 SQL Server 2000，则不必在每条 SQL 语句之后使用分号，**不过某些数据库软件要求必须使用分号。**

####4. ***SQL  DDL、DML、DCL***

SQL (结构化查询语言)是用于执行查询的语法。其包括三个部分：DDL、DML、DCL

1. **DDL is Data Definition Language statements. Some examples:数据定义语言，用于定义和管理 SQL 数据库中的所有对象的语言**

   >1. CREATE - to create objects in the database 创建
   >
   >2. ALTER - alters the structure of the database 修改
   >
   >3. DROP - delete objects from the database 删除
   >
   >4. TRUNCATE - remove all records from a table, including all spaces allocated for the records are removed TRUNCATE TABLE [Table Name]。
   >
   >   下面是对Truncate语句在MSSQLServer2000中用法和原理的说明：
   >
   >   Truncate table 表名 速度快,而且效率高,因为:
   >
   >   TRUNCATE TABLE 在功能上与不带 WHERE 子句的 DELETE 语句相同：二者均删除表中的全部行。但 TRUNCATE TABLE 比 DELETE 速度快，且使用的系统和事务日志资源少。
   >
   >   DELETE 语句每次删除一行，并在事务日志中为所删除的每行记录一项。TRUNCATE TABLE 通过释放存储表数据所用的数据页来删除数据，并且只在事务日志中记录页的释放。
   >
   >   TRUNCATE TABLE 删除表中的所有行，但表结构及其列、约束、索引等保持不变。新行标识所用的计数值重置为该列的种子。如果想保留标识计数值，请改用 DELETE。如果要删除表定义及其数据，请使用 DROP TABLE 语句。
   >
   >   对于由 FOREIGN KEY 约束引用的表，不能使用 TRUNCATE TABLE，而应使用不带 WHERE 子句的 DELETE 语句。由于 TRUNCATE TABLE 不记录在日志中，所以它不能激活触发器。
   >
   >   TRUNCATE TABLE 不能用于参与了索引视图的表。
   >
   >5. COMMENT - add comments to the data dictionary 注释
   >
   >6. GRANT - gives user's access privileges to database 授权
   >
   >7. REVOKE - withdraw access privileges given with the GRANT command 收回已经授予的权限

   ​

2. **DML is Data Manipulation Language statements. Some examples:数据操作语言，SQL中处理数据等操作统称为数据操纵语言**

   >1. SELECT - retrieve data from the a database 查询
   >
   >2. INSERT - insert data into a table 添加
   >
   >3. UPDATE - updates existing data within a table 更新
   >
   >4. DELETE - deletes all records from a table, the space for the records remain 删除
   >
   >5. CALL - call a PL/SQL or Java subprogram
   >
   >6. EXPLAIN PLAN - explain access path to data 
   >
   >   Oracle RDBMS执行每一条SQL语句，都必须经过Oracle优化器的评估。所以，了解优化器是如何选择(搜索)路径以及索引是如何被使用的，对优化SQL语句有很大的帮助。Explain可以用来迅速方便地查出对于给定SQL语句中的查询数据是如何得到的即搜索路径(我们通常称为Access Path)。从而使我们选择最优的查询方式达到最大的优化效果。
   >
   >7. LOCK TABLE - control concurrency 锁，用于控制并发

3. **DCL is Data Control Language statements. Some examples:数据控制语言，用来授予或回收访问数据库的某种特权，并控制数据库操纵事务发生的时间及效果，对数据库实行监视等**

   >1. COMMIT - save work done 提交
   >2. SAVEPOINT - identify a point in a transaction to which you can later roll back 保存点
   >3. ROLLBACK - restore database to original since the last COMMIT 回滚
   >4. SET TRANSACTION - Change transaction options like what rollback segment to use 设置当前事务的特性，它对后面的事务没有影响．

## 4. SQL语句详解

### 4.1 SQL的数据定义　DDL

SQL的数据定义部分包括对SQL模式(Schema)、基本表(关系，Table)、视图(View)、索引(Index)的创建或撤销。

1. SQL模式的创建和撤销

   一个SQL模式被定义为基本表的集合，由模式名和模式拥有者的用户名或账号来确定，并包含模式中每个元素(基本表、视图、索引等)的定义，创建了一个SQL模式，就是定义了一个存储空间。

   有时也就直接用数据库代替它

   SQL模式的创建可用语句CREATE实现，其语法是：

   ```sql
   CREATE SCHEMA <模式名>　AUTHORIZATION <用户名>
   # 或
   CREATE DATABASE  <模式名>　AUTHORIZATION <用户名>
   ```

   ​

2. SQL模式的撤销

   当一个SQL模式及其属性的基本表、视图等元素都不需要时，可以使用DROP语句撤销这个SQL模式，DROP语句的语法如下：

   ```sql
   DROP SCHEMA <模式名>　[CASCADE | RESTRICT]
   ```

   CASCADE(连续锁)方式：执行DROP语句时，把SQL模式及其下属的基本表、视图、索引等所有元素全部撤销

   RESTRICT(约束式)方式：执行DROP语句时，只用当SQL模式中没有任何下属元素时，才能将它撤销，否者拒绝执行DROP语句

### 4.2 SQL提供的基本数据类型

1. 数据型

   ```sql
   INTEGER                  长整形(也可以写成INT)
   SMALLINT                 短整形
   REAL                     取决于机器精度的浮点数
   DOUBLE PRECISION         取决于机器精度的双精度浮点数
   FLOAT(n)                 浮点数，精度至少为n位数字
   NUMERIC(p, d)            定点数，由p位数字(不包括符号、小数点)组成，小数点后面有d位数字(也可以写							成DECIMAL(p, d)或DEC(p, d))
   ```

   ​

2. 字符串型

   ```sql
   CHAR(n)                  长度为n的定长字符串
   VARCHAR(n)               具有最大长度的n的变长字符串
   ```

   ​

3. 位串型

   ```sql
   BIT(n)                    长度为n的二进制字符串
   BIT VARYING(n)            最大长度为n的变长二进制位串
   ```

   ​

4. 时间型

   ```sql
   DATE                      日期，包含年、月、日，形为YYYY-MM-DD
   TIME                      时间，包含一日的时、分、秒，形为HH:MM:SS 
   ```

SQL允许在以上的域上执行比较操作，但算术运算只限于数值型



SQL允许用户使用"CREATE DOMAIN"语句**定义新的域**，例如：

```sql
CREATE DOMAIN PERSON_NAME CHAR(10)
```

定义的新域可以被作为基本数据类型看待。

### 4.3 基本表的创建、修改和撤销

在SQL模式下创建基本表

1. 基本表的创建

   创建基本表就是定义基本表的结构，基本表结构的定义可以使用CREATE语句实现

   ```sql
   CREATE TABLE SQL 模式名，基本表名
   (列名　类型，
    ...
    完整性约束，
   ...)
   ```

   完整性约束主要有三种子句：主键子句(PRIMARY KEY)、检查子句(CHECK)和外键子句(FOREINGN KEY)

   如，有如下三个关系：

   供应商关系：S($\underline{SNO}$, SNAME, SADDR)

   零件关系： P($\underline{PNO}$, PNAME, COLOR, WEIGHT)

   供应情况关系：SPJ($\underline{SNO}$, $\underline{PNO}$, PRICE, QTY)

   对于第一个和第三个关系，其创建语句如下：

   ```sql
   CREATE TABLE S
   	(SNO CHAR(4) NOT NULL,
        SNAME CHAR(20) NOT NULL,
        SADDR CHAR(10),
        PRIMARY KEY(SNO));


   CREATE TABLE SPJ
   	(SNO CHAR(4) NOT NULL,
        PNO CHAR(4) NOT NULL,
        PRICE NUMERIC(7,2),
        QTY SMALLINT,
        PRIMARY KEY(SNO, PNO),　　　　　　　　　　　 # 主键必定非空，实体完整性
        FOREIGN KEY(SNO) REFFERENCES S(SNO)　　　　
        FOREIGN KEY(PNO) REFFERENCES P(PNO)　　　　# 外键体现了参照完整性
        CHECK(QTY BETWEEN 0 AND 100000));
   ```

   对于表S，加NOT NULL可以规定某个属性不能为空，由于主键是SNO，所以对于SNO的定义可以不加NOT NULL。CKECK语句比较复杂，功能比较多。

2. 基本表结构的修改

   > 1. 增加新的属性用“ALTER ... ADD ...”语句，语法如下：
   >
   >    ```sql
   >    ALTER TABLE 基本表名(S) ADD 新属性名(TELE) 新属性名(CHAR(12));
   >    ```
   >
   >    注意：新增加的属性不能定义为"NOT NULL"，原有元组在这个新属性上的取值都为NULL
   >
   > 2. 删除原有的属性用"ALTER ... DROP ..."语句，语法如下：
   >
   >    ```sql
   >    ALTER TABLE 基本表名　DROP 属性名　[CASCADE | RESTRICT]
   >    ```
   >
   >    CASCADE方式：在删除某属性时，所有引用到该属性的视图或约束也要一起自动的删除
   >
   >    RESTRICT方式：只有在没有视图或约束引用到该属性的前提下才能删除这个属性
   >
   > 3. 撤销基本表可以使用"DROP TABLE"语句，在撤销一个基本表后，其所有数据也就丢失了。
   >
   >    ```sql
   >    DROP TABLE 基本表名　[CASCADE | RESTRICT]
   >    ```
   >
   >    CASCADE和RESTRICT的用法与上述类似

### 4.4 视图的创建和撤销

在SQL中，外模式一级数据结构的基本单位时视图(View)，视图从若干基本表或其他视图构建出来，这种构建方法采用后述的SELECT语句来实现，。**在创建一个视图时，系统把视图的定义放在数据字典中，而并不存储图对应的数据，在用户使用视图时才会去求相应的数据**。因此，视图被称为"虚表"。

> 1. 视图的创建
>
>    创建视图可用"CREATE VIEW"语句实现：
>
>    ```sql
>    CREATE VIEW 视图名　(列表名)
>    AS SELECT 查询语句
>    ```
>
>    如下：
>
>    ```sql
>    CREATE VIEW JSP_NAME (JNO, JNAME, SNO, SNAME, PNO, PANEM, QTY)
>    	AS SELECT J.JNO,JNAME,S.SNO,SNAME,P.PNO,PNAME,QTY
>    	FROM S, P, J, SPJ
>    	WHERE S.SNO=SPJ.SNO
>    	  AND P.PNO=SPJ.PNO
>    	  AND J.JNO=SPJ.JNO
>    ```
>
>    ​
>
> 2. 视图撤销
>
>    ```sql
>    DROP VIEW 视图名;
>    ```

### 4.5 SQL的数据查询

1. SELECT语句格式

在关系代数中，最常用的是下述表达式：

​		　　　　　　　　$π_i,j$($σ_F$($R_1$X...X$R_m$)) 

这里：$R_1$...$R_m$是关系，F是公式，i,j是属性

针对上述的表达式，SQL设计的SELECT-FROM-WHERE句型如下：

```sql
SELECT i,j
FROM R1...Rm
WHERE F
```

在WHERE中F可以使用的运算符有：

> 1. 算术运算符：<, <=, >, >=, <>或!=
> 2. 逻辑运算符：AND, OR, NOT
> 3. 集合成员资格运算符：IN, NOT IN
> 4. 谓词：EXISTS, ALL, SOME, UNIQUE, LIKE
> 5. 聚合函数：AVG(平均值), MIN, MAX, SUM, COUNT
> 6. 还可以是其它SELECT语句的嵌套
> 7. IS NULL, BETWEEN .... AND...., 

2. SELECT语句的句法

   SELECT语句的完整句法如下：

   ```sql
   SELECT [DISTINCT] 目标表的列名或列表达式序列（全部属性可以用*来表示）
   FROM 基本表名(或)视图序列表|表引用
   [ WHERE 行条件表达式 ]
   [ GROUP BY 列名序列
    	[ HAVING 组条件表达式　]]
   [ ORDER BY 列名　[ ASC|DESC], ... ]
   ```

   整个语句的执行过程如下：

   > 1. 读取FROM子句中基本表、视图的数据，执行笛卡儿积操作(或读取表引用所返回的查询结果或多表联接的结果)
   > 2. 选取满足WHERE子句中给出的条件表达式的元组
   > 3. 按GROUP子句中指定列的值分组，同时提取满足HAVING子句中组条件表达式的那些组
   > 4. 按SELECT子句中给出的列名或列表达式求值输出
   > 5. ORDER子句对输出的目标表进行排序，按附加说明ASC升序排列，或按DESC降序排列

   SELECT语句中，WHERE子句称为"行条件子句"，GROUP子句称为"分组子句"，HAVING子句称为"组条件子句"，ORDER子句称为"排序子句"

3. 联接操作

   联接条件可在WHERE中指定，也可以在FROM子句中指定。

   ​									联接类型及其说明：

   |       连接类型       |                    说明                    |
   | :--------------: | :--------------------------------------: |
   |    INNER JOIN    |           内联接：结果为两个联接表中的匹配行的联接           |
   | LEFT OUTER JOIN  | 左外联接：结果包括左表（出现在JOIN子句的左边）中的所有行，不包括右表中的不匹配行 |
   | RIGHT OUTER JOIN | 右外联接：结果包括右表（出现在JOIN子句的右边）中的所有行，不包括左表中的不匹配行 |
   | FULL OUTER JOIN  |      完全外联接：结果包括所有联接表中的所有行，不论它们是否匹配       |
   |    CROSS JOIN    | 交叉联接：结果包括两个联接表中所有可能的行组合，交叉联接返回的是两个表的笛卡儿积 |

   ​								联接条件和说明

   |  连接条件   |  说明  |
   | :-----: | :--: |
   | ON　联接条件 |      |

   ​

4. ​









