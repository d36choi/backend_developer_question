자바에서 모든 클래스는 사실 Object를 암시적으로 상속받고 있는 것이다.  
그런 점에서 Object는 모든 클래스의 조상이라고 할 수 있다. 그 이유는 모든 클래스가 공통으로 포함하고 있어야 하는 기능을 제공하기 위해서다.  

# java.lang.Object에 정의되어있는 (public) method를 아는대로 나열해 보시오
 
 - toString
 - equals & hashcode
     - 객체의 논리적인 일치 여부를 확인. equals의 오버라이딩엔 hashcode 구현도 필수다.
 
 - finalize
    - 호출 안하는 걸 권장. 가비지 컬렉션에게 객체 해제는 일임 하니까 굳이 개발자가 제어하지 않아도 된다.
 - clone
    - 객체의 복사. 오버라이딩 해 구체적으로 복사 가능
## java.lang.Object의 equals와 hashCode의 관계에 대해서 설명하시오
- 두 개의 객체가 equals()가 true라면 hashCode()의 리턴값은 같아야 하는가 ?
- 두 개의 객체가 equals()가 false라면 hashCode()의 리턴값은 달라야 하는가 ?

[Object class](https://opentutorials.org/module/516/6241)
