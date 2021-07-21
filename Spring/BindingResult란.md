# BindingResult란?
1. 스프링이 제공하는것으로 검증오류를 보관하는 객체이다.
2. @ModelAttribute에 데이터 바인딩 시 오류가 발생해도 컨트롤러가 호출된다.
3. 객체 타입 오류로 바인딩이 실패하는 경우에 FieldError를 생성하여 객체에 넣어준다.
4. 사용자가 직접 검증로직을 구현한 것과 다르게 해당 입력받는 타입과 맞지 않으면 다르게 에러를 표현해준다.

![image](https://user-images.githubusercontent.com/50834204/126457637-3484f081-ba64-4bf7-96dd-c45161834dd2.png)
5. BindingResult는 순서가 중요하기 때문에 @ModelAttribute 뒤에 작성해야한다.

#### BindingResult 오류를 검증하는 방법은 3가지가 잇다.
1. 직접 검증로직을 작성하기
2. FieldError 사요ㅕㅇ하기
3. validation 사용하기

#### BindingResult의 구현체
- BindingResult는 인터페이스이며 Errors 인터페이스를 상속받고 있다.(인터페이스 끼리의 상속은 extends를 사용함)
- 실제 구현체는 BeanPropertyBindingresult 객체로 두 인터페이스 모두 구현하고 있기 때문에 둘다 사용이 가능하다.
- BindingResult가 Errors를 상속받아 더 많은 기능을 제공하고 있기 때문에 보통 BindingResult를 많이 사용한다.




