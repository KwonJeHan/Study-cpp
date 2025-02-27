# 알고리즘 학습 정리

**2025/02/17 [포텐업] 게임 개발자 양성 과정**

---

## 탐색 알고리즘

### 너비 우선 탐색 (BFS)

그래프나 트리에서 시작 정점으로부터 인접한 모든 정점들을 우선적으로 방문하는 탐색 알고리즘

두 가지 큐를 사용하여 구현되며 BFS는 주로 최단 경로를 찾거나 그래프의 구조를 파악하는데 사용



#### 너비 우선 탐색의 특징

- 최단 경로를 찾을 수 있다.
- DFS보다 반복문에 의존하기 때문에 스택 오버플로우를 발생시키지 않는다.
- 그래프의 구조를 파악하는 데 유용하다.
- 시간 복잡도는 $O(V+E)$다. ($V$는 정점의 수, $E$는 간선의 수)



### 레드 블랙 트리 (Red-Black Tree)

이진 탐색 트리의 일종으로, 균형 잡힌 이진 탐색 트리를 유지하기 위한 자가 균형 이진 검색 트리다.

보통 이진 탐색 트리는 편향적으로 저장이 되는 경우가 발생할 수 있는데 이를 개선한 자가 균형 트리의 한 종류 이다.

각 노드는 추가적인 색상 정보를 가지고 있어서 트리의 균형을 유지한다.

이러한 특성 때문에 레드-블랙 트리는 검색, 삽입, 삭제 연산에 대해 다음의 시간 복잡도 O(logn)을 보장한다.



#### 레드 블랙 트리의 특징

1. 균형 유지 : 모든 경로에 대해 노드의 개수가 동일한 것은 아니지만, 각 경로에 대해 블랙 노드의 개수는 동일하다.
   * 블랙 노드의 개수를 셀 때 자기 자신은 세지 않는다.
2. 노드 색상 : 각 노드는 레드 또는 블랙 중 하나의 색상을 갖는다.
3. 규칙
   * 노드는 레드 혹은 블잭 중의 하나다.
   * 루트 노드는 블랙이다.
   * 모든 리프 노드(자식 노드가 없는 노드)들(NIL)은 블랙이다. (null노드를 NIL노드로 표기한다.)
   * 레드 노드의 양쪽 자식 노드는 언제끼지나 모두 블랙이다.
   * 어떤 노드에서 자식 NIL노드들 까지 가는 경로들의 블랙 노드의 수는 같다. (이때 자기 자신은 세지(카운트)하지 않는다.)



#### NIL 노드란

* 존재하지 않는다는 것을 의미하는 노드를 NIL 노드라고 한다.
* 자식 노드가 없을 때 자식 노드를  NIL 노드로 표기한다.
* 값이 있는 다른 노드와 동등하게 다룬다.



#### 레드 블랙 트리의 연산

1. **회전 **: 부모-자식 노드의 위치를 서로 바꾸는 연산. 방향에 따라서 우회전(Right-Rotate)과 좌회전(Left-Rotate)로 나뉜다.
2. **삽입** : 이진 탐색 트리에서 삽입한 후에 레드-블랙 트리의 규칙에 맞게 조정한다.
3. **삭제** : 이진 탐색 트리에서 삭제한 후에 레드-블랙 트리의 규칙에 맞게 조정한다.
4. **탐색 **: 이진 탐색 트리와 마찬가지로 특정 값을 찾거나 범위 검색을 수행할 수 있다.



#### 회전

* 우회전 : 왼쪽 자식과 부모의 위치를 교환

X와 Y 교환

```c++
       X		
      /
     Y
    / \
   A   B
```

우회전 전

```c++
     Y
    / \
   A   X
      /
     B
```

우회전 후



* 좌회전 : 오른쪽 자식과 부모의 위치를 교환

X와 Y 교환

```c++
     X
      \
       Y
      / \
     A   B
```

좌회전 전

```c++
       Y
      / \
     X   B
      \
       A
```

좌회전 후



#### 삽입

- 이진 탐색 트리와 같은 방식으로 삽입한 후에 레드 블랙 트리의 규칙에 맞게 노드를 재조정한다.
- 레드 블렉 트리에 새 노드를 삽입하면, 이 노드를 빨간색으로 설정하고, 양쪽 자식 노드를 Nil로 지정한다.
- 새 노드를 삽입한 후에는 레드 블랙 트리의 규칙을 만족하는 지 확인하고, 만족하지 않는 경우에는 이를 복구한다.
  1. 노드는 레드 혹은 블랙 중의 하나다 → 위배되는 경우가 없다.
  2. 루트 노드는 블랙이다 **→ 위배될 가능성은 있으나 처리가 쉽다 (루트 노드만 검은색으로 설정하면 됨).**
  3. 모든 리프 노드(자식 노드가 없는 노드)들(NIL)은 블랙이다. (null노드를 NIL노드로 표기한다) → 자식 노드를 모두 검은색인 NIL로 설정하기 때문에 위배되는 경우가 없다.
  4. 레드 노드의 양쪽 자식 노드는 언제나 모두 블랙이다 **→ 위배될 가능성이 있다. 이 경우의 처리가 까다롭다.**
  5. 어떤 노드에서 자식 NIL노드들까지 가는 경로들의 블랙 노드의  수는 같다. (이때 자기 자신은 세지(카운트)하지 않는다.) → 위의 규칙들을 맞추면 위배되는 경우가 없다.



**삽입 과정**

- 레드 블랙 트리는 일반적인 이진 탐색 트리(BST) 삽입 과정을 따르지만, 레드 블랙 트리의 속성(5 가지 규칙) 을 유지하기 위해 추가적인 조정이 필요할 수 있다.
- 새로운 노드는 항상 레드로 삽입되며, 부모와 연속된 레드가 발생하면 재조정 과정을 거친다.

| 설명                                                         |
| ------------------------------------------------------------ |
| 새로운 노드는 항상 레드로 삽입 (Black-Height 균형을 쉽게 유지하기 위해) |
| 삽입 후 부모가 블랙이면 문제 없음 → 그대로 유지              |
| 부모가 레드일 경우, 연속된 Red가 발생하여 속성 위반 → 재조정 필요 |
| 삼촌 노드의 색에 따라 Case 1~3 중 하나로 해결                |



**삽입 후 삽입한 노드와 부모 노드가 모두 빨간색(4번 위배)인 경우의 처리**

* 이 때는 다음과 같이 3 가지의 경우로 나눠서 처리해야 한다.

* Case 1 → Case 2 → Case 3 순서로 해결된다.

* 회전 후에도 루트 노드는 항상 Black으로 유지해야 한다.

| 케이스 | 상황                                               | 해결 방법                                                    |
| ------ | -------------------------------------------------- | ------------------------------------------------------------ |
| Case 1 | 부모가 레드, 삼촌도 레드                           | 부모와 삼촌을 Black, 할아버지를 Red로 변경 후, 할아버지 기준으로 다시 검사 |
| Case 2 | 부모가 레드, 삼촌은 블랙 또는 NIL (지그 재그 형태) | 부모를 기준으로 좌회전 또는 우회전 후 Case 3으로 진행        |
| Case 3 | 부모가 레드, 삼촌은 블랙 또는 NIL (일직선 형태)    | 부모를 Black, 할아버지를 Red로 변경 후, 할아버지를 기준으로 회전 |
