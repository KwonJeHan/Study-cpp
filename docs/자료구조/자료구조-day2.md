# 자료구조 학습 정리

**2025/01/07 [포텐업] 게임 개발자 양성 과정**

---

## 선형 자료구조

### 연결 리스트(링크드 리스트)

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/LinkedList.png">

**데이터를 노드라고 하는 곳에 분산해 저장하며 다음 항목을 가리키는 주소도 함께 저장한다.**

노드는 데이터 필드와 링크 필드로 구성

* 데이터 필드 : 리스트의 데이터를 저장
* 링크 필드 : 다른 노드의 주소값을 저장(포인터)

단점 : 검색(탐색)이 느리다.



#### 추상 자료형

**1. 객체 (Object)**

- 같은 타입 요소들의 순차적 모임

**2.연산(Functions)**

- LinkedList CreateList()

  빈 리스트를 생성하고 이를 반환한다.

- Insert(pos, item)

  리스트의 pos 위치에 새로운 요소 item을 삽입한다.

- Delete(pos)

  리스트의 pos 위치에 있는 요소를 삭제한다.

- GetEntry(pos):

  리스트의 pos 위치에 있는 요소를 반환한다.

- Find(item):

  리스트에 요소 item이 있는지를 살핀다.

- Replace(pos, item):

  pos 위치에 있는 요소를 새로운 요소 item으로 바꾼다.

- Size():

  리스트 안의 요소의 개수를 반환한다.

- Display():

  리스트 안의 모든 요소들을 출력한다.



#### 주요 연산

**1. 리스트 생성**

자료가 없고, 가리키는 노드가 없는 빈 노드 Head를 가진 리스트 생성

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/1.LinkedList_Creation.png">

**2. 삽입 연산 (Insert)**

원하는 위치에 노드를 삽입한다

- 리스트가 비어있는 경우 → Head 노드를 추가한 새 노드로 교체한다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/2.LinkedList_Insertion1.png">

- 리스트가 비어있지 않은 경우 → 추가할 위치의 앞뒤 노드의 next 포인터를 적절하게 변경한다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/2.LinkedList_Insertion2.png">

**3. 삭제 연산 (Delete)**

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/3.LinkedList_Deletion.png">

**4. 리스트 순회(Traverse)**

Head 노드에서 시작해 하나 씩 노드를 순회한다

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/4.LinkedList_Traverse.png">

---

### 더블 연결 리스트

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/DoubleNode.png">

**연결 리스트와 유사하지만 다음 항목을 가리키는 주소에 더해 이전 항목을 가리키는 주소도 함께 저장한다.**

* 데이터 필드 : 리스트의 데이터를 저장
* 링크 필드 next : 다른 노드의 주소 값을 저장 (포인터)
* 링크 필드 previous : 다른 노드의 주소 값을 저장 (포인터)



#### 추상 자료형

**1. 객체 (Object)**

- 임의의 접근 방법을 제공하는 같은 타입 요소들의 순차적 모임

**2. 연산(Functions)**

- LinkedList CreateList()

  빈 리스트를 생성하고 이를 반환한다.

- InsertFirst(item)

  리스트의 첫 번째 위치에 새로운 요소 item을 삽입한다.

- InsertLast(item)

  리스트의 마지막 위치에 새로운 요소 item을 삽입한다.

- PopFirst()

  리스트 첫 번째 요소를 반환하고, 리스트에서 이를 삭제한다.

- PopLast()

  리스트 마지막 요소를 반환하고, 리스트에서 이를 삭제한다.

- Find(item):

  리스트에 요소 item이 있는지를 순차적으로 검색하고, 이를 반환한다.

- FindReverse(item)

  리스트에 요소 item이 있는지를 역순으로 검색하고, 이를 반환한다.

- Delete(item)

  리스트에 요소 item이 있는지를 검색하고, 찾으면 이를 삭제한다.

- Size():

  리스트 안의 요소의 개수를 반환한다.

- Display():

  리스트 안의 모든 요소들을 출력한다.



#### 주요 연산

1. 리스트 생성

   자료가 없고, 가르키는 노드가 없는 빈 노드 Head를 가진 리스트 생성

   <img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/3.doublelink.png.png">

2. 삽입 연산 (Insert)

   원하는 위치에 노드를 삽입한다

   <img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/3.insert.png">

3. 삭제 연산 (Delete)

   <img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/3.delete.png">

4. 리스트 순회(Traverse)

- 순차 탐색: first 노드에서 시작해 하나 씩 노드를 순회한다

  <img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/4.serch.png">

- 역순 탐색: last 노드에서 시작해 하나 씩 노드를 거꾸로 순회한다

  <img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/4.reverseserch.png">
