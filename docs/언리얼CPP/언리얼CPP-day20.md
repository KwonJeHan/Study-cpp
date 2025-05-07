# 언리얼 C++ 학습 정리

**2025/04/30 [포텐업] 게임 개발자 양성 과정**

---

## 게임 플로우 다듬기

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/387.ModifyWBP_HpBar.png">

UserWidget 블루프린트 WBP_HpBar의 위젯 배치를 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/388.ModifyABHpBarWidget.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/389.ModifyABHpBarWidget.h2.png">

Hp 변경 시 수치가 업데이트 되도록 ABHpBarWidget 헤더 파일을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/390.ModifyABHpBarWidget.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/391.ModifyABHpBarWidget.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/392.ModifyABHpBarWidget.cpp3.png">

수정한 헤더 파일을 기반으로 cpp 파일의 로직을 수정 및 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/393.ModifyABCharacterBase.cpp.png">

바뀐 로직에 따라 기존에 구현했던 로직도 변경해야 하므로 ABCharacterBase 클래스의 cpp 파일에 구현했던 최대 체력 값 설정 부분 로직을 변경하고 델리게이트에 등록 부분을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/394.ModifyABHUDWidget.cpp.png">

마찬가지로 ABHUDWidget 클래스의 cpp 파일에 구현한 HpBar의 최대 체력 스탯 설정 부분의 SetMaxHp 함수를 UpdateStat 함수로 변경한다.

