## <전략패턴>

### [@Ho-Tea](https://github.com/Ho-Tea)

- Review
  - 


- SourceCode
  ``` java
  
  ```


### [@hwanvely](https://github.com/Hwanvely)

- Review
  * 전략패턴은 알고리즘중에서 달라지는 부분을 찾아내고 이 부분을 캡슐화하여 각각의 알고리즘을 수정을 용이하게 해준다.
  * 이때 상속보다는 구성(a에는 b가 있다)을 사용하기 위하여 인터페이스를 이용하여 레퍼런스를 통해 구현된 알고리즘을 서브클래스에서 사용할 수 있도록한다.
  * 또한 구현보다는 상위형식에 맞춰서 프로그래밍 하기 위하여 다형성을 활용하여 supertype을 사용하고 supertype의 레퍼런스를 사용한다


- SourceCode
  ``` java
  public abstract class Character {
    WeaponBehavior weapon;

    public Character() { }

    public void setWeapon(WeaponBehavior w) {
        this.weapon = w;
    }
    public void fightType(){
        weapon.useWeapon();
    }
  }
  public interface WeaponBehavior {
    public void useWeapon();
  }
  public class SwordBehavior implements WeaponBehavior{

    @Override
    public void useWeapon() {
        System.out.println("검을 휘두릅니다");
    }
  }
  public class King extends Character{

    public King(){
        weapon = new SwordBehavior();
    }

  } ```


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
