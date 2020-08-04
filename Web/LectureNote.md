# 부스트코스_웹 풀스택Lecture Note

### 오리엔테이션



* 벡엔드: 웹이 어떻게 동작하는지
  * 서버는 무엇? 프로토콜은 무엇?
  * split 과 JSP는 무엇? 
  * Spring 프레임워크를 통해서 배운다. 

* 프론트엔드: 
  * HTML
  * CSS
  * Javascript: 동적인 웹 페이지 작성
* 6개의 파트:
  * 파트별로 프로젝트가 있음. 
  * 필요한 개념을 강의로 배우고, 연관 프로젝트를 수행
  * 코드리뷰 가능: 유로
* 과정 이후에 가능한 것:
  * 웹 서비스의 전반적인 지식 가능
  * 웹 서비스 제작 가능/ 게시판 혹은 블로그



* 당부의 말:
  * 매일매일 학습일지를 쓰면서 정리하고 돌아보기
  * 웹 서핑을 많이 하면서 페이지 변경 등등의 개발자의 입장으로 살펴보자. 



---



### 웹 프로그래밍 기초

#### 1) 웹 프로그래밍을 위한 프로그램 언어들

저급언어/고급언어/컴파일러 존재

웹 프로그래밍에서 가장 인기있는 **프로그래밍 언어**: 파이썬, PHP, 자바스크립트, 자바, 루비

##### 생각해보기:

1. 프론트 엔드부터 서버개발까지 한 가지 언어를 사용한다면 어떤 언어를 사용하게 좋을까? 자바스크립트
2. 다양한 라이브러리, 쉬운 개발, 적은코드, 읽기 쉬운코드는? 파이썬
3. 프로그래밍 언어에게 좋은 커뮤니티가 있다는 것은 어떤 장점을 가질까? 서로 피드백과 리뷰가 가능함. 함께 발전할 수 있는 플랫폼이 존재하게 됨. 



#### 2) 웹의 동작(HTTP 프로토콜 이해)

HTTP 규약: 웹 브라우저와 웹 서버간의 통신을 위한 규약 

- 인터넷(네트워크 통신)의 이해:
  - 인터넷: TCP/IP 기반의 네트워크가 연결된 네트워크들의 네트워크(네트워크의 결합체)
- 서버/클라이언트 모델을 따름: 클라이언트가 **요청**을 서버에 보내면 서버가 **응답**을 보내는 형태.
- 연결을 맺고 끊기 때문에 클라이언트의 요청 이전 상황을 모르는 무상태(stateless) 특징을 가지고 있음.(불특정 다수가능, 이전 정보유지 불가)
- 정보유지를 위해서 cookie와 같은 기술이 발전함. 

URL(Uniform Resource Locator): 웹 상의 자원의 위치를 나타내는 경로 혹은 주소

- 프로토콜의 종류+서버의 아이피주소 혹은 도메인 이름+문서의 경로+문서 이름 
- 소프트웨어 서버를 찾기 위해서는 포트값이 필요함
  - 하나의 물리적 컴퓨터에는 여러 서버가 존재할 수 있는데 각 서버는 각 다른 포트값을 가져야 함.  
- HTTP로 클라이언트와 서버가 통신하려면 특정 요청 형식을 따라야 함. 
  - 다양한 요청 메서드: GET/POST/PUT/PUSH/OPTIONS(GET의 경우에는 요청바디가 없음.) 
  - 요청 URI: 요청하는 자원의 위치
  - HTTP 프로토콜 버전

##### 생각해보기:

1. HTTP에 S가 붙은 HTTPS의 차이 및 용도는? HTTP에 보안을 강화시킨 것임. 



#### 3) 웹 Front-End 와 웹 Back-End

##### 웹 Front-end(웹 브라우저) 

사용자에게 웹을 통해서 웹 콘텐츠(문서 사진 동영상)등을 제공하는 것.

사용자의 요청에 반응해서 동작함. 

역할:

* 잘 보여주기 위한 구조, 배치, 디자인등이 필요함.
* 사용자의 요청을 잘 반영해야 함.
* HTML/CSS/JavaScript
  * HTML: 구조를 형성. 매우 계층적으로 표현이 되어 있음. 
  * CSS: 디자인을 담당. 
  * JavaScript: 웹의 동적인 부분을 담당. 클릭 및 사용자의 움직임을 담당. 

##### 웹 Back-end

프로그램의 뒷 쪽, 서버 입에서 개발이 진행됨. 

백엔드는 클라이언트의 요청을 받아서 해결하고 다시 넘겨주는 역할을 함. 

백엔드 개발자가 알아야할 것:

* 프로그래밍 언어를 하나는 알아야 함: JAVA, 파이썬, PHP, JavaScript(여기서는 자바 사용)
* 웹의 동작 원리
* 알고리즘, 자료구조
* 운영체제(서버에 자주 사용되는 리눅스), 네트워크
* 프레임워크(Spring)
* DBMS 데이터 관련(MySQL, Oracle)



---

#### 4)browser의 동작

Browser: 

* 서버에서 전송한 데이터가 클라이언트에 도착해야할 곳. 
* 데이터를 해석해주는 파서와 데이터를 화면에 표현해주는 렌더링엔진이 포함되어 있음. 
* 개발을 할 때 반드시 알아야 하는 내부는 아니지만 최적화된 웹개발을 할 수 있음. 
* 브라우저가 어떻게 HTML, CSS, 레이아웃 등을 파싱하고 계산하는지에 대한 원리가 담겨있음. 
* DOM tree로 브라우저 엔진이 작동함. (사진을 참고)



---

#### 5) browser에서의 웹 개발

#### 6) 웹서버

* URL 주소의 웹서버에 찾아가 해당 주소에 있는 애용을 보여줌. 
* 웹 서버 소프트웨어: 클라이언트가 요청하는 HTML문서나 리소스를 전달하는 것. 
  * 웹 브라우저나 **웹 크롤러**가 요청하는 리소스는 정적 데이터거나 동적인 결과일 수 있음. 
    * 정적: 이미지, HTML 파일, CSS 파일, JavaScript 파일 같이 저장되어 있는 데이터
    * 동적: 웹 서버로 실행되는 프로그램의 결과 
  * 클라이어트와 서버는 HTTP로 소통함.
* HTTP 프로토콜은 서버와 클라이언트가 통신할 때 필요한 규약.(규칙) 
* 렌더링: 가져온 이미지, CSS, HTML같은 것들을 하나로 합쳐서 함께 보여줌. 
* 웹 서버 소프트웨어 종류:
  * Apache, Nginx, Microsoft, Google 웹 서버 
  * Apache를 가장 많이 사용하며 오픈소스임. Nginx(차세대 웹서버로 불림)가 올라오고 있음.

웹 크롤링(Crawling): 웹 상에 존재하는 contents를 수집하는 작업: 

1. HTML페이지를 가져와서, HTML/CSS등을 파싱하고, 필요한 데이터만 추출하는 기법임. 
2. Open API를 제공하는 서비스에 Open API를 호출해서 받은 데이터 중 필요한 데이터만 추출하는 기법
3. Selenium등 브라우저를 프로그래밍으로 조작해서, 필요한 데이터만 추출하는 기법.



##### 생각해보기

* 네이버, 구글과 같은 검색을 할 수 있는 사이트에서 검색어를 입력하면 검색어가 포함된 웹 페이지 목록을 보여주는데 네이버와 구글은 검색어가 포함된 웹페이지를 어떻게 알 수 있었을까? 

웹 크롤러가 주소별로 웹을 크롤링(자주 업데이트 되므로 자주 이터레이팅함.)하고 리소시들을 주소별로 검토함. 검색어가 언급된 횟수와 page rank알고리즘을 사용해 리소스를 랭킹함. 쿼리 발생시 랭크에 맞게 링크와 리소스의 일부를 렌더링하여 브라우저에 보여줌. 



---

#### 7) WAS

Web Application Server 

클라이언트/서버 구조: 클라이언트는 서비스를 제공하는 서버에 정보를 요청하여 응답받은 결과를 사용함. 

DBMS: 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어.

미들웨어: DBMS를 직접 클라이언트가 연결되어 동작하는 방식이 보안 등의 문제를 일으킴.

* 클라이언트 쪽 비지니스 로직이 많을 경우 클라이언트 관리로 인한 비용이 많이 발생하여 미들웨어 서버에서 비즈니스 로직을 동작하여 클라이언트는 입출력만 담당하도록 함. 
* 미들웨어에서 대부분의 로직을 수행하고 데이터 조작할 일이 있을 때 DBMS에 접속하도록 함. 
* 클라이언트의 크기가 매우 작아지고 변경시 중앙의 미들웨어만 변경하면 됨. 

WAS: 동적인 기능이 필요하게 되므로, 복잡한 DBMS에 연관되며 미들웨어가 필요하게 됨.

* 프로그램 실행 환경과 데이터베이스 접송 기능을 제공
* 여러 트랜잭션(논리적 작업단위)을 관리.
* 업무처리하는 비지니스 로직을 수행함. 

* 웹 서버의 기능도 기본적으로 제공함.(이때 WAS, 톰캣같은 것으로 사용할 것.)
* 대용량 웹 어플리케이션의 경우 웹서버와 WAS를 분리하여 사용함. 



---

## HTML - FE

#### 1) HTML Tags

계층적으로 되어 있음.

모든 태그를 외울 필요 없이 필요한 태그를 가져다 쓸 수 있으면 됨. 

#### 2) HTML Layout 태그

* hearder: 상단 
  * <'div'> 로 세션을 나누어서 class id 선언을 hearder로 함. 
* section: 
  * 각 부분들에 대해서 세션 태그를 줌. 
* nav: navigation
  * 네이게이션 태그를 줌. 
* footer: 하단
  * footer라는  태그를 사용함. 
* aside: 사이드에서 사용함. 



> HTML, CSS 관련 문법 학습
>
> 톰캣 다운로드, 서블릿 파일 실행 실습

---

### Servlet - BE

#### 1) Servlet이란?

자바 웹 어플리케이션의 구성요소 중 동적인 처리를 하는 프로그램의 역할.

서블릿을 정의해보면 WAS에 동작하는 JAVA 클래스이다. 



#### 2) 서블릿 작성 방법

**서블릿은 동적으로 응답 결과를 만들어 내는 것.**

이미 만들어서 가지고 있는 것이 아니라, 요청이 들어오면 응답할 코드를 만들어 내고 그 코드로 응답을 하게 하는 것. 

* HTTP protocol에서 클라이언트가 요청하면 서버가 요청을 받아서 응답을 함. 
* 서버에서는 요청을 받아내는 객체와 응답하는 객체를 만들어 낸다. 

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{}
```

위의 코드에서 request와 response가 각각 서버에서 생성한 요청 객체와 응답 객체이다. 



###### Servlet 3.0이상/이하 사용

* 서블릿 버전 3.0이상을 사용할 시에는 web.xml파일을 사용하지 않고 자바 annotation으로 url pattern을 지정한다. 
* 3.0 이하를 사용할 때에는 web.xml파일이 생성되어 그곳에 소스코드가 있는 클래스 이름, url pattern등이 등록되어 있다. 
  * 클라이언트에서 요청이 왔을 때, web.xml파일을 참고하여서 해당 클래스를 찾아서 응답하는 것이다. 

###### 실습 소스 코드

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
  response.setContentType("text/html;charset=utf-8");
  PrintWriter out = response.getWriter();
  out.print("<h1>1부터 10까지 출력</h1>");
  for(int i=1;i<=10;i++){
    out.print(i+"<br>");
  }
  out.close();
}
```

위에서 `print()`를 쓰거나 `println()`을 쓰거나 차이가 없음. 

* 자바에서는 new line이 되지만 html에서는 enter로 new line이 되는 것이 아니라 br 태그가 있어야 하기 때문. 
* 첫번째 라인의 `setContentType()`은 응답하는 형식을 정해주는 것임. 위의 경우 응답 형식이 text인 html이라는 것을 지정해주는 것임. 



#### 3) Servlet 라이프 사이클

서블릿 객체의 생성부터 소멸까지의 과정 라이프 사이클을 둘러본다. 

HTTP Servlet 생명주기: **init() -> service()-> destroy() **

처음 호출 시 => init() 호출 / 초기 1회 

* 메모리에 올리는 작업

Server 메소드 호출 => 응답하는 모든 내용은 서비스에 구현

마지막 => destroy() 호출 / 말기 1회 

* 메모리에서 삭제하여 종료.



**Service 메소드:** 

* WAS는 매번 service만 호출한다.
* Override 하지 않았다면 부모의 service를 호출 할 것.
  * 부모의 service메소드에서는 클라이언트의 요청이 GET일 경우 자신이 가지고 있는 doGet메소드를 호출
  * 클라이언트의 요청이 POST일 경우 자신이 가지고 있는 doPost를 호출



#### 4) Request, Response 객체 이해하기

 WAS는 웹 브러우저로부터 Servlet 요청을 받는다. 

* 받은 요청을 HttpServletRequest 객체를 생성하여 저장
  * 헤더정보, 파라미터, 쿠키, URL, 등등의 정보를 읽는 메소드를 가짐.
  * Body의 stream을 읽는 메소드를 가짐. 
* 응답을 보내기 위한 HTTPServletResponse객체를 생성.   
  * WAS는 어떤 클라이언트가 요청을 보냈는지 알고 있고 응답을 보내기 위함 객체.
  * Content type, 응답코드, 응답 메세지 등을 전달. 
* 생성된 두 객체를 서블릿에 전달. 



**클라이언트가 서버에 요청 정보를 보낼 때:**

<mark>헤더정보:</mark>

​	*웹 브라우저가 전송한 모든 헤더 정보 출력해보기*

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{
  response.setContentType("text/html"); //type setting
  PrintWriter out = response.getWriter(); //출력 writer 선언
  out.println("<html>"); //html 코드시작
  out.println("<head><title>form</title></head>");
  out.println("<body>");
  
  Enumeration<String> headerNames = request.getHeaderNames(); //request가 가지고 있는 header 이름을 문자열 enumeration 객체로 반환해줌. 
  while(headerNames.hasMoreElements()) {
    String headerName = headerNames.nextElement();
    String headerValue = request.getHeader(headerName); //header의 정보를 알아내는 메소드
    out.println(headerName + " : " + headerValue + " <br> "); //응답결과 전송함. 
  }
  
  out.println("</body>");
  out.println("</html>");
}
```



<mark>파라미터:</mark>

http://localhost:8080/firstweb/param?name=kim&age=5 라는 URL에서 '?'뒤에 있는 것들이 parameter이고, '&'로 구분되어 있음.

'='기준으로 앞은 parameter의 이름, 뒤에는 해당 값이 적혀져 있음.

​	*parameters 출력해보기*

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{
  response.setContentType("text/html"); //type setting
  PrintWriter out = response.getWriter(); //출력 writer 선언
  out.println("<html>"); //html 코드시작
  out.println("<head><title>form</title></head>");
  out.println("<body>");
  
  String name = request.getParameter("name");//parameter이름에 해당하는 값을 가져오는 메소드(문자열로 반환)
  String age = request.getParameter("age");
  
  out.println("name: "+name+"<br>");
  out.println("age: "+age+"<br>");
  
  out.println("</body>");
  out.println("</html>");
}
```

이러한 parameter는 반드시 URL로 전송해야하는 것은 아니고, html의 <form> 태그를 사용하여서 input에 넘길 parameters를 지정할 수도 있다. 



<mark>그 외 정보:</mark>

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{
  response.setContentType("text/html"); //type setting
  PrintWriter out = response.getWriter(); //출력 writer 선언
  out.println("<html>"); //html 코드시작
  out.println("<head><title>form</title></head>");
  out.println("<body>");
  
  String uri = request.getRequestURI();
  StringBuffer url = request.getRequestURL();
  String contentPath = request.getContextPath();
  String remoteAddr = request.getRemoteAddr();
  
  out.println("uri: "+ uri + "<br>");
  out.println("url: "+ url + "<br>");
  out.println("contentPath: "+ contentPath + "<br>");
  out.println("remoteAddr: "+ remoteAddr + "<br>");
  
  out.println("</body>");
  out.println("</html>");
}
```

각각 클라이언트 요청 정보가 가지고 있는 다른 기타 정보들을 출력해본다. 

