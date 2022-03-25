자바에서 모든 클래스는 사실 Object를 암시적으로 상속받고 있는 것이다.  
그런 점에서 Object는 모든 클래스의 조상이라고 할 수 있다. 그 이유는 모든 클래스가 공통으로 포함하고 있어야 하는 기능을 제공하기 위해서다.  

# java.lang.Object에 정의되어있는 (public) method를 아는대로 나열해 보시오
 
 - **getClass**
     - class 이름
 - **clone**
     - 인스턴스의 내용을 복사한 새 객체 생성
 - **toString**
 - **equals & hashcode**
     - 객체의 논리적인 일치 여부를 확인. equals의 오버라이딩엔 hashcode 구현도 필수다.
 - **finalize**
    - 호출 안하는 걸 권장. 가비지 컬렉션에게 객체 해제는 일임 하니까 굳이 개발자가 제어하지 않아도 된다.
 - **clone**
    - 객체의 복사. 오버라이딩 해 구체적으로 복사 가능

## java.lang.Object의 equals와 hashCode의 관계에 대해서 설명하시오

equals 는 객체의 **값이 동일한지** 판별한다. (논리적 동치)
hashcode 는 **같은 객체**인지 판별한다.

둘다 기본적으로는 객체의 메모리주소를 기반으로 한다. `equals` 는 객체 주소가 동일한지를 보고, `hashcode`는 객체 메모리 주소의 해시 값을 본다.

만약 equals를 값비교로 재정의하는 경우 hashcode도 재정의 해야만 한다.

그 이유는 재정의하지않으면 해시 자료구조를 쓸 때, 한 객체를 생성해 집어넣고 값이 같은 다른 객체를 통해 해시테이블을 조회하면 우리는 개념적으로
이미 집어넣은 객체를 조회할거라 생각하지만 hashcode는 재정의되지않아 객체 메모리 주소를 통해 찾기 때문이다.

```java
Food food = new Food("burger");
menu.put(menu, "5000");
menu.get (new Food("burger")) 
// --> ERROR
```
그래서 우린 Value Object를 정의할 땐, equals and hashcode를 **항상 같이** 재정의 해줘야 하는 것이 좋다.

* 참고로 이와 hashcode()가 재정의되고 equals()가 재정의되지 않으면 해시 버킷은 찾지만 찾은 데이터가 해당 객체인지를 판별할 수 없어서 결국엔 못찾는다.

## hashCode() 값이 모두 같다면 어떤 일이 벌어지나요?

해시 테이블에 넣은 모든 데이터가 같은 해시 버킷에 들어가기때문에 결국 리스트와 같이 필요 데이터를 찾으려면 전체 조회하게 될 것이다.


## 원시타입 변수는 == 로 값의 비교가 가능한 이유는?

원시타입 변수는 스택에 생성되지만 그 값은 상수 풀에 저장되어있다.
스택에 메모리할당되는 원시타입 변수는 상수 풀에 있는 실제 값의 주소값을 참조하는 것이다.
결국 == 는 값을 비교해 true or false가 나오지만 **내부에서 실제로는 주소비교인 것이다.**




[Object class](https://opentutorials.org/module/516/6241)
[hashcode, equals](https://jisooo.tistory.com/entry/java-hashcode%EC%99%80-equals-%EB%A9%94%EC%84%9C%EB%93%9C%EB%8A%94-%EC%96%B8%EC%A0%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B3%A0-%EC%99%9C-%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C)
