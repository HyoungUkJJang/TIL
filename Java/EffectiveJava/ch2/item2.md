# 생성자에 매개변수가 많다면 빌더를 고려하라
* 정적 팩터리와 생성자는 매개변수가 많을 경우 대응하기 어렵다는 공통점이 존재한다.
* 이러한 상황에서는 원래 점층적 생성자 패턴을 주로 사용해왔다.

```java
public class NutritionFacts{
	private final int servingSize;
	private final int servings;
	private final int calories;
	private final int fat;
	private final int sodium;
	private final int carbohydrate;

// 필수항목
public NutritionFacts(int servingSize, int servings) {
	this servingSize=servingSize;
	this.servings = servings;
}

// 선택항목 하나 추가
public NutritionFacts(int servingSize, int servings, int calories) {
	this servingSize=servingSize;
	this.servings = servings;
	this.calories = calories;
}

// … 이런 식으로 선택항목 사항을 늘려가면서 만든다.
```

* 만약 입력받는 매개변수가 6개가 아니라 더 많아진다고 생각했을때, 점층적 생성자 패턴은 매개변수가 많아지면 클라이언트 코드를 작성하거나 읽기가 어려운 단점이 존재한다.
* 타입이 같은 매개변수가 연달아 존재하면 잡기 힘든 버그로 이어 질 수도 있기 때문이다.


```java
public class NutritionFacts{
	private int servingSize;
	private int servings;
	private int calories;
	private int fat;
	private int sodium;
	private int carbohydrate;

// 자바빈즈 패턴
public Nutritionfacts() {};

// 세터 메서드
public void setServingSize(int value);
public void setServings(int value);
public void setCalories(int value);
...~~

// 사용 예
psvm {
	NutritionFacts ob = new NutritionFacts();
	ob.setServingSize(200);
	ob.setCalories(300);
}

```

* 자바빈즈 패턴은 생성자 패턴과 달리 세터 메서드를 이용하여 작성하기 때문에 보기 더 쉽지만 객체가 완전히 생성되기 전까지는 일관성이 무너진 상태에 놓이게 된다.

* 점층적생성자 패턴은 매개변수를 생성자에서 확인하면 일관성을 유지할 수 있었는데 자바빈즈 패턴은 그 일관성이 무너지게 되버린다. 
* 또한 불변으로 만들수가 없다.
* * 대안 방법으로 생성자 패턴의 안정성과 자바빈즈 패턴의 가독성을 합한 빌더패턴을 이용하는 것이다.*

## 빌더패턴
* 빌더패턴은 필수 매개변수만 생성자or정적 팩터리로 호출하여 객체를 얻고 선택 매개변수는 세터 메서드를 활용하는 것이다.
* 그후 매개변수가 없는 build 메서드를 호출하여 불변인 객체를 얻는 방법이다.

```java

public class Nutritionfacts{

	private final int servingSize;
	private final int servings;
	private final int calories;
	private final int fat;
	private final int sodium;
	private final int carbohydrate;

	public static class Builder{
	
	//필수
	private final int servingSize;
	private final int servings;

	//선택
	private int calories;
	private int fat;
	private int sodium;
	private int carbohydrate;

	public Builder(int servingSize, int servings){
	this.servingSize = servingSize;
	this.servings = servings;
	}

	public Builder calories(int value) {
	calories = value;
	return this;
	}

	public Builder fat(int value) {
	fat = value;
	return this;
	}
	// ..이런 방식으로 선택 메서드 작성

	public Nutritionfacts build(){
	return new Nutritionfacts(this);
	}
}

private Nutritionfacts(Builder builder) {
	servingSize = builder.servingSize;
	servings = builder.servings;
	calories = builder.calories;
	// .. ~~~
	}
}
```

### 빌더패턴 사용예시

``` java
Nutritionfacts ob = new Nutritionfacts.Builder(100,200).caloreis(100).sodium(200).fat(300).carbohydrate(10).build();
```

* 이 패턴의 장점은 쓰기 쉽고 읽기가 쉽다는 장점이 있다. 
* 빌더 패턴은 계층적으로 설계된 클래스와 함께 사용하면 좋다.
