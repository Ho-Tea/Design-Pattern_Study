## <전략패턴>

### [@Ho-Tea](https://github.com/Ho-Tea)

- Review
  - 


- SourceCode
  ``` java
  
  ```


### [@hwanvely](https://github.com/Hwanvely)

- Review
  


- SourceCode
  ``` java
  
  ```


### [@jihwan2da](https://github.com/jihwan2da)

- Review  
  

- 객체의 행위 각각 대해서 그 객체와 코드적으로 엮이지 않는 전략을 클래스로 만드는 것이다.  
그래서 그 전략 행위에 대해서도 재사용을 할 수 있고, 개발 확장에도 용이하다.  
그 전략 클래스를 만드는 방법은 캡슐화와 다형성을 활용하는 인터페이스나, 추상클래스를 활용하여 만든다.  
즉 유사항 행위들을 캡슐화하는 것이다. 이렇게 행위 각각에 대해서 전략 클래스를 만들면 직접   
행위를 수정하지 않고 전략을 바꿔주기만 함으로써 행위를 유연하게 확장 가능하게 된다.


- SourceCode
  ``` java
  public interface Duck {
    void display();

    void quack();

    void fly();
  }
  
  public class MallardDuck implements Duck{

    @Override
    public void display() {
        quack();
        fly();
    }

    @Override
    public void quack() {
        System.out.println("끽끽");
    }

    @Override
    public void fly() {
        System.out.println("날지 않아요 저는~");
    }
  }
  
  public class RedheadDuck implements Duck{
    @Override
    public void display() {
        quack();
        fly();
    }

    @Override
    public void quack() {
        System.out.println("꼭꼭");
    }

    @Override
    public void fly() {
        System.out.println("저는 날개로 날아요~");
    }
  }
  ```
- 예를들어 MallardDuck과 RedheadDuck 클래스가 있고, 이 두 클래스는 Duck 인터페이스를  
구현했다고 가정해보자. MallarDuck은 끽끽울고 날지 않고, RedheadDuck은 꼭꼭울고 난다.  
그러다가 시간이 흘러 MallardDuck이 진화를 해서 날 수 있다고 가정을 해보자.  
그러면 MallardDuck의 fly 메서드를 수정하면 될 것이다. 하지만 이는 매우 번거로운 행위이고,  
OCP원칙에 어긋난다. 또한 지금 같은 방식은 시스템이 확장되었을 때 유지보수하기 힘들다.  
예를 들어, RedheadDuck과 같이 나는 오리가 여러개 추가될 때 마다 RedheadDuck과 같은  
메서드를 똑같이 생성해야 된다. 그러면 메서드가 중복이 발생되고, 수정 시 매우 힘들어 진다.  



- 이제 위 문제를 해결해 줄 전략 패턴을 적용해보자.  
위에서의 문제는 fly 메서드의 확장이 어렵다는 것이다. (메서드의 중복이 일어나고, 수정도 자주   
일어나는데 수정하는데 시간이 너무 많이 걸린다.) quack 메서드도 같은 의미로 확장이 어렵다고 하자.  
그래서 자주 바뀌는 행위에 대해서 따로 클래스를 만들어서 그 행위는 행위대로 관리하고, 오리는   
오리대로 관리하되, 오리는 동적으로 그 행위를 가질 수 있도록 코드를 짜보자.

  ``` java
  public interface FlyableStrategy {
    void fly();
  }
  
  public class WingFlyStrategy implements FlyableStrategy{
    @Override
    public void fly() {
        System.out.println("저는 날개로 날아요~");
    }
  }
  
  public class NoFlyStrategy implements FlyableStrategy{
    @Override
    public void fly() {
        System.out.println("날지 않아요 저는~");
    }
  }
  
  public interface QuackableStrategy {
    void quack();
  }
  
  public class KkikKkikQuackStrategy implements QuackableStrategy{
    @Override
    public void quack() {
        System.out.println("끽끽");
    }
  }
  
  public class KkokKkokQuackStrategy implements QuackableStrategy{
    @Override
    public void quack() {
        System.out.println("꼭꼭");
    }
  }
  ```
- 자주 바뀌는 행위(Fly, Quack)에 대해서 각각 행위에 대한 전략 인터페이스(FlyableStrategy, 
QuackableStrategy)를 만들고 그 행위의 구현체들을 만들어서 오리와 행위를 각각 관리 하도록 하였다.  
행위 자체를 오리와 상관없이 관리 하도록 하여 확장에 더욱 용이해졌다. 

  ``` java
  public class RedheadDuck implements Duck{

    private QuackableStrategy quackableStrategy;
    private FlyableStrategy flyableStrategy;

    @Override
    public void display() {
        quack();
        fly();
    }

    public void setQuackableStrategy(QuackableStrategy quackableStrategy) {
        this.quackableStrategy = quackableStrategy;
    }

    public void setFlyableStrategy(FlyableStrategy flyableStrategy) {
        this.flyableStrategy = flyableStrategy;
    }

    @Override
    public void quack() {
        this.quackableStrategy.quack();
    }

    @Override
    public void fly() {
        this.flyableStrategy.fly();
    }
  }
  
  public class MallardDuck implements Duck{

    private QuackableStrategy quackableStrategy;
    private FlyableStrategy flyableStrategy;

    @Override
    public void display() {
        quack();
        fly();
    }

    public void setQuackableStrategy(QuackableStrategy quackableStrategy) {
        this.quackableStrategy = quackableStrategy;
    }

    public void setFlyableStrategy(FlyableStrategy flyableStrategy) {
        this.flyableStrategy = flyableStrategy;
    }

    @Override
    public void quack() {
        this.quackableStrategy.quack();
    }

    @Override
    public void fly() {
        this.flyableStrategy.fly();
    }
  }
  ```
- 오리는 행위에 대한 전략 인터페이스(QuackableStrategy, FlyableStrategy)가지고 있고, setter
같은 방식으로 동적으로 자유롭게 변경이 가능하도록 해주었다.  
이렇게 되면 오리의 우는 행위나 나는 행위가 바뀌더라도 다른 행위 전략으로 동적으로 바꿔주기만 하면되고,
행위가 추가되더라도 오리와 상관없이 따로 관리되고 있기 때문에 행위 전략에 관련된 코드만 수정하면 되서 유지보수와 확장에 용이하다.  
  

- 전략패턴은 나중에 팩터리패턴과 같이 쓰면 효율적인 코드를 작성할 수 있을 거 같다.


### [@PARK9898](https://github.com/PARK9898)

- Review
  


- SourceCode
  ``` java
  
  ```




## 최종 요약
