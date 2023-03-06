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
  


- SourceCode
  ``` java
  
  ```



### [@PARK9898](https://github.com/PARK9898)

- Review
  - 전략 패턴을 활용하면 기존 코드 변경을 최소화 한다 (ocp 패쇄 원칙)
  - 사용자의 요구에 따라 유연하게 하위 인터페이스 알고리즘의 변경이 용이함.
  - 템플릿 메소드 패턴과의 차이점을 공부해보는것도 좋다고 생각함 -> 템플릿 메소트 패턴은 추상 클래스를 사용하여 원하는 메서드마 뽑아서 클래스로 사용가능 (전략패턴과의 차이점 확인해보기)
  - 오브젝트 자체를 둘로 분리한다고 생각한다
  - 전략 패턴을 말 그대로 받아드려도 된다 생각함 자신이 원하는 것에 따라 전략(설계되어 있는 인터페이스로 받아드려도 될 것 같음)을 선택하여 클래스르 생성할 수 있다는 점에서 장점을 가진다


- SourceCode
  ``` java
  public abstract class Robot {

    private String name;
    private MovingStrategy movingStrategy; // 인터페이스임
    private AttackStrategy attackStrategy;

    public Robot(String name) {
        this.name = name;
    }

    public void move() {
        movingStrategy.move();
    }

    public void attack() {
        attackStrategy.attack();
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public MovingStrategy getMovingStrategy() {
        return movingStrategy;
    } // 전략을 설정 

    public void setMovingStrategy(MovingStrategy movingStrategy) {
        this.movingStrategy = movingStrategy;
    }
      public AttackStrategy getAttackStrategy() {
        return attackStrategy;
    }

    public void setAttackStrategy(AttackStrategy attackStrategy) {
        this.attackStrategy = attackStrategy;
    }
  }

  public class Atom extends Robot{

    public Atom(String name) {
        super(name);
    }

  }

  public class WalkingStrategy implements MovingStrategy {
    @Override
    public void move() {
        System.out.println("I can only walk.");
    }
  } // 인터페이스를 구현

  public class Client {
     public static void main(String[] args) {
       
        Robot atom = new Atom("Atom");              // 아톰 객체 생성

        atom.setMovingStrategy(new FlyingStrategy());       // 이동 전략 설정 : 날기
        atom.setAttackStrategy(new PunchStrategy());        // 공격 전략 설정 : 펀치

        System.out.println("My name is " + atom.getName());
        atom.move();
        atom.attack();
    }
  }
  ```




## 최종 요약
