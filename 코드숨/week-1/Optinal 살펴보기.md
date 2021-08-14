# Optional 이란
* 참고 사이트  - https://johngrib.github.io/wiki/java-optional/

* 옵셔널은 주로 “결과 없음(no result)”을 나타낼 필요가 있고 null을 사용하면 오류가 발생할 수 있는 메소드의 리턴 타입으로 사용하기 위한 것이다. 타입이 옵셔널인 변수는 절대로 null이 아니어야 하며, 항상 옵셔널 인스턴스를 가리켜야 한다.

## 옵셔널 사용 시 주의해야할 사항
* 옵셔널은 필드 타입이나 파라미터로 사용하기에 적정하지 않다.
* 옵셔널은 제한적으로 라이브러리 메소드 등에서 “결과 없음”을 표현하기 위해 설계된 것이다.
* 옵셔널을 필드 멤버로 사용하면 해당 클래스를 Serializable할 때 문제가 된다.
* 가급적 return 구문에서만 사용해보자.
* 옵셔널 클래스는 필드 형식으로 사용할 것을 가정하지 않았기 때문에 Serializable 인터페이스를 구현하지 않는다. 즉 도메인 모델에 옵셔널을 사용하면 직렬화 모델을 사용하는 도구나 프레임워크에 문제가 생길 수 있다. 직렬화 모델이 필요하다면 옵셔널로 값을 반환받을 수 있는 메소드를 추가하는 방식을 권장함 !



## 옵셔널 생성 메소드
* Optinal.of - value가 null인 경우에 NPE 예외를 던져준다. 반드시 값이 있어야 하는 객체인 경우에 해당 메소드를 사용한다.
``` java

Optional<String> str = Optional.of("hello");

```

* Optional.ofNullable - value가  null인 경우에 비어있는 Optional을 반환해준다. 값이 null일수도 있는 곳에 해당 메소드를 사용한다.
``` java

Optional<String> str = Optional.ofNullable(null);

```

* Optional.empty - 비어있는 옵셔널을 생성해준다. 조건에 따라 분기를 태우거나 반환할 값이 없는 경우에도 사용함
``` java

Optional<String> str = Optional.empty();

```


## 옵셔널 객체 메소드
* filter - predicate 값이 참이면 필터를 통과시키고 거짓이면 통과되지 않는다.
* map - mapper 함수를 통해 입력값을 다른 값으로 변환하는 메소드
* flatMap - mapper 함수를 통해 입력값을 다른 값으로 변환하는 메소드 
* ifPresent - 최종 연산이 끝난 후 값이 비어있지 않다면 입력값으로 주어진다. 
* isPresent - 연산을 끝낸 후 객체가 존재하는지 여부를 판별한다
* get - 옵셔널 객체의 값을 가져오고 비어있으면 예외를 던져준다.
* orElse - 연산을 끝난 후에도 객체가 비어있다면 기본값으로 제공할 객체를 지정한다.
* orElseGet - 연산을 끝난 후에도 옵셔널 객체가 비어있다면 기본값으로 제공할 함수를 지정한다.
* orElseThrow - 연산을 끝난 후에도 객체가 비어있다면 함수를 통해 예외를 던져준다.
