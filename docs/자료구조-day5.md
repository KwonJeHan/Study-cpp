# 자료구조 학습 정리

**2025/01/10 [포텐업] 게임 개발자 양성 과정**

---

## 선형 자료구조

### 덱(Deque)

**Double_Ended Queue의 줄임말로 front와 end에서 모두 삽입과 삭제가 가능한 큐**



#### 추상 자료형

**1. 객체(Object)**

Front와 Rear를 통한 접근을 허용하는 요소들의 모음

**2. 연산(Functions)**

- AddFront(e)

  전달된 요소 e를 덱의 맨 앞에 추가한다.

- DeleteFront()

  덱이 비어있지 않으면 맨 앞 요소를 삭제하고 반환한다

- AddRear(e)

  전달된 요소 e를 덱의 맨 뒤에 추가한다.

- DeleteRear()

  덱이 비어있지 않으면 맨 뒤 요소를 삭제하고 반환한다.

- IsEmpty()

  큐가 비어있으면 true를 반환하고 비어있지 않으면 false를 반환한다.

- GetFront()

  비어있지 않으면 맨 앞 요소를 삭제하지 않고 반환한다

- GetRear()

  비어있지 않으면 맨 뒤 요소를 삭제하지 않고 반환한다

- IsFull()

  덱이 가득 차 있으면 true를 반환하고 그렇지 않으면 false를 반환한다.



#### 덱 연산 수행

① AddFront(A);

② AddRear(B);

③ AddFront(C);

④ AddRear(D);

⑤ DeleteFront();

⑥ DeleteRear();

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Deque.png">

---

## 비선형 자료구조

### 해시테이블(HashTable)

**키(Key)와 값(Value)이 하나의 쌍(Pair)을 이루는 추상 자료형**

키와 값을 연결(Mspping)하는 과정을 해싱(Hashing)이라고 한다.

빠른 탐색, 삽입, 삭제 속도를 가지기 때문에 여러 항목 간의 관계를 저장하는데 유용하게 사용된다.

해시 충돌 : 서로 다른 데이터를 해시한 결과가 동일한 경우

* 해시 함수를 통해 얻은 해시의 결과가 같은 경우
* 해시 충돌이 발생하면 **체이닝(chaining)-(메모리)**이나 **Open Addressing-(복잡함)**을 통해서 해결한다.



#### 추상 자료형

- 인터페이스와 기능 구현을 분리한 자료형
- 기능 구현 부분을 명시하지 않아(추상화 함) 사용할 때는 기능을 어떻게 동작하는 지를 몰라도 된다는 편리함이 있다.
- 대표적인 자료형에는 해시테이블(HashTable), 딕셔너리(Dictionary) 등이 있다.
