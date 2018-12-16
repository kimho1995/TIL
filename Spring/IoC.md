# IoC

IoC는 제어의 역전 이라고 부른다. 다른 많은 프로그램들과는 다르게 제어의 역전 패턴이 자바 웹 개발에서 특히 인기를 끄는 이유는 **프로그램의 생명주기에 대한 주도권이 웹 애플리케이션 컨테이너에 있기 때문이다.** 게임 엔진의 경우에는 초기화,  실행, 종료 같이 애플리케이션의 흐름 제어에 관한 부분을 직접 만든다. 그리고 실행 중인 메인 루프가 포함되어 프로그램이 종료되기 전까지 계속 실행 안에서 동작한다.

그러나 자바 기반의 웹 프로그램 기반 시에는 doGet, doPost 같은 메서드들의 파라미터와 함꼐 호출돤다. 이런 상황에서 파일 처리이나 데이터베이스 처리를 하는 클래스들의 인스턴스를 관리를 해야하고, 일괄적으로 인스턴스 관리를 하기 위해서 객체의 생성을 관리할 수 있는 도구의 필요성이 대두 되었다

**이 와 같은 의미로 디자인 패턴의 원칙 중 하나로 의존성 관계역전 DIP가 있다.**

의존관계 역전 원칙은 두 가지 내용을 담고 있습니다. **첫 번째로 상위 모듈은 하위 모듈에 의존해서는 안되고, 인터페이스에 의존해야한다. 두 번쨰로 추상화는 세부 상황에 의존해서는 안된다. 세부 사항이 추상화에 의존해야한다는 내용입니다.**

단순하게 생각해서 인터페이스를 활용함으로써 결합도를 낮추자는 뜻입니다. **하지만 자바에서는 인터페이스를 사용하더라도 결국 인스턴스화하기 위해서는 반드시 객체 생성에 필요한 코드가 수반되므로 결합도를 완전히 분리해 낼 수 없습니다. 결국 프로그램이 온전히 동작하기 위해서는 인스턴스화할 수 있는 코드에 대한 의존성을 잦게됩니다. 이것을 대신 해결 해주는 것이 바로 의존숭 주입(DI) 입니다.**

최근에는 제어의 역전 이라는 말 뜻이 너무 광범위하고 일반적이어서 제어의 역전보다는 의존성 주입을 많이 사용합니다.

## IoC 구현 방법

### DL
* 저장소에 저장되어 있는 빈(Bean)에 접근하기 위하여 개발자들이 컨테이너에서 제공하는 API 를 이용하여 사용하고자 하는 빈(Bean) 을 Lookup 하는 것


### DI
* 각 계층 사이, 각 클래스 사이에 필요로하는 의존 관계를 컨테이너가 자동으로 연결해주는것
* 각 클래스의 사이의 의존 관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것

* Setter Injection 
    * 인자가 없는 생성자나 인자가 없는 static factory 메서드가 bean을 인스턴스화 하기 위하여 호출된 bean 의 setter 메서드를 호출하여 실체화하는 방법
    * 세터를 생성 후 의존성 산입 방식이기에 구현시에 조금더 유연할 수 있다.
* Constructor Injection
    * 생성자를 이용하여 클래스 사이의 의존 관계를 연결
    * 생성자 파라미터를 지정함으로써 생성하고자하는 객체가 불필요 하는 것을 명확하게 알 수 있다.
    * Setter 메서드를 제공하지 않음으로 간단하게 필드를 불변 값으로 지정할 수 있다.
* @Autowired
    * 어노테이션으로 의존성 주입
    * **순환 참조 의존성을 방지 할 수 있다.**

## 용어 정리

* bean - 스프링에서 제어권을 가지고 직접 만들고 객체를 붕여 하는 오브젝트
* bean factory -  스프링 IoC를 당담하는 핵심 컨테이너
* application context - bean factory를 확장한 IoC 컨테이너
    * 빈의 등록/생성/조회/반환/관리의 기능은 bean factory 와 같지만, 여기에 spring의 각종 부가 서비스를 추가로 제공한다. ApplicationContext는 application context가 구현해야 하는 interface이여, BeanFactory 를 상속한다.



## 출처: 
* [I's Story](http://isstory83.tistory.com/91)

