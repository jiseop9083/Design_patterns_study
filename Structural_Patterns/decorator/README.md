 # Decorator Pattern

 - 객체가 가지고 있는 기능을 확장하기 위하여 추가적인 기능을 가진 객체로 덧씌우는 방법
 - => 추가적인 기능을 동적으로 넣었다가 뺄 수 있게 한다!

 ![decorator pattern](./decorator_pattern.png)
 
 ----
 
 ### example
  - 버거집에서 와퍼(Whopper), 치즈버거(CheeseBurger) 치킨버거(ChickenBurger) 세종류의 버거를 판다고 한다.
  - 또한, 추가적으로 콜라(Cola), 감자튀김(FrenchFries), 아이스크림(Icecream), 치킨너켓(ChickenNugget) 등 사이드 메뉴를 판다.
  - 버거는 하나만 주문해야하고 사이드메뉴는 원하는 것을 여러번 추가할 수 있다.
  - 주문을 받는 프로그램을 decorator pattern을 이용해 만들어보자

 1. **Component**(Burger): 각 버거와 데코레이터의 부모 클래스
 2. **Concrete Component**(Whopper, CheeseBurger, ChickenBurger): 버거의 종류
 3. **Decorator**(CondimentDecorator): 사이드의 부모 클래스
 4. **Conrete Decorator**(Cola, FrenchFries, Icecream, ChickenNugger): 각 사이드 메뉴 클래스


### code
 ---- 
 1. Burger
```
public abstract class Burger {
	String description = "untitled";
	
	public String getDescription() {
		return description;
	}
	
	public abstract double cost();
}
```

2. CondimentDecorator
```
public abstract class CondimentDecorator extends Burger {
	public abstract String getDescription();
}
```

3. Whopper(CheeseBurger와 ChickenBurger는 생략, 구조는 똑같음)
```
public class Whopper extends Burger {
	public Whopper() {
		description = "Whopper";
	}
	
	public double cost() {
		return 7.3;
	}
}
```

4. Cola(FrenchFries, Icecream, ChickenNugger는 생략, 구조는 같음)
```
public class Cola extends CondimentDecorator {
	Burger burger;
	
	public Cola(Burger burger) {
		this.burger = burger;
	}
	
	public String getDescription() {
		return burger.getDescription() + " + Cola";
	}
	
	public double cost() {
		return burger.cost() + 0.8;
	}
}
```

5. main
```
public static void main(String[] args) {
		Burger burger1 = new Whopper();
		System.out.println(burger1.cost() + "$ "  + burger1.getDescription()); // Whopper
		
		Burger burger2 = new CheeseBurger();
		burger2 = new Cola(burger2);
		burger2 = new FrenchFries(burger2);
		burger2 = new ChickenNugget(burger2);
		System.out.println(burger2.cost() + "$ "  + burger2.getDescription()); // Cheese burger with cola, French fries and chicken nugget
		
		Burger burger3 = new ChickenBurger();
		burger3 = new Icecream(burger3);
		System.out.println(burger3.cost() + "$ "  + burger3.getDescription()); // chicken burger with icecream
		
	}
 ```
