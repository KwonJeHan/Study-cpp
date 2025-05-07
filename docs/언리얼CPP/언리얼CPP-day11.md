# 언리얼 C++ 학습 정리

**2025/04/17 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 공격 판정

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/101.CreateCollisionProfile1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/102.CreateCollisionProfile2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/103.CreateCollisionProfile3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/104.CreateCollisionProfile4.png">

프로젝트 세팅에서 공격 판정을 위한 CollisionProfile을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/108.CreateABAnimationAttackInterfaceCPPClass.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/109.ImplementABAnimationAttackInterface.h.png">

인터페이스 C++ 클래스를 만들고 AttackHitCheck 함수를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/105.CreateAnimNotifyCPPClass.png">

애니메이션 몽타주에서 사용할 노티파이를 위해 AnimNotify C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/106.ImplementAnimNotify.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/107.ImplementAnimNotify.cpp.png">

애니메이션 노티파이가 발생할 때마다 공격 판정을 체크하기 위해 함수를 만들고 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/110.AddNotifyToAnimationMontage.png">

애니메이션 몽타주의 필요한 시점에 생성해놓은 애니메이션 노티파이를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/111.CreateABCollision.hToUseMacro.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/112.ImplementABCollision.h.png">

매크로 구현 용도로 사용할 C++클래스를 에디터 툴에서 생성하지 않고 파일 탐색기 내에서 직접 생성하고 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/113.NotifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/114.NotifyABCharacterBase.h2.png">

공격을 감지하고 대미지 받았을 때의 이벤트를 위한 함수를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/115.NotifyABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/116.NotifyABCharacterBase.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/117.NotifyABCharacterBase.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/118.NotifyABCharacterBase.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/119.NotifyABCharacterBase.cpp5.png">

추가한 함수들의 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/120.CreateABCharacterNonPlayerCPPClass.png">

공격 판정 체크 테스트를 위해 ABCharacterBase를 부모로 하는 ABCharacterNonePlayer를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/121.ModifyABCharacterBase.h.png">

ABCharacterBase에서 콜리전 설정설정을 하고 모든 캐릭터에 콤보 공격 기능을 기본으로 사용하기 위해 콤보 액션 몬타주 애셋과 콤보 액션 데이터 애셋을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/122.SetABCharacterNonPlayer.png">

에디터에 ABCharacterNonPlayer를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/123.AddDeadSectionToABCharacterBase.h1.png">

ABCharacterBase 헤더에 죽음 상 설정과 죽음 애니메이션 재생을 위한 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/124.AddDeadSectionToABCharacterBase.h2.png">

죽음 몽타주 애셋 설정을 위한 오브젝트와 죽음 이벤트에 사용할 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/125.CreateDeadMontageAM_Dead.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/126.SetBlendOption.png">

새로운 애니메이션 몽타주 슬롯 DeadSlot을 만들고 Dead 애니메이션을 배치해 죽음 애니메이션 몽타주를 생성한다. 이때 Blend Option에서 Enable Auto 옵션을 해제해야 죽은 캐릭터가 다시 일어나지 않는다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/127.AddDeadSlotToAnimationBlueprint.png">

애니메이션 블루프린트에 DeadSlot을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/128.SetDeadMontageAssetABCharacterBase.cpp.png">

생성한 죽음 애니메이션 몽타주 애셋을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/129.ImplementFunctionABCharacterBase.cpp.png">

선언한 죽음 이벤트를 위한 함수를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/130.ModifyFunctionABCharacterBase.cpp.png">

테스트를 위해 함수를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/131.ImplementABCharacterNonPlayer.h.png">

생성해놨던 ABCharacterNonPlayer 헤더에 죽음 상태 설정 함수를 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/132.ImplementABCharacterNonPlayer.cpp.png">

오버라이드한 함수를 구현한다. (죽은 후 DeadEventDelayTime 이후 사라지도록 구현)
