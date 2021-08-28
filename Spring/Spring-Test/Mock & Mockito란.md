#### https://johngrib.github.io/wiki/java-mockito/
##### https://mangkyu.tistory.com/145?category=761302 참고하여 학습했습니다.

### Mock
***
- Mock은 진짜 객체와 비슷하게 동작을 하지만 개발자가 직접 객체의 행동을 관리하는 객체
***

### Mockito
***
- Mock을 쉽게 만들고 관리, 검증할 수 있는 기능들을 제공한다.
***

### 사용법
1. @Mock : Mock 객체를 만들어 반환
2. @Spy : Stub하지 않은 메소드들을 원본 메소드 그대로 사용하는 어노테이션
3. @InjectMocks : @Mock, @Spy로 생성된 가짜 객체를 자동으로 주입시켜주는 어노테이션
4. @MockBean: 스프링 컨텍스트에 mock객체를 등록하고 스프링 컨텍스트에 의해 @Autowired가 동작할 때 등록된 mock 객체를 사용할 수 있도록 동작하게 해준다.


#### Mock 객체 만들기
- mock(className.class) 식으로 Mock 객체를 받을 수 있다.
- Mock 객체는 내부의 코드는 모두 동작하지 않고, 리턴값으로 0, false, null로 대체함


## MockMvc란?
***
**서블릿 컨테이너 구동 없이 시물레이션된 MVC 환경에 모의 HTTP 요청을 전송하는 기능을 제공한다.** 
***

### MockMvc - perform()
* MockMvc가 제공해주는 perform() 메소드는 브라우저에서 서버로 url을 요청하듯 컨트롤러를 실행시킬 수 있는 메소드이다. RequestBilder 객체를 인자로 받고 MockMvcRequestBuilders의 정적 메소드를 이용해서 생성한다.
* ResultActions 인터페이스를 반환한다.

#### perform() 메소드와 같이 사용할 수 있는 정보
- param/params : 요청 파라미터 설정
- header/headers : 요청 헤더 설정
- cookie : 쿠키설정
- content : 요청 본문 설정
- requestAttr : 요청 스코프에 객체 설정
- sessionAttr : 세션 스코프에 객체 설정

### MockMvcRequestBuilders
* Get, Post, Put, Delete 요청 방식과 매핑되는 get(), post(), put(), delete() 메소드를 제공한다.
 메소드와 함께 전송할 param, header, content, contentType 등을 추가로 셋팅하여 테스트가 가능하다.
    
 

* 메소드들은 MockHttpServiletRequestBuilder 객체를 리턴하며 HTTP 관련 정보를 설정할 수 있다. 

#### MockMvcRequestBuilders 메소드
- isOk() -> 응답 상태코드가 정상적인 처리(200)인지 확인
- isNotFound() -> 응답 상태코드가 404 Not Found인지 확인
- isMethodNotAllowed() -> 응답 상태코드가 메소드 불일치(405)인지 확인
- isInternalServerError() -> 응답 상태코드가 500인지 확인
- is(int status) -> 몇번 응답코드가 설정되어있는지 확인

### andExpect()
- perform 메소드를 이용하여 요청을 전송하면 ResultActions 객체를 리턴하게 된다. 이 객체는 응답결과를 검증할 수 있는 andExpect() 메소드를 제공해준다. 
- andExpect()가 요구하는 ResultMatcher는 MockMvcResultMatchers에 정의된 정적 메소드를 통해 생성할 수 있다.

### MockMvcresultMatcher 메소드
- isOk() -> 응답 상태코드가 200인지 확인
- isNoContent() -> 응답 상태코드가 204인지 확인
- isNotFound() -> 응답 상태코드가 404인지 확인
- isMethodNotAllowed() -> 응답 상태코드가 405인지 확인
- isInternalServerError() -> 응답 상태코드가 500인지 확인
- is(int status) -> 몇번의 상태코드가 설정되었는지 확인

