# 언리얼 멀티 C++ 학습 정리

**2025/05/21 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 무브먼트의 확장

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/134.CreateCharacterMovementComponentCPPClass(ABCharacterMovementComponent).png">

CharacterMovementComponent 클래스를 부모로 하는 C++ 클래스 ABCharacterMovementComponent를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/135.CreateIA_Teleport.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/136.SetIA_TeleportToIMC1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/137.SetIA_TeleportToIMC2.png">

텔레포트 기능 구현에 사용할 InputAction을 생성하고 생성해서 사용하고 있던 Input Mapping Context들에 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/138.ModifyArenaBattle.h(AddLogMacro).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/139.ModifyArenaBattle.cpp(AddLogMacro).png">

ArenaBattle 헤더 파일에 텔레포트 기능 디버깅을 위해 사용할 매크로를 선언하고 cpp 파일에서 정의한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/140.ImplementABCharacterMovementComponent.h.png">

텔레포트 기능 구현에 필요한 변수 및 함수를 위에서 생성한 ABCharacterMovementComponent 헤더 파일에 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/141.ImplementABCharacterMovementComponent.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/142.ImplementABCharacterMovementComponent.cpp2.png">

cpp 파일에 헤더 파일에서 선언한 함수들의 로직을 정의한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/143.ModifyABCharacterBase.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/144.ModifyABCharacterBase.cpp.png">

새로운 Movement Component 클래스를 생성하지 않고 직접 만든 MoveComponent를 사용하기 위해 생성자에 초기화 오브젝트 인자를 사용하도록 변경한다. 먼저 ABCharacterBase 헤더 파일의 생성자를 변경하고 이에 따라 cpp 파일의 생성자 인자도 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/145.ModifyABCharacterNonPlayer.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/146.ModifyABCharacterNonPlayer.cpp.png">

ABCharacterBase 클래스와 동일하게 ABCharacterNonPlayer 클래스의 헤더 및 cpp 파일 내용도 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/147.ModifyABCharacterPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/148.ModifyABCharacterPlayer.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/149.ModifyABCharacterPlayer.h3.png">

마찬가지로 ABCharacterPlayer 클래스도 변경하는데 추가로 헤더 파일에 텔레포트 기능 구현을 위한 함수 및 변수도 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/150.ModifyABCharacterPlayer.cpp1.png">

cpp 파일에 로직 구현을 위해 필요한 헤더 파일을 추가하고 생성자에 초기화 오브젝트 인자를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/151.ModifyABCharacterPlayer.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/152.ModifyABCharacterPlayer.cpp3.png">

ConstructHelpers를 사용해 위에서 생성해준 IA_Teleport를 할당하고 텔레포트 입력을 바인딩한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/153.ModifyABCharacterPlayer.cpp4.png">

헤더 파일에서 선언한 텔레포트 함수를 구현한다. 여기까지 구현하면 서버는 제대로 작동하지만 클라이언트 캐릭터는 제대로 작동하지 않는다. 따라서 클라이언트-서버 움직임 동기화가 필요하다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/154.ModifyABCharacterMovementComponent.h1.png">

ABCharacterMovementComponent 클래스 파일로 돌아가 로직을 추가한다. 헤더 파일에 Movement 데이터 변경을 위해 클래스를 확장한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/155.ModifyABCharacterMovementComponent.h2.png">

클래스 확장 외에도 클라이언트에서 서버로 명령을 보내는 등에 필요한 함수도 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/156.ModifyABCharacterMovementComponent.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/157.ModifyABCharacterMovementComponent.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/158.ModifyABCharacterMovementComponent.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/159.ModifyABCharacterMovementComponent.cpp4.png">

헤더 파일에서 선언한 함수들을 각각 구현한다.
