---
title: "[Database]MySQL_4" 
date: 2020-07-28
tags: DataBase
keywords:
  - database
  - CS	
  - MySQL
---

### MySQL_DELETE

다음은 **생활코딩**에서 Database를 공부하면서 요약 및 정리한 내용이다. 

<mark>CRUD</mark> 에서 **DELETE** 부분에 해당하는 DELETE 문법이다. 

 <small>DELETE는 매우 간단하고 쉬운 논리이며 문법이지만 가장 조심해서 사용해야 한다. 잘못 쓰면.. (이하 생략)</small>



###### 기본 문법: 

```mysql
DELETE FROM 테이블_이름 WHERE 삭제_행_조건;
```



밑에서 MySQL사이트에서 제공하는 문법을 살펴보면 WHERE 문에 조건으로 나와 있다. WHERE문은 필수적으로 사용해야하는 사항은 아니지만 사용하지 않는다면 **모든 행이 DELETE** 되는 대참사가 발생할 수 있으니 WHERE 조건을 잘 서술해야한다. 

<img src="/Users/yunjung/Desktop/MD/sql_delete.png" alt="sql delete" />



###### 예시:

``` mysql
DELETE FROM bookList WHERE id = 6; 
```



Id 6번에 입력되어 있는 책과 관련 정보가 모두 삭제될 것이다. (전체 행 삭제)



**<mark>* 주의사항: UPDATE와 마찬가지로 WHERE 문을 빠뜨리면 모든 행이 DELETE 되므로 매우 조심하여야 한다. 삭제하고 싶은 부분만 잘 선택하여 사용하자. </mark>**









