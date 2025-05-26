# 언리얼 멀티 C++ 학습 정리

**2025/05/12 [포텐업] 게임 개발자 양성 과정**

---

## 커넥션과 오너십

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/19.ModifyABPlayerController.h.png">

ABPlayerController 헤더 파일에서 빙의 함수 OnPossess를 오버라이드 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/20.ModifyABPlayerController.cpp.png">

cpp 파일에 헤더 파일에서 오버라이드한 함수의 Super 콜을 하고 로그를 확인하기 위해 만들었던 매크로를 사용해 로그 내용을 출력한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/21.ModifyABCharacterPlayer.h.png">

플레이어 캐릭터도 빙의 함수 및 소유 확인을 위한 함수들을 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/22.ModifyABCharacterPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/23.ModifyABCharacterPlayer.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/24.ModifyABCharacterPlayer.cpp3.png">

플레이어 컨트롤러 클래스와 동일하게 로그 내용을 출력하기 위해 cpp파일에 헤더 파일에서 오버라이드한 함수들의 내용을 작성한다.

---

## 액터의 역할과 커넥션 핸드셰이킹

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/25.ModifyArenaBattle.h.png">

액터 역할의 종류를 로그를 통해 시각적으로 확인하기 위해 기존에 ArenaBattle 헤더 파일에 작성했던 매크로의 내용을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/26.ModifyABCharacterPlayer.cpp.png">

ABCharacterPlayer 클래스 cpp 파일에 구현한 PostNetInit 함수의 매크로 출력 부분을 수정한다.

---

## 액터 리플리케이션 기초

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/27.CheckNetLoadOnClient.png">

에디터에서 배치한 액터의 디테일 옵션 중 Replication - Net Load On Client 옵션을 활성화 해야 기본적인 리플리케이션이 적용된다 (기본값으로 활성화되어 있다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/28.HowSetReplicatesProperty.png">

액터의 속성을 리플리케이션 할 때의 방법이다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/29.ModifyABFountain.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/30.ModifyABFountain.h2.png">

ABFountain 클래스의 헤더 파일에 네트웍으로 복제할 액터의 속성을 Replicated 키워드를 사용해 지정하고 복제할 속성을 추가하기 위해 GetLifetimeReplicatedProps 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/31.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/32.ModifyABFountain.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/33.ModifyABFountain.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/34.ModifyABFountain.cpp4.png">

cpp 파일에서 DOREPLIFETIME 매크로 사용을 위한 헤더를 추가하고 헤더 파일에서 선언한 함수 GetLifetimeReplicatedProps에 사용해 복제할 속성 정의를 추가한다.

또한, 생성자에 bReplicates 옵션을 true로 설정하고 Tick 함수에 서버와 클라이언트에서 이루어 질 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/35.HowCallReplicatesCallBackFunction.png">

위 방법과 다른 방법으로 리플리케이션 콜백 함수를 호출하는 방법이 있다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/36.ModifyABFountain.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/37.ModifyABFountain.h2.png">

ABFountain 헤더 파일을 수정한다. 속성값 변경 시 호출할 콜백 함수를 UFUNCTION으로 선언하고 Replicated로 지정했던 액터의 속성을 ReplicatedUsing으로 변경해 호출할 콜백 함수로 지정한다.

또한 로그 출력으로 액터 채널이 열릴 때의 시점을 확인하기 위해 OnActorChannelOpen 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/38.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/39.ModifyABFountain.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/40.ModifyABFountain.cpp3.png">

로그 출력을 위해 ArenaBattle 헤더 파일을 추가하고 OnActorChannelOpen 함수에 로그 출력 로직을 작성한다. 기존에 Tick 함수에 작성했던 클라이언트 로직을 삭제하고 헤더 파일에서 선언한 콜백 함수의 로직으로 옮긴다.
