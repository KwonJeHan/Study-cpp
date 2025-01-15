# 게임 프로그래밍 실습(콘솔 엔진)



**2025/01/02 목표**

Engine(GameEngine)

* Gameloop

### 게임 루프

현재 프레임 - 이전 프레임 = deltaTime

60FPS -> 1/60초

게임 루프가 빠르게 순환되면 FPS가 높고 게임이 부드럽고 빠르게 움직인다.





**2025/01/03 목표**

Engine(GameEngine)

* Singleton

Actor (물체)

Level/Scene (레벨)

RTTI (RunTime Type Information)

* dynamic_cast

PCH (PreCompiledHeader)

* 컴파일 시간 단축을 위해 사용

DLL (Dynamic Linking Library)



**2025/01/06 목표**

Core.h 헤더 추가

* 메모리 릭 검사 추가

* 메모리 삭제 함수 추가

* 콘솔 출력 함수 Log 추가

RTTI.h 추가

빌드 이벤트 추가



**2025/01/08 목표**

List로 컨테이너 업데이트 및 적용

Vector2 클래스 추가 (위치)

Actor 업데이트 (위치)

Engine -> 콘솔 위치 설정 및 렌더(std::cout)

Engine -> 타겟 프레임 설정

액터 이동 시켜보기(엔진 데모)

DLL/EXE 합치기

커서 안보이게 하기



**2025/01/09 목표**

화면 지우기(Clear)

List 자료구조에 삭제 함수(Erase) 추가

Actor/Level/Engine 클래스에서 액터 제거하는 함수 추가

문자열 흘리기 데모 -> %(모듈러 연산)



**2025/01/13 목표**

업데이트

* 액터 추가 로직 변경

텍스트 스크롤 데모 완성

* 방향키 입력에 따라 흐르는 방향 제어

비행 슈팅 게임 시작

* 플레이어 (좌우로 이동)
* 탄약 (위로 이동)
* 탄약 생성



**2025/01/14 목표**

엔진 업데이트

* 클리어 로직 업데이트
* 버퍼(Buffer) - char*
* DrawableActor 업데이트 - 색상(속성-프로퍼티)

플레이어 로직 업데이트



FlightShootingGame

탄약 생성

* 탄약의 움직임 구현
* float -> int 로직
* deltaTime (프레임 시간)

랜덤 함수 추가

* int / float

적 생성

* 생성 위치는 랜덤 (범위)
* 좌우 이동
  * float -> int
  * deltaTime (프레임 시간)



TextScrollDemo

메뉴 생성



**2025/01/15 목표**

콘솔 엔진 프로그래밍

FlightShootingGame

* Actor의 IsActive 함수 -> isActive && !isExpired 로 조건 변경
* DrawableActor에 Width() Getter 추가
* TestLevel의 Update에서 적 생성 로직을 SpawnEnemy 함수로 분리
* 적 종류 추가
* 플레이어 탄약과 적 비행기 충돌 처리
* 적 탄약과 플레이어 충돌 처리
* DrawableActor에 Intersect 함수 추가
* 적 비행이 탄약 생성
* 문자 만들 때 한자로 변환해보기  - ● ▲ ★ ◆ ♠ ♥

SokobanGame
