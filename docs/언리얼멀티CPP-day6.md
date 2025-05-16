# 언리얼 멀티 C++ 학습 정리

**2025/05/16 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 공격 구현 개선

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/98.ModifyMontageTickType1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/99.ModifyMontageTickType2.png">

애니메이션 Montage에 배치한 AttackHitCheck 노티파이의 Montage Tick Type을 Branching Point로 변경한다. (클라이언트가 서버를 공격했을 때 공격이 한번에 두 번 적용되는 버그 디버깅)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/100.ModifyDefaultEngine.ini(SetPacketLag).png">

렉이 발생하는 경우를 가정하기 위해 DefaultEngine.ini 파일에 의도적으로 패킷 랙을 발생시키는 구문 추가

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/101.ModifyABCharacterPlayer.h.png">

렉이 발생하는 경우 클라이언트의 반응이 많이 느려지는 문제를 해결하기 위해 기존에 구현했던 공격 기능을 개선하여 다시 설계한다.

ABCharacterPlayer 클래스의 헤더 파일에 편의를 위해 공격 애니메이션 재생 기능을 하는 함수를 추가하고 클라이언트가 공격한 시간 및 서버와의 시간 차를 기록하기 위한 변수를 선언한다. 또한 기존에 구현했던 RPC 함수의 검증 속성을 Unreliable로 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/102.ModifyABCharacterPlayer.cpp1.png">

ABCharacterPlayer 클래스의 cpp 파일 내용도 수정한다.

서버 시간을 측정하기 위해 필요한 헤더 파일을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/103.ModifyABCharacterPlayer.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/104.ModifyABCharacterPlayer.cpp3.png">

기존에 구현했던 Attack 함수 로직도 클라이언트 로직을 나눠서 따로 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/105.ModifyABCharacterPlayer.cpp4.png">

편의성을 위해 선언한 PlayAttackAnimation 함수의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/106.ModifyABCharacterPlayer.cpp5.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/107.ModifyABCharacterPlayer.cpp6.png">

공격 판정을 하던 AttackHitCheck 함수의 로직도 새로 개선한 공격 기능의 설계에 맞게 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/108.ModifyABCharacterPlayer.cpp7.png">

ServerRPC의 검증 함수에 개선된 공격 기능 설계에 필요한 검증 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/109.ModifyABCharacterPlayer.cpp8.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/110.ModifyABCharacterPlayer.cpp9.png">

ServerRPC 함수 내에도 공격 요청 시간 값을 계산하는 등의 방법으로 공격 기능 판정 부분 로직을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/111.ModifyABCharacterPlayer.cpp10.png">

MulticastRPC 함수는 서버와 본인 클라이언트를 제외한 나머지 클라이언트를 대상으로 공격 애니메이션 처리 로직을 구현한다. 

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/112.ModifyABCharacterPlayer.h.png">

ABCharacterPlayer 클래스의 헤더 파일에 액터 충돌 판정을 위한 ServerRPC 함수를 추가로 선언한다.

---

