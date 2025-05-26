# 언리얼 멀티 C++ 학습 정리

**2025/05/15 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 공격 구현

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/80.ModifyABCharacterPlayer.h(Single).png">

멀티플레이 환경으로 캐릭터 공격 기능을 구현하기 전에 먼저 캐릭터 공격을 싱글로 변경 구현한다. 이를 위해 ABCharacterPlayer 클래스의 헤더 파일에 필요한 함수와 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/81.ModifyABCharacterPlayer.cpp1(Single).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/82.ModifyABCharacterPlayer.cpp2(Single).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/83.ModifyABCharacterPlayer.cpp3(Single).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/84.ModifyABCharacterPlayer.cpp4(Single).png">

ABCharacterPlayer 클래스의 cpp 파일에 공격 로직 구현을 위해 필요한 헤더 파일을 추가하고 헤더 파일에서 선언한 함수 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/85.ModifyABCharacterPlayer.h(Multi).png">

앞서 만들어놓은 싱글 버전으로 구현한 공격 기능을 토대로 멀티플레이 환경으로 변경한다. 이를 위해 필요한 리플리케이션 및 RPC 함수들을 ABCharacterPlayer 클래스 헤더 파일에 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/86.ModifyABCharacterPlayer.cpp1(Multi).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/87.ModifyABCharacterPlayer.cpp2(Multi).png">

ABCharacterPlayer 클래스 cpp 파일에 멀티플레이 환경으로 변경하기 위해 필요한 헤더 파일을 추가하고 생성자에서 bReplicates를 true로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/88.ModifyABCharacterPlayer.cpp3(Multi).png">

헤더 파일에서 리플리케이션 프로퍼티로 선언한 변수를 GetLifetimeReplicatedProps 함수의 DOREPLIFETIME 매크로로 리플리케이션에 등록하고 기존 Attack 함수 로직을 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/89.ModifyABCharacterPlayer.cpp4(Multi).png">

AttackHitCheck 함수는 공격 판정을 서버에서만 진행하도록 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/90.ModifyABCharacterPlayer.cpp5(Multi).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/91.ModifyABCharacterPlayer.cpp6(Multi).png">

서버와 클라이언트 간 네트워크를 위한 RPC 함수들의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/92.ModifyABCharacterPlayer.cpp7(Multi).png">

리플리케이션 프로퍼티로 등록한 변수가 변경될 시 작동하도록 선언한 OnRep_CanAttack 함수도 내용을 구현한다.

위 과정들을 통해 기존 싱글로 구현되었던 공격 판정 로직을 서버와 클라이언트 간 동기화 로직으로 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/93.ModifyArenaBattle.h1(LogMacro).png">

공격 판정은 네트워크 멀티플레이로 구현했지만 액터 컴포넌트가 아직 리플리케이션을 구현하지 않았기 때문에 클라이언트는 피격당해도 HUD의 HP 양이 감소하지 않는다. 이를 구현하기 전에 먼저 디버깅 용도로 기존에 매크로 정의를 해놓은 ArenaBattle 헤더 파일에 컴포넌트가 사용할 역할 정보 출력 매크로를 정의한다. (기존 매크로는 Actor 기준의 매크로여서 컴포넌트는 사용할 수 없다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/94.ModifyArenaBattle.h2(LogMacro).png">

기존에 생성한 로그 매크로를 복사해 위에서 컴포넌트를 위해 새로 생성한 매크로로 변경해 새로운 로그 매크로를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/95.ModifyABCharacterStatComponent.h.png">

HP와 관련된 기능이 있는 ABCharacterStatComponent 클래스의 헤더 파일에 리플리케이션 구현을 위해 필요한 함수들을 선언하고 CurrentHp 프로퍼티에 리플리케이션 옵션을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/96.ModifyABCharacterStatComponent.cpp1.png">

cpp 파일에서는 리플리케이션 및 로그 출력에 필요한 헤더 파일을 추가하고 생성자에서 컴포넌트의 리플리케이션을 활성화한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/97.ModifyABCharacterStatComponent.cpp2.png">

이후 리플리케이션 구현을 위해 헤더 파일에서 선언한 함수들을 구현한다.
