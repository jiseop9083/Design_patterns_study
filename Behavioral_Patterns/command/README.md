 # Command pattern
 
  - 일련의 기능을 하나의 객체를 캡슐화한다.
  - execute메소드를 통해 기능을 수행시킨다.
  - 매개변수를 통해 여러 요구사항을 추가할 수도 있고 로그나 작업취소기능도 지원한다.

 ![command pattern](./command_pattern.png)


 --- 
  1. Command: 객체의 인터페이스, execute메소드를 가짐
  2. ConcreteCommand: command 구현하는 부분
  3. receiver: command에 의해서 변화하는 부분, 기능을 수행하면서 변화하는 부분
  4. invoker: 커멘드를 저장하는 부분

---
 ## example
  - 불을 켜고 끄려고한다.
  - 이를 command pattern으로 구현해보자

  1. Command(Command): 커멘드 객체의 인터페이스
  2. ConcreteCommand(LightOffCommand, LightOnCommand): 기능을 구현하는 부분
  3. receiver(Light): command에 의해 불이 실제로 꺼지고 켜지는 부분
  4. invoker(RemoteControl): 커멘드를 저장하고 관리하는 부분
