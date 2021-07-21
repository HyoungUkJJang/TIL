# BindingResult란?
### 스프링이 제공하는것으로 검증오류를 보관하는 객체이다.
### @ModelAttribute에 데이터 바인딩 시 오류가 발생해도 컨트롤러가 호출된다.
### 객체 타입 오류로 바인딩이 실패하는 경우에 FieldError를 생성하여 객체에 넣어준다.
### 사용자가 직접 검증로직을 구현한 것과 다르게 해당 입력받는 타입과 맞지 않으면 다르게 에러를 표현해준다.
![image](https://user-images.githubusercontent.com/50834204/126457637-3484f081-ba64-4bf7-96dd-c45161834dd2.png)

