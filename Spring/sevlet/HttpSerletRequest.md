HTTP 요청 메시지를 개발자가 직접 파싱해서 사용하기엔 많은 불편함이 따르게된다. 서블릿은 개발자가 HTTP 요청 메세지를 편리하게 사용할 수 있도록 개발자 대신에 HTTP 요청 메시지를 파싱해준다. 
그 결과를 HttpServletRequest 객체에 담아서 제공해준다.


1. 구조

- START LINE : HTTP메소드, URL, 쿼리스트링, 스키마, 프로토콜
- HEADER : 헤더 조회
- BODY : form 파라미터 형식, message body 데이터 직접 조회

2. 부가기능

- 임시 저장소 기능 : HTTP 요청이 시작부터 끝까지 유지되는 임시 저장소기능
- 세션 관리 기능 


중요한것은 Request, Response 둘다 HTTP응답 메시지를 편리하게 사용하도록 도와주는 객체라는 점이다.


HTTP 요청 데이터는 주로 3가지 방법을 사용한다.

1. Get - 쿼리 파라미터
- /url?username=uk&age=26
- 메세지 바디 없이 url의 쿼리 파라미터에 데이터를 포함해서 전달함
- 검색, 페이징에 사용됨


2. Post - html form
- content-type : application/x-www.form-urlencoded
- 메시지 바디에 쿼리 파라미터 형식으로 전달 username=uk&age=26
- 회원가입, 주문, html form에 사용


3. HTTP message body 에 데이터를 직접 담아서 요청
- HTTP API에서 주로 사용 JSON, XML, TEXT 정보를 그대로 담아서 전달가능
- 주로 JSON을 사용
- POST, PUT, PATCH 에서 사용가능



