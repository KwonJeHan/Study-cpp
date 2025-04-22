# 언리얼 C++ 학습 정리

**2025/04/08 [포텐업] 게임 개발자 양성 과정**

---

## 무한 맵의 제작

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/190.CreateABStageGimmickCPPClass.png">

무한 맵을 만들기 위해 스테이지의 기믹에 대한 내용을 가지는 C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/191.CheckStageMeshSocket.png">

스테이지로 사용할 스태틱 메시의 소켓 위치를 확인한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/192.ImplementABStageGimmick.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/193.ImplementABStageGimmick.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/194.ImplementABStageGimmick.h3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/195.ImplementABStageGimmick.h4.png">

무한 맵 제작에 필요한 기본적인 기능의 틀을 먼저 만들고 기타 세세한 기능들을 구현하기 위해 헤더 파일에 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/196.ImplementABStageGimmick.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/197.ImplementABStageGimmick.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/198.ImplementABStageGimmick.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/199.ImplementABStageGimmick.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/200.ImplementABStageGimmick.cpp5.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/201.ImplementABStageGimmick.cpp6.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/202.ImplementABStageGimmick.cpp7.png">

헤더 파일에 구현한 내용을 토대로 필요한 로직들을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/203.CreateBP_ABStageGimmickBlueprint.png">

위에서 만든 ABStageGimmick C++ 클래스를 부모로 하는 액터 블루프린트 클래스를 생성하고 결과를 확인한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/204.ModifyABStageGimmick.h.png">

NPC와의 전투 파트를 위한 기능을 구현하기 위해 헤더 파일에 Fight Section 내용을 추가 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/205.ModifyABStageGimmick.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/206.ModifyABStageGimmick.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/207.ModifyABStageGimmick.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/208.ModifyABStageGimmick.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/209.ModifyABStageGimmick.cpp5.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/210.ModifyABStageGimmick.cpp6.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/211.ModifyABStageGimmick.cpp7.png">

추가 구현한 내용을 토대로 CPP 파일에 필요한 로직들을 구현한다.
