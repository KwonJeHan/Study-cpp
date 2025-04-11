# 언리얼 C++ 학습 정리

**2025/04/10 [포텐업] 게임 개발자 양성 과정**

---

## 언리얼 엔진 게임 제작 기초

#### 게임 콘텐츠의 구조

게임 제작을 위해 언리얼 엔진은 자체적으로 설계한 프레임 웍을 제공한다. 이를 **게임플레이 프레임웍**이라고 부르며 줄여서 **게임 프레임웍**이라고 한다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/GameFrameWork.png">



* **월드(World)**

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/World.png">



* **게임 모드(Game Mode)**

게임 규칙을 지정하고 게임을 판정하는 최고 관리자 액터로 형태가 없으며 언리얼 엔진에서 하나의 게임에는 반드시 하나의 게임모드만 존재한다. 또한 입장할 사용자의 규격을 지정할 수 있다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/GameMode.png">



* **기믹(Gimmick)**

게임 진행을 위한 이벤트를 발생시키는 사물 액터

주로 이벤트 발생을 위한 충돌 영역을 설정하는데, 이를 트리거(Trigger)라고 한다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Gimmick.png">



* **플레이어(Player)**

게임에 입장한 사용자 액터로 형태가 없다.

게임 모드의 로그인을 통해 사용자가 게임 월드에 입장하면 플레이어가 생성되며 사용자와의 최종 커뮤니케이션을 담당한다. (입력 장치의 해석, 화면 장치로의 출력)

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Player.png">



* **폰(Pawn)**

무형의 액터인 플레이어가 빙의해 조종하는 액터로 인간형 폰을 별도로 캐릭터라고 지칭한다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Pawn.png">



## 캐릭터와 입력 시스템

### 블루프린트 캐릭터 CPP 캐릭터로 구현

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/1.includepath.png">

빌드 시스템에 IncludePath를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/2.SetABBPlayerController.png">

GameMode에서 PlayerController 클래스를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/4.SetABBPlayerController2(NoInclude).png">

PlayerController 클래스에 만든 PlayerController를 참조로 받아 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/3.DefaultPawnClass.png">

cpp에서 애셋화된 클래스를 참조받을 때 뒤에 _C를 붙여주는 것이 중요하다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/5.BeginPlayOverride.png">

PlayerController에 BeginPlay 이벤트를 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/6.BeginPlay_FInputModeGameOnly.png">

FInputModeGameOnly로 게임이 시작했을 때 마우스 포인터가 보이지 않고 바로 캐릭터를 조종할 수 있게 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/7.AddComponent_ABFountain.h.png">

ABFountain에 UPROPERTY로 컴포넌트를 추가한다

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/8.AddComponent_ABFountain.cpp.png">

추가한 컴포넌트들을 이름 설정 및 생성, 루트 컴포넌트 배치 및 계층 구조를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/9.SearchFountainAsset.png">

컴포넌트들에 추가할 애셋을 검색하고 해당 애셋을 각 컴포넌트에 할당한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/10.WaterLocation.png">

SetRelativeLocation으로 컴포넌트의 트랜스폼을 설정해 줄 수 있다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/11.SetCPPCharacterClassInGameMode.png">

DefaultPawnClass에 생성해둔 CPP 기반 Character 클래스를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/12.SetCPPCharacterResourceAndAnimBlueprint.png">

설정한 DefaultPawnClass에 리소스와 애니메이션 블루프린트를 할당한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/13.SetCPPCharacterComponentLocationAndRotator.png">

캐릭터 컴포넌트의 캡슐 컴포넌트 크기와 Location,Rotation 값을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/14.AddSpringArmAndCameraComponent.png">

캐릭터 컴포넌트에 SpringArm과 Camera 오브젝트를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/15.SetSpringArmAndCameraComponent1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/16.SetSpringArmAndCameraComponent2.png">

Header 파일을 Including 해주고 계층 구조 등 여러 옵션을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/17.IncludingPathEnhancedInput.png">

빌드 시스템에 EnhancedInput Path를 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/18.AddInputMapping.png">

MappingContext와 InputAction을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/19.IncludeHeader.png">

MappingContext와 InputAction 설정에 필요한 Header를 Includin 해준다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/20.SetInputMapping.png">

MappingContext와 InputAction 리소스를 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/21.AddSubSystemMappingContextOnBeginPlay.png">

BeginPlay 이벤트에 SubSystemMappingContext를 생성하는 로직을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/22.OverrideSetupPlayerInputComponent.png">

SetupPlayerInputComponent를 오버라이드한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/23.AddInputActionValue.h.png">

InputAction에 값을 할당한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/24.AddMoveAndLook.png">

Move와 Look 함수를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/25.BindingMoveAndLookAndJJump.png">

InputAction을 각 Action에 Binding 한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/26.SetMoveAndLookFuction.png">

Move와 Look 함수를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/27.SetMovementAndbUseControllerRotation.png">

Movement와 bUseControllerRotation을 설정해 움직임에 어색한 점을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/28.IA_MoveAddModifiers.png">

언리얼 에디터에서 IA_Move에 Moditiers에 Swizzle->YXZ를 추가해 C++ 클래스에서 사용하는 축과 맞춘다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/29.ChangeAddMoveInputAxis.png">

축을 동일하게 맞추었으므로 C++ 클래스에서 설정했던 축도 바꾼다.
