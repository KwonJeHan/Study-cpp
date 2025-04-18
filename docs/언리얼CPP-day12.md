# 언리얼 C++ 학습 정리

**2025/04/18 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 스텟과 위젯

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/133.ModifyABCharacterPlayer&ABCharacterBase1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/134.ModifyABCharacterPlayer&ABCharacterBase2.png">

CharacterPlayer와 CharacterBase의 코드를 정리한다.

(해당 장의 구현과는 큰 연관이 없는 코드 정리 작업이다. Player부분에 있던 캐릭터 설정 부분 코드를 Base로 옮기고 스켈레탈 메시와 애니메이션 블루프린트 리소스를 최신화 시켰다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/136.CreateUserWidgetBluprint1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/137.CreateUserWidgetBluprint2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/138.CreateUserWidgetBluprint3.png">

유저 위젯 블루프린트를 만들고 외형 정보를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/139.CreateUserWidgetCPPClass.png">

위에서 만든 유저 위젯 블루프린트의 부모가 될 C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/140.SetParentUserWidgetBlueprint.png">

유저 위젯 블루프린트의 부모를 설정한다. (블루프린트를 만들기 전에 먼저 C++ 클래스를 만들고 해당 C++ 클래스를 부모로 블루프린트를 만들어도 된다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/135.CreateActorComponentCPPClass.png">

캐릭터의 스탯 상태을 설정하기 위해  ActorComponent를 부모로 하는 C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/141.ImplementABCharacterStatComponent.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/142.ImplementABCharacterStatComponent.h2.png">

ABCharacterStatComponent 헤더 파일 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/143.ImplementABCharacterStatComponent.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/144.ImplementABCharacterStatComponent.cpp2.png">

ABCharacterStatComponent cpp 파일 내용을 구현한다.

(Tick 함수는 사용할 필요가 없기 때문에 삭제했다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/145.ModifyArenaBattleDemo.Build.cs.png">

UMG 모듈을 사용하기 위해 프로젝트 빌드 파일에 내용을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/146.ImplementABHpBarWidget.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/147.ImplementABHpBarWidget.cpp.png">

유저 위젯 블루프린트의 부모로 설정하기 위해 생성한ABHpBarWidget 클래스의 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/148.AddSectionToABCharacterBase.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/149.AddSectionToABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/150.AddSectionToABCharacterBase.cpp2.png">

생성한 스텟 컴포넌트와 위젯 컴포넌트를 캐릭터에서 사용하기 위해 Stat/Widget Section의 내용을 구현한다.
