# 언리얼 멀티 C++ 학습 정리

**2025/05/23 [포텐업] 게임 개발자 양성 과정**

---

## PvP 게임의 완성

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/183.ModifyABGameInterface.h.png">

캐릭터 리스폰 처리 및 PVP 정보 처리를 게임 모드에서 하기 위해 인터페이스를 통해 함수를 오버라이드하도록 설계한다.

ABGameInterface 클래스 헤더 파일에 필요한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/184.ModifyABGameMode.h.png">

인터페이스에서 선언한 함수 구현을 위해 ABGameMode 클래스 헤더 파일에 오버라이드하고 플레이어 스타트 액터를 랜덤으로 지정하기 위한 배열을 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/185.ModifyABGameMode.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/186.ModifyABGameMode.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/187.ModifyABGameMode.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/188.ModifyABGameMode.cpp4.png">

cpp 파일에 함수 구현을 위한 헤더 파일을 추가하고 오버라이드 선언한 함수의 로직을 구현한다. (OnPlayerKilled 함수는 차후 구현)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/189.ModifyABCharacterStatComponent.h.png">

ABCharacterStatComponent 클래스 헤더 파일에 캐릭터 사망 시 스텟 초기화를 위한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/190.ModifyABCharacterStatComponent.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/191.ModifyABCharacterStatComponent.cpp2.png">

헤더 파일에서 선언한 캐릭터 스텟 초기화 함수를 cpp 파일에 구현한다. 또한 기존에 스탯 초기화를 위해 사용한 로직을 주석 처리하고 구현한 수탯 초기화 함수를 사용하고 생성자에서 실행한 컴포넌트 리플리케이션 활성화 구문을 InitializeComponent에서 실행하도록 변경 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/192.ModifyDefaultArenaBattle.ini.png">

플레이어 캐릭터 사망 후 리스폰 시 캐릭터 외형이 랜덤으로 변하도록 구현한다. 이를 위해 우선 DefaultArenaBattle.ini 파일에 사용할 애셋들을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/193.ModifyABCharacterPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/194.ModifyABCharacterPlayer.h2.png">

대미지 처리 함수에 추가적인 로직 구현을 위해 ABCharacterPlayer 클래스 헤더 파일에 오버라이드하고 캐릭터의 PVP 관련 이벤트 처리를 위한 함수 및 변수를 선언한다. 또한 플레이어 캐릭터 메시 랜덤 변경을 위해 UCLASS와 UPROPERTY에 config 설정도 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/195.ModifyABCharacterPlayer.cpp1.png">

cpp 파일에 함수 로직 구현을 위한 헤더 파일을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/196.ModifyABCharacterPlayer.cpp2.png">

플레이어 사망 시 기존에 플레이어 컨트롤러를 비활성화 하기만 한 부분을 주석처리하고 플레이어 리스폰을 가정해 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/197.ModifyABCharacterPlayer.cpp3.png">

오버라이드한 대미지 처리 함수에 추가 로직을 구현한다. 게임 모드에 인터페이스를 통해 접근해 PVP 정보를 처리한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/198.ModifyABCharacterPlayer.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/200.ModifyABCharacterPlayer.cpp6.png">

Attack 함수와 ServerRPCAttack 함수에서 구현했던 타이머를 통한 공격 종료 판정 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/199.ModifyABCharacterPlayer.cpp5.png">

공격 타이밍 검증 판정에서 기존에 AttackTime보다 크면 검증을 통과하던 로직에서 렉이나 기타 요인으로 불가피하게 판정을 통과하지 못 할 가능성이 있기 때문에 판정을 조금 널널하게 하기 위해 AttackTime에 0.4를 뺀 값으로 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/201.ModifyABCharacterPlayer.cpp7.png">

플레이어 리스폰 시 플레이어의 상태를 리셋하는 함수 로직을 구현한다. 죽었을 시 설정했던 여러 항목들을 모두 복구하고 리스폰 위치를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/202.ModifyABCharacterPlayer.cpp8.png">

공격이 끝나면 공격 중에 MovementMode를 None으로 설정해 이동하지 못하게 했던 로직을 다시 Walking으로 설정해 이동할 수 있도록 하는 함수를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/206.ModifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/207.ModifyABCharacterBase.h2.png">

이제 캐릭터 메시 랜덤 변경 기능이 NPC 캐릭터만이 아닌 Player 캐릭터도 적용되어야 하므로 기존에 ABCharacterNonPlayer 클래스에 구현한 함수를 ABCharacterBase로 옮긴다. 이를 위해 우선 ABCharacterBase 클래스 헤더 파일에 선언에 필요한 헤더 파일을 추가하고 함수와 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/208.ModifyABCharacterBase.cpp.png">

cpp 파일로 기존에 ABCharacterNonPlayer 클래스 cpp 파일에 구현한 함수를 옮겨와 부분 수정을 해 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/203.ModifyABCharacterNonPlayer.h.png">

ABCharacterNonPlayer 클래스의 헤더 파일에선 ABCharacterBase 클래스로 옮긴 함수 및 변수 선언 부분을 주석 처리한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/204.ModifyABCharacterNonPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/205.ModifyABCharacterNonPlayer.cpp2.png">

cpp 파일도 동일하게 헤더 파일에서 주석처리한 함수 구현부를 주석처리하고 기존에 구현한 메시 변경 로직을 변경한 로직에 맞게 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/209.ModifyABCharacterPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/210.ModifyABCharacterPlayer.h2.png">

ABCharacterPlayer 클래스의 헤더 파일에 캐릭터 플레이어 메시 정보 업데이트를 위한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/211.ModifyABCharacterPlayer.cpp1.png">

cpp 파일에 헤더 파일에서 선언한 함수를 구현하기 위한 헤더 파일을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/212.ModifyABCharacterPlayer.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/213.ModifyABCharacterPlayer.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/214.ModifyABCharacterPlayer.cpp4.png">

헤더 파일에서 선언한 함수를 구현한다. 메시 인덱스의 경우 PlayerID를 활용해서 인덱스 값을 결정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/215.CreatePlayerStateCPPClass(ABPlayerState).png">

플레이어 스테이트 설정을 실습해보기 위해 PlayerState를 부모로 하는 ABPlayerState C++ 클래스를 생성한다. 

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/216.ModifyABGameMode.cpp.png">

ABGameMode 클래스 cpp 파일의 생성자에서 플레이어 스테이트 클래스를 지정한다. 현재는 다른 기능들을 구현하지 않지만 PlayerState는 다양한 기능을 제공한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/217.ModifyABGameState.h.png">

남은 시간, 경기 종료 및 재시작 등 게임 규칙 관련 변수 설정을 위해 ABGameState 클래스 헤더 파일에 필요한 함수 및 변수를 선언한다. 또한, 기존에 기본적인 기능만 가지고 있던 GameStateBase를 상속하던 부분을 GameState를 상속하도록 변경한다.

사용하지 않는 HandleBeginPlay와 OnRep_ReplicatedHasBegunPlay 함수는 주석처리한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/218.ModifyABGameState.cpp.png">

cpp 파일에서 리플리케이트할 속성 값인 RemainingTime을 GetLifrtimeReplicatedProps 함수에 DOREPLIFETIME으로 변수를 등록하고 생성자에서 값을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/219.ModifyABGameMode.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/220.ModifyABGameMode.h2.png">

게임 규칙 설정 및 적용을 위해 GameMode를 사용한다.

GameState와 동일하게 GameModeBase를 상속하던 부분을 GameMode를 상속하도록 변경한다.

또한, 게임 규칙 설정에 필요한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/221.ModifyABGameMode.cpp1.png">

cpp 파일에서 선언한 해놓고 구현하지 않았던OnPlayerKilled 함수를 구현한다. 다른 플레이어를 처치한 플레이어의 스테이트에 점수를 추가하고 점수가 2점 이상일 시 맵이 변경된다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/222.ModifyABGameMode.cpp2.png">

경기 시간 관리 함수 및 경기 종료 함수 로직을 구현한다.
