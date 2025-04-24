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

