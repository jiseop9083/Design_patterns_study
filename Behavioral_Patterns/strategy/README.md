 # Stragegy Pattern 

 - **객체가 할 수 있는 행위를 인터페이스로 구현하고 행위에 대한 전략을 수정하는 방법**


  ![strategy_pattern](./strategy_pattern.png)
 
 ## 예시
 
 - ```Duck``` 이라는 추삳클래스를 상속받는 ```MallardDuck```과 ```DecoyDuck``` 이 있다.
 - ---

 - 이때, 행위를 객체와 분리시켜 행위(openTruck)만 변경하면 쉽게 수정할 수 있을 것이다.


 1. Duck 클래스(abstract context)
 ```
 public abstract class Duck{
	FlyBehavior flyBehavior;
	public Duck() {}
	
	public void swim() {
		System.out.println("duck is swimming");
	}
	public abstract void display();
	
	public void performFly() {
		flyBehavior.fly();
	}
	
	public void setFly(FlyBehavior flyBehavior) {
		this.flyBehavior = flyBehavior;
	}
}
 
 ```
 

2. MallardDuck 클래스와 DecoyDuck클래스 (concrete context)
```
public class MallardDuck extends Duck{
	public MallardDuck() {
		flyBehavior = new FlyWithWings();
	}
	
	public void display() {
		System.out.println("I'm mallard.");
	}
}

public class DecoyDuck extends Duck{	
	public DecoyDuck() {
		flyBehavior = new FlyNoWay();
	}
	
	public void display() {
		System.out.println("I'm Decoy duck.");
	}
}
```

3. FlyBehavior interface(strategy)
 ```
public interface FlyBehavior{
	public void fly();
}
	
```

4. FlyNoWay와 FlyWithWings 클래스(concrete strategy)
```
public class FlyNoWay implements FlyBehavior{
	public void fly() {
		System.out.println("I can't fly!");
	}
}

public class FlyWithWings implements FlyBehavior{
	public void fly() {
		System.out.println("I'm flying!");
	}
}
```




