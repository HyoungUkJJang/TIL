Stream

- sequence of elements supporting sequential and parallel aggregate operator
- 데이터를 담고 있는 저장소(컬렉션)이 아님
- 스트림이 처리하는 데이터 소스를 변경하지 않음
- 무제한일 수도 있음
- 중개 오퍼레이션은 근본적으로 lazy함
- 손쉽게 병렬처리가 가능하다.

스트림 파이프라인
- 0 또는 다수의 중개 오퍼레이션과 한개의 종료 오퍼레이션으로 구성
- 스트림 데이터 소스는 오직 터미널 오퍼레이션을 실행할 때만 처리함

중개 오퍼레이션
- 스트림을 리턴함
- stateless / stateful 오퍼레이션으로 더 상세하게 구분가능

종료 오퍼레이션
- 스트림을 리턴하지 않는다.

