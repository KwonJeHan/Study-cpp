# C++ 학습 정리

**[포텐업] 게임 개발자 양성과정**

---

### 콘솔 입출력



#### **콘솔 출력**

C++ 에서는 값을 콘솔에 출력 할 때 std::cout 함수를 사용한다. 해당 함수 뒤에 << 연산자를 사용해 출력하고자 하는 값을 전달하면 콘솔 화면에 해당 값을 출력한다. 또한 std::cout 함수를 사용하려면 iostream 헤더를 추가하는 전처리 과정이 필요하다.



**Hello World 출력하기**

```c++
// 헤더 추가
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
}
```



**std::cout 활용**

```c++
#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    std::cout << "Hello" << " " << "World!" << "\n";
    std::cout << 1 << 'one' << "string" << std::end1;
}
```



#### **콘솔 입력**

C++ 에서 어떠한 데이터를 콘솔에서 입력 받을 때 std::cin 함수를 사용한다. 해당 함수 뒤에 >> 연산자를 사용하고 연산자 뒤에 데이터를 저장할 변수를 정의하면 데이터 입력 시 해당 변수에 입력 받을 수 있다. 위의 std::out과 마찬가지로 함수를 사용하려면 iostream 헤더를 추가해야 한다.



**Hello World 입력하기**

```c++
#include <iostream>

int main()
{
    int number1, number2;
    std::cout << "첫 번째 숫자 입력 : ";
    std::cin >> number1;
    
    std::cout << "두 번째 숫자 입력 : ";
    std::cin >> number2;
    
    int result = number1 + number2;
    std::cout << "덧셈 결과 : " << result << "\n";
}
```



**std::cin 활용**

```c++
#include <iostream>

int main()
{
    // 문자열 입력
    char name[100], language[200];
    
    std::out << "이름을 적어주세요: ";
    std::cin >> name;
    
    std::cout << "좋아하는 프로그래밍 언어를 적어주세요 : ";
    std::cin >> language;
    
    std::cout << "이름 : " << name << "\n";
    std::cout << "좋아하는 프로그래밍 언어 : " << language << "\n";
    
    // >>연산자를 사용한 구분 입력
    int number1, number2;
    std::cout << "두개의 숫자를 입력해주세요 : ";
    std::cin >> number1 >> number2;
    
    int result = number1 + number2;
    std::cout << "덧셈 결과 : " << result << "\n"; 
}
```



##### **정리**

* iostream 헤더를 추가해 std::cout과 std::cin 함수를 사용할 수 있다.
* std::cout 함수와 << 연산자를 사용해 원하는 값을 콘솔에 출력할 수 있다.
* std::cin 함수와 >> 연산자를 사용해 원하는 데이터를 콘솔에서 입력 받아 변수에 저장할 수 있다.
* 여러 데이터를 출력하거나 입력 받을 때는 각 연산자(<<, >>)를 여러 단계로 구분해서 사용할 수 있다.



#### **연습문제**

**문제 1**

사용자로부터 총 10개의 정수를 입력 받아서 그 합을 출력하는 프로그램을 작성해보자.



**문제 2**

사용자로부터 이름과 전화번호를 입력 받아서 배열에 저장한 다음, 그대로 출력해주는 프로그램을 작성해보자.



**문제 3**

숫자 하나를 입력 받아서 그 숫자에 해당하는 구구단을 출력하는 프로그램을 작성해보자.

예를 들어 9를 입력하면 구구단의 9단을 출력해야 한다.



**문제 4**

영업사원의 급여 계산 프로그램을 작성해보자.

회사는 모든 영업사원에게 매달 300만원의 기본 급여와 물품 판매 가격의 15%에 해당하는 돈을 지급해야 한다.

예를 들어서 세윤이라는 직원의 이번 달 물품 판매 금액이 100만원이라면 300 + 100 * 0.15 = 315만원을 급여로 지급 받는다.

다음 실행 예시를 참고해 프로그램을 작성하자.

```markdown
판매 금액을 만원 단위로 입력(종료는 -1): 100
이번 달 급여: 315만원
판매 금액을 만원 단위로 입력(종료는 -1): 200
이번 달 급여: 330만원
판매 금액을 만원 단위로 입력(종료는 -1): -1
```



---



### C++ 동작 방식



```c++
// 전처리(Pre-Process).
#include <iostream>

// 진입점(Entry Point).
int main()
{
    // 출력.
    std::cout << "Hello World\n";

    // 의미 없음. 바로 종료되지 말라고 추가.
    std::cin.get();
}

```



**C++로 작성된 프로그램 빌드 과정**

1. 전처리 단계
   * 전처리기가 처리
   * 작성된 코드의 문법적 검토
   * 주석 제거
   * 실제 컴파일 가능한 소스로 변환
2. 컴파일 단계 - 파일 단위로 처리 (cpp)
   * 컴파일러가 처리
   * 소스 코드를 어셈블리 코드로 변환
3. 어셈블리 단계
   * 어셈블러가 처리
   * 중간 파일인 obj 파일로 변환
4. 링크 단계
   * 링커가 처리
   * obj 파일을 연결해 실행 가능한 파일 생성



<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/cpp-process.png">
