# 재귀 vs. 반복

알고리즘 유형: 이분 탐색
작성일시: Sep 21, 2020 7:08 PM

**Binary Search** 이분탐색을 구현하면서, 계속 런타임 에러가 났다. 처음에 재귀로 구현을 시작했는데, 재귀에 너무 큰 값이 들어오면서 stack overflow 에러가 났나 싶어서 다시 while 문으로 구현했다. 하지만 while 문으로 구현한 이후에도 계속 런타임 에러가 떠서 확인해보니, n과 m을 헷갈려서 잘못 적었던 것이었다. 

이왕 while 문으로 구현해서 맞은 거, 재귀와 비교해 보자 해서 재귀를 돌려 보았더니, 재귀가 훨씬 빠르고 메모리 효율도 좋은 것이었다. 일반적으로 생각했을 때, 재귀는 매번 메모리를 할당하면서 새로운 함수를 call 해주어야 하고, 또 그만큼의 시간과 공간이 더 필요해서 반복문에 비해 성능이 다소 떨어진다고 알고 있었지만, 훨씬 빠르고 메모리 효율도 좋아서 그 이유에 대해서 찾아보게 되었다. 정답은 **Tail-recursion.** 



## Tail-Recursion



### Tail-Recursion이란?

Tail-Recursion이란 recursion 함수에서 가장 나중에 실행되는 명령어를 뜻한다. 마지막 시행 명령이 재귀 호출이라면, 해당 함수는 tail-recursion의 형태를 가지고 있다고 할 수 있다. 



### Tail-Recursion의 효능

Tail-recursion은 주로 non tail recursion에 비교해서 성능이 더 좋은 것으로 나타난다. 마지막 recursion을 call 하고, 해당 호출에 연산이 포함되어 있지 않는다면 컴파일러에 의해서 해당 tail-recursion 함수는 optimize 된다. 이 이유는, tail-recursion 함수의 경우, 함수의 가장 마지막으로 실행하는 것이 recursive call이기 때문에 현재 머물고 있는 함수에 더 이상 진행할 instruction이 없고 따라서 현재 함수를 stack에 저장하지 않아도 된다. 때문에 non tail recursion 보다 더 빠르고, stack 메모리를 사용하지 않는 장점을 지닌다. 



주의할 것은 다음과 같이 마지막에 recursive 함수 호출은 한다고 하더라도, 연산이 끼어 있다면, optimize 될 수 없다. 

```java
static int fac(int num){
	if(num == 0)
		return 1;
	
	return n*fac(num-1);
}
```



### 결과 비교

다음에 백준에서 이분탐색을 각각 재귀와 반복문으로 구현했을 때의 결과 차이를 비교해보겠다. 첫번재 줄이 tail recursion으로 이분탐색을 구현했을 때이고, 두번째가 반복문으로 구현했을 때 인데 메모리와 시간의 속도가 모두 재귀가 현저히 좋은 결과임을 확인할 수 있다. 



<img src="Baekresult.png" width=60% />





**<small>[참고 자료]: [https://www.geeksforgeeks.org/tail-recursion/](https://www.geeksforgeeks.org/tail-recursion/) </small>**

