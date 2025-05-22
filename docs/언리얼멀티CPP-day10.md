# 언리얼 멀티 C++ 학습 정리

**2025/05/22 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 아이템과 스탯의 구현

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/160.ModifyDefaultEngine.ini.png">

아이템 및 스탯을 구현하기 이전에 DefaultEngine.ini 파일에서 설정했던 패킷렉 부분을 주석 처리한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/161.ModifyABItemBox.cpp.png">

디버깅 테스트를 더 수월하게 할 수 있도록 기존 ABItem 클래스 cpp 파일에 정의한 랜덤 아이템 로직을 수정한다. (배치된 상자에 아이템이 설정되어 있으면 설정된 아이템을 사용하도록 한다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/162.SetItemToItemBox.png">

맵에 배치된 상자들에 각각 디버깅에 필요한 아이템들을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/163.ModifyABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/164.ModifyABCharacterBase.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/165.ModifyABCharacterBase.cpp3.png">

스탯 관리는 서버에서만 하도록 변경한다. 포션과 스크롤의 경우 스탯 정보만 가지고 있기 때문에 전체 로직을 서버 로직으로 변경하지만 웨폰의 경우 메시는 서버와 클라이언트 모두에 표시되어야 하므로 따로 변경하지 않고 스탯과 관련한 로직만 서버 로직으로 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/166.ModifyABCharacterStatComponent.h1.png">

HP 정보의 경우 SimulateProxy를 포함한 모든 클라이언트에게 전송하지만 스탯 정보는 캐릭터를 소유한 클라이언트에만 전송하도록 설정해 네트워크로 전송할 데이터를 줄인다. 

우선 ABCharacterStatComponent 클래스의 헤더 파일을 수정한다.

스탯 정보와 HP 정보 리플리케이트를 위한 OnRep 함수를 UFUNCTION으로 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/167.ModifyABCharacterStatComponent.h2.png">

사용할 리플리케이트 속성을 선언하고 각각 OnRep 함수를 할당한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/168.ModifyABCharacterStatComponent.h3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/169.ModifyABCharacterStatComponent.h4.png">

추가된 리플리케이트 속성에 따라 기존에 구현했던 함수와 델리게이트 선언을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/170.ModifyABCharacterStatComponent.cpp1.png">

헤더 파일에서 선언한 내용에 따라 cpp 파일도 수정한다.

DOREPLIFETIME 매크로로 프로퍼티를 리플리케이션에 등록하는데 위에서 말한 설계 내용대로 HP는 모든 클라이언트에 전송하지만 스탯은 캐릭터를 소유한 클라이언트에만 전송하도록 하기 위해 매크로 뒤에 _CONDITION을 추가하고 인수로 COND_OwnerOnly를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/171.ModifyABCharacterStatComponent.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/172.ModifyABCharacterStatComponent.cpp3.png">

새로 추가한 OnRep 함수와 기존에 구현한 함수 모두 델리게이트로 이벤트를 발행하도록 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/173.ModifyABCharacterStatComponent.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/174.ModifyABCharacterStatComponent.cpp5.png">

헤더 파일에서 수정한 내용과 맞도록 cpp 파일의 함수 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/175.ModifyABHpBarWidget.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/176.ModifyABHpBarWidget.cpp.png">

ABStatComponent 클래스에서 변경한 로직으로 인해 다른 C++ 클래스 파일들도 조금씩 수정해야 한다.

ABHpBarWidget 클래스의 헤더와 cpp 파일을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/177.ModifyABHUDWidget.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/178.ModifyABHUDWidget.cpp.png">

동일하게 ABHUDWidget 클래스 헤더와 cpp 파일도 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/179.ModifyABCharacterBase.cpp.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/180.ModifyABCharacterPlayer.cpp.png">

ABCharacterBase와 ABCharacterPlayer 클래스의 cpp 파일에서 구현한 함수의 내용도 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/181.ModifyABCharacterStat.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/182.ModifyABCharacterStat.h2.png">

NetSerialize를 사용한 데이터 설계로 네트웍으로 전송할 구조체 데이터를 직접 설계해본다.

이를 통해 데이터 양을 최소화 할 수 있고 데이터가 자주 배꿜 경우 유용하게 활용할 수 있다. 또한 플래그를 설정해서 불필요한 데이터 전송을 건너뛸 수 있고 정수 데이터로 변환해 크기를 줄일 수 있다.

위와 같이 ABCharacterStat 클래스 헤더 파일에 NetSerialize 함수를 선언 및 구현한다. 일종의 압축 및 저장, 불러오기 기능이라고 생각할 수 있다.

또한 WithNerSerializer를 설정하기 위한 템플릿도 선언한다.
