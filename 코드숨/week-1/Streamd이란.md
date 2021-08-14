# 스트림이란 
* https://galid1.tistory.com/674 님의 게시글을 보며 따라하며 학습하였습니다.
* 데이터 처리 연산을 지원하도록 소스에서 추출된 연속된 요소
* 스트림은 특정 요소 형식으로 이루어진 연속된 값 집합 인터페이스를 제공한다. Collection은 시간, 공간 복잡성과 관련된 요소의 저장 및 접근 연산이 주 이지만 Stream은 filter, sotred, map 과 같은 데이터를 처리하기 위한 계산식이 주 이다.

* Stream은 Collection, 배열 I/O 자원 등의 데이터 제공 소스로부터 데이터를 소비한다.

* Stream은 filter, map reduce, find, match, sort 등 함수형 프로그래밍 언어에서 일반적으로 지원하는 연산과 데이터베이스와 비슷한 연산을 지원한다.


## Streamr과 Collection의 차이
1. 계산 시점에서 차이가 있다.  
	* Collection은 자료구조가 포함하는 모든 데이터를 메모리에 저장하는 자료구조 이며 요소들은 포함이 되기 전에 꼭 계산이 완료되어야 한다.
	* * Stream의 경우는 요청할 때만 요소를 계산하는 고정된 자료구조(추가,삭제 불가)이다.
3.  반복의 차이
	* Colleccion은 사용자가 직접 for-each를 통해 반복문을 만들어 연산 처리를 작성해야 한다.
	* * Stream은 반복을 알아서 처리하고, 결과 Stream값을 어딘가에 저장해주는 내부반복을 사용한다. 
	1. 반복자를 사용할 필요가 없다는 장점이 있다.
	2. 병렬성 처리의 이점 - 외부반복을 사용할 경우 병렬처리를 위해 스레드간의 공유자원에 대해 동기화를 처리해 주어야 하지만 내부 반복은 관리할 필요가 없다.
	
### 스트림 사용방법
```java
public class StereamEx {
	public void static main(String[] args) {
		List<Integer> list = new ArrayList<>();
		for(int i=0;i<10;i++) {
			list.add(i);
		}
			
		//filter 프리디케이트를 인수로 받아 true에 해당하는 요소 반환
		List<Integer> filterEx = list.stream().filter(i -> i > 3).collect(Collectos.toList());

		// 중복을 제거해줌
		List<Integer> distinctEx = 	list.stream().distinct().collect(Collectors.toList());
		for (Integer ex : distinctEx) {
    		System.out.println("ex = " + ex);
		}
		
		// takeWhile(jdk1.9 이상) 스트림 요소가 filter 비교 대상을 기준으로 순서대로 정렬되어 있는 경우에 인수로 전달받은 프리디케이트가 처음으로 false를 반환하기 전까지 포함하는 스트림을 반환

		// dropWhile 인수로 전달받은 프리디케이트가 true를 버리고 나머지 요소들을 포함하는 스트림을 반환

		// map 스트림을 새로운 스트림으로 변환하는 연산을 해준다.
		List<String> mappingEx = list.stream().map(i -> 				String.valueOf(i)).collect(Collectors.toList());
		for (String ex : mappingEx) {
  		  System.out.println("ex = " + ex);
		}

		// anyMatch 프리디케이트 값이 하나라도 존재하면 true
		boolean b = list.stream().anyMatch(i -> i > 4) // true
		boolean f = list.stream().anyMatch(i -> i > 12) // false

		// noneMatch anyMatch와 반대다.	
		boolean b = list.stream().anyMatch(i -> i > 4) // false
		boolean f = list.stream().anyMatch(i -> i > 12) // true

		// findFirst 첫번째 요소를 반환해준다.
		int n = list.stream().findFirst().get(); // 0 

		// 리듀싱 모든 스트림의 요소를 처리하여 하나의 값으로 도출한다. 스트림의 요소가 하나의 값으로 줄어들 때 까지 람다는 각 요소를 반복하여 연산 및 조합을 한다.
		int sum = list.stream().reduce(0, (a,b) -> { sout(a+" "+b); return a+b; });

	}
}
```
 







