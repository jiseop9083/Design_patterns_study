 # Factory Method Pattern
 
 - 객체를 만들기 위해 factory라는 method를 이용한다
 - factory methed 내에서 객체를 생성하여 생성을 자식 클래스에 미룰수 있게 한다.

  ![factory method](./factory_method_pattern.png)
  
  ---


 ## example
 
 - pizza가게에 CheezePizza와 PepperoniPizza가 있다고 하자.
 - pizza가게는 체인점이어서 NewYork에도 있고 Chicago에도 있다고 하자(두 지역의 피자 스타일이 다르다)
 - pizza를 **생성**하는 프로그램을 설계해보자

--- 
 1. Creator(PizzaStore): 실제 factory method가 존재하는 클래스
 2. ConcreteCreator(ChicagoStylePizzaStore, NYStylePizzaStore): factory method가 정의되는 곳
 4. Product(Pizza): 제품의 추상 클래스
 5. ConcreteProduct(ChicagoStyleCheesePizza, ChicagoStylePepperoniPizza, NYStylePepperoniPizza, NYStylePizzaStore): 제품

---

 ### code 
1. PizzaStore
```
public abstract class PizzaStore {
	// factory method
	public abstract Pizza createPizza(String item);
	public Pizza orderPizza(String type) {
		Pizza pizza = createPizza(type);
		
		pizza.prepare();
		pizza.bake();
		pizza.cut();
		pizza.box();
		
		return pizza;
	}
}

```

2. ChicagoStylePizzaStore(NYStylePizzaStore은 생략, 형식은 같다)
```
public class ChicagoStylePizzaStore extends PizzaStore {
	public Pizza createPizza(String item) {
		if( item.equals("cheese"))
			return new ChicagoStyleCheesePizza();
		else if(item.equals("pepperoni"))
			return new ChicagoStylePepperoniPizza();
		else return null;
	}
}

```

3. Pizza
```
public abstract class Pizza {
	protected String name = "None";
	
	public Pizza() {}
	
	public String getName() {
		return name;
	}
	public void cut() {
		System.out.println("Cutting: " + name);
	}
	public void prepare() {
		System.out.println("Preparing: " + name);
	}
	public void bake() {
		System.out.println("Baking :" + name);
	}
	public void box() {
		System.out.println("Boxing :" + name);
	}
}
```

4. ChicagoStyleCheesePizza(ChicagoStylePepperoniPizza, NYStylePepperoniPizza, NYStylePizzaStore은 생략, 형식은 같다)
```
public class ChicagoStyleCheesePizza extends Pizza {
	
	public ChicagoStyleCheesePizza() {
		this.name = "Chicago cheese pizza";
	}
}

```

5. main
```
public static void main(String[] args) {
		
		PizzaStore nyStore=  new NYStylePizzaStore();
		
		PizzaStore chicagoStore = new ChicagoStylePizzaStore();
		Pizza pizza = nyStore.orderPizza("cheese");
		System.out.println("Ethan ordered a " + pizza.getName());
		pizza = chicagoStore.orderPizza("cheese");
		System.out.println("Joel ordered a " + pizza.getName());
		
		
	}
 ```

 
