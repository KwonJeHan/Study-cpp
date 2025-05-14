# 언리얼 멀티 C++ 학습 정리

**2025/05/13 [포텐업] 게임 개발자 양성 과정**

---

## 액터 리플리케이션 빈도와 연관성

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/41.FindUnrealInsights.exe.png">

언리얼 엔진 설치 폴더를 찾아 UnrealInsights 실행 파일 경로를 찾고 프로그램을 실행하기 쉽도록 바로가기를 만들어 바탕화면에 배치하거나 작업 표시줄에 고정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/42.AddEnvironmentVariablePath.png">

제어판 - 시스템 - 고급 시스템 설정 - 환경 변수의 Path에 위에서 찾은 실행 파일 경로를 새로 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/43.CreateNetworkInsightsEditor.bat.png">

프로젝트 폴더 내에 배치 파일을 만든다. 파일 이름은 NetworkInsightsEditor.bat 으로 하고 파일 내용은 위와 같이 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/44.ConnectLocalHostIPToUnrealInsights.png">

배치 파일을 실행해 언리얼 에디터를 실행하고 UnrealInsights를 실행하면 위와 같은 창이 나오는데 로컬 호스트 IP와 Connection한다. (기본값으로 로컬 호스트 IP가 작성되어 있다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/45.SetUnrealInsightsLayout.png">

현재 Live 상태인 에디터를 선택해 실행하면 위와 같이 네트워크 상태를 볼 수 있는데 이를 보기 편리하게 레이아웃을 정리한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/46.ModifyABFountain.cpp.png">

클라이언트와 서버 간 통신 빈도가 많으면 성능 면에서 문제가 될 수 있으므로 네트워크 데이터를 줄이기 위해 1초에 1번으로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/47.ModifyABFountain.h.png">

네트워크 데이터를 줄이는 만큼 데이터 공백이 생기기 때문에 클라이언트 로직 내에서 움직임이 부드럽게 보이도록 보완할 필요가 있다. 이를 위해 데이터 전송과 관련된 시간을 저장할 변수를 ABFountain 클래스의 헤더 파일에 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/48.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/49.ModifyABFountain.cpp2.png">

cpp 파일에서 기존에 구현해놨던 함수 OnRep_ServerRotationYaw에 헤더 파일에서 선언한 시간 관련 변수 값을 설정하는 로직을 작성하고 Tick 함수에서 해당 변수를 사용해 보간 처리를 통해 컴포넌트 회전이 부드럽게 보이도록 하는 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/50.ModifyABFountain.h.png">

ABFountain 클래스의 헤더 파일에 연관성 판정을 진행하기 위한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/51.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/52.ModifyABFountain.cpp2.png">

cpp 파일에 헤더 파일에서 선언한 연관성 판정 함수의 로직을 작성하고 거리 판정에 사용하는 값을 언리얼 엔진이 설정한 기본값보다 줄여서 4000000(약 20미터)으로 설정한다.

---

## 액터 리플리케이션 로우레벨 플로우

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/53.ModifyABFountain.h.png">

ABFountain 클래스의 헤더 파일에 네트워크를 포화 상태의 로그를 확인하기 위해 의도적으로 네트워크를 포화 상태로 만들기 위한 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/54.ModifyABFountain.cpp.png">

cpp 파일의 BeginPlay 함수의 서버 로직에 네트워크가 포화될 정도의 값을 가진 데이터를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/55.ModifyDefaultEngine.ini.png">

DefaultEngine.ini 파일에 cpp 파일에서 설정한 데이터 값보다 작도록 TotalNetBandwidth를 설정하고 LogNetTraffic도 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/56.ModifyABFountain.h.png">

기존에 네트워크 포화 상태를 테스트하기 위해 작성한 부분을 모두 주석 처리하고 휴면 상태 설정 실습 전 분수대에 배치된 PoinLight의 색상을 일정 시간마다 변하게 하는 로직을 구현하기 위해 ABFountain 클래스의 헤더 파일에 함수와 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/57.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/59.ModifyABFountain.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/58.ModifyABFountain.cpp2.png">

cpp 파일에 로직 작성을 위해 필요한 헤더 파일을 추가하고 헤더 파일에서 선언한 함수의 로직을 구현한다. 그리고 DOREPLIFETIME에 속성 정의를 추가하고 BeginPlay의 서버 로직에 색상 값이 랜덤으로 변하는 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/60.ModifyABFountain.cpp.png">

생성자에 휴면 상태로 시작하도록 하기 위한 열거형 값을 설정하고 서버 로직에 휴면 상태를 깨우기 위한 로직을 작성하고 테스트한다.
