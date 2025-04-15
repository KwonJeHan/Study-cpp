# 언리얼 C++ 학습 정리

**2025/04/15 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 콤보 액션

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/79.CreateAnimationMontage.png">

공격 콤보 액션에 사용할 AnimationMontage를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/80.CreatePrimaryDataAssetCPP.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/81.SetDataAssetCppHeader.png">

콤보 액션 제어에 사용할 변수를 정의하기 위해 C++클래스를 생성하고 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/82.CreateDataAsset.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/82.SetDataAsset.png">

만들어놓은 C++ 클래스를 기반으로 언리얼 에디터에서 DataAsset을 만들고 수치를 조정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/83.ModifyAnimationBlueprint.png">

애니메이션 블루프린트의 내용을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/84.CreateIA_Attack.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/85.SetIA_Attack.png">

공격 액션 입력을 위한 InputAction(IA_Attack)을 생성하고 트리거를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/86.SetIMC1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/87.SetIMC2.png">

생성한 IA_Attack을 InputMappingContext에 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/88.ModifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/89.ModifyABCharacterBase.h2.png">

ABCharacterBase 헤더 파일에 공격 콤보 액션을 처리할 때 사용할 함수와 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/90.SetABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/91.SetABCharacterBase.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/92.SetABCharacterBase.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/93.SetABCharacterBase.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/94.SetABCharacterBase.cpp5.png">

선언한 함수 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/95.ModifyABCharacterPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/96.ModifyABCharacterPlayer.h2.png">

CharacterPlayer 헤더 파일에 공격 키를 바인딩할 함수와 InputAction을 설정할 오브젝트를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/97.ModifyABCharacterPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/98.ModifyABCharacterPlayer.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/99.ModifyABCharacterPlayer.cpp3.png">

 InputAction을 설정하고 공격 키를 바인딩한 후 함수의 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/100.SetABCharacterBlueprint.png">

에디터에서 캐릭터 블루프린트를 열어 AnimationMontage와 DataAsset을 설정한다.
