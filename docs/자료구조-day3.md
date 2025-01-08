# 자료구조 학습 정리

**2025/01/08 [포텐업] 게임 개발자 양성 과정**

---

## 선형 자료구조

### 스택

**데이터가 저장된 순서를 기억하는 방법에 관련한 추상 자료형**

가장 나중에 저장된 데이터가 가장 먼저 출력된다.(LIFO, Last In First Out)

스택의 삽입과 삭제가 발생하는 곳으로 하나의 스택 변수(top or head가 일반적)를 사용하며 데이터 삽입 시 top(or head)을 증가시키고, 삭제 시 감소시킨다.



#### 추상 자료형

**1. 객체 (Object)**

- 0개 이상의 원소(데이터)를 갖는 유한 순서 리스트

**2. 연산(Functions)**

- Stack CreateStack(maxStackSize)

  스택의 크기가 maxStackSize인 빈 스택을 생성하고 이를 반환한다. (⇒ 공간확보)

- Boolean IsFull(stack)

  if ( stack의 element 개수) == maxStackSize) )

  then { 'true' 반환 }

  else { 'false' 반환 }

- Stack Push(stack, item)

  if ( IsFull(stack) )

  then { 'StackFull' 출력 }

  else { 스택의 가장 위에 item을 삽입하고 스택을 반환 }

- Boolean IsEmpty(stack)

  if ( top < 1)

  then { 'true' 반환 }

  else { 'false' 반환 }

- Element Pop(stack)

  if ( IsEmpty(stack) )

  then { 'StackEmpty' 출력 }

  else { 스택의 가장 위에 있는 element를 삭제하고 이를 반환한다. }



#### 스택 연산 수행

① CreateStack(3);

② Push(stack, 'S');

③ Push(stack, 'T');

④ Pop(stack);

⑤ Push(stack, 'R');

⑥ Push(stack, 'P');

⑦ Push(stack, 'Q');

⑧ Pop(stack);

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/stack1.png">

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/stack2.png">
