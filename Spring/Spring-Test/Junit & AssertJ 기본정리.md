#### https://bibi6666667.tistory.com/231 님의 게시글을 보면서 학습하였습니다.

# Junit
- 자바의 단위 테스트를 위한 라이브러리

### Junit의 assert메소드
- assertEquals(A,B) - 객체 A와 B가 같은 값을 가지고 있는지 확인
```java
        Task task = new Task();
        task.setTitle("test");
        task.setId(1L);

        assertEquals(task.getTitle(), "test"); // true
        assertEquals(task.getId(),1L); // true
```
- assertArrayEquals(A,B) - 배열 A와 B의 값이 같은지 확인
```java
        List<Task> arrA = new ArrayList<>();
        List<Task> arrB = new ArrayList<>();

        Task taskA = new Task();
        taskA.setTitle("taskA");
        taskA.setId(1L);
        
        arrA.add(taskA);
        arrB.add(taskA);
        assertArrayEquals(arrA.toArray(), arrB.toArray()); // true
```
- assertSame(A,B), assertNotSame(A,B) - A와 B가 같은 객체인지 아닌지 확인
```java
        Task taskA = new Task();
        taskA.setTitle("taskA");
        taskA.setId(1L);


        Task taskB = new Task();
        taskB.setTitle("taskB");
        taskB.setId(2L);

        Task copyTask = taskA;

        assertSame(taskA,copyTask); // true
        assertNotSame(taskB, copyTask); // 값이 다르기 때문에 테스트 통과
```
- assertTrue(A), assertFalse(A) - 조건 A가 참, 거짓인지 확인
```java
        Task taskA = new Task();
        taskA.setTitle("taskA");
        taskA.setId(1L);

        assertTrue(taskA.getTitle().equals("taskA")); // true
        assertFalse(taskA.getId().equals(2L)); // 거짓이기 때문에 테스트 통과
```
- assertNull(A), assertNotNull(A) - A가 null인지 아닌지 확인
```java
        Task taskA = new Task();
        assertNull(taskA.getId()); // true

        Task taskB = new Task();
        taskB.setTitle("taskB");
        taskB.setId(2L);
        assertNotNull(taskB.getId()); // 널이 아니기 때문에 테스트 통과
```

### Junit의 어노테이션
- @Test() : 메소드 위에 작성하여 테스트 메소드임을 명시해준다.

- @Ignore : 메소드 위에 @Ignore를 붙이면 해당 메소드는 테스트 하지 않는다.

- @BeforeEach : Test메소드 실행 전에 항상 먼저 실행시킬 메소드에 작성하여준다.

- @BeforeAll : 테스트 클래스가 실행될 때 한번만 실행되는 메소드

- @AfterEach : Test메소드 실행 후에 항상 실행시킬 메소드에 작성하여준다.

- @AfterAll : 클레스에 테스트가 모두 끝난 뒤에 한번만 실행되는 메소드



# AssertJ
- Junit의 테스트코드에 사용되고 테스트코드의 가독성과 편의성을 더 높여주는 라이브러리다.
- AssertJ의 테스트코드는 assertThat()으로 시작한다. 또한 메소드를 연쇄적으로 호출하여 테스트 코드를 작성할 수 있다.



### AssertJ 의 메소드
- isEqualsTo(Object o) : 실제 값이 주어진 값과 같은지 확인
```java
        Task taskA = new Task();
        taskA.setId(1L);
        taskA.setTitle("taskA");

        assertThat(taskA.getId()).isEqualTo(1L); // 값이 같다 true
        assertThat(taskA.getTitle()).isEqualTo("taskB"); // 값이 다르다 false

```
![](https://images.velog.io/images/gudnr1451/post/0119ca24-5094-451e-9131-8fab0f3b59b3/image.png)

- isNotEqualsTo(Object o) : 실제 값이 주어진 값과 다른지 확인
```java
        Task taskA = new Task();
        taskA.setId(1L);
        taskA.setTitle("taskA");

        assertThat(taskA.getId()).isNotEqualTo(2L); // 값이 다르기 때문에 테스트 통과
        assertThat(taskA.getTitle()).isNotEqualTo("taskA");  // 값이 같기 때문에 테스트 실패

```
- isInstanceOf(Class<?> Type), isNotInstanceOf(Class<?> Type) : 실제 값이 주어진 유형의 인스턴스 인지 확인
```java
	Task taskA = new Task(); // 같은 클래스
        taskA.setId(1L);
        taskA.setTitle("taskA");

        assertThat(taskA).isInstanceOf(Task.class); // 같은 클래스 true
        assertThat(taskA).isNotInstanceOf(org.springframework.scheduling.config.Task.class); // 다른클래스 true

```
- isNull, isNotNull : null인지 확인 / null이 아닌지 확인
```java
	Task taskA = new Task(); // 같은 클래스
        taskA.setId(1L);
        assertThat(taskA.getTitle()).isNull(); //  null이므로 true
        assertThat(taskA.getId()).isNotNull(); // null이 아니므로 테스트 통과
        
```
- isSameAs, isNotSameAs : 실제 값이 주어진 값과 동일한지 확인 / 다른지 확인
```java
        Task taskA = new Task();
        taskA.setId(1L);
        taskA.setTitle("taskA");

        Task copyTask = taskA;

        Task taskB = new Task();
        taskB.setId(1L);
        taskB.setTitle("taskA");

        assertThat(taskA).isSameAs(copyTask); // 같은 객체를 참조하므로 true

        assertThat(taskA).isSameAs(taskB); // 값은 같지만 다른 객체 이므로 false
        assertThat(taskA).isNotSameAs(taskB); // 다른 객체이기 때문에 테스트 통과

```
