# 자료구조 학습 정리

**2025/02/04 [포텐업] 게임 개발자 양성 과정**

---

## STL 컨테이너

### STL deque

Double Ended Queue 자료구조

크기가 가변적이고 앞/뒤에서 삽입 삭제가 가능하며 중간에 데이터 삽입/삭제는 용이하지 않다.

구현 난이도가 있으며 랜덤 접근이 가능하다.



#### deque를 사용해야 하는 경우

1. 앞, 뒤에서 삽입, 삭제를 한다.
   * deque를 사용하는 가장 큰 이유
2. 저장할 데이터 개수가 가변적이다.
   * deque는 동적으로 크기가 변하기 때문에 데이터 수를 미리 알 수 없어도 사용 가능
3. 검색을 하지 않는다.
   * 검색이 필요하면 map, set, unordered_map(hashtable)을 사용
4. 데이터를 랜덤하게 접근하고 싶다.(예약 기록)
   * vector와 같이 랜덤 접근이 가능하다. 사용 방법도 동일



#### deque과 vector를 비교할 때 고려 사항

deque은 앞과 뒤에서 삽입과 삭제 성능이 vector보다 좋지만 이외의 기능은 vector보다 성능이 좋지 않다.

주로 데이터가 들어온 순서대로 순차적으로 처리해야 할 때 deque을 활용한다.



### 연관 컨테이너

시퀀스 컨테이너 = vector, lsit, deque

**연관 컨테이너** = key-value를 짝으로 데이터를 저장, 따라서 데이터를 저장하고 읽을 때 key가 필요

map, set, unordered_map 등이 있으며 중복되지 않은 key(키)를 사용해 데이터를 저장한다.

key가 중복되는 경우 컨테이너 앞에 multi를 붙인 컨테이너 타입을 사용한다.

**연관 컨테이너는 검색 속도가 중요한 경우 사용한다.**



#### map, set과 unordered_map, unordered_set의 차이점

* map과 set
  * 자료를 정렬해 저장
  * 반복자로 데이터를 순회할 때 데이터를 저장한 순서대로 순회하지 않고 정렬된 순서대로 순회
* unordered_map과 unordered_set
  * 자료를 정렬하지 않는다.
  * hash 자료구조를 사용해 검색 속조가 map, set에 비해 빠르다.
* 선택 기준
  * map, set : 데이터를 정렬해 저장하고 싶을 때
  * unordered_map, unordered_set : 정렬은 필요 없고, 빠른 검색을 하고 싶을 때



### STL unordered_map

자료구조는 해시 테이블(Hash Table)이다.

해시 테이블에 자료를 저장할 때는 key 값을 해시 함수에 대입해 버킷(bucket) 번호를 구하고, 이를 사용해 빈 슬롯에 데이터를 저장한다.

key 값을 해시 함수에 입력해 나오는 버킷 번호에 데이터를 저장하기 때문에 삽입/삭제/검색 속도가 거의(평균적으로) 일정하다.



#### unordered_map을 사용할 때

1. 많은 데이터를 저장하고, 검색 속도가 중요한 경우
2. 너무 빈번하게 자료의 삽입, 삭제가 필요하지 않을 경우
3. 한 번에 대량의 데이터를 저장한 뒤 검색 속도가 중요할 경우

저장한 자료가 적을 때는 메모리 낭비와 검색 시 오버헤드가 생기며 검색 속도만을 생각해 unordered_map을 사용하는 것은 좋지 않다.

**컨테이너의 추가/삭제 작업은 list, vector, deque가 더 빠르며 적은 양의 데이터를 저장하고 검색할 때는 vector가 더 빠를 때도 있다.**
