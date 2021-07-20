# Abstract factory

## abstract factory
상세화된 자식클래스를 정의하지 않고도 서로 관련성이 있거나 독립적인 여러 객체의 군을 생성하기 위한 인터페이스를 제공한다
concrete factory에서 여러 product를 선택해 생성한다. -> 이를 선택할 수 있다

### 1. 사용처
 - 관련성이 있는 객체를 묶어서 함께 사용되어야할 때
 - product 클래스에 대한 인터페이스만 제공하고 싶을때

### 2. 구조
 - client: abstractFactory, abstractProduct를 interface함
 - concreteProduct: 구체적인 객체
 - abstractProduct: concreteProduct의 일반적인 형태
 - concreteFactory: concreteProduct를 생성하는 곳
 - abstractFactory: concreteFactory의 일반적인 형태

 ![이미지](./abstract_factory_pattern.png)

### 3. 특징
 - concrete class의 고립, client는 인터페이스를 통해 concrete class에 접근한다.
 - product를 바꾸기 쉽다. 그냥 바꾸면 더 수정할 필요가 없다.
 - pruduct간 일관성이 있도록 한다
 - 새로운 product를 만드는 것이 어렵다

### 4. 예시
  **factory method에서 나온 예시를 응용하겠다.**
 
  [factoy method pattern](https://github.com/jiseop9083/Design_patterns_study/edit/main/Creational_Patterns/factory_method/)
 
  **이 때 필기구는 각 세트별로 판매해야한다. stationaryA의 연필, 볼펜과 stationaryB의 지우개 수정테이프를 판매하는 식의 섞어팔기는 허용되지 않는다**
 
 </p>
 
 - abstractFactory: stationary의 인터페이스
 - concreteFactory: stationaryA, stationaryB
 - abstractProduct: pencil, ballPoint, eraser, correctionTape
 - concreteProduct: stationaryA의 pencil, stationaryB의 eraser 등등
