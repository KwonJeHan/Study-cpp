# 언리얼 C++ 학습 정리

**2025/04/25 [포텐업] 게임 개발자 양성 과정**

---

## 행동트리 모델

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/265.CreateAIControllerCPPClass.png">

행동 트리를 사용하기 위한 로직을 구현할 AIController를 부모로 하는 ABAIController C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/266.ModifyABCharacterNonPlayer.cpp.png">

구현하기 전에 먼저 생성한 AI 행동 트리를 사용할 ABCharacterNonPlayer에 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/267.CreateBlackBoard&BehaviorTree.png">

AI 행동 로직에 사용할 블랙보드와 행동트리를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/268.SetBlackBoard&BehaviorTree.png">

기본적인 행동트리 노드를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/269.ImplementABAIController.h.png">

ABAIController 헤더 파일에 AI 행동 실행 및 중지 함수, 생성한 블랙보드와 행동트리를 할당할 오브젝트를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/270.ImplementABAIController.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/271.ImplementABAIController.cpp2.png">

헤더 파일에 선언한 내용을 기반으로 cpp 파일에 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/272.SetNavMeshBoundsVolume1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/273.SetNavMeshBoundsVolume2.png">

AI가 행동할 구역을 설정하기 위해 에디터에서 NavMeshBoundVolume을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/274.SetProjectSettingsNavigationMesh.png">

배치되어있는 오브젝트뿐만 아니라 생성되는 오브젝트도 NavigationMesh를 사용할 수 있도록 프로젝트 세팅의 설정을 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/275.ModifyBlackboard&BehaviorTree.png">

블랙보드에 정찰 로직을 구현하기 위한 키를 생성하고 행동트리의 내용을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/276.CreateBTTaskNodeCPPClass.png">

행동트리 Task 노드 로직을 구현하기 위한 BTTask_FindPatrolPos C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/277.ModifyArenaBattleDemo.Build.cs.png">

생성한 C++ 클래스를 구현하기 전에 Build.cs 파일에 사용할 모듈들을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/278.CreateABAI.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/279.ImplementABAI.h.png">

구현할 때 직관성과 편의성을 위해 ABAI 헤더 파일을 생성하고 매크로를 구현한다.
