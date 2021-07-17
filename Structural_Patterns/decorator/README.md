 # Decorator Pattern

 - 객체가 가지고 있는 기능을 확장하기 위하여 추가적인 기능을 가진 객체로 덧씌우는 방법
 - => 추가적인 기능을 동적으로 넣었다가 뺄 수 있게 한다!

 ![decorator pattern](./decorator_pattern)
 
 ----
 
 ### example
  - 버거집에서 와퍼(Whopper), 치즈버거(CheeseBurger) 치킨버거(ChickenBurger) 세종류의 버거를 판다고 한다.
  - 또한, 추가적으로 콜라(cola), 감자튀김(FrenchFries), 아이스크림(Icecream), 치킨너켓(ChickenNugget) 등 사이드 메뉴를 판다.
  - 버거는 하나만 주문해야하고 사이드메뉴는 원하는 것을 여러번 추가할 수 있다.
  - 주문을 받는 프로그램을 decorator pattern을 이용해 만들어보자

 1. 
