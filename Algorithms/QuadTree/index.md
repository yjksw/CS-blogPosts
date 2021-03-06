---
title: "[알고리즘] 쿼드 트리"
date: 2020-08-12
tags: Algorithms
keywords:
  - CS
  - Algorithms	
  - Quad Tree
---
자료구조 중 처음 들어본 <small>(배웠는데 기억 못하는)</small> 개념이 나와서 정리해본다. 알고리즘 문제 중 분할 문제를 푸는 중에 쿼드 트리를 사용하는 알고리즘 이라는 언급을 보고 쿼드 트리라는 것이 어떠한 것인지 살펴보기로 한다. 

* QuadTree(쿼드트리): 자료구조의 트리를 기반으로 자식노드가 4개인 트리를 의미함. 

대랑의 좌표 데이터를 메모리 안에 압축하기 위해서 사용하는 기법 중 하나로, 주어진 공간을 항상 4개로 분할해 재귀적으로 표현한다. 

<img src="quadTree.png" alt="Quad Tree"/>

대표적으로 사용되는 쿼드 트리의  사용처는 검은 색과 흰 색 밖에 없는 흑백 그림을 압축해서 표현하는 것이다. 쿼드 트리를 사용해서 해당 문제를 해결하는 것을 간단히 살펴보자. 



## 쿼드트리 응용 예시

**흑백그림 압축표현 하기** 

다음 3가지를 기억하고 논리를 따라가면 된다. 

1. 그림의 모든 픽셀이 검은 색일 경우 쿼드 트리의 압축 결과는 그림 크기에 상관없이 B가 됨.
2. 그림의 모든 픽셀이 흰 색일 경우 쿼드 트리의 압축 결과는 그림 크기에 상관없이 W가 됨. 
3. 같은 색이 아니라면, 이 그림의 가로 세로에 대해서 2로 나누어 4개의 조각으로 나눈 다음에 재귀를 사용하여 쿼드 트리압축을 진행함. 
   * 각각 4개의 분할된 그림에 대해서 전체가 흑색이면 B가 되고 전체가 흰색이면 W가 됨.
   * 만일 같은 색깔로 나누어지지 않으면 X로 표시한 후, 재귀로 들어가 색갈이 나올 때까지 반복함. 



## 쿼드트리를 응용한 그림 압축하기 코드

자바로 트리를 구현하는 방법 중 하나는, 재귀로 하나씩 파고드는 것이다. 재귀와 분할정복에 대해서 몇 문제를 풀어보니 중요한 것은 다음 두가지 이다.

1. 언제 return 할 것인지.
2. 재귀로 들어가는 반복적인 규칙

위 두가지를 고려하여 쿼드 트리로 위의 흑백 그림에 대해서 푸는 코드를 작성해보자. 

문제는 [백준 2630번](https://www.acmicpc.net/problem/2630) 를 참고하였다.



```java
//Divide and Conquere 분할정복
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;

class Main {
  static int[][] arr;
  static int b = 0;
  static int w = 0;
  
  public static void main(String[] args){
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    
    try{
      int n = Integer.parseInt(br.readLine());
      arr = new int[n][n];
      for(int i=0;i<n;i++){
        String[] temp = br.readLine.split(" ");
        for(int j=0;j<n;j++){
          arr[i][j] = Integer.parseInt(temp[j]);
        }
      }
      solve(0, 0, n);
    } catch (IOException e){}
      System.out.println(w);
  		System.out.println(b);
  }
  
  public static void solve(int x, int y, int size){
    int num = arr[x][y];
    for(int i=x;i<x+size;i++){
      for(int j=y;j<y+size;j++){
        if(num != arr[i][j]){
          solve(x, y, size/2);
          solve(x+size/2, y, size/2);
          solve(x, y+size/2, size/2);
          solve(x+size/2, y+size/2, size/2);
          return;
        }
      }
    }
    if(num == 1)
      b++;
    else 
      w++;
    return;
  }
}
```







<small>별건 아니고 이진트리에서 4개 버전이 쿼드 트리였다..</small>

