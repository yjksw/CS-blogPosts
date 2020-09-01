# Java  유용 문법 모음

> Java를 사용해서 코딩 테스트 준비 겸 알고리즘 문제를 풀어보다 알아두면 유용한 자바 문법이나 코드 등등을 맥락없이 적어놓는 메모장 같은 페이지.



## StringBuilder & StringBuffer

알고리즘은 맞지만 시간초과가 걸릴 때 유용함. 

* String 변수에 '+' 연산자를 써서 이어붙이면 매번 새로운 메모리를 할당하기 때문에 시간초과가 걸림.
* StringBuilder 를 사용하면 동일한 메모리에 append 하므로 시간측면에서 유용함. 

```java
StringBuilder sb = new StringBuilder();
sb.append("Hello ");
sb.append("My name is Yun");
sb.append("\n");
System.out.println(sb);
```



## BufferedReader

* Scanner를 사용하여서 많은 데이터를 입력할 때 시간초과가 일어나기도 함. 

* 한꺼번에 버퍼에 저장했다가 한번에 읽어드리는 BufferedReader가 확연히 빠르게 동작함. 

```java
import java.io.*;
import java.util.StringTokenizer;

class Main{
  public static void main(String[] args){
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    String input = "";
    
    try{
      input = br.readLine();
    } catch(IOException e){}
    StringTokenizer st = new StringTokenizer(input);
    
    int n = Integer.parseInt(st.nextToken());
    int m = Integer.paresInt(st.nextToken());
    
    br.close();
  }
}
    
```

* BufferedReader는 항상 try-catch를 사용해서 읽음.
* 한줄 씩 밖에 읽을 수 없고, 반드시 String으로 들어오기 때문에 입력 데이터에 대한 가공이 필요함.
  * StringTokenizer로 원하는 문자 기준으로 나눌 수 있음.
  * Integer.parseInt를 사용하여 스트링을 정수로 변함.
  * 반드시 close() 해주어야 함. 



## Iterator

* 여러모로 유명하고 유용하나 Stack등에 대한 자료구조에 있어서 pop을 하지 않고 데이터 처음부터 읽을 수 있음.

```java
import java.util.Iterator;

class Main{
  public static void main(String[] args){
    public static Stack<Integer> st = new Stack<Integer>();
    st.push(1);
    st.push(2);
    st.push(3);
    
    Iterator value = st.iterator();
    while(value.hasNext()){
      System.out.println(value.next());
    }
  }
}
```



## 자바 2차원 배열 정렬하기 

자바에서는 Arrays.sort() 함수를 통해서 손쉽게 배열을 정렬할 수 있다. 하지만 Comparator를 상속 받아서 배열을 정렬하는 이 메소드를 제대로 이해하기 위해서는 상속받은 Comparator 인터페이스의 성질과 override 하고 있는 메소드 들에 대해서 잘 이해하는 것이 좋다.

다음을 자바에서 2원 배열을 먼저 1번째 원소에 대해서 정렬하고, 1번째 원소가 같을 때 2번째 원소의 값에 대해서 정렬하는 것에 대한 코드이다. 알고리즘 문제를 풀면서 다차원 배열을 정렬할 때 매우 유용하므로 기록한다. 

```java
import java.util.Arrays;
import java.util.Comparator;

class Main{
  public static void main(String[] args){
    int[][] arr = new int[10][2];
    
    //위의 2차원 배열 arr에 대해서 1번째 원소에 대해서 정렬하고, 같다면 2번째 원소에 대해서 정렬하기
    Arrays.sort(arr, new Comparator<int[]>(){
      public int compare(int[] t1, int[] t2){
        if(t1[0] == t2[0])
          return t1[1] - t2[1];
        else
          return t1[0] - t2[0];
      }
    });
  }
}
```



## 자바 배열 복사하기 

자바에서는 배열을 복사할 때 2가지로 나뉜다. 배열이 모두 주소값으로 지정이된다는 것은 모두 알 것이다. 그때 중요한 것은 배열을 다음 두가지 중 어떠한 복사를 할 것인지 이다. 

**1. Shallow copy (얕은 복사) **

* 복사를 했을 때 주소가 가리키는 것만 바꿈. 
* source의 배열이 변경되면 해당 배열 또한 같은 주소를 가지고 있으므로 함께 변경됨. 

**2. Deep copy (깊은 복사)**

* 복사를 했을 때, 새로운 배열이 생성되어 동일한 값 다른 주소를 가진 배열이 생성됨



---

자바 자료구조, stack queue dequeue tree graph hashmap pair 등등 알리

dfs bfs 코드 적기

슬라이딩 윈도우 기법 -> dp에서 유용

LCS/ LIS 코드 적기 

(코드랑 문법이랑 나누자!)

https://plplim.tistory.com/30  연산문제 더 나은 코드 