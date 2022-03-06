
# interface 와 abstract가 어떻게 다른지 설명해주세요

메서드의 구현여부다. 메서드나 하나라도 구현되어있다면 (내용이 정의된 케이스가 있다면)

abstract 여야 한다.

## abstract class 는 왜쓸까요?

확장되는 클래스들이 많은데, 특정 메서드는 무조건 구현되어야하면서

메서드들이 각자 별도의 내용으로 구현되어야한다면 추상클래스로 만들어놓으면 좋다.

## interface는 왜 쓸까요?

클래스 추상화 과정에서 공통된 행위를 갖는 표준을 선언한다.

## final class는 언제쓸까요?

더이상 확장 불가, 자식을 가질 수 없는 클래스다. String이 그러하다.

## default method는?

java 8 도입. 하위 호환성을 위해 도입되었고 interface에 내용을 포함한다.

## abstract class 와 일반 class의 다른점은?


