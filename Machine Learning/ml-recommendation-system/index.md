# [머신러닝] 추천 시스템 기술

모 기업에서 인턴을 하면서 맡은 업무가 <mark>개인화 추천 모델 구현</mark>이었다. 맡은 업무는 딥러닝 기반의 개인화 추천 모델을 제작하는 것이지만 기존에 회사에서 가지고 있는 추천 시스템의 경우 협업 필터링 등으로 이미 구현이 되어 있었기 때문에 간단히 개인화 추천 시스템에 대한 브리핑을 해주시면서 감을 잡을 수 있도록 해주셨다. 

추천 시스템 기술을 처음 접해보면서 어떠한 것인지 공부하며 기록해보려고 한다. 



### 추천이란?

추천이란 간단히 말해서 사용자(user)에게 관심이 있을 것으로 예상이 되는 아이템(item)을 제안하는 것이다. 특정 아이템에 대한 특정 사용자의 선호도 또는 평가를 예측하는 것이 매우 중요하다. 

우리가 흔히 생각해 낼 수 있는 추천 시스템은 페이스북과 같은 것에서의 광고 추천, 넷플릭스나 왓챠와 같은 OTT 서비스에서의 영화 추천 시스템이다. 



### 접근 방식

추천 시스템 기술에서의 접근 방식은 크게 다음과 같은 3가지가 있다. 

* 내용 기반 필터링 (Content-based Filtering)
* 협업 필터링 (Collaborative Filtering)
* 하이브리드 (Hybrid)



#### 1) 내용 기반 필터링

사용자의 프로필이나 아이템의 content 정보를 이용하는 방법이다. 사용자의 선호도, 취향 등을 파악하는 방법이 핵심이다. 예를 들어, 회원가입 시 사용자에게 선호하는 아이템 또는 분야 등에 대해서 선택하도록 하여 선호도를 파악하여 해당 정보를 기반으로 추천을 한다. 또는 사용자의 과거에 평가한 아이템 분석을 통해서 선호도를 파악할 수 있다. 

<img src="contentbased.jpeg" alt="Content-based Filtering">



#### 2) 협업 필터링

협업 필터링은 여러 사용자들의 활동, 기호 정보들을 분석하여, 각 사아요자에게 적합한 아이템을 추천하도록 한다. 예를 들어서 사용자 A와 유사하다고 판단되는 사용자 B가 최근 구매한 상품을 사용자 A에게도 추천하도록 하는 것이다. 

<img src="collaborative.jpeg" alt="Collaborative Filtering">



#### 3) 내용 기반 필터링 & 협업 필터링의 장단점

|      | 내용 기반 필터링                                             | 협업 필터링                                                  |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 장점 | 사용자의 명시적인 기호 정보를 직접적으로 반영한다. <br>다른 사용자의 정보나 평가, 행동 등이 필요하지 않다.<br>새로 추가된 아이템에 대한 추천이 가능하다. | 대부분의 경우 추천 성과가 우수하다.<br>잠재적인 특징을 고려하여 다양한 범위의 추천이 가능하다. |
| 단점 | 사용자의 명시적인 프로필 얻기 어려움이 있다.<br>명시적으로 표현된 특징만 다룰 수 있고 잠재적인 것을 캐치하기 어렵다.<br>추천하는 항목이 비슷한 장르에 머무르는 한계가 있다. | 초기 사용자에 대한 믿을만한 추천이 어렵다. Cold start가 존재한다.<br>한번도 평가되지 않은 아이템은 추천 대상에서 제외된다. sparsity, coverage |



#### 4) 하이브리드

위에서의 내용 기반 필터링과 협업 필터링을 결합하여 사용한다. 결합하는 방식을 다양하기 때문에 어떠한 하이브리드 방식을 택하는지는 매우 광범위 하다. 하지만 간단히 보아서 위의 두가지 방식을 같이 사용함으로 각자의 단점을 보완한다는 장점을 가지고 있다. 다만 시스템적으로 매우 복잡해질 수 있는 단점이 있다. 



#### 5) 협업 필터링 기술 분류

본 기업에서 중점적으로 사용하고 있는 협업 필터링 기술은 다음과 같이 분류된다. 

* 메모리 기반(Memory-based) 협업 필터링
  * 사용자 또는 아이템 간의 유사도를 계산하고 그것을 바탕을 추천 결과를 생성하는 방식으로 유사도를 계산하는 방식이 매우 중요함. 
  * **대표 알고리즘**: User-based CF / Item-based CF
  * **장점**: 구현이 간단하고 이해하기 쉬움.
  * **한계**: 1) 새로운 사용자와 아이템에 대한 cold start 문제 2) Rating matrix의 sparsity 문제 3) 큰 데이터 셋에 대해 제한된 scalability
* 모델 기반(Model-based) 협업 필터링
  * 데이터(rating matrix)에 내재되어 있는 패턴이나 속성을 학습한 모델을 만들고, 이것을 바탕으로 추천 결과를 생성하는 방식. 
  * **대표 알고리즘**: Slope-One EF / Matrix Facotrization
  * **장점:** sparsity, scalability 문제에 상대적으로 더 잘 대처하는 것이 가능하고 예측 성능이 향상됨. 
  * **한계:** 1) 모델 구축 비용이 큼 2) 예측 성능과 scalability 사이의 trade-off 3) 차원 감소로 인한 정보손실(SVD 실행 시 발생)
* 하이브리드(Hybrid) 방식 협업 필터링
  * 메모리 기반 방식과 모델 기반 방식을 결합하여 사용하는 방식 
  * **대표 알고리즘**: 메모리 기반과 모델 기반의 조합 
  * **장점**: 각 방식의 단점을 보완하고 장점만을 취합할 수 있음
  * **한계:** 구현이 복잡해지고 비용이 증가함. 









**<small>[참고 자료]: https://www.samsungsemiconstory.com/2265, </small>**
