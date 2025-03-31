# 객체 지향 프로그래밍

**2025/03/31 [포텐업] 게임 개발자 양성 과정**

---

## 기초 설정

### 언리얼 c++ 프로젝트 만드는 과정

**비주얼 스튜디오 설치 버전**

visual studio installer에서 수정->개별 구성 요소에서 MSVC v143 - VS 2022 C++ x64/x86 빌드 도구 (v14.38-17.8) 체크 후 설치하고 영어 언어팩도 설치한다.

파일 탐색기에서 프로젝트 폴더를 열어 Intermidiate 폴더와 솔루션 파일 삭제 후 uproject 파일 Shift+우클릭 해서 Generate Visual Studio project files 선택하고 다시 솔루션 파일 열어서 빌드

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UnrealInstallerSetting.png">



**비주얼 스튜디오 개인 설정**

DebugGame Editor 부분 우클릭 후 customize -> commands -> Toolbar -> Standard -> Solution Configuration 선택 후 Modify Selection 하고 Width 수치를 200으로 설정

Output 툴바는 고정으로 설정



에디터와 비주얼 스튜디오 모두 언어는 영어로 설정한다.

일단 에디터의 맵&모드에서 맵은 모두 지우기로 삭제해준다.





프로젝트 파일에서 Source 폴더가 핵심, 해당 폴더에서 파일을 지우고 Generate Visual Studio project files 시 파일이 지워짐

마찬가지로 파일을 추가하고 같은 작업 시 파일이 생김



헤더 파일 변경 시 켜져 있던 언리얼 에디터를 끄고 프로세스가 완전히 꺼질 때까지 기다린 후 솔루션에서 다시 디버깅 없이 시작으로 다시 컴파일하여 에디터를 연다.

언리얼 에디터 우하단 조각모음 같이 생긴 아이콘이 livecoding이다.

소스 파일에만 변경이 발생 시 에디터가 켜진 상태에서 그냥 빌드를 하면 오류가 발생한다. 그냥 빌드가 아니라 단축키 Ctrl+Alt+F11을 해서 livecoding으로 컴파일 해야 오류 없이 작동한다.



## 언리얼 C++ 코딩 표준

프로그래밍을 작성하는데 지켜야 하는 프로그래밍 이름 규칙, 작성 방법 등을 지정한 가이드 라인으로 코딩 스타일, 코딩 컨벤션이라고도 한다.



**절대적으로 좋은 코딩 표준이란 없다.**

* 이전에 내가 사용한 코딩 표준이 항상 옳은 것은 아니다.

**중요한 것은 코딩 표준을 정하고 잘 따르는 것이다.**

* 이미 프로젝트에 코딩 표준이 있다면 그대로 따라야 한다.

프로젝트의 모든 코드는 한 사람이 만든 것처럼 보여야 한다. 또한 좋은 소프트웨어 회사들은 자신만의 코딩 표준이 있다.

#### 언리얼 엔진은 자체적으로 코딩 표준을 정했기 때문에 기존 C++ 코딩 방법을 버리고 언리얼 엔진 코딩 표준을 따라야 한다.



**언리얼 엔진 코딩 표준 링크**

https://dev.epicgames.com/documentation/ko-kr/unreal-engine/epic-cplusplus-coding-standard-for-unreal-engine?application_version=5.5



## 언리얼 C++ 기본 타입

**게임 제작의 특징**

* 데이터 정보가 명확해야 한다.
* 단일 컴퓨터에서 최대 퍼포먼스를 뽑아내야 한다.
* 네트워크 상에서 데이터 통신이 효율적이고 안정적이어야 한다.

#### 데이터 타입의 애매 모호함은 게임 개발 시 문제를 일으킬 수 있다.



**int 타입과 크기**

언리얼은 int를 사용하지 않고 int32를 사용한다.



**언리얼 엔진에서 사용하는 기본 타입**

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UnrealStandardType">



**bool 타입 선언**

bool은 크기가 명확하지 않다.

헤더에는 가급적 bool 대신 uint8 타입을 사용하되 Bit Field 오퍼레이터를 사용한다.

일반 uint8과의 구분을 위해 b접두사를 사용한다.

Cpp 로직에선 자유롭게 bool을 사용한다.



**캐릭터 인코딩 링크**

https://dev.epicgames.com/documentation/ko-kr/unreal-engine/character-encoding-in-unreal-engine



**TCHAR와 FString**

유니코드를 사용해 문자열 처리를 통일한다.

* 2Byte로 사이즈가 균일한 UTF-16을 사용하며 유니코드를 위한 언리얼 표준 캐릭터 타입은 TCHAR이다.

문자열은 언제나 TEXT 매크로를 사용해 지정하며 문자열을 다루는 클래스로 FString을 제공한다.



솔루션에서 툴바의 file -> Save~~as -> save 드롭다운 -> save with encoding -> Unicode (UTF-8 with signature) - Code Page 65001으로 설정 시 언리얼 에디터에서 한글 출력이 제대로 나온다.



**FName**

에셋 관리를 위해 사용되는 문자열 체계

* 대소문자 구분 없음
* 한번 선언 시 바꿀 수 없음
* 가볍고 빠름
* 문자를 표현하는 용도가 아닌 에셋 키를 지정하는 용도로 사용한다. 빌드 시 해시값으로 변환된다.



**FText**

다국어 지원을 위한 문자열 관리 체계

* 일종의 키로 작용
* 별도의 문자열 테이블 정보가 추가로 요구된다.
* 게임 빌드 시 자동으로 다양한 국가별 언어로 변환됨
