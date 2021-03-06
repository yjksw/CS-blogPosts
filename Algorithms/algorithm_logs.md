# 알고리즘 학습일지

## Dynamic Programming

- DP에서 중요한 것은 규칙을 찾거나, 일반식을 찾는 것이 키 포인트
- 배열을 사용하라.
- 부분 문제를 해결하는데 초점을 두어서 이전 부분 수열을 사용하여 일반식을 도출하라. 
- 다양한 문제에 대해서 다양한 일반식과 규칙이 존재하기 때문에 최대한 많은 문제를 푸는 것이 중요!
- DP와 분할정복의 차이는 둘 다 더 작은 것으로 더 나눌 수 있지만 DP의 경우 더 작은 요소가 반복적으로 일어난다. (중요!)
  - 예. 피보나치



## Back-tracking

* DFS와 유사함. 
* Stack 을 사용하거나, 배열로 방문 여부를 측정하도록 함. 
* Index 참조가 많다면 배열이 더 효율적임. 
* DFS이지만 더 이상 가능성이 없는 부분에서는 빠져나와 back-track을 함.
* Brute-force의 마인드를 가지고 tree를 설계하고 DFS 형식으로 탐색하며, 가능성 없는 부분은 더 이상 가지 않는다가 키 포인트. 



## Greedy 

* 순간에 최선의 것을 선택.
* 코딩을 하기 전에 어느 순간에 최선이 무엇인지부터 문제 속에서 찾아라. 
* 문제 속에서 순간순간의 최선의 선택이 해답이 된다는 것이 확인되면 greedy를 사용하기.



## 분할정복

* 더 작은 부분으로 나누어서 반복적으로 수행했을 때, 답을 도출할 수 있는 경우이다. 주로 작게 나누어진 sub-problem이 반복되지 않는다.
* 굉장히 많은 종류의 문제들이 있으니 최대한 많이 풀어보는 것을 추천. 
* 세그먼트 트리를 활용한 분할정복 문제도 많이 있음.



## Segment Tree

* 구간합, 구간 최소값, 구간 최댓값 빠르게 lgN 으로 계산할 때 필요한 자료구조
* 위의 문제들에서 값이 변경되었을 때 빠르게 업데이터 하기 위해 필요한 자료구조



## 수열 규칙

- 그 앞의 규칙에 더해서 뒤에 무언가가 나오는 경우 등에 대해서 해결할 때는, 수열의 규칙을 찾는 것이 중요하다.
  - Ex. 모든 숫자는 1과 3과 4로 이루어질 수 있을 때 숫자 n을 1,3,4로 조합할 수 있는 경우의 수는 얼마인가?
    - 1부터 n 까지 그 규칙을 찾으면 이 규칙 수열 p에 대해서 p(n-1)+p(n-3)+p(n-4) 이다.



## Binary Search 이분 탐색

* 어떤 정렬된 값들 사이에서 특정 값을 빠르게 찾을 때 좋은 탐색
* 중복된 값이 있을 때 유용한 이진탐색 응용:
  * 특정한 값보다 큰 값이 처음 나오는 upper bound 
  * 특정한 값보다 작지 않은 값이 처음 나오는 lower bound 

* Parametric Search: 
  * 정렬된 수열 내에서 특정 값을 탐색하는 것보다, **특정 범위**내에서 **특정 조건**을 만족하는 값을 찾을 때 유용함. 

