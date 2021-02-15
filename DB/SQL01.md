## 📝 SQL (Structured Query Language)

### DCL (Data Control Language)
- grant 
- revoke
- deny

### DDL (Data Definition Language) 데이터 정의어
- create
- alter
- drop
- rename
- truncate

### DML (Data Manipulation Language) 데이터 조작어
- create
- select
- update
- delete

### TCL (Transaction Control Language) 트랜잭션 제어어
- begin transaction
- commit
- rollback
- savepoint

begin transaction을 하고 commit하면 디스크에 쓰고 메모리에만 있던 트랜잭션을 commit 하면 디스크에 쓰고 rollback하면 메모리를 비움.

savepoint는 트랜잭션 시작하는 포인트를 준다.


### DB, User 생성

#### 접속하기

```
$> docker start mysql5
$> docker exec -it mysql5 bash
// 우리는 mydeal server에서 할 것.
#> mysql -u <user> -p
# example
#> mysql -u root -p
#> mysql -u mydeal -p
mysql> show databases;
mysql> use testdb;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+------------------+
| Tables_in_testdb |
+------------------+
| Dept             |
| Emp              |
+------------------+
2 rows in set (0.00 sec)

mysql> desc Dept;
+-------+------------------+------+-----+---------+----------------+
| Field | Type             | Null | Key | Default | Extra          |
+-------+------------------+------+-----+---------+----------------+
| id    | tinyint unsigned | NO   | PRI | NULL    | auto_increment |
| pid   | tinyint unsigned | NO   |     | 0       |                |
| dname | varchar(31)      | NO   |     | NULL    |                |
+-------+------------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)

mysql> desc Emp;
+--------+------------------+------+-----+---------+----------------+
| Field  | Type             | Null | Key | Default | Extra          |
+--------+------------------+------+-----+---------+----------------+
| id     | int unsigned     | NO   | PRI | NULL    | auto_increment |
| ename  | varchar(31)      | NO   |     | NULL    |                |
| dept   | tinyint unsigned | NO   | MUL | NULL    |                |
| salary | int              | NO   |     | 0       |                |
+--------+------------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> show create table Emp;
+-------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table | Create Table                                                                                                                                                                                                                                                                                                                                                                                                     |
+-------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Emp   | CREATE TABLE `Emp` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `ename` varchar(31) COLLATE utf8mb4_unicode_ci NOT NULL,
  `dept` tinyint unsigned NOT NULL,
  `salary` int NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`),
  KEY `dept` (`dept`),
  CONSTRAINT `Emp_ibfk_1` FOREIGN KEY (`dept`) REFERENCES `Dept` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=251 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci |
+-------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.02 sec)

mysql> show index from Emp;
+-------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| Table | Non_unique | Key_name | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
+-------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| Emp   |          0 | PRIMARY  |            1 | id          | A         |         250 |     NULL |   NULL |      | BTREE      |         |               | YES     | NULL       |
| Emp   |          1 | dept     |            1 | dept        | A         |           5 |     NULL |   NULL |      | BTREE      |         |               | YES     | NULL       |
+-------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
2 rows in set (0.02 sec)
```

**mysql의 index는 모두 binary tree이다.**

#### DB 생성하기

#### DB 삭제하기

#### User + Host 생성하기

```
# User 생성
mysql> create user <user-name>@'<host>' identified by '<password>';
mysql> create user dooo@'%' identified by 'dooo!';
mysql> create user dooo@'211.234.55.66' identified by 'dooo!';
# 권한 부여
mysql> grant all privileges on *.* to '<user-name>'@'<host>';
mysql> grant all privileges on *.* to 'dooo'@'%';
// 접속 호스트가 %이면 어느 ip든 접속 가능. 특정 ip만 접속하게 하고 싶으면 명시해줄 것
# 특정 DB 권한 부여
mysql> grant all privileges on <DB>.* to '<user-name>'@'<host>';
mysql> grant all privileges on dooodb.* to 'dooo'@'%';
// root의 경우 %에 권한 부여하지 말고 특정 ip에만 해주는 게 좋음

# 적용하기
mysql> flush privileges;

# 권한 확인
mysql> show grants for '<user-name>'@'<host>';
mysql> show grants for dooo@'%';
mysql> show grants for dooo;
# 권한 삭제(취소)
mysql> revoke all privileges on <db-name>.* from <user-name>@'<host>';
mysql> revoke all privileges on dooodb.* from dooo@'%';
# User 삭제
mysql> drop user '<사용자>'@'<host>';
mysql> drop user dooo@'%';
mysql> select current_user(); // 현재 접속된 유저가 누구인지 확인 가능
```

#### Table 생성
**Primary key는 음수가 나올 수 없기 때문에 unsgined를 걸어주는 게 좋음.**

```
MySQL8 Document to create Table
CREATE TABLE [IF NOT EXISTS] Student (
	id int unsigned not null auto_increment COMMENT '학번',
	name varchar(31) not null COMMENT '학생명',
	createdate timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '등록일시',
	graduatedt varchar(10) DEFAULT NULL COMMENT '졸업일',
	auth tinyint(1) unsigned NOT NULL DEFAULT '9' COMMENT '0:sys, 1:super, ...',
	…,
	PRIMARY KEY (id),
	FOREIGN KEY <key-name>(col3)
       REFERENCES Tbl1(id) ON [DELETE|UPDATE] [CASCADE | SET NULL | NO ACTION | SET DEFAULT]
  	UNIQUE KEY unique_stu_id_name (createdate, name)
) ENGINE=InnoDB AUTO_INCREMENT=45 DEFAULT CHARSET=utf8;

desc Student;
```

```
create table Dept2 like Dept; // Dept의 구조만 가져와서 create
create table Dept3 AS select * from Dept; // Dept의 구조와 데이터까지 모두 가져와서 create

create table Emp2 AS select * from Emp;
// 이 경우는 인덱스, primary key 등은 복사되지 않으므로 따로 만들어 줘야 함. 
```