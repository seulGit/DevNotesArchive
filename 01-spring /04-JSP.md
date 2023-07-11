JSP
===

### JSP 태그의 종류와 사용방법

- JSP내에서 java 코드를 사용할 수 있다
but JSP가 HTML 기반이기떄문에 JAVA코드를 넣어서 동작시키려면
JSP태그 사이에 삽입해야한다
- 사용자에게 HTMl 코드만 전송하는 장점이 있음

지시자( <%@ %> ) : 페이지 속성 지정
주석( <%-- %> )
선언( <%! %> :변수, 메서드의 선언
표현식 (<%= %) 결과값 출력
스크립트릿 (<% %> : JAVA 코드 삽입시 사용
액션태그<jsp:action)</jsp:action> : 페이지 삽입, 공유, 자바 빈 사용
jsp:forward : 페이지간의 제어 이동
jsp:useBean : 자바 빈을 페이지에서 사용할 수 있게
jsp:param : forward include 안에서 세트로 사용. 파라미터 받아올때 사용

액션태그<jsp:action)</jsp:action> : 페이지 삽입, 공유, 자바 빈 사용
jsp:forward : 페이지간의 제어 이동
jsp:useBean : 자바 빈을 페이지에서 사용할 수 있게
jsp:param : forward include 안에서 세트로 사용. 파라미터 받아올때 사용

<br/>

### JSP 내장객체 구조와 생명주기

- request : 요청관련처리
- response : 응답관련처리
- out : 출력
request, response, out 객체들은 브라우저에서 서버로
요청을하고 서버에서 브라우저로 회신해준후 이객체들은 모두 소멸
request, response는 요청을 처리하는 과정에서 사용되는
JSP와 서블릿이 모두 공유한다
- page (x) : include와 연동해서 사용하는 객체/데이터를 가져올떄 사용
- config
- application
- exception
- pageContext (x)
- session


