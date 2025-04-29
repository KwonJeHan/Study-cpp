# 언리얼 C++ 학습 정리

**2025/04/29 [포텐업] 게임 개발자 양성 과정**

---

## 헤드업디스플레이(HUD)의 구현

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/329.CreateUserWidgetBlueprint(WBP_ABHUD).png.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/330.SetWBP_ABHUD.png">

UserWidget을 기반으로 하는 블루프린트 클래스 WBP_ABHUD를 생성하고 위젯을 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/331.CreateUserWidgetCPPClass(ABHUDWidget).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/332.ModifyParentClassToABHUDWidget.png">

유저 위젯을 상속받는 ABHUDWidget C++ 클래스를 생성하고 위에서 만든 WBP_ABHUD의 부모 클래스로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/333.ModifyABPlayerController.h.png">

생성한 위젯을 화면에 추가해 UI를 볼 수 있도록 하기 위해 ABPlayerController 헤더 파일에 위젯의 클래스 정보와 객체 정보를 저장할 클래스와 오브젝트를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/334.ModifyABPlayerController.cpp.png">

헤더 파일에서 선언한 클래스와 오브젝트에 애셋을 설정하고 화면에 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/335.CreateUserWidgetBlueprint(WBP_CharacterStat).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/336.SetWBP_CharacterStat.png">

캐릭터 스탯에 관한 정보를 표시하기 위해 UserWidget 블루프린트 클래스 BP_CharacterStat을 생성하고 위젯을 배치 및 세부사항을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/337.ModifyWBP_ABHUD.png">

ABHUD 블루프린트에 위에서 생성한 CharacterStat 블루프린트를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/362.초기화프로세스정리.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/338.ModifyABCharacterStatComponent.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/339.ModifyABCharacterStatComponent.cpp.png">

기존에 BeginPlay에서 초기화하던 스탯 데이터를 더 빠른 시점에 초기화 시킬 수 있는 InitializeComponent로 변경해 더 안전하게 초기화한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/340.ImplementABHUDWidget.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/341.ImplementABHUDWidget.cpp.png">

ABHUDWidget은 NativeConstruct를 사용해 스탯 데이터가 변경될 때 자동으로 처리할 수 있도록 설계

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/342.CreateUserWidgetCPPClass(ABCharacterStatWidget).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/343.ModifyParentClassToABCharacterStatWidget.png">

UserWidget 클래스를 상속받는 ABCharacterStatWidget C++ 클래스를 생성하고 CharacterStat 블루프린트의 부모로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/344.ImplementABCharacterStatWidget.h.png">

바로 구현할 내용은 아니지만 ABCharacterStatWidget 헤더 파일에 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/345.CreateInterfaceCPPClass(ABCharacterHUDInterface).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/346.ImplementABCharacterHUDInterface.h.png">

캐릭터 HUD 설정에 사용할 Interface C++ 클래스를 생성하고 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/347.ModifyABHUDWidget.h.png">

ABHUDWidget 헤더 파일에 필요한 함수와 오브젝트를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/348.ModifyABHUDWidget.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/349.ModifyABHUDWidget.cpp2.png">

선언만 해두고 구현하지 않았던 NativeConstruct 함수의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/350.ModifyABCharacterPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/351.ModifyABCharacterPlayer.h2.png">

생성한 HUDInterface 클래스를 상속하고 함수를 구현하기 위해 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/352.ModifyABCharacterPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/353.ModifyABCharacterPlayer.cpp2.png">

헤더 파일에 선언한 내용을 토대로 함수의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/354.ModifyABCharacterStatComponent.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/355.ModifyABCharacterStatComponent.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/356.ModifyABCharacterStatComponent.h3.png">

델리게이트를 사용하기 위해 델리게이트를 선언하고 사용할 함수 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/357.ModifyABCharacterStatComponent.cpp.png">

헤더 파일에 구현한 내용을 토대로 기존에 구현했던 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/358.ModifyABCharacterStatWidget.h.png">

선언만 해두고 아직 구현하지 않고 있던 ABCharacterStatWidget 헤더 파일의 내용을 추가해 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/359.ImplementABCharacterStatWidget.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/360.ImplementABCharacterStatWidget.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/361.ImplementABCharacterStatWidget.cpp3.png">

리플렉션 기능을 사용해 CharacterStat 위젯의 텍스트 블록 내용을 변경하는 로직을 구현한다.

---

## 게임 플로우 다듬기

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/363.ModifyABCharacterNonPlayer.cpp.png">

NPC 캐릭터가 죽었음에도 5초 동안 살아서 행동하는 현상을 막기 위해  ABCharacterNonPlayer cpp 파일에서 SetDead 함수 실행 시 AI 명령의 전달을 중지하는 로직을 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/364.ModifyABCharacterPlayer.h.png">

플레이어 캐릭터 역시 죽어서도 입력 가능하던 현상을 수정하기 위해 ABCharacterPlayer 헤더 파일에 SetDead 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/365.ModifyABCharacterPlayer.cpp.png">

헤더 파일에서 선언한 SetDead 함수의 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/366.ModifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/367.ModifyABCharacterBase.h2.png">

캐릭터의 이동 속도인 MovementSpeed를 설정하기 위해 ABCharacterBase 헤더 파일에 ApplyStat 함수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/368.ModifyABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/369.ModifyABCharacterBase.cpp2.png">

cpp 파일에서 ApplyStat 함수 로직을 구현하고 스탯 변경 시 발행되는 이벤트에 함수를 등록한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/370.CreateABItemDataCPPClass(ABPotionItemData,ABScrollItemData).png">

현재 무기 아이템 데이터만 구현이 되어있는데 다른 종류의 아이템들도 구현하기 위해 ABItemData 클래스를 상속받는 ABPotionItemData와 ABScrollItemData C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/371.CreateABItems.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/372.ImplementABItems.h.png">

아이템 종류가 많아졌기 때문에 헤더 파일 Include의 편의성을 위해 따로 ABItems 헤더 파일을 생성하고 내용을 작성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/373.ModifyABWeaponItemData.h.png">

생성자를 구현하지 않았던 ABWeaponItemData에 생성자를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/374.ModifyABWeaponItemData.cpp.png">

cpp 파일의 생성자에서 Weapon 아이템 타입을 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/375.ImplementABPotionItemData.h.png">

생성해놓은 ABPotionItemData 헤더 파일에도 생성자와 Hp 회복에 사용할 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/376.ImplementABPotionItemData.cpp.png">

ABWeaponItemData와 마찬가지로 cpp 파일에 타입을 설정하는데 Potion으로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/377.ImplementABScrollItemData.h.png">

ABScrollItemData 역시 헤더 파일에 생성자와 캐릭터의 기본 스탯 데이터를 가져올 BaseStat 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/378.ImplementABScrollItemData.cpp.png">

ABScrollItemData 역시 cpp 파일에 타입을 Scroll로 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/379.ModifyABCharacterStatComponent.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/380.ModifyABCharacterStatComponent.h2.png">

ABCharacterStatComponent 헤더 파일에서 Potion 사용 시dhk Scroll 사용 시 캐릭터 스탯 변화 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/381.ModifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/382.ModifyABCharacterBase.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/383.ModifyABCharacterBase.h3.png">

Include 했던 헤더 파일을 ABItems 헤더로 변경하고 포션 획득 시와 스크롤 획득 시 수집 처리를 위한 함수 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/384.CreateABItemPotionDataAsset.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/385.CreateABItemScrollDataAsset.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/386.SetABItemsDataAsset.png">

구현한 Potion과 Scroll C++ 클래스를 기반으로 하는 데이터 애셋을 여러 종류 만들고 각각 원하는 기능을 데이터 애셋 수치 조정을 통해 구현한다.

