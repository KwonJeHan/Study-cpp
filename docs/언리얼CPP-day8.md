# 언리얼 C++ 학습 정리

**2025/04/11 [포텐업] 게임 개발자 양성 과정**

---

## 캐릭터 컨트롤 설정

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/30.AddABCharacterControlDataHeader1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/31.AddABCharacterControlDataHeader2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/32.AddABCharacterControlDataHeader3.png">

캐릭터 카메라 데이터 애셋을 구현하기 위해 ABCharacterControlData C++ 클래스를 만들고 변수를 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/33.MakeMiscellaneousDataAsset.png">

만든 C++ 클래스를 기반으로 에디터에서 Miscellaneous -> DataAsset을 만든다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/34.ModifyIA_Action.png">

기존에 생성했던 InputAction들을 수정해서 재생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/35.ModifyIMC1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/36.ModifyIMC2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/37.ModifyIMC3.png">

수정한 InputAction에 따라 InputMappingcontext도 재생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/38.AddEnumInABCharacterBaseHeader.png">

ABCharacterBase 헤더 파일에 사용할 Enum(열거형)을 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/39.AddFunctionAndTMapInABCharacterBaseHeader.png">

이어서 ABCharacterPlayer에서 사용할 가상함수와 TMap 오브젝트를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/40.ImplementFunctionAndModifyConstructor.png">

생성자에 앞에서 생성한 DataAsset을 리소스로 하는 오브젝트를 선언하고 토대가 될 가상함수도 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/41.AddFunctionInABCharacterPlayerHeader.png">

ABCharacterPlayer 헤더 파일에 플레이어 시점 변경에 필요한 로직 함수들을 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/42.ChangeInputSectionInABCharacterPlayerHeader.png">

InputSection에 생성해놨던 InputActionObject들도 위의 내용에 따라 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/43.IncludeABCharacterControlData.h.png">

ABCharacterControlData 헤더를 import 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/44.SetInputObjectResource.png">

InputAction 리소스들을 각 Object에 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/45.SetCurrentCharacterControlType.png">

게임 초기 시점은 Quarter 시점으로 설정해 놓는다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/46.BindInputAction.png">

오버라이딩한 가상함수에서 오브젝트들을 모두 Binding해준다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/47.ImplementQuarterMove.png">

QuarterMove 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/48.ImplementShoulderMove.png">

ShoulderMove 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/49.ImplementShoulderLook.png">

ShoulderLook 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/50.ImplementChangeCharacterControl.png">

캐릭터 시점을 변경하는 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/51.ImplementSetCharacterControlData.png">

시점 관련 값을 설정하는데 사용할 SetCharacterControlData 로직을 작성한다. 

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/52.ImplementSetCharacterControl.png">

캐릭터 컨트롤 타입에 대응하는 데이터 애셋과 해당 애셋을 사용해 관련된 값을 설정하고 최종 MappingContext를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/53.SetCharacterControlInBeginPlay.png">

BeginPlay 부분에서 캐릭터의 컨트롤 타입 값을 설정해준다.
