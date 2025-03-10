# 알고리즘 학습 정리

**2025/02/06 [포텐업] 게임 개발자 양성 과정**

---

## 일반 알고리즘

### 알고리즘 분석

알고리즘을 설계하거나 잘 알려진 알고리즘을 적용할 때 그 알고리즘의 성능을 이해하는 것이 중요하다.

알고리즘의 성능을 평가하는 여러 가지 기준이 있지만 대체로 가장 관심 있는 부분은 수행 속도다.



#### 최악 분석

대부분의 알고리즘이 모든 경우에 같은 성능을 보이지는 않는다. 일반적으로 다루는 자료에 따라 다양한 성능을 보인다.

대표적으로 최상, 최악, 평균의 세 경우로 분류한다.

**최악 분석을 사용하는 이유**

1. 많은 알고리즘들이 대부분의 실행에서 최악의 성능을 보인다.
2. 많은 알고리즘들이 최상의 경우 똑같은 성능을 보인다.
3. 평균 성능을 계산하는 것이 쉽지 않은 경우가 있다.
4. 최악의 경우는 성능의 상위 한계를 의미한다.



#### O 표기법

**알고리즘의 성능을 정형적으로 표현하는 가장 일반적인 표기법이다.**

| 순위     | O-표기법                                                     |
| -------- | ------------------------------------------------------------ |
| O(1)     | 상수 시간. (입력 데이터의 크기에 관계없이 동일한 성능).      |
| O(logN)  | 로그. (입력 데이터 크기 증가율 > 연산 횟수 증가율)           |
| O(N)     | 선형. (입력 크기 & 연산 횟수 비례)                           |
| O(NlogN) | 로그 선형. (입력 크기 2배 증가 시 연산횟 수가 2배가 조금 넘게 증가). |
| O(N^2)   | 입력 크기n 연산 횟수 $n^2$                                   |
| O(N^3)   | 입력 크기 $n$ 연산 횟수 $n^3$. 두 $n\times n$ 행렬의 곱      |
| O(2^n)   | 지수. (지수적으로 증가함)                                    |



**시간 복잡도 나열**

오른쪽으로 갈수록 성능이 떨어진다.

O(1) < O(logN) < O(NlogN) < O(n^2) < O(2^n) < O(n!)



### 재귀 함수

**자기 자신을 호출하는 함수**

재귀 함수는 보통 두 부분으로 구성된다.

1. **종료 조건** : 재귀 함수가 자기 자신을 반복해서 호출하다가 특정 조건을 만족하면 호출을 멈추고 값을 반환한다. 이 때, **종료 조건**이 반드시 필요하다. 종료 조건을 만족하면 함수는 재귀 호출을 중단하고 값을 반환한다.
2. **입력의 변경** : 재귀 함수가 자기 자신을 호출하여 더 작은 입력에 대해 작업을 수행한다. 이때, 입력이 기본적으로 작아져야 하고 종료 조건으로 수렴해야 한다.



#### 재귀 함수의 장점

주로 순환적인 문제를 해결하는데 사용되며 코드의 가독성과 유지 보수성을 높일 수 있다.



#### 재귀 함수 사용 시 주의 점

작성 시 반드시 먼저, **종료 조건**을 고려해야 한다. 또한 스택 오버플로우와 같은 부작용을 주의해야 한다.(재귀 함수를 활용해 문제를 해결할 수 있는 지를 고민)



### Brute-Force 알고리즘

가장 직접적이고 간단한 방법으로 문제를 해결하는 방법으로 **가능한 모든 경우의 수를 하나 씩 시도하여 문제를 해결하려고 시도하는 것을 의미한다.** 이러한 방법은 간단하고 이해하기 쉽지만, 문자열이 매우 크고 패턴의 길이가 긴 경우에는 비효율적일 수 있다.



### 이진 탐색

**정렬된 배열 또는 리스트**에서 특정한 값을 찾는 알고리즘이다.  배열이나 리스트의 중간 값을 기준으로 탐색 범위를 반으로 줄여가며 원하는 값을 찾아나간다.

O(log n)의 시간 복잡도를 가지므로 매우 효율적인 탐색 알고리즘 중 하나다.
