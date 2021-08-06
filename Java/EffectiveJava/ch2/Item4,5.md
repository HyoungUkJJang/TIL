# Item4 - 인스턴스화를 막으려면 private 생성자를 사용하자
```java
public class InstanceClass {
	// 기본생성자가 만들어지는것을 방지한다.
	private InstanceClass () {
		throw new AssertionError();
	}
}
```

* 명시적 생성자가 private 기 때문에 클래스 밖에서 생성할 수 없다.

# Item5 - 자원을 직접 명시하지 말고 의존 객체 주입을 사용하자
 * 의존 객체 주입은 유연성과 테스트 용이성을 높여준다.
```java

public class SpellChecker {
	private final Lexicon dictionary;

	public SpellChecker(Lexicon dictionary) {
		this.dictionary = Object.requireNonNull(dictionary);
	}

	public boolean isValid(String word) {...}
	public List<String> suggestions(String typo) {...}
}

```

* 위 코드에서 dictionary 하나의 자원을 사용하고 있지만 자원이 몇개든 의존관계가 어떻든 잘 작동한다. 또한 불변을 보장하여 안심하고 공유가 가능하다.

* 클래스가 내부적으로 하나 이상의 자원에 의존하고, 자원이 클래스 동작에 영향을 준다면 싱글턴과 정적 유틸리티는 사용하지 않는것이 좋다.

