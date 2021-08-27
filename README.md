

<font color=red size=5>文章链接</font>

~~~bash
https://gitee.com/fakerlove/database-management-system
~~~



# 数据库系统概论-第五版





# 1. 绪论

## 1.1. 数据库4个基本概念

### 1.1.1. 数据

> 描述事物的符号记录，数据与其语义是不可分的。

### 1.1.2. 数据库

> 数据库是长期存储在计算机内、有组织的、可共享的大量数据的集合。
> **数据库中数据基本特点**：永久存储、有组织和可共享三个基本特点。**数据库中数据**都是按照某一种数据模型来组织、描述和存储的。

### 1.1.3. 数据库管理系统(DBMS)

> 科学地组织和存储数据，高效的获取和维护数据。
>
> 是位于用户和操作系统之间的一层数据管理软件

主要功能：

1. 数据定义功能
2. 数据组织、存储和管理功能
3. 数据操纵功能
4. 数据库的事务管理和运行管理
5. 数据库的建立和维护功能
6. 其他功能（例如通信功能等）

### 1.1.4 数据库系统(DBS)

> 数据库系统是由数据库DB、数据库管理系统DBMS（及其应用开发工具）、应用程序和数据库管理员组成的存储、管理、处理和维护数据的系统

## 1.2. 数据管理

> 对数据进行**分类、组织、编码、存储、检索和维护**，它是数据处理的中心问题。数据处理是指对各种数据进行收集、存储、加工和传播的一系列活动的总和。

### 1.2.1 发展过程

人工管理阶段、文件系统阶段、数据库系统阶段

### 1.2.2 三个阶段对比

| 特点           | 人工管理阶段       | 文件系统阶段             | 数据库系统阶段                                 |
| -------------- | ------------------ | ------------------------ | ---------------------------------------------- |
| 管理者         | 程序员             | 文件系统                 | 数据库管理系统                                 |
| 数据面向对象   | 某一应用程序       | 某一应用                 | 部门企业                                       |
| 数据的共享程度 | 无共享，冗余度极大 | 共享性差，冗余度答       | 共享性高，冗余度低                             |
| 数据独立性     | 不独立             | 独立性差                 | 具有高度的物理独立性和一定的逻辑独立性         |
| 数据结构化     | 无结构             | 记录内有结构、整体无结构 | 整体结构化，用数据模型描述                     |
| 数据控制能力   | 应用程序自己控制   | 应用程序自己控制         | DBMS提供数据安全性、完整性、并发控制和恢复能力 |

### 1.2.3 数据库系统特点

1. 数据结构化（与文件系统的本质区别）

2. 共享性高，冗余度低且易扩展

3. 数据独立性高（独立性指应用程序与逻辑结构、物理存储相互独立）

   不会因为系统数据存储结构与数据逻辑结构的变化而影响应用程序

4. 数据统一管理和控制

   数据的安全性保护，数据的完整性检查，并发控制和数据库的恢复

### 1.2.4 使用数据库系统好处

1. 使用数据库系统可以大大提高应用开发的效率
2. 当数据逻辑结构需要改变是，开发人员不必修改应用程序，或者只需要修改很少一部分
3. 使用数据库系统可以减轻DBA维护系统的负担

## 1.3. 数据模型

> 数据模型是数据库用来对现实世界进行抽象的的工具，是数据库中用于提供信息表示和操作手段的形式框架
>
> **数据模型的数据库系统的核心和基础**

### 1.3.1. 数据模型分类

#### 概念模型

> 表示方法，实体-联系方法，该方法用E-R 图来描述现实世界的概念模型，E-R方法也称为E-R 模型

+ 实体

  客观存在并可相互区别的事务称为实体

+ 属性

  实体所具有的某一特性称为属性

+ 码

  唯一标识实体的属性集称为码

+ 实体型

  用实体名及其属性集合来抽象和刻画同类实体，称为实体性

+ 实体集

  同一类型实体的集合称为实体集

+ 联系

  实体之间的联系通常是指不同实体集之间的联系



#### 逻辑模型和物理模型

* 第二类中的逻辑模型：**层次模型、网状模型、关系模型**、面向对象数据模型、对象关系数据模型、半结构化数据模型等
* 第二类中的物理模型：是对数据最底层的抽象。描述了数据在系统内部的表示方式和存取方法



### 1.3.2. 数据模型的三大组成要素

* 数据结构

  描述数据库的组成对象以及对象之间的联系

* 数据操作

  数据操作是指对数据库中各种对象型的实例值允许执行的操作的几个，包括操作及有关的操作规则

* 数据的完整性约束条件

  数据的完整性约束是一族完整性的规则

### 1.3.3. 各模型优缺点

#### 层次模型

> * 像一颗倒立的树，结点的双亲是唯一的
>
> * 有且只有一个结点没有双亲结点，这个结点称为根结点
> * 根以外的其他结点有且只有一个双亲结点两个条件的记录以及它们之间联系的集合为层次模型

优点：

1. 数据结构简单清晰
2. 查询效率高
3. 提供了良好的完整性支持

缺点：

1. 现实世界中很多联系时非层次化的
2. 程序编写复杂，如果一个节点具有多个双亲节点，只能引入冗余数据。插入删除限制多
3. 查询子女节点必须通过双亲节点
4. 由于结构严密，层次命令趋向于结构化

#### 网状模型

> 典型的代表是DBTG 系统

特点

* 允许多个结点没有双亲结点
* 允许一个结点有多个双亲结点
* 允许两个结点之间有多种联系
* 要为每个联系命名并指出该联系有关的双亲记录和子女记录

优点：

1. 能够更为直接的描述现实世界
2. 具有良好的性能，存取效率较高

缺点：

1. 结构比较复杂
2. 语言复杂，不好掌握使用
3. 用户需要了解系统结构的细节，因为联系是通过存取路径实现的

#### 关系模型

特点

* 关系模型要求关系必须是规范化
* 关系的每一个分量必须是一个不可分的数据项
* 操作对象和操作结果都是关系
* 关系模型把存取路径向用户隐蔽起来，用户只要指出干什么或找什么，不必详细说明怎么干或怎么找

优点：

1. 建立在严格的数据概念基础上
2. 概念单一
3. 存取路径对用户透明，简化工作

缺点：

存取路径隐蔽，导致查询效率不高，为了提升性能，DMBS必须对用户查询请求进行优化

## 1.4. 数据库系统的结构

### 1.4.1. 数据库系统模式的概念

> 模式是数据库中全体数据的**逻辑结构和特征的描述**，它仅仅涉及型(type)的描述，不涉及具体的值。模式的一个具体值称为模式的一个实例。

### 1.4.2. 三级模式结构

> 模式、外模式、内模式

#### 模式

模式也称逻辑模式，是数据库中**全体数据**的*逻辑结构和特征的描述*，是所有用户的公共数据视图

#### 外模式

外模式也称用户模式，它是数据库用户能够看见和使用的**局部数据**的*逻辑结构和特征的描述*。是数据库用户的数据视图，是与某一应用有关的数据的逻辑表示。

一个数据库可以有多个外模式。即使对模式中的同一种数据，在外模式的结构中，类型，长度，保密级别都可以不同

#### 内模式

+ 也称存储模式，一个数据库只有一个内模式。它是**数据物理结构和存储方式的描述**，是数据在数据库内部的组织方式。

+ 索引的组织方式

  B+树，Bitmap，Hash

+ 记录的存储方式

  顺序存储，堆存储，按hash 方法存储



在数据库系统中，通常用三级模式来描述数据库，其中外模式是用户与数据库的接口，是应用程序可见到的数据描述，概念模式是对数据整体的逻辑结构的描述，而内模式描述了数据的物理结构

### 1.4.3. 数据库的二级映像功能与数据独立性



* 外模式/模式映像
  模式改变，对映象做修改，可以保证外模式不变，保证了**逻辑独立性**。

  + 保证数据的逻辑独立性

    当模式改变时，数据库管理员对外模式/模式映像作相应改变，使外模式保持不变

    应用程序是依据数据的外模式编写的，应用程序不必修改与程序的逻辑独立性，简称数据的逻辑独立性

  + 有一个外模式/模式映像定义外模式与模式之间的对应关系，映像定义通常包含在个外模式的描述中

* 模式/内模式映象
  内模式改变（数据库的存储结构改变），对映象做修改，可以保持模式不变，保证了**物理独立性**。



## 1.5. 数据库系统的组成

1. 数据库是由数据库、数据库管理系统(及其开发工具)、应用程序、数据库管理员组成
2. 硬件平台及数据库、软件、人员



# 2. 关系数据库

> 按照数据模型三要素，关系模型由数据结构、关系操作集合和关系完整性约束三部分组成
>
> acid 原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）.

## 2.1. 关系模型数据结构及形式化定义

![](https://gitee.com/fakerlove/picture_1/raw/master/20200325210436333.png)

> 关系模型的数据结构非常简单，只包含单一的数据结构——关系

### 2.1.1. 关系

> 关系是关系模式某一时刻的内容或状态
>
> 关系在域上D笛卡尔积的子集
> 关系可以有三种类型：**基本关系（基本表）、查询表、试图表。**

* **域**

  域是一组具有相同数据类型的值的集合

* 笛卡尔积

  $给定一组域D_1,D_2,D_3,D_n的笛卡尔积为D_1*D_2*D_3=\{d_1,d_2,d_n\}$

  每一个元素$(d_1,d_2,d_3)叫做一个元组，每一个元素中的每一个值d_i叫做一个分量$

  一个域允许的不同取值个数称为这个域的基数



#### 1) 基本关系

有6 条性质

* 列是同质的，即每一列中的分量是同一类型的数据
* 不同列可能出自同一个域，称其中的每一列为一个属性，不同的属性要给予不同的属性名
* 列的顺序是无所谓的，即列的次序可以任意交换
* 任意两个元祖的候选码不能去相同的值
* 行的顺序也是 无所谓的
* 分量必须取原子值，即每一个分量都必须是不可分的数据项

#### 2) 查询表

#### 3) 视图表

### 2.1.2. 关系模式

> 关系的描述称为关系模式 ，可形式化的表示为**R(U,D,DOM,F)**
> 其中R为关系名，U为组成该关系的属性名集合，D为U中属性所来自的域，DOM为属性向域的映象集合，F为属性间数据的依赖关系集合。

组成部分

* 关系数据结构
* 关系操作
* 关系的完整性约束

### 2.1.3 关系数据库

>
> 关系数据库：关系数据库也有型和值之分，型是关系模式，是对关系数据库的描述。值是关系模式在某一时刻对应的关系集合。

区别

* 关系模式：对关系的描述称为关系模式，可以形式化表示为R(U,D,DOM,F)
* 关系：是关系模式某一时刻的状态或者内容，关系模式是静态的，而关系是动态的。

### 2.1.4. 关系模式与关系的区别

关系模式是型；关系是值，是关系模式的实例。
例如S(num,name,age)是关系模式，组成的表是关系，即某一时刻关系模式的值

- **关系模式**
  对关系的描述
  静态的、稳定的
- **关系**
  关系模式在某一时刻的状态或内容动态的、随时间不断变化的关系模式和关系往往统称为关系
- `在数据库学科中可以把关系模式理解为表的结构、属性之间的关系、约束条件，把关系理解为二维表`

## 2.2. 关系操作



![](https://gitee.com/fakerlove/picture_1/raw/master/20200325225006454.png)



### 2.2.1 基本操作

**查询操作**： 选择、投影、连接、除、并、差、交、笛卡尔积
选择、投影、并、差、笛卡尔积是五种基本操作
**数据更新**：插入、删除、修改

### 2.2.2 关系数据语言的分类

#### 1) 关系代数

关系代数是用关系的运算来表达查询要求，代表：ISBL；

#### 2) 关系演算

关系演算语言用谓词来表达查询要求；关系演算又可按照谓词变元的基本对象是元组变量还是域系变量分为元组关系演算和域关系演算

- **元组关系演算语言**
  谓词变元的基本对象是元组变量；
  代表：APLHA, QUEL；
- **域关系演算语言**
  谓词变元的基本对象是域变量；
  代表：QBE；

#### 3) 结构化查询语言

具有关系代数和关系演算双重特点的语言；
代表：SQL（Structured Query Language） ；



## 2.3. 关系完整性约束 

### 1) 实体完整性约束-主键约束

若属性A是基本关系R的主属性，则属性A不能取空值

### 2) 参照完整性约束-外键约束

##### 外码（Foreign Key）

- 设F是基本关系R的一个或一组属性，但不是关系R的码。如果F与基本关系S的主码Ks相对应，则称F是基本关系R的`外码`,即该码是另一个表的主码。
- 基本关系R称为`参照关系`（Referencing Relation），即本表。
- 基本关系S称为`被参照关系`（Referenced Relation） 或`目标关系`（Target Relation），即外码对应的主码所在的表。

若属性F是基本关系R的外码，它与基本关系S的主码K相对应，则对R中的每个元组在F上的值，必须为空值或者S中某个元组的主码值

若属性（或属性组）F是基本关系R的外码它与基本关系S的主码Ks相对应（基本关系R和S不一定是不同的关系），则对于R中每个元组在F上的值必须为：

- 或者取空值（F的每个属性值均为空值）

- 或者等于S中某个元组的主码值

- 外码的值要么为空，要么为S中某个元组的主码值
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200325213436384.png)

  例2

  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200325213454494.png)

  例3

  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200325213733135.png)

### 3) 用户定义的完整性约束

* 性针对某一具体关系数据库的约束条件。它反映了某一具体应用所涉及的数据必须满足的语义要求。

- 针对某一具体关系数据库的约束条件，反映某一具体应用所涉及的数据必须满足的语义要求
- 关系模型应提供定义和检验这类完整性的机制，以便用统一的系统的方法处理它们，而不要由应用程序承担这一功能

## 2.4. 关系代数

> 关系代数运算是以集合运算为基础的运算

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2019070222234085.png)

### 2.4.1 传统的集合运算

#### 并

![image](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123141654-1604480583.png)

举例

 ![image](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123142717-1747513796.png)

#### 差

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123143498-200778541.png)

举例

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123144342-726634882.png)

#### 笛卡尔积

> R和S 具有相同的元数，且对应的属性的类型也相同
>
> 下面是RxS的结果，R和S使用上图中的R，S

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123145154-798312210.png)



#### 交

> 即属于R又属于S的元组(行)组成

### 2.4.2 专门的关系运算

#### 选择

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123146732-289507973.png)

举例

> 选择出满足条件的元组的操作叫做选择
>
> 选择A2值为a或b的元祖

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123147498-1130626773.png)

![](https://gitee.com/fakerlove/picture_1/raw/master/872539-20161020123148123-905080733.png)





#### 投影

> 关系R上的投影是从R上选择出若干属性列出组成新的关系

#### 连接

> $连接也被\theta 连接，它是从两个关系的笛卡尔积中选取属性满足一定条件的元组$
>

连接运算中有两种最重要也是最为常用的连接，一种是等值连接，一种是自然连接

* $\theta 为"=" 的连接运算称为等值连接$

  从广义笛卡尔积中选取A,B 属性值相等的那些元组

* 自然连接是一种特殊的等值连接

  要求两个关系中进行比较的分量必须是同名的属性，且在结果中把重复的属性列去掉



#### 除

> 设关系R除以关系S的结果为关系T,则T包含所有在R但不在S上的属性及其值，且T的元组与S的元组的所有组合都在R中

## 2.5 关系演算

### 2.5.1 元组关系演算语言



### 2.5.2 元组关系演算







# 3. 数据库标准语言SQL



## 3.1. SQL概述

![](https://gitee.com/fakerlove/picture_1/raw/master/20200331221423732.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20190702222134134.png)

### 3.1.1. SQL特点

**① 综合统一**

- 集数据定义语言 DDL(Data Definition Language)，数据操纵语言 DML（Data Manipulation Language），数据控制语言 DCL(Data Control Language) 功能于一体。
- 可以独立完成数据库生命周期中的全部活动：
  - 定义关系模式，插入数据，建立数据库；
  - 对数据库中的数据进行查询和更新；
  - 数据库重构和维护
  - 数据库安全性、完整性控制等
- 用户数据库投入运行后，可根据需要随时逐步修改模式，不影响数据的运行。
- 数据操作符统一

**② 高度非过程化**

- 非关系数据模型的数据操纵语言“面向过程”，必须制定存取路径
- SQL只要提出“做什么”，无须了解存取路径。
- 存取路径的选择以及SQL的操作过程由系统自动完成。

**③ 面向集合的操作方式**

- 非关系数据模型采用面向记录的操作方式，操作对象是一条记录
- SQL采用集合操作方式：
  - 操作对象、查找结果可以是元组的集合
  - 一次插入、删除、更新操作的对象可以是元组的集合

**④ 以同一种语法结构提供多种使用方式**

- SQL是独立的语言
  - 能够独立地用于联机交互的使用方式
- SQL又是嵌入式语言
  - SQL能够嵌入到高级语言（例如C，C++，Java）程序中，供程序员设计程序时使用

**⑤ 语言简洁，易学易用**

- SQL功能极强，完成核心功能只用了9个动词。

| SQL功能  | 动词                   |
| -------- | ---------------------- |
| 数据查询 | SELECT                 |
| 数据定义 | CREATE、DROP、ALTER    |
| 数据操纵 | INSERT、UPDATE、DELETE |
| 数据控制 | GRANT、REVOKE          |

### 3.1.2. 基本概念

- SQL支持关系数据库三级模式结构

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331110731265.png)
**基本表**

- 本身独立存在的表
- SQL中一个关系就对应一个基本表
- 一个(或多个)基本表对应一个存储文件
- 一个表可以带若干索引

**存储文件**

- 逻辑结构组成了关系数据库的内模式
- 物理结构是任意的，对用户透明

**视图**

- 从一个或几个基本表导出的表
- 数据库中只存放视图的定义而不存放视图对应的数据
- 视图是一个虚表
- 用户可以在视图上再定义视图

### 3.1.3 数据字典

- `数据字典`是`关系数据库管理系统内部`的一组`系统表`，`它记录了数据库中所有的定义信息，包括关系模式定义、视图定义、索引定义、完整性约束定义、各类用户对数据库的操作权限、统计信息等`。
- 关系数据库管理系统在执行SQL的数据定义语句时，实际上就是在更新数据字典表中的相应信息。
- 在进行查询优化和查询处理时，数据字典中的信息是其重要依据。



## 3.2. 数据定义

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20190702222236757.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20190702222247274.png)



**没有那种数据库支持所有的sql和特性**

### 3.2.1 数据定义概览

SQL的数据定义功能: `模式定义`、`表定义`、`视图`和`索引`的定义

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331111801271.png)

### 3.2.2 SCHEMA

**定义模式实际上定义了一个`命名空间`**

- 在这个`空间`中可以`定义`该`模式`包含的`数据库对象`，例如`基本表`、`视图`、`索引`等。
- 在CREATE SCHEMA中可以接受CREATE TABLE，CREATE VIEW和GRANT子句。
- `CREATE SCHEMA <模式名> AUTHORIZATION <用户名>[<表定义子句>|<视图定义子句>|<授权定义子句>]`
- 如果没有指定<模式名>，那么<模式名>隐含为<用户名>

#### ① 定义模式

> dbo database owner 数据库的创建者,创建该对象的用户. guest 顾客 能够访问数据库中对象的数据, 要求dbo分配权限给guest, 一般给他查看的权限select

- 这里我先创建一个数据库用户：
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331182533348.png)

**[例1]定义一个学生-课程模式S-T**

```sql
CREATE SCHEMA "S-T" AUTHORIZATION BitHachi; -- 为用户BitHachi定义了一个模式S-T
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331181949185.png)

- 如果没有指定<模式名>，那么<模式名>隐含为<用户名>

```sql
CREATE SCHEMA AUTHORIZATION BitHachi；-- <模式名>隐含为用户名BitHachi 这个不知道咋回事，没出结果，默认模式BitHachi没创建出来，没显示
```

**[例2]为用户BitHachi创建了一个模式S-T，并在其中定义了一个表TAB1。**

```sql
CREATE SCHEMA "S-T" AUTHORIZATION BitHachi
CREATE TABLE TAB1(
COL1 SMALLINT, 
COL2 INT,
COL3 CHAR(20),
COL4 NUMERIC(10,3),
COL5 DECIMAL(5,2)
);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331183828758.png)

#### ② 删除模式

- `DROP SCHEMA <模式名> <CASCADE|RESTRICT>`
- `CASCADE(级联)`
  删除模式的同时把该模式中所有的数据库对象全部删除
- `RESTRICT(限制)`
  如果该模式中定义了下属的数据库对象（如表、视图等），则拒绝该删除语句的执行。
- 当该模式中没有任何下属的对象时才能执行。
- 以下是运行结果，至于为什么是错误的，暂且放在这里，等熟悉相关知识之后，再来解决。

```sql
DROP SCHEMA "S-T" CASCADE;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331185339714.png)

```sql
DROP SCHEMA "S-T" RESTRICT;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331185358937.png)

### 3.2.3 TABLE

#### ① 定义基本表的标准格式

```sql
CREATE TABLE <表名>(
      <列名> <数据类型>[ <列级完整性约束条件> ]
      [，<列名> <数据类型>[ <列级完整性约束条件>] ]
       ………
      [，<表级完整性约束条件> ]
 );
```

- `如果完整性约束条件涉及到该表的多个属性列，则必须定义在表级上，否则既可以定义在列级也可以定义在表级。`

#### ② 数据类型

- SQL中`域`的概念用`数据类型`来实现
- 定义表的`属性`时 需要指明其`数据类型及长度`
- 选用哪种数据类型
  - 取值范围
  - 要做哪些运算
- 以下是通用数据类型，不同数据库的数据类型可能有所不同，可查相关文档。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331204116766.png)

#### ③ 修改基本表

```sql
ALTER TABLE <表名>
[ ADD <新列名> <数据类型> [ 完整性约束 ] ]
[ DROP <完整性约束名> ]
[ ALTER COLUMN<列名> <数据类型> ];
```

**[例8]向Student表增加“入学时间”列，其数据类型为日期型。**

- 不论基本表中原来是否已有数据，新增加的列一律为空值。

```sql
ALTER TABLE Student ADD S_entrance DATE;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331204924961.png)

**[例9]将年龄的数据类型由字符型（假设原来的数据类型是字符型）改为整数。**

```sql
ALTER TABLE Student ALTER COLUMN Sage INT;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/202003312058252.png)
**[例10]增加课程名称必须取唯一值的约束条件。**

```sql
ALTER TABLE Course ADD UNIQUE(Cname);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331210051649.png)

#### ④ 删除基本表

**标准格式：**
`DROP TABLE <表名>［RESTRICT| CASCADE］；`

- ```
  RESTRICT
  ```

  ：删除表是有限制的。

  - 欲删除的基本表不能被其他表的约束所引用
  - 如果存在依赖该表的对象，则此表不能被删除

- ```
  CASCADE
  ```

  ：删除该表没有限制。

  - 在删除基本表的同时，相关的依赖对象一起删除

**[例11] 删除Student表**

- 基本表定义被删除，数据被删除

- 表上建立的索引、视图、触发器等一般也将被删除

- 还是和上述删除模式情况一样，加了CASCADE和RESTRUCT删除不了

  ```sql
    DROP TABLE  Student  CASCADE ;
  ```

**［例12］若表上建有视图，选择RESTRICT时表不能删除**

```sql
    CREATE VIEW IS_Student      
	AS 
	    SELECT Sno,Sname,Sage
	    FROM  Student
    	    WHERE Sdept='IS';
	 DROP TABLE Student RESTRICT;   
456
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331211031754.png)

```
--ERROR: cannot drop table Student because other objects depend on it
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331211422875.png)

**[例12]如果选择CASCADE时可以删除表，视图也自动被删除**

- 这里还是跟之前的情况一样，删除不了，可能是我用的数据库不同叭

```sql
	DROP TABLE Student CASCADE; 	    
 --NOTICE: drop cascades to view IS_Student
	SELECT * FROM IS_Student;
--ERROR: relation " IS_Student " does not exist 
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331212048889.png)

### 3.2.4 INDEX

**建立索引的目的：`·加快查询速度·`**

- 谁可以建立索引？
  - DBA 或 表的属主（即建立表的人）
  - DBMS一般会自动建立以下列上的索引
  - PRIMARY KEY
  - UNIQUE
- 谁维护索引？
  DBMS自动完成
- 使用索引
  DBMS自动选择是否使用索引以及使用哪些索引
- RDBMS中索引一般采用B+树、HASH索引来实现
  - B+树索引具有动态平衡的优点
  - HASH索引具有查找速度快的特点
- 采用B+树，还是HASH索引 则由具体的RDBMS来决定
- 索引是关系数据库的内部实现技术，属于内模式的范畴
- `CREATE INDEX`语句定义索引时，可以定义索引是`唯一索引、非唯一索引或聚簇索引`

#### ① 建立索引的标准格式

**语句格式**

```sql
CREATE [UNIQUE] [CLUSTER] INDEX <索引名> 
ON <表名>(<列名>[<次序>][,<列名>[<次序>] ]…);
```

**[例13]**

```sql
CREATE CLUSTERE INDEX Stusname ON   Student(Sname);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331213415383.png)

- 在Student表的Sname（姓名）列上建立一个`聚簇索引`
- 在最经常查询的列上建立聚簇索引以提高查询效率
- `一个基本表上最多只能建立一个聚簇索引`
- 经常更新的列不宜建立聚簇索引

**[例14]为学生-课程数据库中的Student，Course，SC三个表建 立索引。**

- Student表按学号升序建唯一索引
- Course表按课程号升序建唯一索引
- SC表按学号升序和课程号降序建唯一索引

```sql
CREATE UNIQUE INDEX  Stusno ON Student(Sno);
CREATE UNIQUE INDEX  Coucno ON Course(Cno);
CREATE UNIQUE INDEX  SCno ON SC(Sno ASC,Cno DESC);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331213840821.png)

#### ② 删除索引

**`DROP INDEX <索引名> ON <表名>;`
`DROP INDEX <表名>.<索引名>;`**

- 删除索引时，系统会从数据字典中删去有关该索引的
  描述。

**[例15] 删除Student表的Stusname索引**

```sql
   DROP INDEX Stusno ON Student;
   //等价
   DROP INDEX Student.Stusno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200331214610775.png)

## 3.3. 数据查询

![](https://gitee.com/fakerlove/picture_1/raw/master/20200329000307604.png)



### 3.3.1 表数据及结构

- 本篇文章都是围绕这三个表展开的。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032813213186.png)

### 3.3.2 SELECT语句的一般格式

先从整体上了解一下SELECT的格式，关键字的位置。

```sql
SELECT [ALL|DISTINCT]   
<目标列表达式> [别名] [ ，<目标列表达式> [别名]] … 
FROM   <表名或视图名> [别名]   [ ，<表名或视图名> [别名]] …
[WHERE <条件表达式>]
[GROUP  BY<列名1>
[HAVING  <条件表达式>]]
[ORDER BY <列名2> [ASC|DESC] 
4567
```

### 3.3.4 单表查询

#### 1) 选择表中的若干列

##### ① 查询指定列

- `查询指定列`

**[例1] 查询全体学生的学号与姓名。**

```sql
SELECT Sno,Sname 
FROM Student;
12
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328135208205.png)

**[例2] 查询全体学生的姓名、学号、所在系。**

```sql
SELECT Sname,Sno,Sdept 
FROM Student;
12
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328135455514.png)

##### ② 查询全部列

- 选出所有属性列：在SELECT关键字后面列出所有列名 ，将<目标列表达式>指定为 *

**[例3] 查询全体学生的详细记录。**

```sql
SELECT  Sno,Sname,Ssex,Sage,Sdept 
FROM Student;
//两种方式
SELECT  *FROM Student;
4
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328135818333.png)

##### ③ 查询经过计算的值

- `SELECT子句的<目标列表达式>可以为：`
  算术表达式
  字符串常量
  函数
  列别名

###### ❶ 算术表达式

**[例4] 查全体学生的姓名及其出生年份。这里假定目前年份是2004年。**

```sql
SELECT Sname,2004-Sage 
FROM Student;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032814033625.png)

###### ❷ 字符串常量及函数

**[例5] 查询全体学生的姓名、出生年份和所有系，要求用小写字母表示所有系名，这里假定目前年份是2004年。**

```sql
 SELECT Sname,'Year of Birth: ', 2004-Sage, LOWER(Sdept)
 FROM Student;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328141350942.png)

###### ❸ 使用列别名改变查询结果的列标题

```sql
SELECT Sname NAME,'Year of Birth: '  BIRTH,
2000-Sage  BIRTHDAY,
LOWER(Sdept)  DEPARTMENT
FROM Student;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328160601977.png)

#### 2) 选择表中的若干元组（行）

##### ① 关键词DISTINCT去掉表中重复的行

- 如果没有指定DISTINCT关键词，则缺省为ALL

```sql
SELECT Sno FROM SC;
/*等价于：*/
SELECT ALL  Sno  FROM SC;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328161832665.png)
**[例6] 查询选修了课程的学生学号。指定`DISTINCT`关键词，去掉表中重复的行**

```sql
SELECT DISTINCT Sno
FROM SC;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328162001839.png)

##### ② 查询满足条件的元组（行）

- 常用的查询条件

| 查询条件             | 谓词                                                |
| -------------------- | --------------------------------------------------- |
| 比较                 | =，>，<，>=，<=，!=，<>，!>，!<；NOT+上述比较运算符 |
| 确定范围             | BETWEEN AND，NOT BETWEEN AND                        |
| 确定集合             | IN，NOT IN                                          |
| 字符匹配             | LIKE，NOT LIKE                                      |
| 空值                 | IS NULL，IS NOT NULL                                |
| 多重条件（逻辑运算） | AND，OR，NOT                                        |

###### ❶ 比较大小

**[例7]查询计算机科学系全体学生的名单。**

```sql
SELECT Sname
FROM Student
WHERE Sdept='CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032816282199.png)
**[例8] 查询所有年龄在20岁以下的学生姓名及其年龄。**

```sql
SELECT Sname,Sage 
FROM Student 
WHERE Sage < 20;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328162928740.png)
**[例9]查询考试成绩有不及格的学生的学号。**

```sql
SELECT DISTINCT Sno
FROM  SC
WHERE Grade<60;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328163026662.png)

###### ❷ 确定范围

**谓词:**

- `BETWEEN … AND …`
- `NOT BETWEEN … AND …`

**[例10] 查询年龄在20~23岁（包括20岁和23岁）之间的学生的**

```sql
SELECT Sname,Sdept,Sage
FROM  Student
WHERE Sage 
BETWEEN 20 AND 23; 
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328163244178.png)
**[例11] 查询年龄不在20~23岁之间的学生姓名、系别和年龄**

```sql
SELECT Sname,Sdept,Sage
FROM  Student
WHERE Sage NOT BETWEEN 20 AND 23;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328163336398.png)

###### ❸ 确定集合

**谓词：**

- `IN <值表>,`
- `NOT IN <值表>`

**[例12]查询信息系（IS）、数学系（MA）和计算机科学系（CS）学生的姓名和性别。**

```sql
SELECT Sname,Ssex
FROM  Student
WHERE Sdept IN ( 'IS','MA','CS' );
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328163512481.png)
**[例13]查询既不是信息系、数学系，也不是计算机科学系的学生的姓名和性别。**

```sql
SELECT Sname,Ssex
FROM Student
WHERE Sdept NOT IN ( 'IS','MA','CS' );
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032816395250.png)

###### ❹ 字符匹配

**谓词：**

- `[NOT] LIKE ‘<匹配串>’ [ESCAPE ‘ <换码字符>’]`

**`匹配串为固定字符串`**
**[例14] 查询学号为201215121的学生的详细情况。**

```sql
SELECT *    
FROM  Student  
WHERE  Sno LIKE '201215121';
/*等价于：*/ 
SELECT  * 
FROM  Student 
WHERE Sno = '201215121';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328164503545.png)

**`匹配串为含通配符的字符串`**
**[例15] 查询所有姓刘学生的姓名、学号和性别。**

```sql
SELECT Sname,Sno,Ssex
FROM Student
WHERE  Sname LIKE '刘%';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328164745872.png)
**[例16] 查询姓"欧阳"且全名为三个汉字的学生的姓名。**

```sql
SELECT Sname
FROM   Student
WHERE  Sname LIKE '欧阳_';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328164907955.png)

**[例17] 查询名字中第2个字为"阳"字的学生的姓名和学号。**

```sql
SELECT Sname,Sno
FROM Student
WHERE Sname LIKE '_阳%';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165007448.png)

**[例18] 查询所有不姓刘的学生姓名。**

```sql
SELECT Sname,Sno,Ssex
FROM Student
WHERE Sname NOT LIKE '刘%';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165047455.png)

###### ❺ 使用换码字符’'将通配符转义为普通字符

- `ESCAPE '＼' 表示“ ＼” 为换码字符`

**[例19] 查询DB_Design课程的课程号和学分。**

```sql
SELECT Cno,Ccredit
FROM Course
WHERE Cname LIKE 'DB\_Design' ESCAPE '\';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165239261.png)

**[例20] 查询以"DB_"开头，且倒数第3个字符为 i的课程的详细情况。**

```sql
SELECT  *
FROM   Course
WHERE  Cname LIKE  'DB\_%i_ _' ESCAPE '\';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165416525.png)

###### ❻ 涉及空值的查询

**谓词：**

- `IS NULL`
- `IS NOT NULL`
- `“IS” 不能用 “=” 代替`

**[例21] 某些学生选修课程后没有参加考试，所以有选课记录，但没有考试成绩。查询缺少成绩的学生的学号和相应的课程号。**

```sql
SELECT Sno,Cno
FROM  SC
WHERE  Grade IS NULL;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165627292.png)

**[例22] 查所有有成绩的学生学号和课程号。**

```sql
SELECT Sno,Cno
FROM  SC
WHERE  Grade IS NOT NULL;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165710331.png)

###### ❼ 多重条件查询

**逻辑运算符：**

- AND和 OR来联结多个查询条件
- AND的优先级高于OR
- 可以用括号改变优先级

**可用来实现多种其他谓词**

- `[NOT] IN`
- `[NOT] BETWEEN … AND …`

**[例23] 查询计算机系年龄在20岁以下的学生姓名。**

```sql
SELECT Sname
FROM  Student
WHERE Sdept= 'CS' AND Sage<20;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328165915595.png)

**改写[例12] 查询信息系（IS）、数学系（MA）和计算机科学系（CS）学生的姓名和性别。**

```sql
SELECT Sname,Ssex
FROM Student
WHERE Sdept IN ( 'IS','MA','CS' );
/*可改写为：*/
SELECT Sname,Ssex
FROM   Student
WHERE  Sdept= 'IS' OR Sdept= 'MA' OR Sdept= 'CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328170055535.png)

#### 3) ORDER BY子句

**ORDER BY子句**

- `可以按一个或多个属性列排序；`
- `升序：ASC；`
- `降序：DESC；`
- `缺省值为升序；`

**当排序列含空值时**

- `ASC`：排序列为空值的元组`最后显示`
- `DESC`：排序列为空值的元组`最先显示`

**[例24] 查询选修了3号课程的学生的学号及其成绩，查询结果按分数降序排列。**

```sql
SELECT Sno,Grade
FROM  SC
WHERE  Cno= '3'
ORDER BY Grade DESC;
4
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328170501500.png)
**[例25] 查询全体学生情况，查询结果按所在系的系号升序排列，同一系中的学生按年龄降序排列。**

```sql
SELECT  *
FROM  Student
ORDER BY Sdept,Sage DESC;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032817053075.png)

#### 4) 聚集函数

**聚集函数：**

- 计数
  `COUNT（[DISTINCT|ALL] *）`
  `COUNT（[DISTINCT|ALL] <列名>）`
- 计算总和
  `SUM（[DISTINCT|ALL] <列名>）`
- 计算平均值
  `AVG（[DISTINCT|ALL] <列名>）`
- 最大最小值
  `MAX（[DISTINCT|ALL] <列名>）`
  `MIN（[DISTINCT|ALL] <列名>）`

**[例26] 查询学生总人数。**

```sql
SELECT COUNT(*)
FROM  Student;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328170802782.png)
**[例27] 查询选修了课程的学生人数。**

```sql
SELECT COUNT(DISTINCT Sno)
FROM SC;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328170847534.png)
**[例28] 计算2号课程的学生平均成绩。**

```sql
SELECT AVG(Grade)
FROM SC
WHERE Cno= '2';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328171143778.png)

**[例29] 查询选修2号课程的学生最高分数。**

```sql
SELECT MAX(Grade)
FROM SC
WHERE Cno= '2';
```

![在这里插入图片描述](picture/20200328170259.png)

**[例30]查询学生201215121选修课程的总学分数。**

```sql
SELECT SUM(Ccredit)
FROM  SC, Course
WHERE Sno='201215121' AND SC.Cno=Course.Cno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328171516930.png)

#### 5) GROUP BY子句

**`GROUP BY`子句分组：**
**细化聚集函数的作用对象**

- 未对查询结果分组，聚集函数将作用于整个查询结果
- 对查询结果分组后，聚集函数将分别作用于每个组
- 作用对象是查询的中间结果表
- 按指定的一列或多列值分组，值相等的为一组

**`HAVING`短语与`WHERE`子句的区别：**

- 作用对象不同
- WHERE子句作用于`基表或视图`，从中选择满足条件的`元组`
- HAVING短语作用于`组`，从中选择满足条件的`组`。

**[例31] 求各个课程号及相应的选课人数。**

```sql
SELECT Cno,COUNT(Sno)
FROM    SC
GROUP BY Cno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032817221647.png)

**[例32] 查询选修了2门以上课程的学生学号。**

```sql
SELECT Sno
FROM  SC
GROUP BY Sno
HAVING  COUNT(*) >2;  
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328172509185.png)

### 3.3.4 连接查询

**连接查询：同时涉及多个表的查询**

**连接条件或连接谓词：用来连接两个表的条件**

**一般格式：**

- `[<表名1>.]<列名1> <比较运算符> [<表名2>.]<列名2>`
- `[<表名1>.]<列名1> BETWEEN [<表名2>.]<列名2> AND [<表名2>.]<列名3>`

**连接字段：连接谓词中的列名称**

- 连接条件中的各连接字段类型必须是可比的，但名字不必是相同的

#### （1）连接操作的执行过程

##### ① 嵌套循环法(NESTED-LOOP)

- 首先在表1中找到第一个元组，然后从头开始扫描表2，逐一查找满足连接件的元组，找到后就将表1中的第一个元组与该元组拼接起来，形成结果表中一个元组。
- 表2全部查找完后，再找表1中第二个元组，然后再从头开始扫描表2，逐一查找满足连接条件的元组，找到后就将表1中的第二个元组与该元组拼接起来，形成结果表中一个元组。
- 重复上述操作，直到表1中的全部元组都处理完毕

##### ② 排序合并法(SORT-MERGE)

**常用于=连接**

- 首先按连接属性对表1和表2排序
- 对表1的第一个元组，从头开始扫描表2，顺序查找满足连接条件的元组，找到后就将表1中的第一个元组与该元组拼接起来，形成结果表中一个元组。当遇到表2中第一条大于表1连接字段值的元组时，对表2的查询不再继续
- 找到表1的第二条元组，然后从刚才的中断点处继续顺序扫描表2，查找满足连接条件的元组，找到后就将表1中的第一个元组与该元组拼接起来，形成结果表中一个元组。直接遇到表2中大于表1连接字段值的元组时，对表2的查询不再继续
- 重复上述操作，直到表1或表2中的全部元组都处理完毕为止

##### ③ 索引连接(INDEX-JOIN)

- 对表2按连接字段建立索引
- 对表1中的每个元组，依次根据其连接字段值查询表2的索引，从中找到满足条件的元组，找到后就将表1中的第一个元组与该元组拼接起来，形成结果表中一个元组

#### （2）等值与非等值连接查询

**等值连接：连接运算符为=**

**[例33] 查询每个学生及其选修课程的情况**

```sql
SELECT  Student.*,SC.*
FROM     Student,SC
WHERE  Student.Sno = SC.Sno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328174005236.png)

**自然连接**

**[例34] 对[例33]用自然连接完成。**

```sql
SELECT  Student.Sno,Sname,Ssex,Sage,Sdept,Cno,Grade
FROM     Student,SC
WHERE  Student.Sno = SC.Sno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328174148296.png)

#### （3）自身连接

- **自身连接：一个表与其自己进行连接**
- **需要给表起别名以示区别**
- **由于所有属性名都是同名属性，因此必须使用别名前缀**

**[例35]查询每一门课的间接先修课（即`先修课的先修课`）**

```sql
SELECT  FIRST.Cno,SECOND.Cpno
FROM  Course  FIRST,Course  SECOND
WHERE FIRST.Cpno = SECOND.Cno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328174958693.png)

#### （4）连接JOIN

**SQL join 用于把来自两个或多个表的行结合起来。**
**标准格式：**

```sql
 SELECT column_name(s)
FROM table1//左表
<xxx JOIN> table2//右表
ON table1.column_name=table2.column_name;
```

**分类：**

- `INNER JOIN (JOIN)`
- `LEFT JOIN (LEFT OUTER JOIN)`
- `RIGHT JOIN (RIGHT OUTER JOIN)`
- `FULL JOIN (FULL OUTER JOIN)`

这里就以SC和Course两个表来检验这四类连接

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328184438818.png)

##### ① INNER JOIN (JOIN)

- `INNER JOIN`：关键字在表中存在至少一个匹配时返回行。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328181150122.png)

```sql
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC INNER JOIN Course ON (SC.Cno=Course.Cno);
/*INNER JOIN 与 JOIN结果相同*/
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC  JOIN Course ON (SC.Cno=Course.Cno);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328184047680.png)

##### ② LEFT JOIN (LEFT OUTER JOIN)

- `LEFT JOIN`：关键字从左表（table1）返回所有的行，即使右表（table2）中没有匹配。如果右表中没有匹配，则结果为 NULL。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328181212136.png)

```sql
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC LEFT JOIN Course ON (SC.Cno=Course.Cno);
/*LEFT JOIN 与 LEFT OUTER JOIN结果相同*/
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC LEFT OUTER JOIN Course ON (SC.Cno=Course.Cno);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328185007546.png)

##### ③ RIGHT JOIN (RIGHT OUTER JOIN)

- `RIGHT JOIN`：关键字从右表（table2）返回所有的行，即使左表（table1）中没有匹配。如果左表中没有匹配，则结果为 NULL。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328181227458.png)

```sql
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC RIGHT JOIN Course ON (SC.Cno=Course.Cno);
/*RIGHT JOIN 与 RIGHT OUTER JOIN结果相同*/
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC RIGHT OUTER JOIN Course ON (SC.Cno=Course.Cno);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328185227724.png)

##### ④ FULL JOIN (FULL OUTER JOIN)

- `FULL JOIN`：关键字只要左表（table1）和右表（table2）其中一个表中存在匹配，则返回行。结合了 LEFT JOIN 和 RIGHT JOIN 的结果。
  ![在这里插入图片描述](picture/20200328187180.png)

```sql
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC FULL JOIN Course ON (SC.Cno=Course.Cno);
/*FULL JOIN 与 FULL OUTER JOIN结果相同*/
SELECT Sno,SC.Cno,Grade,Course.Cno,Cname,Cpno,Ccredit
FROM  SC FULL OUTER JOIN Course ON (SC.Cno=Course.Cno);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328185614975.png)

### （5）复合条件连接

**复合条件连接：WHERE子句中含多个连接条件**

**[例37]查询选修2号课程且成绩在88分以上的所有学生**

```sql
SELECT Student.Sno, Sname
FROM    Student,SC
WHERE Student.Sno = SC.Sno AND   
/* 连接谓词*/
SC.Cno= '2' AND SC.Grade > 88;     
/* 其他限定条件 */
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328190502486.png)
**[例38]查询每个学生的学号、姓名、选修的课程名及成绩**

```sql
SELECT Student.Sno,Sname,Cname,Grade
FROM    Student,SC,Course  /*多表连接*/
WHERE Student.Sno = SC.Sno 
and SC.Cno = Course.Cno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328190635619.png)

### 3.3.6 嵌套查询

#### （1）嵌套查询概述

- 一个SELECT-FROM-WHERE语句称为一个`查询块`
- 将一个`查询块嵌套`在另一个`查询块`的`WHERE`子句或`HAVING`短语的条件中的查询称为`嵌套查询`

**一个例子：**

```sql
 SELECT Sname/*外层查询/父查询*/
 FROM Student
 WHERE Sno IN
(SELECT Sno    /*内层查询/子查询*/
 FROM SC
 WHERE Cno= '2');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328191426836.png)

- 子查询的`限制`： `·不能使用ORDER BY子句·`
- 层层嵌套方式反映了 SQL语言的结构化
- 有些嵌套查询可以用连接运算替代

#### （2）不相关子查询

**`子查询的查询条件不依赖于父查询`**

- 由里向外 逐层处理。即每个子查询在上一级查询处理之前求解，子查询的结果用于建立其父查询的查找条件。

#### （3）相关子查询

**`子查询的查询条件依赖于父查询`**

- 首先取外层查询中表的第一个元组，根据它与内层查询相关的属性值处理内层查询，若WHERE子句返回值为真，则取此元组放入结果表
- 然后再取外层表的下一个元组
- 重复这一过程，直至外层表全部检查完为止

#### （4）带有IN谓词的子查询

**[例39] 查询与“刘晨”在同一个系学习的学生。此查询要求可以分步来完成**

- ① 确定“刘晨”所在系名

```sql
SELECT  Sdept  
FROM     Student                            
WHERE  Sname= '刘晨';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328192246580.png)

- ② 查找所有在CS系学习的学生。

```sql
SELECT  Sno,Sname,Sdept     
FROM    Student                 
WHERE  Sdept= 'CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328192207929.png)
**将第一步查询嵌入到第二步查询的条件中**

```sql
SELECT Sno,Sname,Sdept
FROM Student
WHERE Sdept  IN
(SELECT Sdept
FROM Student
WHERE Sname= '刘晨');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328192431892.png)

- 此查询为不相关子查询。

**[例40]查询选修了课程名为“信息系统”的学生学号和姓名**

```sql
SELECT Sno,Sname /*③ 最后在Student关系中取出Sno和Sname*/
FROM    Student  
WHERE Sno  IN
(  SELECT Sno  	/*② 然后在SC关系中找出选修了3号课程的学生学号*/
	 FROM    SC      
	 WHERE  Cno IN
( SELECT Cno   /*① 首先在Course关系中找出 “信息系统”的课程号,为3号*/
  FROM Course    
  WHERE Cname= '信息系统'
     )
);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328194014135.png)

**用连接查询实现[例40]**

```sql
SELECT Student.Sno,Sname
FROM    Student,SC,Course
WHERE Student.Sno = SC.Sno 
AND SC.Cno = Course.Cno 
AND Course.Cname='信息系统';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328194217851.png)

#### （5）带有比较运算符的子查询

- 带有比较运算符的子查询是指父查询与子查询之间用比较运算符进行连接。当用户能确切知道内层查询返回的是`单个值`时，可以用>、<、=、>=、<= 、!=或< >等`比较运算符`。
- 与ANY或ALL谓词配合使用

**例：假设一个学生只可能在一个系学习，并且必须属于一个系，则在[例39]可以用`= 代替IN`：**

```sql
SELECT Sno,Sname,Sdept
FROM Student
WHERE Sdept  =
(SELECT Sdept
FROM Student
WHERE Sname= '刘晨');
/*两种方式都可以*/
SELECT Sno,Sname,Sdept
FROM Student
WHERE
(SELECT Sdept
FROM Student
WHERE Sname= '刘晨')
= Sdept ;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328210722539.png)
**［例41］找出每个学生超过他选修课程平均成绩的课程号。**

```sql
SELECT Sno, Cno
FROM  SC  x
WHERE Grade >=(SELECT AVG(Grade)  /*相关子查询*/ 
   	           FROM  SC y
              WHERE y.Sno=x.Sno
    );
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032821122791.png)

**`［例41］可能的执行过程：`**
1.从外层查询中取出SC的一个元组x，将元组x的Sno值（201215121）传送给内层查询。

```sql
SELECT AVG(Grade)
FROM SC y
WHERE y.Sno='201215121';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328211628491.png)

2.执行内层查询，得到值88（近似值），用该值代替内层查询，得到外层查询：

```sql
SELECT Sno, Cno
FROM  SC x
WHERE Grade >=88; 
```

3.执行这个查询，得到
（200215121，1）
（200215121，3）

4.外层查询取出下一个元组`重复做上述1至3步骤`，直到外层的SC元组全部处理完毕。结果为:
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020032821122791.png)

#### （6）带有ANY（SOME）或ALL谓词的子查询

**谓词语义：**

- `ANY：任意一个值`
- `ALL：所有值`

**需要配合使用比较运算符:**

|               |                                              |
| ------------- | -------------------------------------------- |
| > ANY         | 大于子查询结果中的某个值                     |
| > ALL         | 大于子查询结果中的所有值                     |
| < ANY         | 小于子查询结果中的某个值                     |
| < ALL         | 小于子查询结果中的所有值                     |
| >= ANY        | 大于等于子查询结果中的某个值                 |
| >= ALL        | 大于等于子查询结果中的所有值                 |
| <= ANY        | 小于等于子查询结果中的某个值                 |
| <= ALL        | 小于等于子查询结果中的所有值                 |
| = ANY         | 等于子查询结果中的某个值                     |
| =ALL          | 等于子查询结果中的所有值（通常没有实际意义） |
| !=（或<>）ANY | 不等于子查询结果中的某个值                   |
| !=（或<>）ALL | 不等于子查询结果中的任何一个值               |

**[例42] 查询其他系中比计算机科学某一学生年龄小的学生姓名和年龄**

```sql
SELECT Sname,Sage
FROM    Student
WHERE Sage < ANY (SELECT  Sage
                 FROM    Student
                  WHERE Sdept= 'CS')
   	 AND Sdept <> 'CS' ; /*父查询块中的条件 */
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328213109641.png)
**执行过程：**

> 关系数据库管理系统（Relational Database Management System：RDBMS）

RDBMS执行此查询时，首先处理子查询，找出 CS系中所有学生的年龄，构成一个集合(20，19)

处理父查询，找所有不是CS系且年龄小于 20 或 19的学生

**用聚集函数实现[例42]**

```sql
SELECT Sname,Sage
FROM   Student
WHERE Sage < (SELECT MAX(Sage)
             FROM Student
             WHERE Sdept= 'CS')
          AND Sdept <> 'CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328213809434.png)

**[例43] 查询其他系中比计算机科学系所有学生年龄都小的学生姓名及年龄。**

- 方法一：用ALL谓词

```sql
SELECT Sname,Sage
FROM Student
WHERE Sage < ALL (SELECT Sage
                 FROM Student
                  WHERE Sdept= 'CS')
              AND Sdept <> 'CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328213933146.png)

- 方法二：用聚集函数

```sql
SELECT Sname,Sage
FROM Student
WHERE Sage < (SELECT MIN(Sage)
               FROM Student
               WHERE Sdept= 'CS')
            AND Sdept <> 'CS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328214050416.png)

**ANY（或SOME），ALL谓词与聚集函数、IN谓词的等价转换关系**

|      | =    | <>或!= | <    | <=    | >    | >=    |
| ---- | ---- | ------ | ---- | ----- | ---- | ----- |
| ANY  | IN   | –      | <MAX | <=MAX | >MIN | >=MIN |
| ALL  | –    | NOT IN | <MIN | <=MIN | >MAX | >=MAX |

#### （7）带有EXISTS谓词的子查询

**EXISTS谓词**

- 存在量词 ∃
- 带有EXISTS谓词的子查询不返回任何数据，只产生逻辑真值“true”或逻辑假值“false”。
  - 若内层查询结果非空，则外层的WHERE子句返回真值
  - 若内层查询结果为空，则外层的WHERE子句返回假值
- 由EXISTS引出的子查询，其目标列表达式通常都用* ，因为带EXISTS的子查询只返回真值或假值，给出列名无实际意义

**NOT EXISTS谓词**

- 若内层查询结果非空，则外层的WHERE子句返回假值
- 若内层查询结果为空，则外层的WHERE子句返回真值

**[例44]查询所有选修了1号课程的学生姓名。**

**思路分析：**

- 本查询涉及Student和SC关系
- 在Student中依次取每个元组的Sno值，用此值去检查SC关系
- 若SC中存在这样的元组，其Sno值等于此Student.Sno值，并且其Cno=‘1’，则取此Student.Sname送入结果关系

**1.用嵌套查询**

```sql
SELECT Sname
FROM Student
WHERE EXISTS(SELECT *
             FROM SC
              WHERE Sno=Student.Sno 
   	AND Cno= '1');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220025911.png)

**2.用连接运算**

```sql
SELECT Sname
FROM Student, SC
WHERE Student.Sno=SC.Sno 
AND SC.Cno= '1';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220145896.png)

**[例45] 查询没有选修1号课程的学生姓名。**

```sql
SELECT Sname
FROM Student
WHERE NOT EXISTS(SELECT *
             FROM SC
              WHERE Sno=Student.Sno 
   	 AND Cno= '1');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220235205.png)

**不同形式的查询间的替换**

- 一些带EXISTS或NOT EXISTS谓词的子查询不能被其他形式的子查询等价替换
- 所有带IN谓词、比较运算符、ANY和ALL谓词的子查询都能用带EXISTS谓词的子查询等价替换
  用EXISTS/NOT EXISTS实现全称量词(难点)
  SQL语言中没有全称量词∀（For all）
  可以把带有全称量词的谓词转换为等价的带有存在量词的谓词：
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220340747.png)
  **例：[例39]查询与“刘晨”在同一个系学习的学生。**
  **可以用带EXISTS谓词的子查询替换：**

```sql
SELECT Sno,Sname,Sdept
FROM Student S1
WHERE EXISTS(SELECT *
           FROM Student S2
           WHERE S2.Sdept = S1.Sdept
      AND S2.Sname = '刘晨');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220610972.png)

**[例46] 查询选修了全部课程的学生姓名。**

```sql
SELECT Sname
FROM Student
WHERE NOT EXISTS(SELECT *
                 FROM Course
                 WHERE NOT EXISTS(SELECT *
                                  FROM SC
                                  WHERE Sno= Student.Sno
                                   AND Cno= Course.Cno)
                 );
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220839126.png)

**用EXISTS/NOT EXISTS实现逻辑蕴函(难点)**

- SQL语言中没有蕴函(Implication)逻辑运算
- 可以利用谓词演算将逻辑蕴函谓词等价转换为：
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328220918284.png)
  **[例47]查询至少选修了学生201215122选修的全部课程的学生号码。
  解题思路：**
- 用逻辑蕴函表达：查询学号为x的学生，对所有的课程y，只要201215122学生选修了课程y，则x也选修了y。
- 形式化表示：
  用P表示谓词 “学生201215122选修了课程y”
  用q表示谓词 “学生x选修了课程y”
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328221001631.png)
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328221513898.png)
  **用NOT EXISTS谓词表示：**

```sql
SELECT DISTINCT Sno
FROM SC SCX
WHERE NOT EXISTS(SELECT *
                FROM SC SCY
                WHERE SCY.Sno = '201215122' 
   	    AND NOT EXISTS(SELECT *
                                FROM SC SCZ
                                WHERE SCZ.Sno=SCX.Sno 
   	        	AND SCZ.Cno=SCY.Cno
   	)
   );
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328221455379.png)

### 3.3.7 集合查询

#### （1） 集合操作的种类

- `并操作UNION`
- `交操作INTERSECT`
- `差操作EXCEPT`

**参加集合操作的各`查询结果`的`列数必须相同`；对应项的`数据类型也必须相同`**

#### （2）集合操作举例

**[例48] 查询计算机科学系的学生及年龄不大于19岁的学生。**
**方法一：**

```sql
SELECT *
FROM Student
WHERE Sdept= 'CS'
UNION SELECT *
       FROM Student
       WHERE Sage<=19;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328231826579.png)

- `UNION`：将多个查询结果`合并`起来时，系统自动`去掉重复元组`。
- `UNION ALL`：将多个查询结果`合并`起来时，`保留重复元组`

**方法二：**

```sql
SELECT  DISTINCT  *
FROM Student
WHERE Sdept= 'CS'  
OR  Sage<=19;
```

**[例49] 查询选修了课程1`或者`选修了课程2的学生。**

```sql
SELECT Sno
FROM SC
WHERE Cno='1'
UNION
SELECT Sno
FROM SC
WHERE Cno= '2';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328231932550.png)

**[例50] 查询计算机科学系的学生与年龄不大于19岁的学生的`交集`**

```sql
SELECT *
FROM Student
WHERE Sdept='CS' 
INTERSECT
SELECT *
FROM Student
WHERE Sage<=19;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232036527.png)

**[例50] 实际上就是查询计算机科学系中年龄不大于19岁的学生**

```sql
SELECT *
FROM Student
WHERE Sdept= 'CS' 
AND  Sage<=19;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232149368.png)

**[例51] 查询选修课程1的学生集合与选修课程2的学生集合的`交集`**

```sql
SELECT Sno
FROM SC
WHERE Cno='1' 
INTERSECT
SELECT Sno
FROM SC
WHERE Cno='2';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232244520.png)

**[例51]实际上是查询既选修了课程1`又`选修了课程2 的学生**

```sql
SELECT Sno
FROM SC
WHERE Cno='1' AND Sno IN
(SELECT Sno
FROM SC
WHERE Cno='2');
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232458730.png)

**[例52] 查询计算机科学系的学生与年龄不大于19岁的学生的`差集`。**

```sql
SELECT *
FROM Student
WHERE Sdept='CS'
EXCEPT
SELECT  *
FROM Student
WHERE Sage <=19;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232558341.png)

**[例52]实际上是查询计算机科学系中年龄大于19岁的学生**

```sql
SELECT *
FROM Student
WHERE Sdept= 'CS' 
AND  Sage>19;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200328232657354.png)





## 3.4. 数据更新

![](https://gitee.com/fakerlove/picture_1/raw/master/20200401161830948.png)

### 3.4.1 基本表更新—TABLE

#### 1) 插入数据

**两种插入数据方式**

1. 插入元组
2. 插入子查询结果

- 可以一次插入多个元组

##### ① 插入元组

**语句格式**

```sql
	INSERT
	INTO <表名> [(<属性列1>[，<属性列2 >…)]
	VALUES (<常量1> [，<常量2>]    …           )
```

功能:将新元组插入指定表中

**INTO子句**

- 属性列的顺序可与表定义中的顺序不一致
- 没有指定属性列
- 指定部分属性列

**VALUES子句**

- 提供的值必须与INTO子句匹配
- 值的个数
- 值的类型

**［例1］ 将一个新学生元组（学号：200215128；姓名：陈冬；性别：男；所在系：IS；年龄：18岁）插入到Student表中。**

```sql
    INSERT
    INTO  Student (Sno，Sname，Ssex，Sdept，Sage)
    VALUES ('200215128'，'陈冬'，'男'，'IS'，18)；
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401132731647.png)
**［例2］ 将学生张成民的信息插入到Student表中。**

```sql
INSERT
INTO  Student
VALUES ('200215126', '张成民', '男',18,'CS'); 
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401132943495.png)

**［例3］ 插入一条选课记录( ‘200215128’，'1 ')。**

```sql
INSERT
INTO SC(Sno,Cno)//RDBMS将在新插入记录的Grade列上自动地赋空值
VALUES ('200215128','1');
//等价
INSERT
INTO SC
VALUES ('200215128','1',NULL);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020040113321448.png)

##### ② 插入子查询结果

**语句格式**

```sql
    INSERT 
    INTO <表名>  [(<属性列1> [，<属性列2>…  )]
    子查询；
```

**功能**
将子查询结果插入指定表中

**INTO子句(与插入元组类似)**

**子查询**

- SELECT子句目标列必须与INTO子句匹配
  值的个数
  值的类型

**[例4] 对每一个系，求学生的平均年龄，并把结果存入数据库。**

**第一步：建表**

```sql
CREATE  TABLE  Dept_age(
Sdept  CHAR(15),       /* 系名*/
Avg_age SMALLINT  /*学生平均年龄*/
);   	 
```

**第二步：插入数据**

```sql
INSERT INTO  Dept_age(Sdept,Avg_age)
SELECT  Sdept,AVG(Sage)
FROM  Student
GROUP BY Sdept;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401134827273.png)

**RDBMS在执行插入语句时会检查所插元组是否破坏表上已定义的完整性规则**

- 实体完整性
- 参照完整性
- 用户定义的完整性
- NOT NULL约束
- UNIQUE约束
- 值域约束

#### 2) 修改数据

**语句格式**

```sql
UPDATE  <表名>
SET  <列名>=<表达式>[，<列名>=<表达式>]…
[WHERE <条件>];
```

**功能**
修改指定表中满足WHERE子句条件的元组

**SET子句**

- 指定修改方式
- 要修改的列
- 修改后取值

**WHERE子句**

- 指定要修改的元组
- `缺省表示要修改表中的所有元组`

**三种修改方式**

1. 修改某一个元组的值
2. 修改多个元组的值
3. 带子查询的修改语句

##### ① 修改某一个元组的值

**[例5] 将学生201215121的年龄改为22岁**

```sql
UPDATE  Student
SET Sage=22
WHERE  Sno='201215121'; 
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401135354968.png)

**[例6] 将所有学生的年龄增加1岁**

```sql
UPDATE Student
SET Sage= Sage+1;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401135500751.png)
**[例7] 将计算机科学系全体学生的成绩置零。**

```sql
UPDATE SC
SET  Grade=0
WHERE  'CS'=( 
SELECT  Sdept
FROM  Student
WHERE  Student.Sno = SC.Sno
	);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020040113581718.png)

**RDBMS在执行修改语句时会检查修改操作是否破坏表上已定义的完整性规则**

- 实体完整性
- 主码不允许修改
- 用户定义的完整性
- NOT NULL约束
- UNIQUE约束
- 值域约束

#### 3) 删除数据

**三种删除方式**

1. 删除某一个元组的值
2. 删除多个元组的值
3. 带子查询的删除语句

##### ① 删除某一个元组的值

```sql
DELETE
FROM Student
WHERE Sno= '200215128';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401140233412.png)

##### ② 删除多个元组的值

**[例9] 删除所有的学生选课记录。**

```sql
        DELETE
        FROM SC；//这个我就不截图了
```

##### ③ 带子查询的删除语句

[例10] 删除计算机科学系所有学生的选课记录。

```sql
DELETE
FROM SC
WHERE  'CS'=(
   SELECT Sdept
   FROM Student
   WHERE Student.Sno=SC.Sno
   	);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401140620653.png)

### 3.4.2 视图—VIEW

**视图的作用：**

1. 视图能够简化用户的操作
2. 视图使用户能以多种角度看待同一数据
3. 视图对重构数据库提供了一定程度的逻辑独立性
4. 视图能够对机密数据提供安全保护
5. 适当的利用视图可以更清晰的表达查询

**视图的特点**

- 虚表，是从一个或几个基本表（或视图）导出的表
- 只存放视图的定义，不存放视图对应的数据
- 基表中的数据发生变化，从视图中查询出的数据也随之改变

**基于视图的操作**

- 查询
- 删除
- 受限更新
- 定义基于该视图的新视图

> 视图的UPDATE、DELETE、INSERT INTO(有受限)，与基本表同步。

#### （1）定义视图

##### ① 建立视图

- **语句格式**

```sql
CREATE  VIEW <视图名>  [(<列名>  [，<列名>]…)]
AS  <子查询>
[WITH  CHECK  OPTION];
```

- 组成视图的属性列名：全部省略或全部指定
- `子查询不允许`含有`ORDER BY`子句和`DISTINCT`短语
- RDBMS执行CREATE VIEW语句时只是把视图定义存入`数据字典`，并不执行其中的SELECT语句。
- 在对视图查询时，按视图的定义从基本表中将数据查出。

**[例1] 建立信息系IS学生的视图。**

```sql
CREATE VIEW IS_Student
AS 
SELECT Sno,Sname,Sage
FROM    Student
WHERE  Sdept= 'IS';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401141734215.png)
**[例2]建立信息系学生的视图，并要求进行修改和插入操作时仍需保证该视图只有信息系IS的学生 。**
**对IS_Student视图的更新操作：**

- 修改操作：自动加上Sdept= 'IS’的条件
- 删除操作：自动加上Sdept= 'IS’的条件
- 插入操作：自动检查Sdept属性值是否为’IS’
  - 如果不是，则拒绝该插入操作
  - 如果没有提供Sdept属性值，则自动定义Sdept为’IS’

```sql
CREATE VIEW IS_Student
AS 
SELECT Sno,Sname,Sage
FROM  Student
WHERE  Sdept= 'IS'
WITH CHECK OPTION;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401142141109.png)
**基于多个基表的视图**

**[例3] 建立信息系选修了1号课程的学生视图。**

```sql
CREATE VIEW IS_S1(Sno,Sname,Grade)
AS 
SELECT Student.Sno,Sname,Grade
FROM  Student,SC
WHERE  Sdept= 'IS' 
AND Student.Sno=SC.Sno 
AND SC.Cno= '1';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401142857172.png)
**基于视图的视图**

**[例4] 建立信息系选修了1号课程且成绩在90分以上的学生的视图。**

```sql
CREATE VIEW IS_S2
AS
SELECT Sno,Sname,Grade
FROM  IS_S1
WHERE  Grade>=90;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401143210685.png)

**带表达式的视图**

**[例5] 定义一个反映学生出生年份的视图。**

```sql
CREATE  VIEW BT_S(Sno,Sname,Sbirth)
AS 
SELECT Sno,Sname,2000-Sage
FROM  Student;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401143446220.png)

**分组视图**

**[例6] 将学生的学号及他的平均成绩定义为一个视图**

```sql
CREATE  VIEW S_G(Sno,Gavg)
AS  
SELECT Sno,AVG(Grade)
FROM  SC
GROUP BY Sno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401143653506.png)
**不指定属性列**
**[例7]将Student表中所有女生记录定义为一个视图**

```sql
CREATE VIEW F_Student(F_Sno,name,sex,age,dept)
AS
SELECT *
FROM  Student
WHERE Ssex='女';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401143941159.png)
**缺点：**

- 修改基表Student的结构后，Student表与F_Student视图的映象关系被破坏，导致该视图不能正确工作。

##### ② 删除视图

**语句的格式:**

```sql
DROP VIEW <视图名>;
```

- 该语句从`数据字典`中删除指定的视图定义
- 如果该视图上还导出了其他视图，使用`CASCADE级联`删除语句，把该视图和由它导出的所有视图一起删除
- 删除基表时，由该基表导出的所有视图定义都必须显式地使用DROP VIEW语句删除

**［例8］ 删除视图IS_S1**

```sql
DROP VIEW IS_S1;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401145332456.png)

- 关于级联删除CASCADE，不知道为什么，删除模式、删除表、删除视图，有约束却删除不了，有待解决，先放这里。

#### （2）查询视图

**用户角度：`查询视图与查询基本表相同`**

**RDBMS实现视图查询的方法**

- 视图消解法（View Resolution）
  - 进行有效性检查
  - 转换成等价的对基本表的查询
  - 执行`修正`后的查询

关系数据库管理系统执行对视图的查询时，首先进行`有效性检查`，检查查询中涉及的表、视图等是否存在。如果存在，则从`数据字典`中取出视图的定义，把定义中的`子查询`和`用户的查询`结合起来，`转换成等价的对基本表的查询`，`然后再执行修正了的查询`。这一转换过程称为`视图消解`(view resolution)。

**[例9] 在信息系学生的视图中找出年龄小于等于20岁的学生。**

```sql
SELECT   Sno,Sage
FROM      IS_Student
WHERE   Sage<=20;
```

IS_Student视图的定义 (参见视图定义例1)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401151344373.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401150136382.png)
**视图消解转换后的查询语句为：**

```sql
 SELECT  Sno，Sage       
 FROM  Student
 WHERE  Sdept= 'IS'  AND  Sage<=20；
```

**[例10] 查询选修了1号课程的信息系学生**

```sql
SELECT  IS_Student.Sno,Sname
FROM     IS_Student,SC
WHERE  IS_Student.Sno =SC.Sno AND SC.Cno= '1';
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401151417241.png)

**视图消解法的局限**

- 有些情况下，视图消解法不能生成正确查询。

**[例11]在S_G视图中查询平均成绩在90分以上的学生学号和平均成绩**

```sql
SELECT *
FROM   S_G
WHERE  Gavg>=90;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401151606151.png)

**S_G视图的子查询定义：**

```sql
CREATE VIEW S_G (Sno,Gavg)
AS 
SELECT  Sno,AVG(Grade)
FROM  SC
GROUP BY Sno;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401151548147.png)

```sql
错误：
SELECT Sno,AVG(Grade)
FROM     SC
WHERE  AVG(Grade)>=90
GROUP BY Sno;

正确：
SELECT  Sno,AVG(Grade)
FROM  SC
GROUP BY Sno
HAVING AVG(Grade)>=90;
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401151818567.png)

#### （3）更新视图

##### ① 更新数据—UPDATE SET

**[例12] 将信息系学生视图IS_Student中学号201215125的学生姓名改为“刘辰”。**
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401152252972.png)

```sql
UPDATE  IS_Student
SET  Sname= '刘辰'
WHERE  Sno= '201215125';
转换后的语句：//基本表和视图表同步更新
UPDATE  Student
SET Sname= '刘辰'
WHERE Sno= '201215125' 
AND Sdept= 'IS'; 
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401152617938.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401152432280.png)

##### ② 插入数据—INSERT INTO

**[例13] 向信息系学生视图IS_Student中插入一个新的学生记录：200215111，赵新，20岁**

```sql
视图IS_Student的定义
CREATE VIEW IS_Student
AS 
SELECT Sno,Sname,Sage
FROM    Student
WHERE  Sdept= 'IS';
//如果加了WITH CHECK OPTION，则视图不能进行插入数据操作
CREATE VIEW IS_Student
AS 
SELECT Sno,Sname,Sage
FROM  Student
WHERE  Sdept= 'IS'
WITH CHECK OPTION;

//插入数据
INSERT
INTO IS_Student
VALUES('200215111','赵新',20);
//插入后基本表Student字段Sdept为空，视图表IS_Student无数据
转换为对基本表的更新：
INSERT
INTO   Student(Sno,Sname,Sage,Sdept)
VALUES('200215129','赵新2',20,'IS');
4567891011121314151617181920212223
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401154939170.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401154949177.png)

##### ③ 删除数据—DELETE

**[例14]删除信息系学生视图IS_Student中学号为200215129的记录**

```sql
DELETE
FROM IS_Student
WHERE Sno= '200215129';
转换为对基本表的更新：
DELETE
FROM Student
WHERE Sno= '200215129' AND Sdept= 'IS';
4567
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401155510155.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401155515911.png)

##### ④ 更新视图的限制

- `更新视图的限制：`一些视图是不可更新的，因为对这些视图的更新不能唯一地有意义地转换成对相应基本表的更新

**例：视图S_G为不可更新视图。**
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401160322767.png)

```sql
UPDATE  S_G
SET          Gavg=90
WHERE  Sno= '200215121';

```

这个对视图的更新无法转换成对基本表SC的更新

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200401160413759.png)

- 允许对行列子集视图进行更新
- 对其他类型视图的更新不同系统有不同限制





## 3.5. 空值处理

### 3.5.1. 空值的约束条件

not null，unique，码属性

## 3.6. 视图

### 3.6.1. 视图消解

执行视图查询时，先进行有效性检查。如果视图、表都存在，就取出视图定义，把定义中的子查询和用户查询结合起来，转换成等价的对基本表的查询。这一转换过程被称为**视图分解**。

### 3.6.2. 视图的作用

1. 视图能够简化用户的操作（简化操作）
2. 视图使用户能以多种角度看待同一数据（多角度）
3. 视图对重构数据库提供了一定程度的逻辑独立性（逻辑独立性）
4. 视图能对机密数据提供安全保护（安全保护）
5. 适当利用视图可以更清晰地表达查询（清晰表达）



在一个项目的实际开发过程中牵涉到复杂业务的时候，我们不可避免的需要使用中间表来进行数据连接，有的同学就说了，我可以采用Hibernate进行主外键进行关联啊？多对多，多对一，一对一，等，采用主外键关联在数据的操作过程中具有很强的耦合性，尤其对于需要经常删改数据表而言，我们是不建议采用主外键关联这种模式，那么，如果我们采用中间表的话，当数据过大在性能上又面临严峻考验，sql视图的出现，在解决中间表的业务逻辑上是不错的选择。ok，首先我们了解什么是视图？

1、视图是表？没错，但是是一张虚拟表，视图的字段是由我们自定义的，视图只供查询，数据不可更改，查询数据来源于我们建立的实体表。

2、使用视图的优势？视图可以将多个复杂关联表，提取出我们需要的信息，优化查询速度。

如何创建视图？

我们先建立三张表；如下:

![wKioL1Ptjj-gJ6DEAACEukazCYo267.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909112735.jpg)![wKiom1PtjSejuuUnAACB0OJ87yg643.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113039.jpg)![wKioL1PtjkDT7Lq1AAB61axLMaw679.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113040.jpg)

这个是典型的一对多和一对一的关系，那么，假如每张表的数据都在一万条数据以上，现在查询在潢高上学的学生姓名？

首先，我们分析一下，在潢高上学？首先是一个高中，那么我们会有一条Sql where school='潢高',

查询出一个List,得到gradeids，然后再到grade中根据gradeids查询这么多grades对应的studentids，在使用这些studentsid查询出students循环最后得到name？

是不是很累赘？查询是不是很影响性能？ 

观察得知，这三张表每两张表之间都是通过id进行关联的，如果我们通过id将三张表组成一张表，是不是很方便？ 

我们来关联学校表和年级表:这个年级ID我们不要，ok？ 

~~~sql
select s.id as schoolId,s.school as schoolName,s.gradeid as gradeid,g.grade as gradeName,g.studentid as studentid from school s,grade g  where s.gradeid=g.id; 
~~~



![wKioL1PtkubC7NSTAAB2kqmCXfY098.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113041.jpg)

那么我们再关联上学生表，学生表的id等于年级表的studentid ok？

~~~sql
SELECT s.id as schoolId,s.school as schoolName,s.gradeid as gradeid,g.grade as gradeName,g.studentid as studentid ,t.`name` as studentName,t.age as studentAge
from school s,grade g,student t where s.gradeid=g.id and  g.studentid=t.id;
~~~



ok，到了这里？我们再看运行结果？ 

![wKioL1Ptk-SAsUfIAAC4KIhRufE356.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113042.jpg)

那么我们想查询在潢高上学的学生姓名，where schoolName='潢高',获取的list循环得到Object，通过Object.getStudentName,就可以了？

所以需要将查询到的结果，建立为一张虚拟表,这样才能操作，通过这个create view 视图名 as 命令建立:

意思就是将查询结果创建为名称为table_sgt的一张虚拟表:

~~~sql
create view table_sgt as(select s.id as schoolId,s.school as schoolName,s.gradeid as gradeid,g.grade as gradeName,g.studentid as studentid ,t.`name` as studentName,t.age as studentAge from school s,grade g,student t where s.gradeid=g.id and  g.studentid=t.id);
~~~



![wKioL1PtlZuQiR_8AABou7EhE2g895.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113043.jpg)

![wKiom1PtlKyj-cb_AAEt4kosx98924.jpg](https://gitee.com/fakerlove/picture_1/raw/master/2014081909113044.jpg)

我们在使用视图的时候，需要把它看做为一张表，建立一张实体表需要做的步骤，视图也都需要(例如，实例化，配置映射文件，对象的属性get,set方法)

注意视图所查询出来的数据只能进行查看，不能增删改！



### 3.6.3. 视图的更新问题

视图是不实际存储数据的虚表，因此对视图的更新，最终要转换为对基本表的更新。**因为有些视图的更新不能惟一有意义地转换成对相应基本表的更新**，所以，并不是所有的视图都是可更新的.
基本表的行列子集视图一般是可更新的。若视图的属性来自集合函数、表达式，则该视图肯定是不可以更新的。



## 3.7 mysql 所有关键字

| ADD                | ALL                 | ALTER              |
| ------------------ | ------------------- | ------------------ |
| ANALYZE            | AND                 | AS                 |
| ASC                | ASENSITIVE          | BEFORE             |
| BETWEEN            | BIGINT              | BINARY             |
| BLOB               | BOTH                | BY                 |
| CALL               | CASCADE             | CASE               |
| CHANGE             | CHAR                | CHARACTER          |
| CHECK              | COLLATE             | COLUMN             |
| CONDITION          | CONNECTION          | CONSTRAINT         |
| CONTINUE           | CONVERT             | CREATE             |
| CROSS              | CURRENT_DATE        | CURRENT_TIME       |
| CURRENT_TIMESTAMP  | CURRENT_USER        | CURSOR             |
| DATABASE           | DATABASES           | DAY_HOUR           |
| DAY_MICROSECOND    | DAY_MINUTE          | DAY_SECOND         |
| DEC                | DECIMAL             | DECLARE            |
| DEFAULT            | DELAYED             | DELETE             |
| DESC               | DESCRIBE            | DETERMINISTIC      |
| DISTINCT           | DISTINCTROW         | DIV                |
| DOUBLE             | DROP                | DUAL               |
| EACH               | ELSE                | ELSEIF             |
| ENCLOSED           | ESCAPED             | EXISTS             |
| EXIT               | EXPLAIN             | FALSE              |
| FETCH              | FLOAT               | FLOAT4             |
| FLOAT8             | FOR                 | FORCE              |
| FOREIGN            | FROM                | FULLTEXT           |
| GOTO               | GRANT               | GROUP              |
| HAVING             | HIGH_PRIORITY       | HOUR_MICROSECOND   |
| HOUR_MINUTE        | HOUR_SECOND         | IF                 |
| IGNORE             | IN                  | INDEX              |
| INFILE             | INNER               | INOUT              |
| INSENSITIVE        | INSERT              | INT                |
| INT1               | INT2                | INT3               |
| INT4               | INT8                | INTEGER            |
| INTERVAL           | INTO                | IS                 |
| ITERATE            | JOIN                | KEY                |
| KEYS               | KILL                | LABEL              |
| LEADING            | LEAVE               | LEFT               |
| LIKE               | LIMIT               | LINEAR             |
| LINES              | LOAD                | LOCALTIME          |
| LOCALTIMESTAMP     | LOCK                | LONG               |
| LONGBLOB           | LONGTEXT            | LOOP               |
| LOW_PRIORITY       | MATCH               | MEDIUMBLOB         |
| MEDIUMINT          | MEDIUMTEXT          | MIDDLEINT          |
| MINUTE_MICROSECOND | MINUTE_SECOND       | MOD                |
| MODIFIES           | NATURAL             | NOT                |
| NO_WRITE_TO_BINLOG | NULL                | NUMERIC            |
| ON                 | OPTIMIZE            | OPTION             |
| OPTIONALLY         | OR                  | ORDER              |
| OUT                | OUTER               | OUTFILE            |
| PRECISION          | PRIMARY             | PROCEDURE          |
| PURGE              | RAID0               | RANGE              |
| READ               | READS               | REAL               |
| REFERENCES         | REGEXP              | RELEASE            |
| RENAME             | REPEAT              | REPLACE            |
| REQUIRE            | RESTRICT            | RETURN             |
| REVOKE             | RIGHT               | RLIKE              |
| SCHEMA             | SCHEMAS             | SECOND_MICROSECOND |
| SELECT             | SENSITIVE           | SEPARATOR          |
| SET                | SHOW                | SMALLINT           |
| SPATIAL            | SPECIFIC            | SQL                |
| SQLEXCEPTION       | SQLSTATE            | SQLWARNING         |
| SQL_BIG_RESULT     | SQL_CALC_FOUND_ROWS | SQL_SMALL_RESULT   |
| SSL                | STARTING            | STRAIGHT_JOIN      |
| TABLE              | TERMINATED          | THEN               |
| TINYBLOB           | TINYINT             | TINYTEXT           |
| TO                 | TRAILING            | TRIGGER            |
| TRUE               | UNDO                | UNION              |
| UNIQUE             | UNLOCK              | UNSIGNED           |
| UPDATE             | USAGE               | USE                |
| USING              | UTC_DATE            | UTC_TIME           |
| UTC_TIMESTAMP      | VALUES              | VARBINARY          |
| VARCHAR            | VARCHARACTER        | VARYING            |
| WHEN               | WHERE               | WHILE              |
| WITH               | WRITE               | X509               |
| XOR                | YEAR_MONTH          | ZEROFILL           |



# 4. 数据库安全性

> 保护数据库以防止不合法使用所造成的的数据泄露、更改或破坏

![](https://gitee.com/fakerlove/picture_1/raw/master/20200424232640388.png)



## 4.1 数据库安全性概述

### 4.1.1 为什么要研究数据库的安全性？

**问题的提出：**

- 数据库的一大特点是数据可以共享
- 数据共享必然带来数据库的安全性问题
- `数据库系统中的数据共享不能是无条件的共享`
- 例： 军事秘密、国家机密、新产品实验数据、
  市场需求分析、市场营销策略、销售计划、
  客户档案、医疗档案、银行储蓄数据

**非法使用数据库的情况：**

- 编写合法程序绕过DBMS及其授权机制（黑客等）
- 直接或编写应用程序执行非授权操作（黑客等）
- 通过多次合法查询数据库从中推导出一些保密数据（黑客等）

### 4.1.2 安全标准简介

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424145136275.png)

#### ① TCSEC/TDI标准的基本内容

- TCSEC/TDI，从四个方面来描述安全性级别划分的指标
  安全策略
  责任
  保证
  文档

#### ② TCSEC/TDI安全级别划分

- 按系统可靠或可信程度逐渐增高
- 各安全级别之间：偏序向下兼容
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424145421961.png)

**B2以上的系统：**

- 还处于理论研究阶段
- 应用多限于一些特殊的部门，如军队等
- 美国正在大力发展安全产品，试图将目前仅限于少数领域应用的B2安全级别下放到商业应用中来，并逐步成为新的商业标准

## 4.2 数据库安全性控制概述

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020042414581032.png)

- 用户要求进入计算机系统时，系统首先根据输入的用户标识进行用户身份鉴定，只有合法的用户才准许进入计算机系统;对已进入系统的用户，数据库管理系统还要进行存取控制，只允许用户执行合法操作;操作系统也会有自己的保护措施;数据最后还可以以密码形式存储到数据库中（例如md5加密密码等信息）。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424151727638.png)

**数据库安全性控制的常用方法：**

- 用户标识和鉴定
- 存取控制
- 视图
- 审计
- 密码存储

## 4.3 数据库安全性控制

### 4.3.1 用户标识与鉴别

- `是系统提供的最外层安全保护措施`
- 用户标识
  每个用户标识由用户名(user name)和用户标识号(UID)两部分组成。
  UID在系统的整个生命周期内是唯–的。系统内部记录着所有合法用户的标识
- 口令
  系统核对口令以鉴别用户身份 （口令可理解为密码）
- 用户标识和口令易被窃取
  每个用户预先约定好一个计算过程或者函数

**常用的用户身份鉴别方法有以下几种：**

#### ① 静态口令鉴别

- 这种方式是当前常用的鉴别方法。
- `静态口令一般由用户自己设定，鉴别时只要按要求输入正确的口令，系统将允许用户使用数据库管理系统。`
- 这些口令是静态不变的，在实际应用中，用户常常用自己的生日、电话、简单易记的数字等内容作为口令，很容易被破解。而一旦被破解，非法用户就可以冒充该用户使用数据库。
- 这种方式虽然简单，但容易被攻击，安全性较低。

#### ② 动态口令鉴别

- 它是目前较为安全的鉴别方式。
- 这种方式的口令是动态变化的，每次鉴别时均需使用动态产生的新口令登录数据库管理系统，即采用一次一密的方法。
- `常用的方式如短信密码和动态令牌方式，每次鉴别时要求用户使用通过短信或令牌等途径获取的新口令登录数据库管理系统。`
- 与静态口令鉴别相比，这种认证方式增加了口令被窃取或破解的难度，安全性相对高一些。

#### ③ 生物特征鉴别

- 它是一种通过生物特征进行认证的技术，其中，生物特征是指生物体唯一具有的，可测量、识别和验证的稳定生物特征，如`指纹、虹膜和掌纹等`。
- 这种方式通过采用图像处理和模式识别等技术实现了基于生物特征的认证，- 与传统的口令鉴别相比，无疑产生了质的飞跃，安全性较高。

#### ④ 智能卡鉴别

- 智能卡是一种不可复制的硬件，内置集成电路的芯片，具有硬件加密功能。
- `智能卡由用户随身携带，登录数据库管理系统时用户将智能卡插入专用的读卡器进行身份验证。`
- 由于每次从智能卡中读取的数据是静态的，通过内存扫描或网络监听等技术还是可能截取到用户的身份验证信息，存在安全隐患。
- 因此，实际应用中一般采用`个人身份识别码(PIN)和智能卡`相结合的方式。这样，即使PIN或智能卡中有一种被窃取，用户身份仍不会被冒充。

### 4.3.2 存取控制

- 数据库安全最重要的一点就是确保只授权给有资格的用户访问数据库的权限，同时令所有未被授权的人员无法接近数据，这`主要通过数据库系统的存取控制机制实现。`

#### ① 存取控制机制组成:

- `定义用户权限`,并将用户权限登记到数据字典中；
  用户对某一数据对象的操作权力称为权限。
- `合法权限检查`,每当用户发出存取数据库的操作请求后(请求一般应包括操作类型、操作对象和操作用户等信息)，`数据库管理系统查找数据字典，根据安全规则进行合法权限检查`，若用户的操作请求超出了定义的权限，系统将拒绝执行此操作。

**`定义用户权限`和`合法权限检查机制`一起组成了`数据库管理系统的存取控制子系统`。**

- `C2级`的数据库管理系统支持`自主存取控制`( Discretionary Access Control, DAC),
- `B1级`的数据库管理系统支持`强制存取控制`( Mandatory Access Control, MAC)。

**这两类方法的简单定义是:**

- (1)在`自主存取控制`方法中，用户对于不同的数据库对象有不同的存取权限，不同的用户对同一对象也有不同的权限，而且用户还可将其拥有的存取权限转授给其他用户。因此自主存取控制非常灵活。
- (2)在`强制存取控制`方法中，每一个 数据库对象被标以一定的密级，每一个用户也被授予某一个级别的许可证。对于任意一个对象， 只有具有合法许可证的用户才可以存取。强制存取控制因此相对比较严格。

### 4.3.3 自动存取控制方法—DAC

- 通过 SQL 的 `GRANT`语句和 `REVOKE`语句实现
- **用户权限组成**
  `数据对象`
  `操作类型`
- 定义用户存取权限：定义用户可以在哪些数据库对象上进行哪些类型的操作
- `定义存取权限称为授权`

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424170609766.png)

#### ① 授权与回收—针对用户

##### 1️⃣ 授权—GRANT

```sql
GRANT语句的一般格式：
       GRANT <权限>[,<权限>]... 
       [ON <对象类型> <对象名>]
       TO <用户>[,<用户>]...
       [WITH GRANT OPTION];
语义：将对指定操作对象的指定操作权限授予指定的用户 
```

**发出GRANT：**

- DBA
- 数据库对象创建者（即属主Owner）
- 拥有该权限的用户

**按受权限的用户:**

- 一个或多个具体用户
- PUBLIC（全体用户）

**WITH GRANT OPTION子句:**

- 指定：可以再授予
- 没有指定：不能传播

**不允许循环授权：**

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424171245996.png)

**[例1] 把查询Student表权限授给用户U1**

```sql
GRANT   SELECT 
ON   TABLE   Student 
TO   U1;
```

> 举个例子而已，不同数据库请参考相关文档，先打基础。有个印象，知道有这么个东西，其实很多数据库管理系统已经将这些封装好了，简洁漂亮的UI，灵活的操作，基本不会用到语句来写。话不多说，直接上图：![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424185706742.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424190053981.png)

**[例2] 把对Student表和Course表的全部权限授予用户U2和U3**

```sql
GRANT ALL PRIVILIGES 
ON TABLE Student, Course 
TO U2, U3;
```

**[例3] 把对表SC的查询权限授予所有用户**

```sql
GRANT SELECT 
ON TABLE SC 
TO PUBLIC;
```

**[例4] 把查询Student表和修改学生学号的权限授给用户U4**

```sql
对属性列的授权时必须明确指出相应属性列名 
	  	GRANT UPDATE(Sno), SELECT 
ON TABLE Student 
TO U4;
4
```

**[例5] 把对表SC的INSERT权限授予U5用户，并允许他再将此权限授予其他用户**

```sql
   GRANT INSERT 
   ON TABLE SC 
   TO U5
   WITH GRANT OPTION;
4
```

**执行例5后，U5不仅拥有了对表SC的INSERT权限，
还可以传播此权限：**
[例6]

```sql
GRANT INSERT ON TABLE SC TO U6
        WITH GRANT OPTION;
12
```

同样，U6还可以将此权限授予U7：

[例7]
`GRANT INSERT ON TABLE SC TO U7;`
但U7不能再传播此权限,因为没有写这条语句`WITH GRANT OPTION`。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424190133651.png)

##### 2️⃣ 回收—REVOKE

**授予的权限可以由DBA或其他授权者用REVOKE语句收回**
REVOKE语句的一般格式为：

```sql
      REVOKE <权限>[,<权限>]... 
      [ON <对象类型> <对象名>]
      FROM <用户>[,<用户>]...;

```

**[例8] 把用户U4修改学生学号的权限收回**

```sql
REVOKE UPDATE(Sno)
ON TABLE Student 
FROM U4;

```

**[例9] 收回所有用户对表SC的查询权限**

```sql
REVOKE SELECT 
ON TABLE SC 
FROM PUBLIC;

```

**[例10] 把用户U5对SC表的INSERT权限收回**

```sql
REVOKE INSERT 
ON TABLE SC 
FROM U5 CASCADE ;

将用户U5的INSERT权限收回的时候必须级联（CASCADE）收回 系统只收回直接或间接从U5处获得的权限
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424190438825.png)

##### 3️⃣ 小结:SQL灵活的授权机制

- DBA：
  拥有所有对象的所有权限
  不同的权限授予不同的用户
- 用户：拥有自己建立的对象的全部的操作权限
  GRANT：授予其他用户
- 被授权的用户
  “继续授权”（WITH GRANT OPTION）许可：可以再授予给其它用户
- 所有授予出去的权力在必要时又都可用REVOKE语句收回

##### 4️⃣ 创建数据库模式的权限

**DBA在创建用户时实现**

```sql
CREATE USER语句格式
              CREATE  USER  <username> 
            ［WITH］［DBA | RESOURCE | CONNECT］

```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020042419081284.png)

#### ② 数据库角色—针对角色

**数据库角色：被命名的一组与数据库操作相关的权限**

- 角色是权限的集合 ，`结合我刚刚上面截得黑色背景图片了解`
- 可以为一组具有相同权限的用户创建一个角色
- 简化授权的过程

##### 1️⃣ 角色的创建

```
CREATE ROLE <角色名>
```

##### 2️⃣ 给角色授权

```sql
 GRANT  <权限>［，<权限>］… 
 ON <对象类型>对象名  
 TO <角色>［，<角色>］…

```

##### 3️⃣ 将一个角色授予其他的角色或用户

```sql
GRANT  <角色1>［，<角色2>］…
TO  <角色3>［，<用户1>］… 
［WITH ADMIN OPTION］ 

```

##### 4️⃣ 角色权限的收回

```sql
REVOKE <权限>［，<权限>］…
ON <对象类型> <对象名>
FROM <角色>［，<角色>］…

```

**[例11]　通过角色来实现将一组权限授予一个用户。**
`步骤如下：`

1. 首先创建一个角色 R1
   `CREATE ROLE R1；`
2. 然后使用GRANT语句，使角色R1拥有Student表的SELECT、UPDATE、INSERT权限

```sql
    GRANT SELECT，UPDATE，INSERT 
    ON TABLE Student 
    TO R1；

```

1. 将这个角色授予王平，张明，赵玲。使他们具有角色R1所包含的全部权限

```sql
   GRANT  R1 
   TO 王平，张明，赵玲；
12
```

1. 可以一次性通过R1来回收王平的这3个权限

```sql
     REVOKE  R1 
     FROM 王平；
12
```

**[例12]　角色的权限修改**

```sql
      GRANT DELETE 
      ON TABLE Student
      TO R1

```

[例13]　角色权限的收回

```sql
    REVOKE SELECT 
    ON TABLE Student
    FROM  R1；

```

### 4.3.4 强制存取控制方法—MAC

**自主存取控制缺点:**

- 可能存在数据的“无意泄露”
- 原因：这种机制仅仅通过对数据的存取权限来进行安全控制，而数据本身并无安全性标记
- 解决：对系统控制下的所有主客体实施强制存取控制策略

------

**强制存取控制（MAC):**

- 保证更高程度的安全性

- 用户能不能直接感知或进行控制,因为对数据进行了加密

- 适用于对数据有严格而固定密级分类的部门

  *军事部门

  *政府部门

  ------

**在强制存取控制中，数据库管理系统所管理的全部实体被分为主体和客体两大类。**

- `主体`是系统中的活动实体
  DBMS所管理的实际用户
  代表用户的各进程
- `客体`是系统中的被动实体，是受主体操纵的
  文件
  基表
  索引
  视图

------

**对于主体和客体，数据库管理系统为它们每个实例(值)指派一个敏感度标记(label)。**
**敏感度标记（Label）分为若干个级别：**

- 绝密（Top Secret）
- 机密（Secret）
- 可信（Confidential）
- 公开（Public）
- `主体的敏感度标记称为许可证级别`（Clearance Level）
- `客体的敏感度标记称为密级`（Classification Level）
- 密级：T>=S>=C>=P

------

**强制存取控制规则：**

- (1)仅当主体的许可证级别`大于或等于客体`的密级时，该主体才能`读取`相应的客体
- (2)仅当主体的许可证级别`等于`客体的密级时，该主体才能`写`相应的客体
- 修正规则
  `主体的许可证级别 <=客体的密级→ 主体能写客体`

**规则的共同点:**

- `禁止`了拥有高许可证级别的主体`更新`低密级的数据对象

### 4.3.5 DAC与MAC共同构成DBMS的安全机制

- 实现MAC时要首先实现DAC
  原因：较高安全性级别提供的安全保护要包含较低级别的所有保护
- 先进行DAC检查，通过DAC检查的数据对象再由系统进行MAC检查，只有通过MAC检查的数据对象方可存取。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200424220933766.png)

## 4.4 视图机制

**把要保密的数据对无权存取这些数据的用户隐藏起来，对数据提供一定程度的安全保护**

- 主要功能是提供数据独立性，无法完全满足要求
- 间接实现了支持存取谓词的用户权限定义

------

**[例14]建立计算机系学生的视图，`把对该视图的SELECT权限授于王平，把该视图上的所有操作权限授于张明`**

```sql
先建立计算机系学生的视图CS_Student
 CREATE VIEW CS_Student AS 
    SELECT  *
    FROM   Student
    WHERE  Sdept='CS'；
```

**在视图上进一步定义存取权限：**

```sql
     GRANT  SELECT
     ON  CS_Student  
     TO 王平;
     
     GRANT ALL PRIVILIGES
     ON  CS_Student  
     TO  张明;
```

## 4.5 审计（Audit） —日志

**什么是审计：**

- `审计日志（Audit Log）`;
  将用户对数据库的所有操作记录在上面
- DBA利用审计日志
  找出非法存取数据的人、时间和内容
- C2以上安全级别的DBMS必须具有

------

**审计分为:**

- `用户级审计`
  针对自己创建的数据库表或视图进行审计 ;
  记录所有用户对这些表或视图的一切成功和（或）不成功的访问要求以及各种类型的SQL操作 ;
- `系统级审计`
  DBA设置 ;
  监测成功或失败的登录要求 ;
  监测GRANT和REVOKE操作以及其他数据库级权限下的操作;

------

```
AUDIT语句：设置审计功能
NOAUDIT语句：取消审计功能
```

------

**［例15］对修改SC表结构或修改SC表数据的操作进行审计**

```sql
AUDIT ALTER,UPDATE  
ON  SC;
```

**［例16］取消对SC表的一切审计**

```sql
           NOAUDIT  ALTER,UPDATE  
           ON  SC;
```

## 4.6 数据加密

- 数据加密
  防止数据库中数据在`存储`和`传输`中失密的有效手段
- 数据加密分为`存储加密`和`传输加密`

------

### 4.6.1 存储加密

- 对于存储加密，一般提供`透明和非透明`两种存储加密方式。
  `透明`存储加密是`内核级加密保护`方式，`对用户完全透明`
  `非透明`存储加密则是通过`多个加密函数`实现的。
- `透明存储加密`是数据在写到磁盘时对数据进行加密，授权用户读取数据时再对其进行解密。由于数据加密对用户透明，数据库的应用程序不需要做任何修改，只需在创建表语句中说明需加密的字段即可。当对加密数据进行增、删、改、查询操作时，数据库管理系统将自动对数据进行加、解密工作。基于数据库内核的数据存储加密、解密方法性能较好，安全完备性较高。

### 4.6.2 传输加密

- 在客户/服务器结构中，数据库用户与服务器之间若采用明文方式传输数据，容易被网络恶意用户截获或篡改，存在安全隐患。因此，为保证二者之间的安全数据交换，数据库管理系统提供了传输加密功能。
- 常用的传输加密方式如`链路加密和端到端加密`。

#### ① 链路加密

- 链路加密对传输数据在链路层进行加密，它的传输信息由报头和报文两部分组成，前者是路由选择信息，而后者是传送的数据信息。这种方式对报文和报头均加密。

#### ② 端到端加密

- 端到端加密对传输数据在发送端加密，接收端解密。它只加密报文，不加密报头。与链路加密相比，它只在发送端和接收端需要密码设备，而中间节点不需要密码设备，因此它所需密码设备数量相对较少。但这种方式不加密报头，从而容易被非法监听者发现并从中获取敏感信息。

## 4.7 统计数据库安全性

- `统计数据库`
  允许用户查询聚集类型的信息（如合计、平均值等）
  不允许查询单个记录信息

------

- `统计数据库中特殊的安全性问题:`
  隐蔽的信息通道
  能从合法的查询中推导出不合法的信息

------

**统计数据库安全性规则：**

- 规则1：任何查询至少要涉及N(N足够大)个以上的记录
- 规则2：任意两个查询的相交数据项不能超过M个
- 规则3：任一用户的查询次数不能超过1+(N-2)/M

> 数据库安全机制的设计目标：
> 试图破坏安全的人所花费的代价 >> 得到的利益





# 5. 数据库完整性



![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020040719260039.png)

## 5.1 数据库完整性概述



### 概念

- 首先先概述一下数据库完整性指的是什么，`数据库完整性`指的是数据的`正确性`和`相容性`。
- 数据的`正确性`是指数据是符合现实世界语义、反映当前实际状况的;比如说人类的性别，只能是男和女。
- 数据的`相容性`是指数据库同一对象在不同关系表中的数据是符合逻辑的。比如说年龄一般都在1-100岁，当然也有超过一百岁的，反正没有两百岁，三百岁成仙的人类。

### 完整性控制机制应具有三大功能



1.提供定义完整性约束条件的机制

- 完整约束条件也称`完整性规则`，是数据库中数据必须满足的语义条件规则
- 为保证数据的正确、有效和相容性的一些规则
- 数据的主码、外码、一些约束规则

2.提供完整性检查的方法

- 数据库管理系统中检查数据是否满足完整性规则的机制称为`完整性检查`
- 一般在执行INSERT、UPDATE、DELETE时检查

3.违约处理

- 数据库管理系统若发现用户的操作违背了完整性约束条件将采取一定的动作，如拒绝(NO ACTION)执行该操作或级联(CASCADE)执行其他操作，进行违约处理以保证数据的完整性。

## 5.2 实体完整性—PRIMARY KEY

### （1）实体完整性的定义

**关系模型的实体完整性**

- CREATE TABLE中用PRIMARY KEY定义

**单属性构成的码有两种说明方法**

- 定义为列级约束条件
- 定义为表级约束条件

**对多个属性构成的码只有一种说明方法**

- 定义为表级约束条件

```sql
举几个例子
将Student表中的Sno属性定义为码

(1)在列级定义主码
CREATE TABLE Student
(Sno  CHAR(9)  PRIMARY KEY，
Sname  CHAR(20) NOT NULL，     
Ssex  CHAR(2) ，
Sage  SMALLINT，
Sdept  CHAR(20));

(2)在表级定义主码
CREATE TABLE Student
(Sno  CHAR(9)，  
Sname  CHAR(20) NOT NULL，
Ssex  CHAR(2) ，
Sage  SMALLINT，
Sdept  CHAR(20)，
PRIMARY KEY (Sno)
); 

将SC表中的Sno，Cno属性组定义为码
CREATE TABLE SC
(Sno   CHAR(9)  NOT NULL， 
Cno  CHAR(4)  NOT NULL，  
Grade    SMALLINT，
PRIMARY KEY (Sno，Cno)     /*只能在表级定义主码*/
); 
```

### （2）实体完整性检查和违约处理

**插入或对主码列进行更新操作时，RDBMS按照实体完整性规则自动进行检查。包括：**

1. 检查主码值是否唯一，如果不唯一则拒绝插入或修改
2. 检查主码的各个属性是否为空，只要有一个为空就拒绝插入或修改

**检查记录中主码值是否唯一的一种方法是进行全表扫描**
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407113110920.png)

- 全表扫描是十分耗时的。为了避免对基本表进行全表扫描，关系数据库管理系统一般 都在主码上`自动建立一个索引`，如图5.2的B+树索引，通过索引查找基本表中是否已经存在新的主码值将大大提高效率。
- 例如，如果新插入记录的主码值是25，通过主码索引，从B+树的根结点开始查找，只要读取三个结点就可以知道该主码值已经存在，所以不能插入这条记录。这三个结点是根结点(51)、中间结点(1230)和叶结点(15 20 25)。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407113604395.png)

## 5.3 参照完整性—REFERENCES

### （1）参照完整性定义

**关系模型的参照完整性定义**

- 在CREATE TABLE中用`FOREIGN KEY`短语定义哪些列为外码
- 用`REFERENCES`短语指明这些外码参照哪些表的主码

**举个例子**

```sql
例如，关系SC中一个元组表示一个学生选修的某门课程的成绩，
（Sno，Cno）是主码。
Sno，Cno分别参照引用Student表的主码和Course表的主码 

定义SC中的参照完整性
CREATE TABLE SC
(Sno    CHAR(9)  NOT NULL， 
Cno     CHAR(4)  NOT NULL，  
Grade    SMALLINT，
PRIMARY KEY (Sno， Cno)，   /*在表级定义实体完整性*/
FOREIGN KEY (Sno) REFERENCES Student(Sno)，  
/*在表级定义参照完整性*/
FOREIGN KEY (Cno) REFERENCES Course(Cno)    
/*在表级定义参照完整性*/
);
```

### （2）参照完整性检查和违约处理

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407113927315.png)

**参照完整性违约处理**

1. 拒绝(NO ACTION)执行
   默认策略
2. 级联(CASCADE)操作
3. 设置为空值（SET-NULL）
   对于参照完整性，除了应该定义外码，还应定义`外码列是否允许空值`

```sql
［例4］  显式说明参照完整性的违约处理示例
CREATE TABLE SC
(Sno   CHAR(9)  NOT NULL，
Cno   CHAR(4)  NOT NULL，
Grade  SMALLINT，
PRIMARY KEY（Sno，Cno）， 				
FOREIGN KEY (Sno) REFERENCES Student(Sno) 
ON DELETE CASCADE     /*级联删除SC表中相应的元组*/
ON UPDATE CASCADE， /*级联更新SC表中相应的元组*/
FOREIGN KEY (Cno) REFERENCES Course(Cno) 	                    
ON DELETE NO ACTION 	
/*当删除course 表中的元组造成了与SC表不一致时拒绝删除*/
ON UPDATE CASCADE   
/*当更新course表中的cno时，级联更新SC表中相应的元组*/
);
```

- 经过测试，当UPDATE更新Student和Course表数据时，SC也自动更新
- 当删除Student的数据时，SC同步删除相应数据
- 当删除Course的数据时，拒绝删除，因为SC中有相应的外码数据，并设置了NO ACTION
- 当删除SC的数据时，对Student和Course无影响

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407115056909.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407115737221.png)

## 5.4 用户定义的完整性—CHECK

- 用户定义的完整性就是针对`某一具体应用的数据`必须满足的语义要求
- RDBMS提供，而不必由应用程序承担

### （1）属性上的约束条件定义

**CREATE TABLE时定义**

- 列值非空（NOT NULL）
- 列值唯一（UNIQUE）
- 检查列值是否满足一个布尔表达式（CHECK）

```sql
1.不允许取空值 

［例5］  在定义SC表时，说明Sno、Cno、Grade属性不允许取空值。

CREATE TABLE SC
(Sno  CHAR(9)  NOT NULL，	
Cno  CHAR(4)  NOT NULL，	
Grade  SMALLINT NOT NULL，	
PRIMARY KEY (Sno， Cno)，  
/* 如果在表级定义实体完整性，隐含了Sno，Cno不允许取空值，
则在列级不允许取空值的定义就不必写了 */
）;

2.列值唯一 

［例6］建立部门表DEPT，要求部门名称Dname列取值唯一，
部门编号Deptno列为主码

CREATE TABLE DEPT
(Deptno  NUMERIC(2)，
Dname  CHAR(9)  UNIQUE，/*要求Dname列值唯一*/
Location  CHAR(10)，
PRIMARY KEY (Deptno)
)；

3. 用CHECK短语指定列值应该满足的条件

［例7］Student表的Ssex只允许取“男”或“女”。

    CREATE TABLE Student
        (Sno  CHAR(9) PRIMARY KEY，
          Sname CHAR(8) NOT NULL，                     
          Ssex  CHAR(2)  CHECK (Ssex IN (‘男’，‘女’) ) ，                
              /*性别属性Ssex只允许取'男'或'女' */
          Sage  SMALLINT，
          Sdept  CHAR(20)
        );
```

### （2）属性上的约束条件检查和处理

- 插入元组或修改属性的值时，RDBMS检查属性上的约束条件是否被满足
- 如果不满足则操作被拒绝执行

### （3）元组上的约束条件的定义

- 在CREATE TABLE时可以用`CHECK`短语定义元组上的约束条件，即`元组级的限制`
- 同属性值限制相比，元组级的限制可以设置不同属性之间的取值的相互约束条件

```sql
［例9］  当学生的性别是男时，其名字不能以Ms.打头。
    CREATE TABLE Student
         (Sno    CHAR(9)， 
          Sname  CHAR(8) NOT NULL，
          Ssex    CHAR(2)，
          Sage   SMALLINT，
          Sdept  CHAR(20)，
          PRIMARY KEY (Sno)，
          CHECK (Ssex='女' OR Sname NOT LIKE 'Ms.%')
          /*定义了元组中Sname和 Ssex两个属性值之间的约束条件*/
        )；
性别是女性的元组都能通过该项检查，因为Ssex=‘女’成立；
当性别是男性时，要通过检查则名字一定不能以Ms.打头
```

### （4）元组上的约束条件检查和违约处理

- 插入元组或修改属性的值时，RDBMS检查元组上的约束条件是否被满足
- 如果不满足则操作被拒绝执行

## 5.5 完整性约束命名子句—CONSTRAINT

### 1) 约束种类

* 静态列级约束
* 静态元组约束
* 静态关系约束
* 动态列级约束
* 动态元组约束
* 东西关系约束



详细的约束

- 非空约束(not null)
- 唯一性约束(unique)
- 主键约束(primary key) PK
- 外键约束(foreign key) FK
- 检查约束(目前MySQL不支持、Oracle支持)



### 2) CONSTRAINT 约束语句格式：

```sql
CONSTRAINT <完整性约束条件名>
［PRIMARY KEY短语
   |FOREIGN KEY短语
   |CHECK短语］
```

举个例子：

```sql
［例10］  建立学生登记表Student，要求学号在90000~99999之间，
姓名不能取空值，年龄小于30，性别只能是“男”或“女”。
 CREATE TABLE Student
      (Sno  NUMERIC(6)
        CONSTRAINT C1 CHECK (Sno BETWEEN 90000 AND 99999),
        Sname  CHAR(20)  
        CONSTRAINT C2 check( NOT NULL),
        Sage  NUMERIC(3)
        CONSTRAINT C3 CHECK (Sage < 30),
        Ssex  CHAR(2)
        CONSTRAINT C4 CHECK (Ssex IN ( '男','女')),
        CONSTRAINT StudentKey PRIMARY KEY(Sno)
      );
在Student表上建立了5个约束条件，包括主码约束（命名为StudentKey）
以及C1、C2、C3、C4四个列级约束。
```

- 这个没有C2应该是为主键就忽略没显示叭
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407124643950.png)

**修改表中的完整性限制**

- 使用ALTER TABLE语句修改表中的完整性限制

```sql
［例13］  修改表Student中的约束条件，要求学号改为在900000~999999之间，
年龄由小于30改为小于40
可以先删除原来的约束条件，再增加新的约束条件
ALTER TABLE Student
DROP CONSTRAINT C1;
        
 ALTER TABLE Student
ADD CONSTRAINT C1 CHECK (Sno BETWEEN 900000 AND 999999);
        
ALTER TABLE Student
DROP CONSTRAINT C3;
        
ALTER TABLE Student
ADD CONSTRAINT C3 CHECK (Sage < 40);
```

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407124617670.png)





## 5.6 域中的完整性限制—DOMAIN

> 关于域的定义有些数据库可能不同，或者定义失败，得观看相关的手册深入学习，但是SQL中是有定义DOMAIN，初学先了解一下叭。

**SQL支持域的概念，并可以用`CREATE DOMAIN`语句建立一个域以及该域应该满足的完整性约束条件。**

```sql
［例14］建立一个性别域，并声明性别域的取值范围
           CREATE DOMAIN GenderDomain CHAR(2)
           CHECK (VALUE IN ('男'，'女') );
这样［例10］中对Ssex的说明可以改写为Ssex GenderDomain

［例15］建立一个性别域GenderDomain，并对其中的限制命名
           CREATE DOMAIN GenderDomain CHAR(2)
           CONSTRAINT GD CHECK ( VALUE IN ('男'，'女') );
           
［例16］删除域GenderDomain的限制条件GD。
           ALTER  DOMAIN  GenderDomain  
           DROP CONSTRAINT GD;
           
［例17］在域GenderDomain上增加限制条件GDD。
          ALTER  DOMAIN  GenderDomain  
         ADD CONSTRAINT GDD CHECK (VALUE IN ( '1'，'0') ); 
         
通过［例16］和［例17］，就把性别的取值范围由('男'，'女')改为 ( '1'，'0') 
123456789101112131415161718
```

## 5.7 断言—ASSERTION

> 关于断言还是和域一样，不同的数据库可能实现方式不同，初学先了解，后期再深入

- 在SQL中可以使用数据定义语言中的`CREATE ASSERTION`语句，通过声明性断言(declarative assertions)来指定更具一般性的约束。
- 可以定义涉及多个表或聚集操作的比较复杂的完整性约束。
- 断言创建以后，任何对断言中所涉及关系的操作都会触发关系数据库管理系统对断言的检查，任何使断言不为真值的操作都会被拒绝执行。

### （1）定义断言

标准语句格式：

```sql
CREATE ASSERTION <断言名> <CHECK子句>
```

- 每个断言都被赋予一个名字，<CHECK子句>中的约束条件与WHERE子句的条件表达式类似。

```sql
[例5.18]限制数据库课程最多 60名学生选修。
CREATE ASSERTION ASSE_SC_DB_ NUM
CHECK(60>=(SELECT count(*)/*此断言的谓词涉及聚集操作count的SQL语句*/
FROM Course,SC
WHERE SC.Cno=Course.Cno AND Course.Cname=数据库)
);

每当学生选修课程时，将在SC表中插入一条元组(Sno, Cno, NULL), 
ASSE_SC_DB_NUM断言被触发检查。如果选修数据库课程的人数已经超过60人，
CHECK子句返回值为“假”，对SC表的插入操作被拒绝。

[例5.19]限制每一 门课程最多60名学生选修。 
CREATE ASSERTION ASSE_SC_CNUMI
CHECK( 60>=ALL( SELECT count (*)/*此断言的谓词，涉及聚集操作count */
FROM SC							/*和分组函数group by的SQL语句*/
GROUP by cno );

[例5.20 限制每个学期每一门课程最多60名学生选修]
首先修改SC表的模式，增加一个“学期(TERM)”的属性。
ALTER TABLE SC ADD TERM DATE;
/*先修改SC表，增加TERM属性，它的类型是DATE*/

然后定义断言:
CREATE ASSERTION ASSE_SC_CNUM2
CHECK (60>=ALL ( select count (*) from SC group by Cno,TERM )); 
```

### （2）删除断言

```sql
DROP ASSERTION <断言名>;
```

- 如果断言很复杂，则系统在检测和维护断言上的开销较高，这是在使用断言时应该注意的。

## 5.8 触发器—TRIGGER

- 触发器（Trigger）是用户定义在关系表上的一类由`事件驱动`的特殊过程
  由服务器自动激活
- 可以进行更为复杂的检查和操作，具有更精细和更强大的数据控制能力

### （1）定义触发器

**CREATE TRIGGER语法格式:**

```sql
CREATE TRIGGER <触发器名>  
       {BEFORE | AFTER} <触发事件> ON <表名>
        FOR EACH  {ROW | STATEMENT}
      ［WHEN <触发条件>］
        <触发动作体>
```

**定义触发器的语法说明:**

1. 创建者：表的拥有者
2. 触发器名
3. 表名：触发器的目标表,不能建立在视图上
4. 触发事件：INSERT、DELETE、UPDATE
5. 触发器类型
   行级触发器（FOR EACH ROW）;
   语句级触发器（FOR EACH STATEMENT）;

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200407140148898.png)

- 例如,假设在［例11］的TEACHER表上创建了一个AFTER UPDATE触发器。如果表TEACHER有1000行，执行如下语句：
  `UPDATE TEACHER SET Deptno=5;`
- 如果该触发器为`语句`级触发器，那么执行完该语句后，触发动作只发生一次
- 如果是`行级`触发器，触发动作将执行1000次

1. 触发条件
   触发条件为真，则执行触发动作体，否则不执行;
   省略WHEN触发条件时，只要触发器激活（触发器事件）则立刻执行触发动作体;
2. 触发动作体
   触发动作体可以是一个匿名PL/SQL过程块;
   也可以是对已创建存储过程的调用;

```sql
［例18］  定义一个BEFORE行级触发器，
为教师表Teacher定义完整性规则“教授的工资不得低于4000元，
如果低于4000元，自动改为4000元”。
    CREATE TRIGGER Insert_Or_Update_Sal 
         BEFORE INSERT OR UPDATE ON Teacher  
        /*触发事件是插入或更新操作*/
         FOR EACH ROW                      /*行级触发器*/
        AS BEGIN                /*定义触发动作体，是PL/SQL过程块*/
              IF (new.Job='教授') AND (new.Sal < 4000) THEN   
              new.Sal :=4000;                
              END IF;
        END;       


［例19］定义AFTER行级触发器，当教师表Teacher的工资发生变化后
就自动在工资变化表Sal_log中增加一条相应记录

   首先建立工资变化表Sal_log
    CREATE TABLE Sal_log
        (Eno    NUMERIC(4)  references teacher(eno)，
          Sal     NUMERIC(7，2)，
          Username  char(10)，
          Date   TIMESTAMP
         )；
              
 [例19]（续）
CREATE TRIGGER Insert_Sal               	
    AFTER INSERT ON Teacher      	/*触发事件是INSERT*/
    FOR EACH ROW
    AS BEGIN
        INSERT INTO Sal_log VALUES(
           new.Eno，new.Sal，CURRENT_USER，CURRENT_TIMESTAMP);
    END;

[例19]（续）
CREATE TRIGGER Update_Sal            	
   AFTER UPDATE ON Teacher    	/*触发事件是UPDATE */
   FOR EACH ROW
   AS BEGIN 
     IF (new.Sal <> old.Sal) THEN INSERT INTO Sal_log VALUES(
          new.Eno，new.Sal，CURRENT_USER，CURRENT_TIMESTAMP);
     END IF;
  END;
```

> 这个可以在Oracle数据库里运行，但是因为我用的是SQL Sever数据库，所以运行不了，不同的数据库，触发器的实现略有不同，详情请查看相关数据库手册。

### （2）激活触发器

- 触发器的执行，是由`触发事件激活`的，并由数据库服务器自动执行
  一个数据表上可能定义了`多个触发器`
- 同一个表上的多个触发器激活时遵循如下的执行顺序：
  （1） 执行该表上的BEFORE触发器；
  （2） 激活触发器的SQL语句；
  （3） 执行该表上的AFTER触发器。

```sql
［例20］执行修改某个教师工资的SQL语句，激活上述定义的触发器。
     UPDATE Teacher SET Sal=800 WHERE Ename='王五';
执行顺序是：
执行触发器Insert_Or_Update_Sal
执行SQL语句“UPDATE Teacher SET Sal=800 WHERE Ename='王五';”
执行触发器Insert_Sal;
执行触发器Update_Sal 
```

### （3）删除触发器

**删除触发器的SQL语法：**
`DROP TRIGGER <触发器名> ON <表名>;`

触发器必须是一个已经创建的触发器，并且只能由具有相应权限的用户删除。

**［例21］ 删除教师表Teacher上的触发器Insert_Sal**

```sql
DROP TRIGGER Insert_Sal ON Teacher;
```



# 总结

数据完整性是为了防止数据库中存在不符合语义的概念，防止错误信息的输入和输出，即所谓垃圾进垃圾出所造成的无效操作和错误结果

数据的安全性是保护句酷防止恶意的破坏和非法的存取

* 安全性措施防范的对象是非法用户和非法对象
* 完整性防范措施的对象是不和语义的数据和不正确的数据

# 6. 关系数据库理论



![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020051223161173.png)

## 6.1 为什么要学习关系数据库规范化理论？

**感性认识：**

- 当我们面对一个实际问题时，我们应该如何去建数据库，建表，库的结构，表的结构我们该如何组织，才能更好的解决问题。
- 如何省内存，提高查询修改删除更新的效率？
- 如何避免可能出现的隐患，如修改删除更新插入等异常？
- 以上就是关系`数据库规范化理论`研究解决的问题,说白了就是告诉你如何才能设计出合适的库和表

**下面我们回顾几个概念和问题，以便更好地学习后面的关系数据库规范化理论**

### 6.1.1 基本概念回顾

- 关系：可简单的理解为二维表
- `关系模式：即二维表的逻辑结构`
- 关系数据库：指采用了关系模型来组织数据的数据库，其以行和列的形式存储数据，`关系型数据库这一系列的行和列被称为表，一组表组成了数据库`。
- 关系数据库的模式：即关系数据库的逻辑结构

### 6.1.2 关系模式的形式化定义

- 这里我们回顾一下《数据库系统概论》中对二维表结构的定义

> 关系模式由五部分组成，即它是一个五元组：
> R(U, D, DOM, F)
> R： 关系名,即表名
> U： `组成该关系的属性名集合`
> D： 属性组U中属性所来自的域。数据的取值范围和类型
> DOM： 属性向域的映象集合
> F： `属性组U上的一组数据依赖。`

**关系数据库规范化理论研究的就是R、F、U，之间的关系。
因为D和DOM对研究表的设计关系不大，所以在学习关系数据库规范化理论时可以将五元组简化成三元组**

> 三元组：`R（U, F）`
> 当且仅当U上的一个关系`r`满足`F`时，`r`称为`关系模式 R（U, F）的一个关系`

### 6.1.3 什么是数据依赖F？

**这里我们对`F`中的`数据依赖`进行简单解释，后面会详细叙述`函数依赖`和`多值依赖`。**

> `数据依赖`是`一个关系内部属性与属性之间的一种约束关系。`
> 这种约束关系是通过`属性间值的相等与否体现出来的数据间相关联系`。
> 它是现实世界属性间相互联系的抽象，是数据内在的性质，是语义的体现。

**数据依赖分类：**

- 函数依赖（Functional Dependency，简记为FD）

> 函数依赖极为普遍地存在于现实生活中。比如描述一个学生的关系，可以有学号(Sno)、姓名(Sname)、 系名(Sdept) 等几个属性。由于一个学号只对应一个学生，一个学生只在一一个系学习。因而当“学号”值确定之后，学生的姓名及所在系的值也就被唯一地确定了。`属性间的这种依赖关系类似于数学中的函数y=f(x)，自变量x确定之后，相应的函数值y也就唯一地确定 了。`

- 多值依赖（Multivalued Dependency，简记为MVD）
- 其他

### 6.1.4 数据依赖F对关系模式的影响

因为`关系数据库规范化理论`主要研究的是`三元组R(U,F)`，U我们都好理解，最重要的是F，这里我们简单的了解一下F对关系模式，即表的逻辑结构的影响，让我们理性的认识为什么学习`关系数据库规范化理论`

**举个例子：**

> [例1]建立一个描述学校教务的数据库,数据库涉及的对象有：
> 学生的学号（Sno）、所在系（Sdept）、系主任姓名（Mname）、课程名（Cname）、成绩（Grade）

这里我们用单一的关系模式Student来表示这些对象：
`Student <U、F>`
该关系的属性集合：
`U ＝｛ Sno, Sdept, Mname, Cname, Grade ｝`

**这里说明一下现实世界的事实语义，关于这些对象之间的联系：**
①一个系有若干学生，但一个学生只属于一个系。
②一个系只有一名(正职)负责人。
③一个学生可以选修多门课程，每门课程有若干学生选修。
④每个学生学习每一一门课程有一个成绩。

于是得到`属性组U上的一组函数依赖F`
F={Sno- > Sdept, Sdept- >Mname, (Sno, Cno)- >Grade}
(如图所示)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512114633879.png)

- 如果只考虑函数依赖这一种数据依赖， 可以得到一个描述学生的关系模式Student <U,F>。表6.1是某一时刻关系模式Student的一个实例，即数据表。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512114920249.png)

**这个关系模式设计的并不好,存在以下问题:**

#### 1️⃣ 数据冗余(Data redundancy)

- 比如，每一个系的系主任姓名重复出现，重复次数与该系所有学生的所有课程成绩出现次数相同，如表6.1所示。这将浪费大量的存储空间。

#### 2️⃣ 更新异常(update anomalies )

- 由于数据冗余，当更新数据库中的数据时，系统要付出很大的代价来维护数据库的完整性，否则会面临数据不一致的危险。 比如，某系更换系主任后，必须修改与该系学生有关的每一个元组。

#### 3️⃣ 插入异常(insertion anomalies )

- 如果一个系刚成立，尚无学生，则无法把这个系及其系主任的信息存入数据库。

#### 4️⃣ 删除异常( deletion anomalies)

- 如果某个系的学生全部毕业了，则在删除该系学生信息的同时，这个系及其系主任的信息也丢掉了。

**鉴于存在以上种种问题，可以得出这样的结论:**

- `Student关系模式不是一个好的模式`。
- `“好”的模式：`
  不会发生插入异常、删除异常、更新异常，数据冗余应尽可能少
- 原因：由存在于模式中的`某些数据依赖`引起的
- 解决方法：通过`分解关系模式`来`消除其中不合适 的数据依赖`

可以把这个单一模式分成3个关系模式：

- `S（Sno，Sdept，Sno → Sdept）;`
- `SC（Sno，Cno，Grade，（Sno，Cno） → Grade）;`
- `DEPT（Sdept，Mname，Sdept→ Mname）`

这三个模式都不会发生插入异常、删除异常的问题，数据的冗余也得到了控制。
`一个模式的数据依赖会有哪些不好的性质，如何改造一个不好的模式`，这就是接下来`2.规范化`要讨论的内容。

## 6.2 规范化

### 6.2.1 规范化研究什么？

- 规范化讨论如何`根据属性间依赖情况来判定关系是否具有某些不合适的性质`
- 通常`按属性间依赖情况来区分关系规范化程度`为`第一范式、第二范式、第三范式和第四范式等`
- 用来改造关系模式，`通过分解关系模式来消除其中不合适的数据依赖，以解决插入异常、删除异常、更新异常和数据冗余问题。`

- 函数依赖
- 码
- 范式
- 2NF
- 3NF
- BCNF
- 多值依赖
- 4NF

**`其中函数依赖、码是为了学习范式、1NF,2NF,3NF……打基础`**

### 6.2.2 函数依赖分类

- 函数依赖
- 平凡函数依赖与非平凡函数依赖
- 完全函数依赖与部分函数依赖
- 传递函数依赖

#### ① 函数依赖

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512124415426.png)

`注意:`函数依赖不是指关系模式R的某个或某些关系满足的约束条件，而是指R的一切关系均要满足的约束条件。

**以下是一个错误的例子：**
`sno->sdept，sno应该唯一决定sdept`
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512122121698.png)

> 函数依赖和别的数据依赖样是语义范畴的概念，只能根据语义来确定一个函数依赖。
> 例如，姓名→年龄这个函数依赖只有在该部门没有同名人的条件下成立。如果允许有同名人，则年龄就不再函数依赖于姓名了。

#### ② 平凡函数依赖与非平凡函数依赖

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512123441752.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512124308463.png)

#### ③ 完全函数依赖与部分函数依赖

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512124551469.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512124821869.png)

#### ④ 传递函数依赖

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512125425925.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512125812948.png)
**直接依赖这里我们举个例子：**
`BH(sno,idCard,address)`

> X：sno 学号
> Y：idCard 身份证号
> Z：address 住址
> X->Y，Y->X，X<->Y，Y->Z
> 所以我们说Z直接依赖于X

### 6.2.3 码

- 码是关系模式中的一个重要概念。在码的定义中有关码的若干定义， 这里用函数依赖的概念来定义码。
- 码唯一决定一个实体集

#### ① 候选码、超码、主码

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512173318920.png)

例题：

**例1：关系模式CTHRSG,** **若最小依赖集为F’={C →T, HR →C,CS →G,HS →R,HT →R}**

解：**L、N类属性为HS，LR属性为CTR。HS+=HS RCTG，包含全部属性，所以为唯一候选码** 

**例2：**

![img](https://gitee.com/fakerlove/picture_1/raw/master/20190602171609125.png)

解：**L或N类属性有E和C, LR类属性ADB，令X=EC,(EC)+=U,EC为R的唯一候选码。**

**例3：**

![img](https://gitee.com/fakerlove/picture_1/raw/master/20190602173853623.png)

**例4：**

![img](https://gitee.com/fakerlove/picture_1/raw/master/20190602175111634.png)

**例5：**

![img](https://gitee.com/fakerlove/picture_1/raw/master/20190602175141126.png)



#### ② 主属性和非主属性

**主属性与非主属性**

- 包含在任何一个候选码中的属性 ，称为`主属性（Prime attribute）`
- 不包含在任何码中的属性称为`非主属性（Nonprime attribute）`或`非码属性（Non-key attribute）`

**举几个例子：**

**[例2]**
关系模式S(Sno,Sdept,Sage)，单个属性Sno是`码`，
SC（Sno，Cno，Grade）中，（Sno，Cno）是`码`

**[例3]**
关系模式R（P，W，A）
P：演奏者 W：作品 A：听众
一个演奏者可以演奏多个作品
某一作品可被多个演奏者演奏
听众可以欣赏不同演奏者的不同作品
`码为(P，W，A)，即All-Key`

#### ③ 外部码

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512174053933.png)

### 6.2.4 范式

- 范式是符合某一种级别的关系模式的集合
- 关系数据库中的关系必须满足一定的要求。满足不同程度要求的为不同的范式。
- 级别越高，表设计的越合理

**范式的种类：**

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512174654832.png)
**各种范式之间存在联系：**

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512174723866.png)

- 某一关系模式`R为第n范式`，可简记为`R∈nNF。`
  一个低一级范式的关系模式，通过`模式分解`可以转换为若干个高一级范式的关系模式的集合，这种过程就叫`规范化`



#### ① 1NF

**1NF的定义:**

- 如果一个关系模式R的所有属性都是`不可分的基本数据项`，则`R∈1NF`
- 第一范式是对关系模式的最起码的要求。不满足第一范式的数据库模式不能称为关系数据库
- 但是满足第一范式的关系模式并不一定是一个好的关系模式

**以下是一个满足1NF，但不是好的关系模式的例子：**

> 关系模式 S-L-C(Sno, Sdept, Sloc, Cno, Grade)
> Sloc为学生住处，假设每个系的学生住在同一个地方

- 这个例子中存在函数依赖，不是一个好的关系模式

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512180223657.png)
**图形化表示：**
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512180252695.png)
**S-L-C不是一个好的关系模式，一个关系模式 R不属于2NF,就会产生以下几个问题:**

- (1)`插入异常`。假若要插入一个学生Sno=S7， Sdept =PHY， Sloc =BLD2， 但该生还未选课，即这个学生`无Cno`,这样的元组就插不进S-L-C中。因为`插入元组时必须给定码值，而这时码值的一部分 为空，因而学生的固有信息无法插入。`
- (2)`删除异常`。假定某个学生只选一门课，如S4就选了一门课C3，现在C3这门课他也不选了，那么C3这个数据项就要删除。而`C3是主属性，删除了C3，整个元组就必须一起删除，使得S4的其他信息也被删除了`，从而造成删除异常，即不应删除的信息也删除了。
- (3)`修改复杂`。某个学生从数学系(MA)转到计算机科学系(CS)，这本来只需修改此学生元组中的Sdept分量即可，但因为关系模式S-L-C中还含有系的住处Sloc属性，学生转系将同时改变住处，因而还必须修改元组中的Sloc分量。另外，如果这个学生选修了k门课，Sdept、 Sloc重复存储了k次，不仅`存储冗余度大`，而且必须无遗漏地修改k个元组中全部Sdept、Sloc 信息，造成`修改的复杂化`。

**为什么会有这些问题呢？**

- 原因：
  Sdept、 Sloc`部分函数依赖于码`。
- 解决方法(也就是2NF的处理方法)
  S-L-C`分解为两个关系模式`，以`消除这些部分函数依赖`
  SC（Sno， Cno， Grade）
  S-L（Sno， Sdept， Sloc）
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020051218241068.png)

#### ② 2NF

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512182506723.png)

- 采用投影分解法将一个1NF的关系分解为多个2NF的关系，可以在一定程度上减轻原1NF关系中存在的插入异常、删除异常、数据冗余度大、修改复杂等问题。
- 将一个1NF关系分解为多个2NF的关系，并不能完全消除关系模式中的各种异常情况和数据冗余。所以又引入了3NF。

#### ③ 3NF

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512182623958.png)
**这里我们对上面的2NF例子再次进行剖析：**![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512183539740.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512183600448.png)

**解决方法：**

- 采用投影分解法，把S-L`分解`为两个关系模式，以`消除传递函数依赖`：
  S-D（Sno， Sdept）
  D-L（Sdept，Sloc）
- S-D的码为Sno， D-L的码为Sdept。
- `分解后的关系模式S-D与D-L中不再存在传递依赖`

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512183916790.png)

- 采用投影分解法将一个2NF的关系分解为多个3NF的关系，可以`在一定程度上解决原2NF关系中存在的插入异常、删除异常、数据冗余度大、修改复杂等问题。`
- 将一个2NF关系分解为多个`3NF`的关系后，`仍然不能完全消除关系模式中的各种异常情况和数据冗余。`

#### ④ BCNF

> BCNF ( Boyce Codd Normal Form)是由Boyce与Codd提出的，比上述的3NF又进了一步，`通常认为BCNF是修正的第三范式，有时也称为扩充的第三范式。`

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512205231973.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512210152674.png)
**下面用几个例子说明属于3NF的关系模式有的属于BCNF，但有的不属于BCNF。**

**[例5] 关系模式C（Cno，Cname，Pcno）**
C∈3NF
C∈BCNF

> 关系模式C(Cno, Cname, Peno)， 它`只有一个码Cno, 这里没有任何属性对Cno部分依赖或传递依赖，所以C∈3NF。`同时C中`Cno`是`唯一的决定因素`， 所以C ∈BCNF。

**[例6]关系模式S(Sno, Sname, Sdept, Sage)**
假定S有两个码Sno，Sname
S∈3NF。
S ∈ BCNF

> `假定Sname也具有唯一性， 那么S就有两个码，这两个码都由单个属性组成，彼此不相交。其他属性不存在对码的传递依赖与部分依赖，所以S∈3NF。`
> 同时S中除Sno、Sname外没有其他`决定因素`，所以S也属于BCNF。

**［例7］关系模式SJP（S，J，P）**
SJP∈3NF，
SJP∈BCNF

> [例6.7]关系模式SJP(S, J, P)中，S是学生，J表示课程，P表示名次。
> 每一个学生选修每门课程的成绩有一定的名次，
> 每门课程中每一名次只有一个 学生(即没有并列名次)。
> 由语义可得到下面的`函数依赖:`
> `(S,J)→P; (J,P)→S`
> 所以(S,J) 与(J,P)都可以作为`候选码`。
> `这两个码各由两个属性组成，而且它们是相交的。`
> `这个关系模式中显然没有属性对码传递依赖或部分依赖。`
> 所以SJP∈3NF，而且除(S,J)与(J,P)以外没有其他决定因素，所以SJP∈BCNF。

**[例8] 关系模式STJ(S, T, J)中，S表示学生，T表示教师，J表示课程。**

> 每一教师只教一门课，
> 每门课有若干教师，
> 某一学生选定某门课， 就对应一个固定的教师。
> 由语义可得到如下的函数依赖。
> `(S,J)→T，(S,T)-J, T→J`
> `函数依赖`关系可以用如图表示
> ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512211613690.png)
> 这里(S,J)、 (S,T)都是`候选码`。
> STJ是3NF,因为`没有任何非主属性对码传递依赖或部分依赖`，
> 但`STJ不是BCNF关系`，`因为T是决定因素，而T不包含码。`

**如何解决才能让STJ是BCNF关系呢？**
![ ](https://gitee.com/fakerlove/picture_1/raw/master/20200512211930747.png)

#### ⑤ 3NF与BCNF的关系

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512212004587.png)

- 3NF和BCNF是在函数依赖的条件下对模式分解所能达到的分离程度的测度。
- 一个模式中的关系模式如果都属于`BCNF`,那么在函数依赖范畴内它已实现了彻底的分离，`已消除了插入和删除的异常。`
- `3NF的“不彻底”性`表现在`可能存在主属性对码`的`部分依赖`和`传递依赖`。

####  6 4NF

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512225549804.png)![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020051222302596.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020051222555721.png)

### 6.2.5 多值依赖

- 前面我们讲了数据依赖分为函数依赖和多值依赖，函数依赖在上面已经叙述了，这里我们再讨论多值依赖。

**用一个例子引入多值依赖：**

**[例9] 学校中某一门课程由多个教师讲授，他们使用相同的一套参考书。每个教员可以讲授多门课程，每种参考书可以供多门课程使用。**

可以用一个非规范化的关系来表示教师T、课程C和参考书B之间的关系
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512221454548.png)
把这张表变成一张规范化的二维表：
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512221538262.png)

- 关系模型Teaching (C, T,B)的`码是(C, T, B)`，即`all-key`,因而`Teaching∈BCNF。`
- 但是当`某一课程(如物理)增加一名讲课教师(如周英)时`，必须插入多个(这里是三个)元组:
  (物理，周英，`普通物理学`)，(物理，周英，`光学原理`)，(物理，周英，`物理习题集`)。
- 同样，`某一门课(如数学)要去掉一本参考书(如微分方程)`，则必须删除多个(这里是两个)元组:
  (数学，`李勇`，`微分方程`)，(数学，`张平`，`微分方程`)。
- 可以看出对数据的增删改很不方便，数据的冗余也十分明显。
- 仔细考察这类关系模式，发现它具有一种称之为`多值依赖`(Multi-Valued Dependency, MVD)的数据依赖。

#### ① 多值依赖的定义

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512222007941.png)

> 例如，在关系模式Teaching中，对于一个(物理，光学原理)有一组T值{李勇，王军}，这组值仅仅决定于课程C上的值(物理)。
> 也就是说对于另一个(物理，普通物理学)，它对应的一组T值仍是{李勇，王军}，尽管这时参考书B的值已经改变了。
> 因此`T多值依赖于C，即C→→T`。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020051222302596.png)

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512223155821.png)

#### ② 平凡多值依赖和非平凡多值依赖

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512223622975.png)
**下面再举一个具有多值依赖的关系模式的例子。**
![ ](https://gitee.com/fakerlove/picture_1/raw/master/20200512223843379.png)

- 对于W的每一个值Wi, S有一个完整的集合与之对应而不问C取何值。所以W→→S(多值依赖)。
  ![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512224201700.png)

**如果用图下图来表示这种对应**
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512224323428.png)

- 则对应W的某一个值Wi的全部S值记作{S}wi (表示此仓库工作的全部保管员)
- 全部C值记作{C}wi (表示在此仓库中存放的所有商品)。
- 应当有{S}wi中的每一个值和{C}wi中的每一个C值对应。
- 于是{S}wi与{C}wi之间正好形成一个完全二分图，因而`W→→S`。
- 由于C与S的完全对称性，必然有`W→→C`成立。

**多值依赖具有以下性质:**

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512224720708.png)

#### ③ 多值依赖与函数依赖的区别

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512225033463.png)



### 6.2.6 规范化小结—重点归纳步骤

* 关系模式R中的属性全是属性

* **任何二元关系模式中的最高范式必定是 BCNF**

- 关系数据库的规范化理论是数据库逻辑设计的工具
- 目的：尽量消除插入、删除异常，修改复杂，数据冗余
- 基本思想：逐步消除数据依赖中不合适的部分
  实质：`·概念的单一化·`

**关系模式规范化的基本步骤:**

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200512225949740.png)



## 6.3 数据依赖的公理系统

### 6.3.1 Armstrong公理的推论

- **合并规则**：若X→Y，X→Z同时在R上成立，则X→YZ在R上也成立。
- **分解规则**：若X→W在R上成立，且属性集Z包含于W，则X→Z在R上也成立。
- **伪传递规则**：若X→Y在R上成立，且WY→Z，则XW→Z。

#### 推论

**一、Armstrong公理系统设关系模式R<U,F>，其中U为属性集，F是U上的一组函数依赖，那么有如下推理规则：**

1. **A1自反律**：若Y⊆X⊆U，则X→Y为F所蕴含；
2. **A2增广律**：若X→Y为F所蕴含，且Z⊆U，则XZ→YZ为F所蕴含；
3. **A3传递律**：若X→Y，Y→Z为F所蕴含，则X→Z为F所蕴含。

根据上面三条推理规则，又可推出下面三条推理规则：

1. **合并规则**：若X→Y，X→Z，则X→YZ为F所蕴含；
2. **伪传递规则**：若X→Y，WY→Z，则XW→Z为F所蕴含；
3. **分解规则**：若X→Y，Z⊆Y，则X→Z为F所蕴含。

**引理**：X→A1A2…Ak成立的充分必要条件是X→Ai成立(i=1,2,…,k)。

#### Armstrong公理系统的证明

1. **A1自反律**：若Y X U，则X→Y为F所蕴含
   证明1
   设Y⊆X⊆U。
   对R<U,F>的任一关系r中的任意两个元组t,s：
   若t[X]=s[X]，由于Y X，则有t[Y]=s[Y]，所以X→Y成立，自反律得证。
2. **A2增广律**：若X→Y为F所蕴含，且Z U，则XZ→YZ为F所蕴含
   证明2
   设X→Y为F所蕴含，且Z⊆U。
   对R<U,F>的任一关系r中的任意两个元组t,s：
   若t[XZ]=s[XZ]，由于X ⊆XZ，Z⊆ XZ，根据自反律，则有t[X]=s[X]和t[Z]=s[Z]；
   由于X→Y，于是t[Y]=s[Y]，所以t[YZ]=s[YZ]；所以XZ→YZ成立，增广律得证。
3. **A3传递律**：若X→Y，Y→Z为F所蕴含，则X→Z为F所蕴含
   证明3
   设X→Y及Y→Z为F所蕴含。
   对R<U,F>的任一关系r中的任意两个元组t,s：
   若t[X]=s[X]，由于X→Y，有t[Y]=s[Y]；
   再由于Y→Z，有t[Z]=s[Z]，所以X→Z为F所蕴含，传递律得证。
4. **合并规则**：若X→Y，X→Z，则X→YZ为F所蕴含
   证明4
   因X→Y ，所以X→XY （增广律 XX→XY即X→XY）
   因X→Z ，所以XY→YZ （增广律）
   因X→XY，XY→YZ
   故X→YZ （传递律）
5. **伪传递规则**：若X→Y，WY→Z，则XW→Z为F所蕴含
   证明5
   因X→Y ，所以WX→WY （增广律）
   因WY→Z ，所以XW→Z （传递律）
6. **分解规则**：若X→Y，Z∈Y，则X→Z为F所蕴含
   证明6
   因Z∈Y 　所以Y→Z （自反律）
   因X→Y 所以X→Z （传递律）

#### 特点

**有效性**是指由F出发根据Armstrong公理推导出来的函数依赖一定在F的闭包中。

**完备性**是指F的闭包中的每一个函数依赖，一定可以由F出发通过Armstrong公理推导出来

因此根据有效性和完备性→引理： 设F为属性集U上的一组函数依赖，X、Y⊆U，X→Y能由F根据Armstrong推导出来的充要条件是Y⊆F的闭包。



### 6.3.2 闭包及其计算

- **定义1**：设F是关系模型R的一个函数依赖集，X,Y是R的属性子集，如果从F中的函数依赖能够推出X→Y，则称F[1]X→Y。
- **定义2**：被F逻辑蕴涵的函数依赖的全体构成的集合，称为F的闭包，记作F+。
- **定义3**：设F是属性集U上的一组函数依赖，则属性集X关于F的闭包X+F定义为X+F={A|A∈U且X→A可由F经Armstrong公理导出}，即X+F={A|X→A∈F+}。
- **定理1**：设关系模型R(U)，F为其函数依赖集，X，Y为U的真子集，则从F推出X→Y的充要条件是Y是X+F的真子集。



#### 1) 首先理解什么是F+ (函数依赖集F的闭包)

![F+](https://gitee.com/fakerlove/picture_1/raw/master/20181125205358907.png)

##### 例题

![题目](https://gitee.com/fakerlove/picture_1/raw/master/20181125205416554.png)
![答案](https://gitee.com/fakerlove/picture_1/raw/master/20181125205432478.png)







#### 2) 属性闭包

![属性闭包](https://gitee.com/fakerlove/picture_1/raw/master/20181125205455552.png)

**`简单来说，属性闭包X+指的就是 所有X可以决定的属性的集合`**
我们也可以用属性闭包判断 X - > Y 是否蕴含于F

##### 一道求属性闭包的例题

![属性闭包例题](https://gitee.com/fakerlove/picture_1/raw/master/2018112520552176.png)
**（1）求A+，先把A所决定的所有的属性依次扫描：**
A+=A
A0=AB （因为有A -> B存在，所以A决定了B，就把B和A放在一起）
A1=ABC （由于A0=AB, AB中的B又决定了C（B->C），所以我们把C也加入属性闭包的集合中）
ABC没有可以决定的属性了，因此最终A+=ABC
**（2）求属性集AD的闭包（AD+）**
这道题和（1）题同理，
首先看F中是否有AD直接决定的属性，看了一下，发现没有 AD-> a 的情况存在
然后，我们考虑AD中的A或D是否有直接决定的属性，扫描一下，发现有！
AD+=AD
AD0=ADB (因为有A->B，所以把B加入属性闭包)
AD1=ADBC (因为第二项是B->C，所以把C也加入属性闭包)
因此最后 AD+ = ADBC



`文字化表述，如何求闭包`

举例子：有关系模式R<U,F>，U={A,B,C,D,E},F={AB→C,B→D,C→E,EC→B,AC→B}，求AB的闭包

①要求AB的闭包，因此先找出来函数依赖F中，左侧包含AB或者A、B的函数依赖：AB→C，B→D。

②令X(0)=AB，Y=CD（根据①的右侧推导），X(1)=X(0)∪Y=ABCD（左侧与右侧的并集）

③进行检验X(0)=X(1)?不等于。继续找左侧为ABCD子集（例如ABC、AC、C）的函数依赖：C→E、AC→B。

④再次进行X(2)=X(1)∪BE=ABCDE

⑤进行检验X(0)=X(2)？也不等于，但是X(2)=U。因此结束，AB的闭包为ABCDE。

因此判断条件有两个就是①是X(0)=X(i) ②是X(2)=U



 ## 6.4 模式分解

### 6.4.1 概念

![](https://gitee.com/fakerlove/picture_1/raw/master/20161229162846498)



> * 分解具有无损连接性
> * 分解要保持函数依赖
> * 分解既要保持函数依赖，又要保持无损连接性



### 6.4.1 判断是否无损连接

#### 算法

- 对于一个分解，有k个子集，n个属性，建立一张k行n列的初始表，对于每一行也就是分解的每个子集，把该分解子集出现的属性对应的列写上ajaj，否则写上bijbij
- 对于每一个依赖，找到左部属性对应的列，根据行的值分组，对于行的值相同的这些行，查看对应右部属性的列，如果这些格子里有a值，那把所有这些格子改成a值，如果没有，改成行最小的b值。**如果某个b值改成a值，那么其他行(不属于当前操作的行)的相同b值也要改成a值**。
- 如果不变则停止，如果出现有一行为a1 a2 ... an，那么说明该连接为无损连接。

#### 例题

已知R<U,F>，U={A,B,C,D,E}，F={A→C,B→C,C→D,DE→C,CE→A}，R的一个分解为R1(AD)，R2(AB)，R3(BE)，R4(CDE)，R5(AE)，判断这个分解是否具有无损连接性。

- 根据每个分解的属性，构造出初始表
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211054351402115.png)
- 然后看第一个依赖A->C，找到A对应的第一列，其中1 2 5行的值相等，找到C对应的第三列，对应格子没有a值，所以全部改成b13b13。
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211056092031146.png)
- 同理看第二个依赖，B->C，把b33b33改成b13b13。
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211056516099856.png)
- 以此类推
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211057216409447.png)
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211057502961728.png)
- ![img](https://gitee.com/fakerlove/picture_1/raw/master/211058348282823.png)
- 最后第三行有a1 a2 a3 a4 a5，所以该分解具有无损连接性。

### 6.4.2 3NF和保持函数依赖的分解

#### 算法

- F=F的最小依赖集
- U0U0={不在F出现的属性}
- U=U-U0U0
- 若F中有函数依赖X->A，使得XA=U，那么分解就是R本身
- 如果没有，将剩下的F按左部分组，得到UiUi，分解就是{R1R1<U1U1,F1F1>，...} ∪ R0R0<U0U0,F0F0>

### 6.4.3 3NF和保持函数依赖和具有无损连接性的分解

#### 算法

- 求出3NF和保持函数依赖的分解。
- X是R的码，让已有的分解∪上一个{R∗R∗<X,FXFX>}。
- 如果分解中有某个UiUi属于X，那么删掉该UiUi，如果X属于某个UiUi，那么删掉。

### 6.4.4 BCNF和具有无损连接性的分解

#### 算法

- 类似递归的方法，首先判断自身是不是BC范式，如果是，无需分解。
- 否则，找到当前关系R的主码，找到一个左边不含主码的依赖X->A，设U1=A，分解出去，**剩下的U2=U-{A}**作为一个关系模式，继续重复上面的步骤。
- 根据X->A的选择的不同，得到的分解也是不同。

### 6.4.5 4NF和具有无损连接性的分解

#### 算法

- 求出BCNF和具有无损连接性的分解。
- 对于一个关系R<U,F>，如果多值依赖X-->Y成立，则分解{R1<X,Y>,R2<X,Z>)}具有无损连接性，其中Z=U-X-Y。







# 7. 数据库设计



![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610115456198.png)

## 7.1 数据库设计概述及六步骤简介

> 数据库设计是指对于一个给定的应用环境，构造最优的数据库模式，建立数据库及其应用系统，使之能够有效地存储数据，满足各种用户的应用需求。

1. 数据库设计的特点
   数据库设计是一项涉及多学科的综合性技术，又是一项庞大的工程项目，具有如下特点：
   (1) 数据库建设是硬件、软件和干件（技术和管理的界面）的结合。
   (2) 数据库设计应该和应用系统设计相结合。
2. 数据库设计方法
   常用的数据库设计方法如下：
   （1）新奥尔良方法：将数据库设计分为若干阶段和步骤
   （2）基于 E-R 模型的设计方法：概念设计阶段广泛采用
   （3）基于 3NF 的设计方法：逻辑阶段可采用的有效方法
   （4）ODL（Object Definition Language）方法：面向对象的数据库设计方法
   （5）计算机辅助设计：ORACLE Designer 2000、SYBASE PowerDesigner
3. `数据库设计的基本步骤`
   数据库设计分为 6 个阶段：
   （1）需求分析：准确了解与分析用户需求（包括数据与处理）。
   （2）概念结构设计：对用户需求进行综合、归纳与抽象，形成一个独立于具体 DBMS的概念模型。
   （3）逻辑结构设计：将概念结构转换为某个 DBMS 所支持的数据模型，并对其进行优化。
   （4）物理结构设计：为逻辑数据模型选取一个最适合应用环境的物理结构（包括存储结构和存取方法）。
   （5）数据库实施：建立数据库，编制与调试应用程序，组织数据入库，并进行试运行。
   （6）数据库运行和维护：对数据库系统进行评价、调整与修改。

> 需求分析和概念设计独立于任何数据库管理系统
> 逻辑设计和物理设计与选用的DBMS密切相关

## 7.2 需求分析—步骤一

> 需求分析是整个数据库设计过程中最重要的步骤之一，是后继各阶段的基础。在需求分析阶段，从多方面对整个组织进行调查，收集和分析各项应用对信息和处理两方面的需求。



![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610121033947.png)

### 7.2.1 收集资料

收集资料是数据库设计人员和用户共同完成的任务。确定企业组织的目标，从这些目标导出对数据库的总体要求。通过调研，确定由计算机完成的功能。

### 7.2.2 分析整理

分析的过程是对所收集到的数据进行抽象的过程，产生求解的模型。

### 7.2.3 数据流图

采用数据流图来描述系统的功能。数据流图可以形象地描述事务处理与所需数据的关联，便于用结构化系统方法，自顶向下，逐层分解，步步细化。

### 7.2.4 数据字典

对数据流图中的数据流和加工等进一步定义，从而完整地反映系统需求。
**数据字典的用途：**
进行详细的数据收集和数据分析所获得的主要结果
**数据字典的内容：**
数据项
数据结构
数据流
数据存储
处理过程



第一阶段收集的基础数据用数据字典来描述

### 7.2.5 用户确认

需求分析得到的数据流图和数据字典要返回给用户，通过反复完善，最终取得用户的认可。



## 7.3 概念结构设计—步骤二

> 概念设计阶段的目标是产生整体数据库概念结构，即概念模式。概念模式是整个组织各个用户关心的信息结构。描述概念结构的有力工具是 E-R 模型。

### 7.3.1 E-R 模型

> **E-R**数据模型是一个广泛用于数据库设计的数据模型，提供了一个方便的图形化表示方法以查看数据、联系和约束。

#### 1) 概念

**实体-联系（entity-relationship, E-R）模型**采用三个基本概念：实体集、联系集、属性。

##### 实体集

数据库包括一组实体集，每个实体集包括任意数量的相同类型的实体。

实体是在现实世界中存在并且区别于其他对象的对象。我们通过把每个实体痛描述该实体的一组属性相关联来表示区别。相同类型的实体的集合为**实体集**。

* 实体（entity）：现实世界中可区别于所有其他对象的一个”事物“或”对象“。每个实体有一组性质，其中一些性质的值可以唯一地标识一个实体。实体可以是实在或抽象的。
* 实体集（entity set）：相同类型（具有相同性质/属性）的一个实体集合。(e.g. 一所给定大学的所有教师的集合定义为实体集instructor)实体集不必互不相交。(e.g. 一个person实体可以是instructor实体、或student实体、或既是instructor实体又是student实体、或都不是。)
* 外延（extension）：实体集的外延指术语实体集的实体的实际集合。(e.g. 大学中实际教师的集合构成了实体集instructor的外延)
* 属性（attribute）：实体集中每个成员所拥有的描述性性质。实体通过一组属性来表示；为某实体集指定一个属性表明数据库为该实体集中每个实体存储相似的信息，但每个实体在每个属性上都有各自的**值（value）**。

 

##### 联系集

**联系**是多个实体间的关联。相同类型的联系的集合为**联系集**。

**联系（relationship）：**多个实体间的相互关联。

**联系集（relationship set）：**相同类型联系的集合。

联系集是n≥2个（可能相同的）实体集上的数学关系。联系集R是

{ (e1, e2, …, en) | e1∈E1, e2∈E2, …, en∈En } 的一个子集，其中E1, E2, …, En为实体集，(e1, e2, …, en)为一个联系。

**参与：**实体集之间的关联。(e.g. 实体集E1, E2, …, En参与（participate）联系集R。)

相同的实体集可能会参与到多于一个联系集中。

**二元（binary）联系集**：设计两个实体集的联系集。数据库系统中的大部分联系集都是二元的，有时联系集会涉及多于两个实体集。

**度（degree）：**参与联系集的实体集的数目称为联系集的度。(e.g. 二元联系集的度为2，3元联系集的度为3。)

**角色（role）：**实体在联系中扮演的功能称为实体的角色。（隐含，一般并不指定。）

在**自环**（**recursive**，i.e. 同样的实体集以不同角色参与一个联系集多于一次）联系集中，有必要使用显式的角色名指明实体是如何参与联系实例的。

联系也可具有**描述性属性（descriptive attribute）**。(e.g. 实体集instructor和student之间的联系集advisor，可将属性date作为描述性属性与该联系关联。)

**联系实例（relationship instance）：**E-R模式中的一个联系实例表示所在建模的现实世界企业中命名实体的一个关联。(e.g. 一个教师ID为45565的instructor实体Katz和一个学生ID为12345的student实体Shankar参与到advisor的一个联系实例中)

给定的联系集中的一个联系实例必须是由其参与实体唯一标识的（不必使用描述属性）。

 

##### 属性

**域（domain）/值集（value set）：**每个属性都有的一个可取值的集合。

实体集的属性是将实体集映射到域的函数，每个实体可以用一组（属性，数据值）对来表示。

 

E-R模型中的属性可进行如下划分：

·简单（simple）属性/复合（composite）属性：

简单属性不能划分为更小的部分；

复合属性可以划分为更小的部分（其他属性）。(e.g. 属性name可设计为一个包括first_name、middle_initial和last_name的复合属性) 复合属性可以有层次，子属性可进一步划分。

·单值（single-alued）属性/多值（mutivalued）属性：

单值属性对一个特定的实体都只有单独的一个值；

多值属性对一个特定的实体有对应的一组值。用花括号表示属性是多值的。(e.g. instructor实体集可有{ phone_number }属性，每个教师可以有0到多个电话号码。) 可对多只属性的取值数目设置上、下界。

·派生（derived）属性：可从别的相关属性或实体派生出来。(e.g. instructor实体集可有属性student_advised表示一个教师指导了多少个学生，可通过统计与一个教师相关联的所有student实体的数目来得到该属性的值) 派生属性的值不进行存储，而是在需要时计算出来。

基属性：存储的属性

#####  约束

**1.** **映射基数**

**映射基数（mapping cardinality）/基数比率：**表示一个实体通过一个联系集能关联的实体的个数。（可用于描述二元联系集和涉及多于两个实体集的联系集）

对于实体A和B之间的二元联系集R，映射基数必然是以下情况之一：

·一对一（one-to-one）：A中的一个实体至多与B中的一个实体相关联，B中的一个实体也至多与A中的一个实体相关联；

·一对多（one-to-many）：A中的一个实体可与B中任意数目（0到多个）实体相关联，B中的一个实体至多与A中的一个实体相关联；

·多对一（many-to-one）：A中的一个实体至多与B中的一个实体相关联，B中的一个实体可与A中任意数目实体相关联；

·多对多（many-to-many）：A中的一个实体可与B中任意数目实体相关联，B中的一个实体可与A中任意数目实体相关联。

![img](https://gitee.com/fakerlove/picture_1/raw/master/1126979-20180106201315518-249044157.png)

 

**2.** **参与约束**

如果实体集E中的每个实体都参与到联系集R的至少一个联系中，实体集E在联系集R中的参与称为**全部的（total）**；

如果实体集E中只有部分实体参与到联系集R的联系中，实体集E到联系集R的参与称为**部分的（partial）**。

 



#### 2) 基本 E-R 模型

##### 基本结构

> 分割为两部分的矩形：代表实体集。第一部分（有阴影）包含实体集的名字，第二部分包含实体集中所有属性的名字；
>
> 菱形：代表联系集；
>
> 未分割的矩形：代表联系集的属性。构成主码的属性以下划线标明；
>
> 线段：将实体集连接到联系集；
>
> 虚线：将联系集属性连接到联系集；
>
> 双线：显示实体在联系集中的参与度；
>
> 双菱形：代表连接到弱实体集的标志性联系集。



E-R 模型通过 E-R 图表示出来。
将所有实体属性和实体之间的联系均描述出来就构成了一个 E-R 图
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020061012072890.png)
**（2）基本 E-R 模型的扩展**
**数据抽象**
一般有 3 种抽象：
(1)分类: 它抽象了对象值和型之间“is member of”的语义。例如：“张英”是“学生”实体中的一员。
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610120502912.png)
(2)聚集 :它抽象了对象内部类型和成分之间“is part of”的语义。例如：若干属性的聚集组成了实体型。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610120538664.png)
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610120617314.png)
(3)概括 :它抽象了类型之间“is subset of”的语义。
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610120637304.png)
**依赖联系**

> 在现实世界中，常常有某些实体对于另一些实体具有很强的依赖关系，即一个实体的存在必须以另一实体的存在为前提。通常把前者称为弱实体。
> 在E-R图中，用双线框表示弱实体，用指向弱实体的箭头表明依赖联系。

**超类和子类**

> 概括定义了类型之间的一种子集联系。
> 例如：学生是一个实体型，本科生、研究生也是实体型。本科生、研究生均是学生的子集。把学生称为超类，本科生、研究生称为学生的子类。
> 在E-R图中，用双竖边的矩形框表示子类，用直线加小圆圈表示超类-子类联系。
> 子类继承超类上定义的全部属性，其本身还可包含其他属性。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610120426133.png)





#### 3) 扩展的E-R模型

##### ISA联系

##### 基数约束

##### Part-of 联系



#### 4) UML

##### 概念

> * UML是一种常用的建模语言。UML类图广泛用于对类建模以及一般的数据建模。
>
> * **对象：**UML类图为对象建模，对象类似实体，包含属性和方法。类图可以说明对象的属性和方法。
>
> * **方法：**UML类图中另外提供的一组函数，可在对象属性的基础上调用以计算值，或更新对象本身。
>
>   UML类图不支持复合或多值属性，派生属性与不带参数的函数等价；
>
>   UML类图支持封装，允许函数和属性带有前缀”+”、”-“或”#”，分别表示公共、私有以及受保护的访问。私有属性只能在类的方法中使用，受保护的属性只能在类和它的子类的方法中使用。
>
> * 关联（association）：在UML类图中联系集称为关联。通过画一条线段连接实体集表示二元联系集，联系集的名称写在线段附近。可用以下两种方式说明联系集：
>
>   a. 可将角色名称写在靠近实体集的线段上，说明联系集中一个实体集的角色；
>
>   b. 可将联系集的名字和属性一起写在方框里，用虚线将该方框连接到表示联系集的连线上。该方框可看作一个实体集，可与其他实体一起参与联系。

##### 组成部分

**统一建模语言（Unified Modeling Language, UML）：**为建立软件系统的不同部分的规范定义而提出的一个标准。组成部分包括

* 类图（class diagram）：类似ER图；
* 用况图（use case diagram）：说明用户和系统之间的交互，特别是用户所执行任务中的每一步操作；
* 活动图（activity diagram）：说明系统不同部分之间的任务流；
* 实现图（implementation diagram）：在软件构件层和硬件构件层说明系统的各组成部分以及它们之间的联系。

#####  约束

UML中使用l..h形式表示**基数约束**，i表示参与联系的实体的最小个数，h表示最大个数。但约束位置与E-R图中正好相反。

e.g.

E2边上的约束0..*和E1边上的0..1表示每个E2实体可以参与至多一个联系，而每个E1实体可以参与任意多的联系，即该联系是从E2到E1多对一的。

可将单个值（如1或*）卸载边上，单个值1等价1..1，单个值*等价0..*。

UML类图支持概化，与E-R图基本相同，包括不想交概化和重叠概化的表示方式。

UML类图还包含一些与E-R表示法并不对应的表示法。

e.g. 连接两个实体的一条线的一端有一个小菱形，表示菱形这一端的实体集包含另一个实体集(e.g. 一个车辆实体可能包含一个发动机实体)。（包含关系在UML中称为”聚合“，注意不应与E-R图中的聚合的含义混淆。）

UML类图还提供表示面向对象语言的特征的表示法（e.g. 接口）。



### 7.3.2 建立 E-R 模型

（1）设计局部 E-R 模型
确定局部结构范围
定义实体
联系定义
属性分配

（2）设计全局 E-R 模型
确定公共实体类型
局部E-R模型的合并
消除冲突

（3）全局 E-R 模型的优化
实体类型的合并
冗余属性的消除
冗余联系的消除



#### 局部ER图合并全局ER图冲突

* 结构冲突
* 命名冲突
* 属性冲突



## 7.4 逻辑结构设计—步骤三

> 逻辑结构设计就是把上述概念模型转换成为某个具体的数据库管理系统所支持的数据模型。

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610121706852.png)

### 7.4.1 E-R 模型向关系模式的转换

**转换原则:**
（1）每一个实体类型转换为一个关系模式，实体的属性就是关系的属性，实体的码就是关系的码。
（2）联系的转换
① 一般1:1，1:m联系不产生新的关系模式，而是将一方实体的码加入到多方实体对应的关系模式中，联系的属性也一并加入。
②m:n联系要产生一个新的关系模式，该关系模式由联系涉及实体的码加上联系的属性（若有）组成。

**具体做法：**

#### 两实体间的 1:1 联系

> 一个 1:1 联系可以转换为一个独立的关系模式，也可以与任意一端对应的关系模式合并。如果转换为一个独立的关系模式，则与该联系相连的各实体的码以及联系本身的属性均转换为关系的属性，每个实体的码均是该关系的候选码。如果与某一端实体对应的关系模式合并，则需要在该关系模式的属性中加入另一个关系模式的码和联系本身的属性。可将任一方实体的主码纳入另一方实体对应的关系中，若有，联系的属性也一并纳入。

例如，如图 6.1 所示的 E-R 图可转换为如下关系模式：
工厂（厂号，厂名，地点，姓名，任期）
厂长（姓名，性别，年龄）
或者：
工厂（厂号，厂名，地点）
厂长（姓名，性别，年龄，厂号，任期）

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610114618423.png)

#### 两实体间的 1:m 联系

> 可将“1”方实体的主码纳入“m”方实体对应的关系中作为外码，同时把联系的属性也一并纳入“m”方对应的关系中。

例如，如图 6.2 所示的 E-R 图转换为如下关系模式：
仓库（仓库号，地点，面积）
商品（货号，品名，价格，仓库号，数量）

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610114805270.png)

#### 同一实体间的 1:m 联系

> 可在这个实体所对应的关系中多设一个属性，作为与该实体相联系的另一个实体的主码。

例如，如图 6.3 所示的 E-R 图可转换为如下关系模式：
职工（工号，姓名，年龄，性别，职称，工资，领导者工号，民意测验）

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/2020061011483790.png)

#### 两实体间的弱实体联系

> 可将被依赖实体的主码纳入弱实体中，作为弱实体的主码或主码中的一部分。

例如，如图 6.4 所示的 E-R 图可转换为如下关系模式：
职工（工号，姓名，年龄，性别，职称）
亲属（工号，亲属姓名，亲属关系）
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610114930133.png)

#### 超类和子类的转换

> 超类、子类实体都可转换为一个关系，并将超类实体的主码加到子类实体中。

例如，如图 6.5 所示的 E-R 图中各个实体的属性为：
职员：职工号，姓名，性别，年龄，参加工作时间
飞行员：飞行小时，健康检查，飞机型号
机械师：学历，级别，专业职称
管理员：职务，职称

该 E-R 图转换为如下关系模式：

职员（职工号，姓名，性别，年龄，参加工作时间）
飞行员（职工号，飞行小时，健康检查，飞机型号）
机械师（职工号，学历，级别，专业职称）
管理员（职工号，职务，职称）

为了查询方便，可在超类实体中增加一个指示器属性，根据指示器的值直接查询子类实体表。所以，职员关系又可以为：
职员（职工号，姓名，性别，年龄，参加工作时间，职员类型）

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610115026486.png)

#### 两实体间的 m:n 联系

> 必须对“联系”单独建立一个关系，该关系中至少包含被它所联系的双方实体的“主码”，如果联系有属性，也要纳入这个关系中。

例如，如图 6.6 所示的 E-R 图转换为如下关系模式：
学生（学号，姓名，性别，年龄）
课程（课程号，课程名，学时）
选修（学号，课程号，成绩）
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610115106841.png)

#### 同一实体间的 m:n 联系

> 必须为这个“联系”单独建立一个关系，该关系中至少应包含被它所联系的双方实体的“主码”，如果联系有属性，也要纳入这个关系中。由于这个“联系”只涉及一个实体，所以加入的实体的主码不能同名。

例如，如图 6.7 所示的 E-R 图转换为如下关系模式：
零部件（代号，名称，价格）
组装（代号，组装件代号，数量）
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610115129617.png)

#### 两个以上实体间的 m:n 联系

> 必须为这个“联系”单独建立一个关系，该关系中至少应包含被它所联系的各个实体的“主码”，若是联系有属性，也要纳入这个关系中。

例如，如图 6.8 所示的 E-R 图可转换为如下关系模式：
供应商（供应商号，供应商名，地址）
零件（零件号，零件名，重量）
项目（项目编号，项目名称，开工日期）
供应（供应商号，项目编号，零件号，零件数）

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610115203139.png)

### 7.4.2 关系模式的优化

> 最核心的就是要遵循数据库设计的nF范式

应用关系规范化理论对上述产生的关系模式进行优化，具体步骤如下：
（1）确定每个关系模式内部各个属性之间的数据依赖以及不同关系模式属性之间的数据依赖。
（2）对各个关系模式之间的数据依赖进行最小化处理，消除冗余的联系。
（3）确定各关系模式的范式等级。
（4）按照需求分析阶段得到的处理要求，确定要对哪些模式进行合并或分解。
（5）为了提高数据操作的效率和存储空间的利用率，对上述产生的关系模式进行适当的修改、调整和重构。

### 7.4.3 设计用户子模式

> 全局关系模型设计完成后，还应根据局部应用的需求，结合具体 DBMS 的特点，设计用户的子模式。

设计子模式时应注意考虑用户的习惯和方便性，主要包括：
（1）使用更符合用户习惯的别名。
（2）可以为不同级别的用户定义不同的视图，以保证系统的安全性。
（3）可将经常使用的复杂的查询定义为视图，简化用户对系统的使用。
![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/202006101202434.png)





### 7.4.4 DDL

一、DML

> DML（data manipulation language）数据操纵语言：
>
> 就是我们最经常用到的 SELECT、UPDATE、INSERT、DELETE。 主要用来对数据库的数据进行一些操作。

```
SELECT 列名称 FROM 表名称
UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值
INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)
DELETE FROM 表名称 WHERE 列名称 = 值
```

二、DDL

> DDL（data definition language）数据库定义语言：
>
> 其实就是我们在创建表的时候用到的一些sql，比如说：CREATE、ALTER、DROP等。DDL主要是用在定义或改变表的结构，数据类型，表之间的链接和约束等初始化工作上

```
CREATE TABLE 表名称
(
列名称1 数据类型,
列名称2 数据类型,
列名称3 数据类型,
....
)

ALTER TABLE table_name
ALTER COLUMN column_name datatype

DROP TABLE 表名称
DROP DATABASE 数据库名称
```

三、DCL

> DCL（Data Control Language）数据库控制语言：
>
> 是用来设置或更改数据库用户或角色权限的语句，包括（grant,deny,revoke等）语句。这个比较少用到。



## 7.5 物理结构设计—步骤四

> 数据库的物理设计是指对一个给定的逻辑数据库模型选取一个最适合应用环境的物理结构的过程。物理设计通常分为两步：

![在这里插入图片描述](https://gitee.com/fakerlove/picture_1/raw/master/20200610122736344.png)

### 7.5.1 确定数据库的物理结构

（1）确定数据的存取方法

- 索引方法的选择
- 聚簇方法的选择

（2）确定数据的存储结构

- 确定数据的存放位置
  基本原则:根据应用情况将易变部分与稳定部分分开存放、存取频率较高部分与存取频率较低部分分开存放
- 确定系统配置
  DBMS产品一般都提供了一些存储分配参数
  同时使用数据库的用户数
  同时打开的数据库对象数
  内存分配参数
  使用的缓冲区长度、个数
  存储分配参数
  …….

### 7.5.2 物理结构进行评价

> 对时间效率、空间效率、维护开销和各种用户要求进行权衡，从多种设计方案中选择一个较优的方案。

评价方法（完全依赖于所选用的DBMS ）

- 定量估算各种方案
  存储空间
  存取时间
  维护代价
- 对估算结果进行权衡、比较，选择出一个较优的合理的物理结构
- 如果该结构不符合用户需求，则需要修改设计

## 7.6 数据库实施—步骤五

**实施阶段的工作主要有：**

- 建立数据库结构
- 数据载入
  数据库结构建立好后，就可以向数据库中装载数据了。组织数据入库是数据库实施阶段最主要的工作。
- 应用程序的编码和调试
- 数据库试运行
  `功能测试`
  实际运行数据库应用程序，执行对数据库的各种操作，测试应用程序的功能是否满足设计要求
  如果不满足，对应用程序部分则要修改、调整，直到达到设计要求
  `性能测试`
  测量系统的性能指标，分析是否达到设计目标
  如果测试的结果与设计目标不符，则要返回物理设计阶段，重新调整物理结构，修改系统参数，某些情况下甚至要返回逻辑设计阶段，修改逻辑结构

## 7.7 数据库运行维护—步骤六

**数据库系统投入正式运行后，对数据库经常性的维护工作主要由 DBA 完成，包括：**

- 数据库的转储和恢复
  在数据库试运行阶段，系统还不稳定，硬、软件故障随时都可能发生
  系统的操作人员对新系统还不熟悉，误操作也不可避免
  因此必须做好数据库的转储和恢复工作，尽量减少对数据库的破坏
- 数据库的安全性、完整性控制
- 数据库性能的监督、分析和改造
- 数据库的重组与重构
  `重组织的目标`
  提高系统性能
  `重组织的工作`
  按原设计要求
  重新安排存储位置
  回收垃圾
  减少指针链
  数据库的重组织不会改变原设计的数据逻辑结构和物理结构
  `数据库重构造`
  根据新环境调整数据库的模式和内模式
  增加新的数据项
  改变数据项的类型
  改变数据库的容量
  增加或删除索引
  修改完整性约束条件



