# 자료구조 학습 정리

**2025/01/09 [포텐업] 게임 개발자 양성 과정**

---

## 선형 자료구조

### 큐(Queue)

**순서대로 처리되는 방법에 대한 추상 자료형**

가장 먼저 들어간 데이터가 가장 먼저 출력된다. (FIFO, First In First Out)

큐읜 한쪽 끝을 front로 정해 삭제 연산만 수행하고, 다른 한쪽 끝을 rear로 정해 삽입 연산만 수행한다.

너비 우선 탐색(BFS)에 활용되며 여러 데이터가 순차적으로 처리돼야 하는 경우에 활용된다.



#### 추상 자료형

**1. 객체 (Object)**

- 선입 선출(FIFO)의 접근 방법을 유지하는 요소들의 모음

**2. 연산(Functions)**

- Queue CreateQueue(maxQueueSize)

  큐의 크기가 maxQueueSize인 빈 큐를 생성하고 이를 반환한다

- Enqueue(e)

  전달된 요소 e를 큐의 맨 뒤에 추가한다.

- Dequeue()

  큐가 비어있지 않으면 맨 앞 요소를 삭제하고 반환한다.

- IsEmpty()

  큐가 비어 있으면 true를 반환하고, 비어있지 않으면 false를 반환한다

- Peek()

  큐가 비어 있지 않으면 맨 앞 요소를 삭제하지 않고 반환한다.

- IsFull()

  큐가 가득 차 있으면 true를 반환하고 그렇지 않으면 false를 반환한다

- Size()

  큐의 모든 요소들의 개수를 반환한다



#### 큐 연산 수행

① CreateQueue(5);

② addQueue('A');

③ addQueue('B');

④ addQueue('C');

⑤ deleteQueue();

⑥ deleteQueue();

⑦ deleteQueue();

⑧ addQueue('D');

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Queue.png">
