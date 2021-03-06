---
title: "[Database]MySQL_6" 
date: 2020-07-28
tags: DataBase
keywords:
  - database
  - CS	
  - MySQL
---

### 관계형 데이터베이스_2

다음은 **생활코딩**에서 Database를 공부하면서 요약 및 정리한 내용이다. 



#### 관계형 데이터베이스의 꽃 JOIN

테이블 JOIN을 대사로 만들어 본다면, 

> MySQL아, bookList 테이블을 읽을 때 author id 에 해당하는 author table의 데이터도 같이 읽어서 한꺼번에 보여줘

<small>모든 것에는 양면이 있다지만, 여기서는 내가 좋은 단물만 빨아서 좋은 것 + 좋은 것을 얻겠다는 것이다. </small>



###### 기본 문법:

```mysql
SELECT * FROM 테이블_이름 LEFT JOIN 조인할_테이블_이름 ON 조인할_조건;
```

여기서 **LEFT JOIN** 부분은 가장 일반적인 JOIN 종류를 하나 쓴 것이고, 본래 RIGTH JOIN, CROSS JOIN, INNER JOIN... 등등 많은 종류의 JOIN 기법이 있다. 나중에 하나씩 예시를 보면서  필요한 것을 적용하면 될 듯 하다. 



###### 예시:

```mysql
SELECT * FROM bookList LEFT JOIN author ON bookList.author_id = author.id;
```

위와 같이 실행하면 본래 두개로 나누어져 있던 테이블을 JOIN 하여 다음과 같이 출력한다. 

| id   | title                                 | author_id | id   | name        | profile   |
| ---- | ------------------------------------- | --------- | ---- | ----------- | --------- |
| 1    | Harry Potter and the Sorcerer's Stone | 1         | 1    | J.K Rowling | author    |
| 2    | Narnia                                | 2         | 2    | C.S. Lewis  | author    |
| 3    | I Love CS                             | 3         | 3    | yjkim       | Developer |
| 4    | How to Study Database                 | 3         | 3    | yjkim       | Developer |

보면 author_id와 id 의 값이 같은 경우 합성하여 테이블을 출력한 것을 볼 수 있다. 

다음은 사용자에게 필요없는 author_id와 id를 생략하고 테이블을 출력해보자. 



```mysql
SELECT id,title,name,profil FROM bookList LEFT JOIN author ON bookList.author_id = author.id;
```

위와 같이 실행하면 **'id' is ambiguous** 하다는 오류가 나타난다. 테이블을 자세히 보니 우리에게는 id 항목이 2개이다. 따라서 bookList의 id 만을 출력하기 위해 다음과 같이 작성하도록 한다. 

```mysql
SELECT bookList.id,title,name,profil FROM bookList LEFT JOIN author ON bookList.author_id = author.id;
```

| id   | title                                 | name         | profile   |
| ---- | ------------------------------------- | ------------ | --------- |
| 1    | Harry Potter and the Sorcerer's Stone | J.K. Rowling | author    |
| 2    | Narnia                                | C.S. Lewis   | author    |
| 3    | I Love CS                             | yjkim        | Developer |
| 4    | How to Study Database                 | yjkim        | Developer |



#### JOIN이 불러온 혁명

위의 예시와 같이 *author&profile* 데이터가 쓰이는 테이블이 여러개라고 생각해보자. 

bookList 테이블 뿐만 아니라, essay, comments 등등의 여러 테이블의 데이터로 *author&profile* 가 포함된다고 할 때, 이렇게 테이블을 분산시켜 놓으면 변경 및 보수가 매우 쉽다.

하지만 테이블을 보고 싶을 때는 한눈에 볼 수 있다. 

> 즉, 테이블을 분리한다는 것은 여러 테이블이 함께 데이터를 공유할 수 있게 된다는 것이다. 





---

<small>생활코딩 강의하시는 egoing님이 투척하신 명언으로 데이터베이스 글을 마무리 하고자 한다. 수학자 *폰 노이만*이 말한 명언이다. ***"수학은 이해하는 것이 아니라 익숙해지는 것이다."*** 오늘 배운 데이터베이스도, CS의 많은 분야들도 막막하고 어렵게 느껴지는 이유는 아직 낯을 가리고 있기 때문이다. 익숙해지는 것이 답이고 그 방법을 반복이다!!</small>



