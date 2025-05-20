# 언리얼 멀티 C++ 학습 정리

**2025/05/19 [포텐업] 게임 개발자 양성 과정**

---

## 움직임 리플리케이션

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/124.ModifyDefaultEngine.ini.png">

움직임 리플리케이션 디버깅을 위해 DefaultEngine.ini 파일에서 LogNetPlayerMovement을 VeryVerbose로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/125.ModifyABCharacterPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/126.ModifyABCharacterPlayer.cpp2.png">

ABCharacterPlayer 클래스의 cpp 파일에 구현한 이동 로직 ShoulderMove와 QuaterMove에 공격이 불가능 할 때(bCanattack이 false일 때) 움직이지 못하도록 로직을 추가한다.
