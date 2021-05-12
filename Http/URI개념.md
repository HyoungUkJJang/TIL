URI(Uniform Resource Identifier)

URI ? L? N? 무슨차이일까,,

URI는 로케이터, 이름 또는 둘다 추가로 분류될 수 있다.

URI는 URL(Resource Locator), URN(Resource Name) 을 포함하고있는 큰 개념이다.

Uniform - 리소스를 식별하는 통일된 방식
Resource - 자원, URI로 식별할 수 있는 모든것(구분할 수있는 모든것 교통정보 등등)
Identifier - 다른 항목과 구분하는데 필요한 정보

URL - Locator 리소스가 있는 위치를 지정
URN - Name: 리소스에 이름을 부여
위치는 변할 수 있지만 이름은 변하지 않는다.

URL 문법 : scheme://[userinfo@][host][:port][/path][?query][#fragment]
ex) https://www.google.com:443/search?q=hello&hl=ko
프로토콜(https://)
호스트명(www.google.com)
포트번호(443)
패스(/search) - 리소스가 있는 경로 계층적 구조로 되어있다
쿼리 파라미터(q=hello&hl=ko) - 키-벨류 형태이고 ?로 시작한다. &으로 계속해서 파라미터를 붙일 수있다
*userinfo는 거의 사용하지않음*

http(80) / https(443) 는 주료 사용하는 포트라 생략이 가능


