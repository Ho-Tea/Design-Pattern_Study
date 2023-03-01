## <전략패턴>

### [@Ho-Tea](https://github.com/Ho-Tea)

- Review
  - 달라지는 부분과 달라지지 않는 부분을 구별해 **캡슐화**(객체지향의 원칙을 준수)
  - 구현보다는 인터페이스에 맞춘 설계를 하자(**다형성**을 활용하자)
  - 상속보다는 구성을 활용하자(두 클래스를 합치는 것을 의미 `FlyBehavior` , `QuackBehavior`)
  - 객체지향의 기초(추상화, 캡슐화, 다형성, 상속)
  - 전략패턴은 객체지향의 원칙을 준수한다


- SourceCode
  ``` java
  public abstract class Duck(){
    FlyBehavior flyBehavior; // 상속보다는 구성을 활용하자
    QuackBehavior quackBehavior;

    // Duck클래스로부터 자주 변하는 fly()와 같은 메서드를
    // 캡슐화 하여 새로운 클래스 집합으로 분리하였다
    void display();
    ...
  }

  public class RubberDuck extends Duck(){ //Duck 클래스에서 quackBehavoir 인스턴스 변수를 상속받는다
    public RubberDuck(){
      quackBehavior = new Quack();  // 다형성을 활용한 사례
    }
    @Override
    void display();
  }

  public interface FlyBehavior{
    public void fly();
  } 
  public interface QuackBehavior{}

  public class FlyWithWings implements FlyBehavior{
    @Override
    void fly(){
      ...
    }
  }
  public class Quack implements QuackBehavior{}
  ```


### [@hwanvely](https://github.com/Hwanvely)

- Review
  


- SourceCode
  ``` java
  
  ```


### [@jihwan2da](https://github.com/jihwan2da)

- Review
  


- SourceCode
  ``` java
  
  ```



### [@PARK9898](https://github.com/PARK9898)

- Review
  


- SourceCode
  ``` java
  
  ```




## 최종 요약