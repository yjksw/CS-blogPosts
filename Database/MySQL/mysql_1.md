---
title: "[Database]MySQL_1" 
date: 2020-07-28
tags: DataBase
keywords:
  - database
  - CS	
  - MySQL
---


### MySQL_CREATE

<mark>CRUD</mark> 에서 **Create** 부분에 해당하는 CREATE 문법이다. 



###### 기본 문법: 

```my
INSERT INTO 테이블_이름 (col1, col2, ...) VALUES(value1, value2, ...)
```



기존에 있는 테이블에 요소를 추가하는 메소드이다. 매우 간단하지마 데이터베이스의 시작이라고 할 수 있다. 원하는 테이블에 각 column에 특정한 값들을  입력시켜서 한꺼번에 넣어줄 수 있다. 이전에 테이블을 생성할 때 NOT NULL이라고 설정한 것들은 반드시 입력해야하며, id와 같은 경우 auto increment가 되어 있는 경우가 많기 때문에 따로 지정하지 않아도 될 때가 많다. 



###### 예시:

``` my
INSERT INTO bookList (title, description, ...) VALUES('MySQL', 'This book is..', ...)
```





> SELECT와 INSERT는 매우 중요하다. 서로가 없으면 의미가 없는 데이터 베이스의 아주 중요한 첫 단추라고 할 수 있다. 

