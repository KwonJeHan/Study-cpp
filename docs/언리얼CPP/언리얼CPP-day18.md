# 언리얼 C++ 학습 정리

**2025/04/28 [포텐업] 게임 개발자 양성 과정**

---

## 행동트리 모델

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/280.ModifyABAIController.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/281.ModifyABAIController.cpp2.png">

NPC의 랜덤 위치로의 정찰 AI를 구현하기 위해 NPC가 스폰되었을 때 NPC의 위치를 블랙보드의 HomePos에 저장한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/282.ImplementBTTask_FindPatrolPos.h.png">

행동트리에 사용하기 위해 생성했던 BTTaskNode를 부모로 하는 C++ 클래스 BTTask_FindPatrolPos 헤더 파일을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/283.ImplementBTTask_FindPatrolPos.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/284.ImplementBTTask_FindPatrolPos.cpp2.png">

태스크가 실행될 때 작동할 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/285.CreateABCharacterAIInterfaceCPPClass.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/286.ImplementABCharacterAIInterfaceCPPClass.png">

ABCharacterAI 인터페이스 C++ 클래스를 생성하고 NPC 캐릭터가 하드코딩으로 구현하지 않도록 하기 위해 필수적으로 구현해야 할 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/287.ModifyABCharacterNonPayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/288.ModifyABCharacterNonPayer.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/289.ModifyABCharacterNonPayer.cpp.png">

ABCharacterAI 인터페이스에서 선언한 함수를 ABCharacterNonPlayer 클래스에서 오버라이드하고 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/290.ModifyBTTask_FindPatrolPos.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/291.ModifyBTTask_FindPatrolPos.cpp2.png">

마찬가지로 ABCharacterAI 인터페이스 클래스를 상속받고 기존에 하드코딩해줬던 부분을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/292.CreateBTServiceCPPClass.png">

행동트리에 설정해 NPC 캐릭터의 감지 관련 로직을 수행하기 위한 BTService_Detect C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/293.ImplementBTService_Detect.h.png">

게임 실행중 매 틱마다 감지할 것이기 때문에 헤더 파일에 생성자와 TickNode 함수를 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/294.ImplementBTService_Detect.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/295.ImplementBTService_Detect.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/296.ImplementBTService_Detect.cpp3.png">

CPP 파일에 NPC 캐릭터의 감지 기능을 위한 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/297.ModifyBB_ABCharacter.png">

블랙보드에 감지된 오브젝트를 저장하기 위해 새로운 오브젝트 타입의 Key값인 Target을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/298.ModifyBT_ABCharacter1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/299.ModifyBT_ABCharacter2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/300.ModifyBT_ABCharacter3.png">

지금까지 구현한 내용을 기반으로 행동트리에 배치 및 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/301.CreateBTDecoratorCPPClass.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/302.CreateBTTaskNodeCPPClass.png">

NPC 캐릭터가 감지를 하고 캐릭터에게 다가온 후 공격을 하는 기능을 추가하기 위해 새로운 BTDecorator C++ 클래스인 AttackRange와 BTTaskNode C++ 클래스인 Attack을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/303.ModifyBT_ABCharacter1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/304.ModifyBT_ABCharacter2.png">

로직을 구현하기 전에 먼저 생성한 C++ 클래스를 기반으로 하는 Task노드를 배치하고 Decorator를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/305.ImplementBTDecorator__AttackRange.h.png">

데코레이터 실행에 필요한 함수인 CalculateRawConditionValue 함수를 AttackRange 헤더 파일에 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/306.ImplementBTDecorator__AttackRange.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/307.ImplementBTDecorator__AttackRange.cpp2.png">

어떠한 경우에 true를 반환하고 false를 반환할 것인지에 대한 로직을 cpp 파일에 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/308.ModifyABCharacterStatComponent.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/309.ModifyABCharacterStatComponent.h2.png">

위의 내용에서 본 것과 마찬가지로 하드코딩을 피하기 위해 AttackRadius 변수와 GetRadius 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/310.ModifyABCharacterStatComponent.cpp.png">

생성자에서 헤더 파일에 선언한 변수 AttackRadius의 값을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/311.ModifyABCharacterBase.cpp.png">

변경한 코드 내용에 따라 ABCharacterBase에서 쓰고 있던 값을 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/312.ModifyABCharacterNonPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/313.ModifyABCharacterNonPlayer.cpp2.png">

필요한 헤더 파일을 추가하고 오버라이드 해놨던 GetAIAttackRange 함수의 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/314.ModifyABCharacterAIInterface.h.png">

공격 기능과 델리게이트를 사용하기 위한 함수를 ABCharacterAI 인터페이스에 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/315.ModifyABCharacterBase.h.png">

NPC 캐릭터의 공격이 끝나는 지점을 알기 위한 함수를 ABCharacterBase 클래스의 헤더 파일에 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/316.ModifyABCharacterBase.cpp.png">

특별히 내용을 구현할 필요가 없으므로 기존 로직에 해당 함수를 추가하는 식으로 기존 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/317.ModifyABCharacterNonPlayer.h.png">

ABCharacterAI 인터페이스에서 선언한 함수를 오버라이드 하고 델리게이트를 저장할 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/318.ModifyABCharacterNonPlayer.cpp.png">

오버라이드한 함수의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/319.ImplementBTTask_Attack.h.png">

생성해놨던 BTTaskNode를 부모로 하는 Attack C++ 클래스 헤더 파일에 태스크 실행 시 호출되는 함수 ExecuteTask를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/320.ImplementBTTask_Attack.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/321.ImplementBTTask_Attack.cpp2.png">

cpp 파일에 태스크 실행 시 NPC 캐릭터가 행동하는데 필요한 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/322.ModifyBT_ABCharacter.png">

플레이어가 죽어도 NPC 캐릭터가 플레이어가 있던 지점에 계속 공격하는 현상을 막기 위해 BTService Detect를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/323.CreateBTTaskNodeCPPClass.png">

NPC 캐릭터가 플레이어에게 공격을 시작한 시점의 방향으로만 계속 공격하는 현상을 수정하기 위해 BTTaskNode 클래스를 부모로 하는 새로운 C++ 클래스 TurnToTarget을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/324.ImplementBTTask_TurnToTarget.h.png">

위에서 구현한 BTTaskNode 클래스와 동일하게 생성자와 ExecuteTask 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/325.ImplementBTTask_TurnToTarget.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/326.ImplementBTTask_TurnToTarget.cpp2.png">

NPC 캐릭터가 한 방향만 보고 공격하지 않도록 플레이어 캐릭터 쪽 방향으로 Rotation을 갱신하는 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/327.ModifyABCharacterNonPlayer.cpp.png">

회전 속도를 하드코딩으로 구현하지 않도록 NonPlayer 클래스에 선언했던 GetAITurnSpeed 함수를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/328.ModifyBT_ABCharacter.png">

구현한 클래스를 기반으로 행동트리를 수정한다.
