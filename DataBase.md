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

### 添加和删除列（修改表的结构）
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

### 添加和删除，更新列（修改表内数据）
```sql
UPDATE   卷面  SET  总评 = 总评 +5   WHERE  班号="300211"
UPDATE  表名   SET  列名 ＝ 表达式

DELETE  FROM  表名  [WHERE  条件]
若WHERE子句缺省，则是无条件删除表中的全部数据，但表仍然存在。

INSERT  INTO  表名[（列名[，列名]…）]  VALUES  （常量[，常量]…）
主键不能为空
```

### 选择

运算符有 <br>
BETWEEN <br>
AND <br>
OR <br>
LIKE <br>
LEN 对字符串求长<br>
```sql
SELECT 列 FROM 表
WHERE 列 LIKE pattern
（%表示缺少的字符，类似正则表达式；'___'表示三个字数） 
```
```sql
SELECT FROM 
 WHERE (运算符)

NAME = '王%'，%表示任意字母
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
INSERT INTO (表名)(列) VALUES(值)
```

### 多表查询(标明列的表来源)
利用不同表中相同的列
```sql
SELECT STUDENT.SNO,SNAME,CLASS,AVG(DEGREE)
	FROM STUDENT,SCORE
	WHERE STUDENT.SNO=SCORE.SNO
```
利用JOIN
```sql
SELECT STUDENT.SNO,SNAME,CLASS,AVG(DEGREE)
	FROM STUDENT
	JOIN SCORE ON STUDENT.SNO=SCORE.SNO
```

### 分组(针对合计函数)
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

### HAVING函数
WHERE 无法与 合计函数一起使用
```sql
SELECT STUDENT.SNO,SNAME,CLASS,AVG(DEGREE)
	FROM STUDENT,SCORE
	WHERE STUDENT.SNO=SCORE.SNO
	GROUP BY STUDENT.SNO,STUDENT.SNAME,STUDENT.CLASS
	HAVING AVG(DEGREE) BETWEEN 80 AND 00
	ORDER BY AVG(DEGREE) DESC
```

### 添加索引
```sql
CREATE  [UNIQUE]  INDEX 索引名 ON  表名（列名[次序][，列名[次序]]…）
CREATE INDEX t ON test (ID)
UNIQUE表示每一索引值只对应唯一的数据记录，一般在主键上建立这样的索引
```

### 复合语句
```sql
DELETE  FROM  FAIL  WHERE SNO =
		(SELECT  SNO  FROM S
			WHERE SN =‘刘萍’)；
删除之中带有选择
```



