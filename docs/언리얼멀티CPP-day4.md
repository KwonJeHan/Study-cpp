# 언리얼 멀티 C++ 학습 정리

**2025/05/14 [포텐업] 게임 개발자 양성 과정**

---

## 액터 리플리케이션 로우레벨 플로우

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/61.ModifyABFountain.cpp(Conditional Property Replication).png">

조건식 프로퍼티 리플리케이션 실습을 위해 DOREPLIFETIME을 DOREPLIFETIME_CONDITION으로 변경하고 매개변수 COND_InitialOnly를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/62.ModifyABFountain.h.png">

액터 리플리케이션 흐름을 확인하기 위해 ABFountain 클래스 헤더 파일에 PreReplication 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/63.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/64.ModifyABFountain.cpp2.png">

실습용으로 선언한 DOREPLIFETIME_CONDITION을 다시 주석처리 하고 기존의 DOREPLIFETIME을 다시 활성화한다. PreReplication 함수 로직은 다른 구현 없이 Super 선언과 로그 처리 로직정도만 작성한다.

---

## RPC 기초

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/65.ModifyABFountain.h.png">

MulticastRPC 실습을 위해 ABFountain 클래스 헤더 파일에 해당 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/66.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/67.ModifyABFountain.cpp2.png">

헤더 파일에서 선언한 함수의 로직을 cpp 파일에 작성하고 BeginPlay() 부분 서버 로직에도 필요한 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/68.ModifyABFountain.h.png">

ServerRPC 실습을 위해 ABFountain 클래스 헤더 파일에 해당 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/70.ModifyABFountain.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/69.ModifyABFountain.cpp1.png">

헤더 파일에서 선언한 함수의 로직을 cpp 파일에 작성하고 위에서 BeginPlay() 부분 서버 로직에 작성한 MulticastRPC 함수 관련 로직은 주석 처리 후 따로 else로 클라이언트 로직 부분을 생성해 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/71.ModifyABFountain.cpp(ClientOwnership).png">

위와 같이 작성하면 오너가 없다고 오류 메세지가 출력된다. 이를 해결하기 위해 오너십 설정을 해줘야 하는데 우선 테스트로 cpp 파일에 작성했던 클라이언트 로직 부분에 오너십 설정을 한다. 이렇게 하면 오류 메세지는 출력 되지 않지만 게임 로직이 내가 원하는 대로 작동하진 않는다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/72.ModifyABFountain.cpp(ServerOwnership).png">

따라서 클라이언트가 아닌 서버 로직에서 오너십 설정을 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/73.ModifyABFountain.h(Validation).png">

명령 검증 함수 실습을 위해 기존에 ABFountain 헤더 파일에 구현했던 ServerRPC함수의 속성에 WithValidation을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/74.ModifyABFountain.cpp(Validation).png">

cpp 파일에 따로 _Validate 접미사를 붙힌 함수를 선언하고 로직을 작성한다. (로직은 간단한 실습용이기 때문에 별다른 로직 없이 true를 반환하도록 한다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/75.ModifyABFountain.h.png">

ClientRPC 실습을 위해 ABFountain 클래스 헤더 파일에 해당 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/76.ModifyABFountain.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/77.ModifyABFountain.cpp2.png">

헤더 파일에서 선언한 함수의 로직을 cpp 파일에 작성하고 BeginPlay() 부분 서버 로직에도 필요한 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/78.ModifyABFountain.cpp1(PropertyReplicationVsNetMulticast).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/79.ModifyABFountain.cpp2(PropertyReplicationVsNetMulticast).png">

프로퍼티 리플리케이션과 넷멀티캐스트 RPC의 특징을 비교해보기 위해 위쪽 사진을 프로퍼티 리플리케이션, 아래쪽 사진은 넷멀티캐스트 RPC를 구현했다. 

두 방법의 유사점으론 모두 서버와 모든 클라이언트의 지정한 함수를 호출할 수 있고, 지정한 데이터 전송을 보장할 수 있으며, 액터의 오너십과 무관하게 연관성으로 동작하는 특징이 있다.

차이점은 프로퍼티 리플리케이션의 경우 해당 방법으로 설정한 데이터는 클라이언트에 반드시 동기화되지만(RPC 전송의 Reliability와 다른 개념) 넷멀티캐스트 RPC는 호출한 타이밍에 클라이언트가 없으면 해당 데이터를 받을 방법이 없다.

따라서 프로퍼티 리플리케이션은 게임에 영향을 미치는 데이터에 (Gameplay Property), 넷멀티캐스트 RPC는 게임과 무관한 휘발성 데이터에 사용하는 것이 좋다.
