# 언리얼 C++ 학습 정리

**2025/04/21 [포텐업] 게임 개발자 양성 과정**

---

## 아이템 시스템

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/168.CreateABItemDataCPPClass.png">

PrimaryDataAsset을 부모로 아이템들의 기본적인 정보를 가지게 될 C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/169.ImplementABItemData.h.png">

아이템의 종류를 열거형으로 생성하고 아이템 타입을 지정할 열거형 변수를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/170.CreateABWeaponItemDataCPPClass.png">

위에서 구현한 ABItemData를 부모로 무기 정보를 가지게 될 C++ 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/171.ImplementABWeaponItemData.h.png">

무기에 대한 스켈레탈 메시를 지정하기 위한 변수를 선언한다. (아이템이 수천, 수만개일 경우 TObjectPtr로 미리 애셋을 불러오는 것보다 TSoftObjectPtr로 상황에 따라 불러오도록 구현하는 것이 애셋 관리 측면의 설계에 좋다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/172.CreateABIW_WeaponDataAsset.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/173.CreateOtherDataAsset.png">

ABWeaponItemData를 인스턴스로 사용하는 데이터 애셋과 테스트용으로 ABItemData를 인스턴스로 사용하는 데이터 애셋들을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/174.SetDataAsset.png">

데이터 애셋의 세부 사항을 설정한다. (ABItemData를 인스턴스로 사용하는 데이터 애셋의 경우 Type 카테고리만 존재한다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/175.CreateABCharacterItemInterfaceCPPClass.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/176.ImplementABCharacterItemInterface.h.png">

아이템 획득 시 이벤트를 의존성을 분리하여 구현하기 위해 해당 이벤트를 선언할 인터페이스 클래스를 만들고 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/167.CreateABItemBoxCPPClass.png">

Actor 클래스를 부모로 캐릭터와 상호작용하게 될 아이템 박스 클래스를 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/177.ImplementABItemBox.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/178.ImplementABItemBox.h2.png">

아이템 박스의 오브젝트, 리소스, 이벤트 등을 설정하기 위해 헤더 파일의 내용을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/179.ImplementABItemBox.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/180.ImplementABItemBox.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/181.ImplementABItemBox.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/182.ImplementABItemBox.cpp4.png">

cpp파일에 위에서 구현한 헤더 파일의 내용을 토대로 필요한 리소스와 이벤트 등을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/183.SetItemDataAssetToItemBox.png">

구현한 아이템 박스 C++ 클래스를 맵에 배치하고 사용할 데이터 애셋을 각각 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/184.ModifyABCharacterBase.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/185.ModifyABCharacterBase.h2.png">

캐릭터의 아이템 종류 별 획득 처리를 위해 캐릭터 베이스 C++ 클래스 헤더 파일의 내용을 수정 및 추가한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/186.ModifyABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/187.ModifyABCharacterBase.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/188.ModifyABCharacterBase.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/189.ModifyABCharacterBase.cpp4.png">

헤더 파일에서 수정 및 추가한 내용에 따라 cpp 파일의 내용을 구현한다.
