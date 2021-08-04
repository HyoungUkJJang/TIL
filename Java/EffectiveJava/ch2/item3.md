# private  생성자나 열거 타입으로 싱글턴임을 보증하라
### 싱글턴
* 인스턴스를 오직 하나만 생성할 수 있는 클래스다.
* 무상태 객체나 설계상에서 유일해야 하는 시스템 컴포넌트를 예로 들 수 있다.

### 싱글턴의 단점
* 클라이언트 테스트가 어렵다. 

```java
// public static final 필드방식 싱글턴
public class Elvis{
	// public static final 필드는 인스턴스를 초기화할때 딱 한번만 호출됨
	public static final Elvis Instance = new Elvis();

	// public이나 protected생성자가 없기때문에 싱글턴이 보장된다.
	private Elvis() {}
	
	public void leaveTheBuilding() {…}
	}
```
* 권한이 있는 클라이언트는 리플렉션 아이템 AccesibleObject.setAccesible을 사용하여 private 생성자를 호출할 수 있다. 이러한 공격을 방어하기 위해 두번 째 객체가 생성되려고 할 때 예외를 던져주도록 설계한다.

```java
// 정적 팩터리 메서드 싱글턴
public class Elvis{
	// public static final 필드는 인스턴스를 초기화할때 딱 한번만 호출됨
	public static final Elvis Instance = new Elvis();

	// public이나 protected생성자가 없기때문에 싱글턴이 보장된다.
	private Elvis() {}
	
	// 항상 같은 객체를 참조하도록 구현함
	public static Elvis getInstance() { return Instance; }

	public void leaveTheBuilding() {…}
	}
```
