# 언리얼 멀티 C++ 학습 정리

**2025/05/09 [포텐업] 게임 개발자 양성 과정**

---

## 게임모드와 로그인

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/1.SetAllowLateJoining.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/2.SetAlwaysOnTop.png">

본격적인 프로젝트 시작 전에 프로젝트 세팅을 먼저 설정한다. Allow late joining 옵션을 켜서 Add another Client 버튼을 활성화하고 Always on top 옵션을 켜서 테스트로 에디터 실행 시 실행 창이 뒤쪽으로 빠져서 번거로운 상황을 없앤다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/3.ModifyArenaBattle.h.png">

멀티플레이 구현 시 디버깅을 환경 조성을 위해 ArenaBattle 헤더 파일에 로그 매크로를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/4.ModifyArenaBattle.cpp.png">

헤더 파일에서 정의한 로그 매크로를 cpp 파일에서 정의한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/5.ModifyABPlayerController.cpp(TestLogMacro).png">

PlayerController의 BeginPlay 함수가 실행되는 타이밍을 확인하기 위해 ABPlayerContorller 클래스의 cpp 파일에서 위에서 정의한 AB_LOG 매크로를 사용해 로그가 출력되도록 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/6.ModifyArenaBattle.h.png">

출력되는 로그 내용의 정보를 더 구체적으로 알 수 있도록 ArenaBattle 클래스의 헤더 파일을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/7.CreateGameStateBaseCPPClass(ABGameState).png">

GameStateBase 클래스를 부모로 하는 ABGameState C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/8.ModifyABGameMode.h.png">

ABGameMode 클래스의 헤더 파일에 로그인 처리를 위한 함수를 오버라이딩한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/9.ModifyABGameMode.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/10.ModifyABGameMode.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/11.ModifyABGameMode.cpp3.png">

cpp 파일에서 게임 스테이트 클래스로 위에서 만든 ABGameState 클래스를 지정하고 헤더 파일에서 오버라이딩한 함수들을 구현한다. (디버깅용으로 함수 실행 타이밍을 알기 위한 Log 출력 로직)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/12.ImplementABGameState.h.png">

ABGameState 클래스의 헤더 파일에도 로그인 처리 관련 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/13.ImplementABGameState.cpp.png">

동일하게 cpp 파일에 헤더 파일에서 선언한 함수들을 구현한다. (마찬가지로 함수 실행 타이밍을 알기 위한 Log 출력 로직)

---

## 커넥션과 오너십

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/14.ModifyABGameMode.cpp(ErrorMessage).png">

ABGameMode 클래스의 cpp파일에 정의한 PreLogin 함수의 매개변수 ErrorMessage에 값을 할당하지 않았었는데 테스트로 할당하고 실행시켜본다. (이를 할당하게 되면 로그인을 통과시키지 않고 오류로 간주한다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/15.ModifyABGameMode.cpp(DeleteStartPlay).png">

커넥션과 오너십 실습에 앞서 테스트를 위해 ABGameMode의 StartPlay의 정의 부분을 삭제한다. (주석 처리)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/16.ModifyABGameMode.cpp(NetDriver).png">

서버 로그인 시 NetDriver를 할당한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/17.ModifyABPlayerController.h.png">

클라이언트 로그인 처리를 위한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/18.ModifyABPlayerController.cpp.png">

선언한 함수들을 구현한다. (함수 실행 타이밍을 알기 위한 Log 출력 로직 및 클라이언트 NetDriver 할당 로직)
