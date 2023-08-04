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

<br/>

### EL(Expression Language)

JSP 스크립트 태그를 제거하기 위해 나온 개념.

- EX : ${parameter.key(name)}
- 목적 : 저장 객체의 출력은 단순화
- 특징
    - page, request, session, application 등의 객체에 접근해 출력을 처리
    - 해당값이 null이거나 공백이라 해도 에러는 발생하지 않음
    - EL은 JSP에서는 기본으로 지원하고 JSTL은 따로 호출해야 한다
- 예시
    - <%= request.getParameter(”name”)%> → ${param.name}
    - <%= userDTO user = (UserDTO)request.getAttribute(”user”) %> → ${user}
- 내장객체
    - ${pageScope}
    - ${requestScope}
    - ${sessionScope}
    - ${applicationScope}
    - ${param}
    - ${cookie}
    - ${header}
    - ${pageContext}
    - #{initParam}
 
- 대표 라이브러리
    - core(c) : 변수선언,조건,제어,반복 등의 기능을 제공
    - formatting(fmt) : 숫자,날짜 시간을 formatting, 국제화, 다국어 지원기능 제공
    - function(fn) : 문자열을 처리하는 함수를 제공
    - database(sql) : DB데이터 입력 수정 삭제 조회
    - xml(x) : xml문서 처리시 사용
 

- 코어 태그
    - <c:set> : 변수에 값을 할당
        - set으로 객체 프로퍼티값을 설정할때는 setter의 리턴타입이 반드시 void
    - <c:out> : 값 출력(무조건 문자열 출력)
        - 어떤값을 넣어도 문자열을 출력해야할때. 태그규칙을 지키기위해.
    - <c:if> : 일반적 if(else if,else xxxxxx)
        - jstl 연산자 표현
            - +, *
            - 연산부호
                
                
                | jstl | 연산부호 |
                | --- | --- |
                | div | / |
                | or | || |
                | and | \&\& |
                | eq | == |
                | ne | != |
                | ge | <, <= |
                | lt | > |
                | le | >= |
    - <c:forEach> : 반복문
        - <c:forEach var=”변수명" items=”목록 데이터" begin=”시작인덱스” end=”종료인덱스”>
            
            컨텐츠
            
            items에 들어올 수 있는 데이터 타입
            
            -배열
            
            -컬렉션
            -iterator
            
            -Map
            
            -콤마로 나열된 문자열들(JSON)
            
            </c:forEach>
            
    - <c:choose> : switch와 동일
    - <c:when> : else if/case문
    - <c:otherwise> : default
    - <c:url> : url 생성
        - 파라미터를 포함한 url생성시 사용
    - <c:redirect> : redirect 처리
 
  ```
  Core	<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
 XML	<%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %>
 formatting	<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
 Database	<%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>
 Functions	<%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>

 prefix는 꼭 c, fmt등으로 지정해야하는것은 아니지만 JSTL에서 권장하는 접두사.
  ```

- JS와 JSTL
JS	JSTL
JS에서는 JSTL의 값을 받을 수 있다	JSTL에서는 JS의 값을 받을 수 없다
