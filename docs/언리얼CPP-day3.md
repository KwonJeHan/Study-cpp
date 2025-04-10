# 언리얼 C++ 학습 정리

**2025/04/03 [포텐업] 게임 개발자 양성 과정**

---

## 언리얼 C++ 델리게이트

C++ 오브젝트 상의 멤버 함수 호출을 일반적이고 유형적으로 안전한 방식으로 할 수 있다.

델리게이트를 사용하여 임의 오브젝트의 멤버 함수에 동적으로 바인딩 시킬 수 있으며, 그런 다음 그 오브젝트에서 함수를 호출할 수 있다.



### 강한 결합과 느슨한 결합

**강한 결합**

* 클래스들이 서로 의존성을 가지는 경우를 의미
  * 예를 들어 Person 클래스가 Card 클래스를 가졌다. 이를 Person 클래스가 Card 클래스에 대한 의존성을 가진다고 한다. 이때 다른 곳에서 인증할 수 있는 새로운 카드가 도입된다고 했을 때 Person 클래스뿐만 아니라 이를 상속받는 자식 클래스들도 수정해야 한다.


**느슨한 결합**

* 실물에 의존하지 말고 추상적 설계에 의존하라 (DIP원칙)
  * 왜 Person은 Card가 필요한가? -> 출입을 확인해야 하기 때문이다. 이때 출입에 관련된 추상적인 설계를 의존(행동에 중심을 둔 추상화 작업)하도록 하자.
  * ICheck를 상속받은 새로운 카드 인터페이스를 선언해 해결하면 Person은 Card에 의존하지 않고, ICheck 인터페이스에 의존하게 되고, ICheck 인터페이스를 상속받는 클래스 들은 가상함수 Check()를 재정의하면 된다.

* 이런 느슨한 결합 구조는 유지 보수를 손쉽게 만들어준다.



**C++에서 함수 포인터를 이용했던 것 대신, 언리얼 C++에서는 델리게이트(Delegate)를 제공해준다.**



#### 발행 구독 디자인 패턴

* 푸시 형태의 알림을 구현하는데 적합한 디자인 패턴
* 발행자와 구독자로 구분된다.
  * 콘텐츠 제작자는 콘텐츠를 생산
  * 발행자는 콘텐츠를 배포
  * 구독자는 배포된 콘텐츠를 받아 소비
  * 제작자와 구독자가 서로를 몰라도, 발행자를 통해 콘텐츠를 생산하고 전달할 수 있다. (느슨한 결합)



**발행 구독 디자인 패턴의 장점**

1. 제작자와 구독자는 서로를 모르기 때문에 느슨한 결합으로 구성된다.
2. 유지 보수가 쉽고, 유연하게 활용될 수 있으며, 테스트가 쉬워진다.
3. 시스템 스케일을 유연하게 조절할 수 있으며, 기능 확장이 용이하다.



**언리얼 엔진은 발행 구독 패턴 구현을 위해 델리케이트 기능을 제공한다.**

**느슨한 결합으로 구현된 발행 구독 모델의 장점**

* 클래스는 자신이 해야 할 작업에만 집중할 수 있다.
* 외부에서 발생한 변경 사항에 대해 영향을 받지 않는다.
* 자신의 기능을 확장하더라도 다른 모듈에 영향을 주지 않는다.



#### 언리얼 델리게이트 선언

**고려 사항**

* 어떤 데이터를 전달하고 받을 것인가? 인자의 수와 각각의 타입을 설계

  * 몇 개의 인자를 전달할 것인가?

  * 어떤 방식으로 전달할 것인가?

  * 일대일로 전달

  * 일대다로 전달

* 프로그래밍 환경 설정
  * C++ 프로그래밍에서만 사용할 것인가?
  * UFUNCTION으로 지정된 블루프린트 함수와 사용할 것인가?
* 어떤 함수와 연결할 것인가?
  * 클래스 외부에 설계된 C++ 함수와 연결
  * 전역에 설계된 정적 함수와 연결
  * 언리얼 오브젝트의 멤버 함수와 연결(대부분의 경우 이 방식을 사용)



#### 언리얼 델리게이트의 설계

**클래스 간의 상호 의존성을 최대한 없앤다.**

하나의 클래스는 하나의 작업에만 집중하도록 설계한다.
