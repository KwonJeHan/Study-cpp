# 언리얼 C++ 학습 정리

**2025/04/24 [포텐업] 게임 개발자 양성 과정**

---

## 게임 데이터 관리

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/225.CreateCharacterStat.csv.png">

게임 데이터로 관리할 캐릭터 스탯 정보를 기록한 csv 파일을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/226.CreateABCharacterStat.h.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/227.ImplementABCharacterStat.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/228.ImplementABCharacterStat.h2.png">

데이터 테이블 기반으로 사용할 ABCharacterStat 헤더 파일을 생성하고 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/229.CreateDataTable.png">

위에서 생성한 ABCharacterStat 파일을 기반으로 데이터 테이블 ABCharacterStatTable을 생성한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/230.ReimportCharacterStat.csv.png">

초기에 만들었던 csv 파일을 Reimport한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/231.CreateABGameSingletonCPPClass.png">

데이터 테이블 애셋을 사용하기 위해 게임 싱글톤으로 만들 Object C++ 클래스를 생성한다. (굳이 싱글톤으로 할 필요는 없다.)

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/232.ImplementABGameSingleton.h.png">

헤더 파일에 싱글톤 구현을 하고 Getter와 변수를 정의한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/233.ImplementABGameSingleton.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/234.ImplementABGameSingleton.cpp2.png">

데이터 테이블을 애셋을 로드하고 데이터 테이블의 값을 관리하기 위한 로직을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/235.SetABGameSingletonToGameSingleton.png">

엔진의 프로젝트 세팅에서 Game Singleton Class를 ABGameSingleton으로 지정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/236.ModifyABCharacterAssetComponent.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/237.ModifyABCharacterAssetComponent.h2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/238.ModifyABCharacterAssetComponent.h3.png">

캐릭터 레벨을 적용시키기 위한 로직을  ABCharacterAssetComponent 헤더 파일에 선언하고 기존에 구현했던 코드들도 그에 따라 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/239.ModifyABCharacterAssetComponent.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/240.ModifyABCharacterAssetComponent.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/241.ModifyABCharacterAssetComponent.cpp3.png">

헤더 파일의 변경된 코드 내용에 맞춰 로직을 수정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/242.ModifyABCharacterBase.h.png">

캐릭터에 레벨과 관련된 스탯을 설정하기 위해 ABCharacterBase 헤더 파일에 Getter와 Setter를 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/243.ModifyABCharacterBase.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/244.ModifyABCharacterBase.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/245.ModifyABCharacterBase.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/246.ModifyABCharacterBase.cpp4.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/247.ModifyABCharacterBase.cpp5.png">

변경된 코드 내용에 맞춰 내용을 변경하고 기존에 하드 코딩으로 설정했던 값들을 모두 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/248.ModifyABCharacterBase.cpp6.png">

무기를 획득했을 때 플레이어가 추가적인 스탯을 지니도록 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/249.ModifyABCharacterBase.cpp7.png">

헤더 파일에서 선언한 Getter와 Setter를 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/250.ModifyABStageGimmick.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/251.ModifyABStageGimmick.h2.png">

스테이지 진행도에 따른 스탯 변화를 구현하기 위해 ABStageGimmick 클래스의 헤더 파일에 Stat Section을 선언한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/252.ModifyABStageGimmick.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/253.ModifyABStageGimmick.cpp2.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/254.ModifyABStageGimmick.cpp3.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/255.ModifyABStageGimmick.cpp4.png">

기존에 구현했던 상자, NPC 생성 코드에 지연 생성 로직을 적용한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/256.ModifyABItemBox.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/257.ModifyABItemBox.cpp2.png">

ABItemBox 클래스의 cpp파일 내용도 수정하는데 해당 코드는 지연 생성 로직을 적욜할 것 없이 코드 위치만 변경해도 되기 때문에 위치를 변경한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/258.ModifyABWeaponItemData.h.png">

무기 아이템이 플레이어 캐릭터에게 제공할 부가 스탯 데이터를 설정하기 위해 내용을 정의한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/259.SetStatABIW_WeaponDataAsset.png">

정의한 내용이 데이터 애셋에 제대로 적용됐는지 확인하고 수치를 조정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/260.CreateDefaultArenaBattle.ini.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/261.ModifyABCharacterNonPlayer.h1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/262.ModifyABCharacterNonPlayer.h2.png">

INI 파일을 활용해 NPC 캐릭터가 생성될 때마다 랜덤으로 메시가 선택되어 생성되도록 하기 위해 DefaultArenaBattle.ini 파일을 생성하고 ABCharacterNonPlayer 헤더 파일을 구현한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/263.ModifyABCharacterNonPlayer.cpp1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP/264.ModifyABCharacterNonPlayer.cpp2.png">

구현한 헤더 파일을 토대로 cpp파일에 로직을 구현한다.
