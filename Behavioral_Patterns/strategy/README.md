 # Stragegy Pattern 

 - **객체가 할 수 있는 행위를 인터페이스로 구현하고 행위에 대한 전략을 수정하는 방법**
 
 ## 예시
 
 - ```Duck``` 이라는 추삳클래스를 상속받는 ```MallardDuck```과 ```DecoyDuck``` 이 있다.
 - ---

 - 이때, 행위를 객체와 분리시켜 행위(openTruck)만 변경하면 쉽게 수정할 수 있을 것이다.

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
