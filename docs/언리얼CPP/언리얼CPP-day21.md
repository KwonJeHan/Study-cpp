# 언리얼 C++ 학습 정리

**2025/05/07 [포텐업] 게임 개발자 양성 과정**

---

## 게임의 완성

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/395.CreateInterfaceCPPClass(ABGameInterface).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/396.ImplementABGameInterface.h.png">

C++ 클래스 간 커플링 방지를 위해 Interfece 클래스로 ABGameInterface를 생성하고 순수 가상 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/397.ModifyABGameMode.h.png">

ABGameMode 헤더 파일에 게임 클리어, 게임 오버 등의 게임 규칙 로직을 구현하기 위해 앞서 만든 인터페이스 클래스를 상속해 함수를 선언하고 필요한 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/398.ModifyABStageGimmick.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/399.ModifyABStageGimmick.cpp2.png">

ABStageGimmick cpp 파일에 NPC가 죽었을 때 점수 획득 처리 및 게임 클리어 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/400.ModifyABCharacterPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/401.ModifyABCharacterPlayer.cpp2.png">

ABCharacterPlayer cpp 파일에 플레이어가 죽었을 때 게임 종료 처리 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/402.ModifyABPlayerController.h.png">

ABPlayerController 헤더 파일에 게임 처리와 관련해 게임 모드에서 호출할 함수를 선언하고 모든 기능을 C++ 클래스로 구현하는 것은 비효율적이므로 블루프린트에서 구현하기 용이한 부분들은 블루프린트 이벤트로 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/403.ModifyABPlayerController.cpp.png">

헤더 파일에서 선언한 함수의 로직을 작성한다. (K2 접두어 함수의 경우 블루프린트 클래스에서 구현할 것이므로 선언만 하고 따로 cpp 파일에서 구현하지 않는다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/404.ModifyABGameMode.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/405.ModifyABGameMode.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/406.ModifyABGameMode.cpp3.png">

ABPlayerController에 구현한 함수를 사용해 게임 처리 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/407.CreatePlayerControllerBlueprintClass(BP_PlayerController).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/408.ModifyBP_ABGameMode.png">

구현한 ABPlayerController를 부모로 하는 블루프린트 클래스 BP_ABPlayerController를 생성하고 게임 모드에서 해당 플레이어 컨트롤러를 기본값으로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/409.ImplementBP_ABPlayerController1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/410.ImplementBP_ABPlayerController2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/411.ImplementBP_ABPlayerController3.png">

블루프린트 클래스에서 구현하기 위해 C++ 클래스에서 구현하지 않고 뒀던 K2 접두어 함수들의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/412.ModifyABPlayerController.cpp.png">

기존에 ABPlayerController cpp 파일의 BeginPlay 함수에서 ABHUDWidget을 생성하고 뷰포트에 추가하던 로직을 블루프린트 클래스에서 더 간단하게 구현하기 위해 삭제한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/413.ModifyBP_ABPlayerController.png">

삭제한 로직을 블루프린트 클래스의 BeginPlay 이벤트에서 다시 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/414.SetWBP_PlayerScore.png">

WBP_ABHUD에 WBP_PlayerScore를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/415.ModifyBP_ABPlayerController1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/416.ModifyBP_ABPlayerController2.png">

ClearScore 증가 로직을 BP_ABPlayerController 블루프린트 클래스에 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/417.CreateSaveGameCPPClass(ABSaveGame).png">

게임 저장 및 불러오기 기능 구현을 위해 SaveGame을 상속받는 C++ 클래스 ABSaveGame을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/418.ImplementABSaveGame.h.png">

헤더 파일에 생성자와 재시도 횟수를 기록하는데 사용할 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/419.ImplementABSaveGame.cpp.png">

헤더 파일에서 선언한 변수를 cpp 파일의 생성자에서 초기화한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/420.ModifyABPlayerController.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/421.ModifyABPlayerController.h2.png">

ABPlayerController 헤더 파일에 게임 진행 중 항상 메모리에서 게임 저장 및 불러오기를 관리하도록 변수를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/422.ModifyABPlayerController.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/423.ModifyABPlayerController.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/424.ModifyABPlayerController.cpp3.png">

cpp 파일 내 함수들 중 게임 저장 및 불러오기 기능이 필요한 부분을 찾아 필요한 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/425.ModifyABPlayerController.h.png">

게임 재시작 횟수가 변경될 때 사용할 함수를 Kismet으로 선언해 블루프린트에서 이벤트 로직을 구현하도록 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/426.ModifyBP_ABPlayerController.png">

블루프린트에서 해당 이벤트 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/427.ModifyABPlayerController.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/428.ModifyABPlayerController.cpp2.png">

위에서 구현한 이벤트가 발행될 부분을 찾아 로직을 수정한다.
