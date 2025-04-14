# 언리얼 C++ 학습 정리

**2025/04/08 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 애니메이션 설정

로코모션(Locomotion) -> 로봇

- 정지/이동

애니메이션의 경우 블루프린트의 사용이 필수적이다.

이벤트 그래프 -> 블루프린트, CPP 모두 가능

애님 그래프 -> 블루프린트 전용

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/54.ImportAsset1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/55.ImportAsset2.png">

애니메이션 설정을 위해 필요한 애셋을 Import 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/56.ReCreateCharacterAndGameMode.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/57.ModifyWorldSetting.png">

캐릭터 블루프린트와 게임 모드를 생성하고 캐릭터 메시의 스켈레탈 메시도 설정한다. 그리고 월드 세팅의 설정도 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/58.CreateAnimationBlueprint.png">

사용할 스켈레톤과 AnimInstance를 선택하고 애니메이션 블루프린트를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/60.WriteABAnimInstance.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/61.WriteABAnimInstance.h2.png">

생성한 C++ 클래스의 헤더 파일을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/62.WriteABAnimInstance.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/63.WriteABAnimInstance.cpp2.png">

생성한 C++ 클래스의 cpp 파일을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/59.CreateAnimInstanceCPP.png">

애니메이션 블루프린트의 부모 클래스가 될 AnimInstance C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/64.CreateBlendSpace1D.png">

애니메이션 설정에 사용할 BlendSpace를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/65.MakeAnimationBlueprint1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/66.MakeAnimationBlueprint2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/67.MakeAnimationBlueprint3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/68.MakeAnimationBlueprint4.png">

애니메이션 블루프린트의 기초 틀을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/72.MakeIdleState.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/69.MakeIdleWalkRunState.png">

Idel 스테이트의 애니메이션을 설정하고 생성해놓은 BlendSpace를 사용해 IdleWalkRun 스테이트를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/70.MakeIdleToWlakRun.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/71.MakeWlakRunToIdle.png">

각 스테이트로 이어지는 트랜지션 로직을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/73.ModifyAnimationBlueprint.png">

점프를 구현하기 위해 애니메이션 블루프린트의 내용을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/74.SetAlias1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/75.SetAlias2.png">

생성한 Alias의 디테일을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/76.MakeJumpToFalling.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/78.MakeLandToLocomotion.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/77.MakeLandState.png">

동일하게 각 스테이트로 이어지는 트랜지션 로직을 설정한다.

WarriorLand 애니메이션의 경우 그냥 배치하는 것이 아닌 Idle 상태와 Additive를 통해 더 자연스러운 애니메이션을 연출할 수 있다.

---

