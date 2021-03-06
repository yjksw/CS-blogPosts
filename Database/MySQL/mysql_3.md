---
title: "[Database]MySQL_3" 
date: 2020-07-28
tags: DataBase
keywords:
  - database
  - CS	
  - MySQL
---

### MySQL_UPDATE

<mark>CRUD</mark> 에서 **UPDATE** 부분에 해당하는 UPDATE 문법이다. 

<small>언제나 그렇듯 강의를 해주시는 egoing님께서는 UPDATE 문법에 관련한 검색하는 과정을 함께하셨다. </small>



###### 기본 문법: 

```my
UPDATE 테이블이름 SET 변경하고_싶은_헤더_타이틀=변경내용1,.. WHERE 변경할_항목의_primaryKEY_또는 조건; 
```



UPDATE의 기본 문법이다. 밑의 그림을 보면 mysql UPDATE 관련 문법을 검색하였을 때 나오는 MySQL 공식 사이트의 표현이다. 여기서 **[]** 구문으로 감싸여져 있는 것은 모두 선택사항이다. 필요한 기능이 있을 시에는 추가하거나 아닌 경우 필수로 적을 필요는 없다. Line 7-14에 *value, assignment, assignment_list* 등등은 위의 기본 문법에 해당사항을 어떻게 적어야 하는 지에 대한 상세설명이라고 할 수 있다. 

<small> 이렇게 각 기술도구들의 공식 사이트를 참고하여 직접 해석하고 적용할 수 있는 능력이 앞으로 이 분야에서 일하고 공부하는데 매우 중요할 것 같다. (어쩌면 많이 외우고 아는 것보다..) </small>

<img src="sql_update.png" alt="sql update" width=70% />



###### 예시:

``` my
UPDATE bookList SET title='I Love CS', author='yjkim' WHERE id=6; 
```



다음과 같이 실행했을 때, id 6번에 있는 데이터의 title과 author의 내용이 변경될 것이다. 물론 해당 데이터는 bookList 테이블에 있는 것들이다. 이것은 아주 <u>기본적인</u> UPDATE에 관련한 문법이고 더 정교하게 *LOW_PRIORITY, LIMIT* 등등의 응용이 가능하다. 



**<mark>* 주의사항: WHERE 문을 빠뜨리면 모든 행이 update 되므로 매우 조심하여야 한다. 변경하고 싶은 부분만 잘 선택하여 사용하자. </mark>**









