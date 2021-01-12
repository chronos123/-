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
ALTER TABLE
 ADD
 
ALERT TABLE 
 DROP COLUMN
```sql
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
LIKE pattern（%表示缺少的字符，类似正则表达式） 
```sql
SELECT FROM 
 WHERE (运算符)
```

### 插入

```sql
INSERT INTO (表明)(列) VALUES(值)
```

### 多表查询
```sql

```
