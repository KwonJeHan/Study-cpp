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
