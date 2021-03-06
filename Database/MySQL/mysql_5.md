---
title: "[Database]MySQL_5" 
date: 2020-07-28
tags: DataBase
keywords:
  - database
  - CS	
  - MySQL
---

### 관계형 데이터베이스_1

다음은 **생활코딩**에서 Database를 공부하면서 요약 및 정리한 내용이다. 



#### 관계형 데이터베이스의 필요성

<small>어디선가 중복의 악취가 난다면... 그것은 개선할 필요가 있다는 신호이다!! *(우리는 효율을 중요시 하는 개발자)*</small>

<small>항상 극단적인 상황을 고려해보자. 데이터가 몇 십개가 아니라.. 몇 억개라고 오바해보자. *(오바는 해결책을 부른다)* </small>



###### 우리의 목표: 중복 해결하기

| id   | title                                 | author      | profile   |
| ---- | ------------------------------------- | ----------- | --------- |
| 1    | Harry Potter and the Sorcerer's Stone | J.K Rowling | author    |
| 2    | Narnia                                | C.S. Lewis  | author    |
| 3    | I Love CS                             | yjkim       | Developer |
| 4    | How to Study Database                 | yjkim       | Developer |

<small>표1. previous_bookList</small>

이런 표가 있을 때, 우리 눈에 중복이 보인다. author에 yjkim과 profile에 developer 항목이다. 이런 중복을 오바해서 몇 억개가 있다고 했을 때, 해당 데이터 내용을 바꾸는 것은.. *불가능*하다. 

이러한 사항들을 개선하기 위해서 관계형 데이터베이스가 출현한 것이다. 

위의 표를 다음과 같이 나눠보자. 

| id   | title                                 | author_id |
| ---- | ------------------------------------- | --------- |
| 1    | Harry Potter and the Sorcerer's Stone | 1         |
| 2    | Narnia                                | 2         |
| 3    | I Love CS                             | 3         |
| 4    | How to Study Database                 | 3         |

<small>표2.bookList</small>

| id   | name         | profile   |
| ---- | ------------ | --------- |
| 1    | J.K. Rowling | author    |
| 2    | C.S. Lewis   | author    |
| 3    | yjkim        | developer |

<small>표3. author</small>



###### 중복 제거의 효율성:

* yjkim이라는 이름을 yunKim으로 변경하고 싶다면 **표1**처럼 중보되는 데이터에 모두 접근해서 일일히 변경할 필요가 없다. **표3**에서 name만 변경하면 ***한꺼번에 변경***할 수 있다. 
* 만약에 yjkim, developer가 2명이라면 각 사람은 다르지만 name과 profile이 같으므로 **표1**에서는 구분하기 어렵다. 그러한 동명이인의 경우 표3에서 id를 추가해 yjkim, developer를 입력하고 **표2**에서 id 값을 다르게 주면 다른 사람이라는 것을 확인할 수 있다. 



###### 위 방법의 단점:

<small>trade-off... 장점이 생기면 단점도 생긴다 :(</small>

* 기존 **표1**은 하나의 테이블에 모두 포함되어 있기 때문에 매우 직관적이다. 하지만 중복의 비효율성을 가지고 있다. 
* 따라서 **표2, 표3** 처럼 나누면 중복이 없어지지만 한눈에 볼 수 없고 별도의 표를 참조해야하지 때문에 직관성이 떨어진다. 



> Trade-off.. MySQL을 사용하면 극복할 수 있다!! (다음글 참고)

