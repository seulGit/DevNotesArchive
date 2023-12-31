
개발자 web필수개론
==============

www : 전세계 모든 사람들이 정보를 공유할 수 있는 공간

### web의 용도

1. 웹서비스(웹사이트)
2. API 웹서비스
3. 사용자 인터페이스(브라우저), IPTV

http : HyperTextTransferProtocol
URI : 리소스 식별자
html : REST(자원의 상태전달) = 네트워크 아키텍쳐

1. client, server : 클라이언트와 서버의 분리
2. StateLess : 요청에 대해 클라이언트의 상태를 저장하지않는다
3. cache : 서버의 응답을 임시저장할 수 있어야한다
4. 계층화 : 서버와 클라이언트 사이에 방화벽 게이트웨이 등 다양한
계층으로 구성 및 확장이 가능해야한다
5. 인터페이스 일관성
6. CoD(Code on Demand) : 특정한 기능을 서버로부터 클라이언트가 받아
코드를 실행할 수 있어야 한다

### 리소스 식별

- URI : 인터넷에서 특정 '자원'을 나타내는 주소값
(말그대로 경로 자체를 나타낸다 / 요청에 의한 응답이 달라질 수 있음)
[www.goott.co.kr/resource/1](http://www.goott.co.kr/resource/1) -> 응답: 커리큘럼.pdf
- URL : 인터넷에서 자원이나 특정한 파일들이 어느 위치인지 식별하는 주소
[www.goott.co.kr/resource/커리큘럼.pdf](http://www.goott.co.kr/resource/%EC%BB%A4%EB%A6%AC%ED%81%98%EB%9F%BC.pdf)

HTTP : 메세지를 주고받는(req,res)형태의 통신규약

Http status code : 응답의 상태를 나타내는 코드
100번대(처리중) : 처리가 진행되고있는상태
200번대(성공) : 요청의 성공
300번대(리다이렉트) : 다른 자원으로의 리다이렉트
400번대(클라이언트에러) : 요청에 에러가 있는 상태
500번대(서버에러) : 서버 처리중 에러가 발생한 상태

200: 성공
201: +리소스 생성
301: 리다이렉트, 리소스가 다른장소로 변경됨
303: 클라이언트에서 자동으로 새로운 리소스로 요청처리
400: 요청 오류(파라미터 에러)
401: 인증실패
404: 리소스x
500: 서버 내부에러(동작처리 에러)
503: 서비스 중지
