# 언리얼 멀티 C++ 학습 정리

**2025/05/20 [포텐업] 게임 개발자 양성 과정**

---

## 물리 움직임 리플리케이션

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/127.CreateBlueprintClass1(MovePlatform).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/128.CreateBlueprintClass2(MovePlatform).png">

물리 움직임(Physics Movement)를 실습하기 위해 언리얼 엔진 에디터에서 BP_MovePlatform이라는 움직이는 얇은 큐브 스태틱 메시를 가진 액터 블루프린트 클래스를 만들고 다음과 같이 구현한다. Default 세팅에서 Replication 항목의 Replicate Movement와 Replicates 옵션을 설정해야 클라이언트 상에도 정상적으로 작동한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/129.CreateBlueprintClass1(PhysicsSphere).png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/130.CreateBlueprintClass2(PhysicsSphere).png">

또 다른 물리 움직임 실습을 하기 위한 액터 블루프린트 클래스를 만들고 구현한다. (두 원기둥 위에 얇은 판같은 사각 큐브를 배치하고 그 위에 구를 떨어트리는 형식) Replication 옵션은 이전 실습과 동일하게 설정하고 이외에도 Root라는 이름으로 추가한 스태틱 메시 옵션 중 Physics 항목을 설정해야 하는데 Simulate Physics 옵션을 키고 (해당 블루프린트는 이벤트 그래프에서 따로 설정) Mass를 500정도로 크게 설정한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/131.SetStaticMeshes.png">

맵에 다음과 같이 액터를 배치한다.

---

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/132.SetStaticMeshesOption1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/UECPP_Multi/133.SetStaticMeshesOption2.png">

블루프린트를 제외한 나머지 스태틱 메시 액터들의 옵션을 설정한다. Physics 항목의 Simulate Physics 옵션을 설정하고 Actor 항목의 Static Mesh Replicate Movement 옵션을 설정해야 서버와 클라이언트에서 해당 스태틱 메시의 위치가 동일하게 적용된다.
