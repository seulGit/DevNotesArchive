# react

실제 DOM과 virtual DOM의 연결

JSX: 리액트에서 생김새를 정의할 때 사용하는 문법

→ HTML같은 Document타입 언어로 보이지만

실제로는 JS코드

JSX의 규칙

1. 태그는 반드시 종료되어야한다
2. 태그와 태그 사이가 비어있으면 안된다
3. DIV을 웬만하면 쓰는게 좋지만 맘에 안들면 fragment 사용 
4. fragment: <></> (div등을 쓰기 애매하면 사용하는 방식)

컴포넌트 생성

리액트의 컴포넌트는 2가지 형태가 있음

과거: class

최근: function

리액트에서의 주석은 return 안쪽과 바깥쪽이 처리하는방식이 다르다.

리턴 바깥: js와 같음

리턴 안쪽: {}가 필요 . /* */

fragment안이냐 밖이냐 에 따라 또 다름

props

사용자가 어떠한 값을 컴포넌트에게 전달해줄때 사용

props는 객체 형태로 전달된다