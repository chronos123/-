### 创建数据库
```sql
CREATE DATABASE DataBaseEG_18231008
ON PRIMARY

(
Name=DataBaseEG_data,
Filename='D:\SQL sever\Myproject\experiment 4\DBEG_data.mdf',
Size=8MB,
Maxsize=unlimited,
Filegrowth=10%
)
```

### 数据库日志
```sql
LOG ON
(
Name=DataBaseEG_log,
Filename='D:\SQL sever\Myproject\experiment 4\DBEG_log.ldf',
Size=3MB,
Maxsize=50MB,
FileGrowth=2MB
)
```

### 创建表

<ul>数据类型
 <li> <b>VARCHAR(7)</b>  </li>
 <li> <b>DATATIME</b>  YYYY-MM-DD HH:MM:SS</li>
 <li> <b>NUMERIC(a,b)</b> a:总位数 b：小数位数</li>
 <li> <b>PRIMARY KEY</b> 主键（表的标识）</li>
</ul>

```sql
use DataBaseEG_18231008

CREATE TABLE STUDENT
(
	SNO VARCHAR(3) NOT NULL,
	SNAME VARCHAR(8) NOT NULL,
	SSEX VARCHAR(2) NOT NULL,
	SBIRTHDAY DATETIME,
	CLASS VARCHAR(6)
	CONSTRAINT PK_student PRIMARY KEY (SNO)
)
GO
```

### 添加和删除列
```sql
ALTER TABLE
 ADD
 
ALTER TABLE 
 DROP COLUMN

添加
ALTER TABLE table_name
ADD column_name datatype

删除
ALTER TABLE table_name 
DROP COLUMN column_name
```


### 选择

运算符有 <br>
BETWEEN <br>
AND <br>
OR <br>
LIKE <br>
```sql
LIKE pattern
（%表示缺少的字符，类似正则表达式；'___'表示三个字数） 
```
```sql
SELECT FROM 
 WHERE (运算符)
```
排序
```sql
SELECT Company, OrderNumber FROM Orders ORDER BY Company

SELECT Company, OrderNumber FROM Orders ORDER BY Company, OrderNumber
(字母相同使用数字)

SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC
(DESC 降序，ASC 升序)
```

### 插入

```sql
INSERT INTO (表明)(列) VALUES(值)
```

### 多表查询
利用不同表中相同的列
```sql
SELECT STUDENT.SNO,SNAME,CLASS,平均分=AVG(DEGREE)
	FROM STUDENT,SCORE
	WHERE STUDENT.SNO=SCORE.SNO
```
利用JOIN
```sql
SELECT STUDENT.SNO,SNAME,CLASS,平均分=AVG(DEGREE)
	FROM STUDENT
	JOIN SCORE ON STUDENT.SNO=SCORE.SNO
```

### 分组
GROUP BY进行分项组合
```sql
SELECT Customer,SUM(OrderPrice) FROM Orders
GROUP BY Customer
（按GROUP BY分项求和，合并）

SELECT COURSE.CNO,CNAME,AVG(DEGREE)
	FROM COURSE
	JOIN SCORE ON SCORE.CNO=COURSE.CNO
	GROUP BY COURSE.CNO,COURSE.CNAME
	ORDER BY AVG(DEGREE) DESC
（按GROUP BY分项求平均，合并）
```

