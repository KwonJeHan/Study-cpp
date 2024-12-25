# C++ 학습 정리

**[포텐업] 게임 개발자 양성과정**

---

### 콘솔 입출력



#### 콘솔 출력

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



#### 콘솔 입력

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



##### 정리

* iostream 헤더를 추가해 std::cout과 std::cin 함수를 사용할 수 있다.
* std::cout 함수와 << 연산자를 사용해 원하는 값을 콘솔에 출력할 수 있다.
* std::cin 함수와 >> 연산자를 사용해 원하는 데이터를 콘솔에서 입력 받아 변수에 저장할 수 있다.
* 여러 데이터를 출력하거나 입력 받을 때는 각 연산자(<<, >>)를 여러 단계로 구분해서 사용할 수 있다.

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



```c++
// 전처리(Pre-Process).
#include <iostream>

// 함수 선언.
// const char* -> 문자열 타입.
void Log(const char* message)
{
    std::cout << message << "\n";
}

// 진입점(Entry Point).
int main()
{
    // 출력.
    //std::cout << "Hello World\n";
    Log("Hello World");

    // 의미 없음. 바로 종료되지 말라고 추가.
    std::cin.get();
}
```

Main.cpp 파일의 내용이다. 해당 내용에서 Log 함수만 따로 Log.cpp 파일로 분리해 빼내고 각 파일을 컴파일한다.



```c++
// 전처리(Pre-Process).
#include <iostream>

// 함수 선언.
// const char* -> 문자열 타입.
void Log(const char* message)
{
    std::cout << message << "\n";
}
```

Log.cpp 파일 내용. 컴파일이 문제없이 된다.



```c++
// 전처리(Pre-Process).
#include <iostream>

// 진입점(Entry Point).
int main()
{
    // 출력.
    //std::cout << "Hello World\n";
    Log("Hello World");

    // 의미 없음. 바로 종료되지 말라고 추가.
    std::cin.get();
}
```

변경된 Main.cpp 파일 내용. Log 함수 선언을 찾지 못해 컴파일에 실패한다. 따라서 아래와 같이 코드를 변경하면 컴파일이 문제없이 성공한다.

```c++
// 전처리(Pre-Process).
#include <iostream>

void Log(const char* message);

// 진입점(Entry Point).
int main()
{
    // 출력.
    //std::cout << "Hello World\n";
    Log("Hello World");

    // 의미 없음. 바로 종료되지 말라고 추가.
    std::cin.get();
}
```

컴파일러는 Main.cpp에 작성된 Log 함수의 선언을 보고 다른 파일에 본문이 있을 것이라고 예상 후 문제없이 컴파일을 진행한다.

그리고 Log 함수의 내용은 Log.cpp파일에 작성되어 있으며 Main.cpp와 Log.cpp 사이에 연관 관계가 없지만, Main.cpp의 Log 함수 선언은 Log.cpp에 작성된 본문과 잘 연결되어 실행된다.

해당 연결 과정은 링커가 담당한다.



##### 정리

* 컴파일러는 C++ 소스 파일을 기준으로 컴파일을 진행한다.
* 컴파일이 완료되면 소스 파일 이름.obj 파일이 생성된다.
* obj 파일 생성 이후 링커는 obj 파일 사이의 연관 관계가 있는지 일일이 확인해 연결 작업을 진행한다.

---

### 인라인(in-line)함수



#### 매크로(Macro)함수

매크로를 활용한 다양한 작업 중 가장 대표적인 것이 매크로 함수를 만드는 것이다.

```c++
#include <iostream>
// 매크로 함수 정의
#define Square(x) ((x) * (x))

int main()
{
    // 매크로 함수 호출
    std::cout << Square(3) << "\n";
}
```

위 코드는 매크로 함수를 정의하고 호출하는 과정을 보여 준다. 매크로 함수의 호출 구문이 함수의 본문으로 완전히 대체되는 것을 알 수 있는데 이렇게 되면 함수의 호출 과정이 사라지므로 성능 상의 이점을 얻을 수 있다.

이처럼 함수 호출 구분이 함수 본문으로 완전히 대체되는 것을 **'함수가 인라인(inline)화 되었다' **라고 표현한다.



#### C++ 기반 함수의 Inline

C++에서는 매크로 뿐만 아니라 인라인 함수를 위한 특별한 키워드를 추가했다.

```c++
#include <iostream>

inline int Square(int x)
{
    return x * x;
}

int main()
{
    std::cout << Square(3) << "\n";
}
```

위 코드처럼 C++에서는 인라인 함수를 만들 때 inline 키워드를 붙여 주기만 하면 된다.



##### 정리

* C++에서는 함수 호출의 성능 향상을 위해 inline 키워드를 사용해 인라인 함수를 만들 수 있다.
* 매크로를 활용한 인라인화는 전처리기가 처리하지만 inline 키워드를 사용한 함수의 인라인화는 컴파일러가 처리한다.
* 컴파일러에 따라서 inline 선언이 오히려 성능 향상에 방해가 된다고 판단 시, 인라인 함수로 만들지 않는다.

---

### typedef / using



#### 타입 앨리어스 (using)

C++ 11부터 도입되었으며 이전에는 타입 앨리어스가 하는 일을 dypedef로 구현했다.

둘 다 비슷한 기능을 하지만 typedef 쪽이 선언하는 순서도 반대라 헷갈리기 쉽고 가독성이 더 떨어진다.

```c++
using IntPtr = int*;
typedef int* IntPtr
```



#### 함수 포인터 선언

타입 앨리어스가 추가되기 전에는 함수 포인터를 typedef로 표현했다.

```c++
using FunctionType = int (*)(char, double);

// FunctionType이란 이름이 중간에 나와 혼동을 줌
typedef int (*FunctionType)(char, double);
```



##### 정리

* 여러 방면에서 타입 앨리어스를 사용하는 것이 유리하기 때문에 타입 앨리어스를 사용할 수 있는 경우 using을 사용한다.
* C++ 11 이전부터 잘 작동하던 코드에는 typedef 키워드를 사용해 치환을 처리한 코드가 있을 것이므로 이를 이해하기 위해서 typedef 구문도 알아두는 것이 좋다.

---

### auto



#### 컴파일 시점에 타입을 결정

auto를 사용하면 변수를 정의할 때 명시적으로 타입을 지정하지 않아도 되며 변수를 초기화 할 때 초기화 값에 따라 자동으로 타입을 결정해 준다.

하지만 변수의 타입을 지정할 때 항상 초기화(값의 대입)가 필요하고 지역 변수에만 사용이 가능하며 클래스의 멤버 변수나 전역 변수, 함수의 인자로는 사용할 수 없다.

개발이 쉽고 간편해지는 장점은 있지만 무분별한 사용은 자료형 파악을 어렵게 하고 가독성이 떨어지므로 피해야 한다.



**문자열과 정수형 변수에 auto를 사용한 예제**

```c++
#include <iostream>

int main()
{
    // const char*
    auto npcName = "King";
    std::cout << npcName << std::end1;
    
    // int
    auto number = 10;
    std::cout << number << std::end1;
}
```

---

### 포인터



**메모리 주소를 저장하는 int 변수**

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    void* ptr = nullptr;
    std::cin.get();
}
```



#### & 연산자

다른 변수의 메모리 주소를 읽어 올 때 사용한다.

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    int var = 8;
    void* ptr = &var;
    std::cin.get();
}
```



#### * 연산자

포인터가 가리키는 주소에 저장된 값에 접근할 때 사용한다. 아래 코드를 실행해 보면 값이 8에서 10으로 변경되는 것을 볼 수 있다.

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    int var = 8;
    void* ptr = &var;
    
    *ptr = 10;
    
    LOG(var);
    
    std::cin.get();
}
```



#### new 연산자를 활용한 동적 할당

힙(heap)에 메모리를 할당하는 경우

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    char* buffer = ner char[8];
    memset(buffer, 0, 8);
    
    delete[] buffer;
    std::cin.get();
}
```



#### 더블 포인터 **

다른 포인터 변수의 메모리 주소를 저장하는 포인터이다.

더블 포인터 역시 다른 변수의 주소를 저장하는데 다른 변수가 포인터일 뿐 **포인터는 다른 변수의 주소를 저장하는 int 변수**라는 것을 잊지 말아야 한다.

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    char* buffer = new char[8];
    memset(buffer, 0, 8);
    
    char** ptr = &buffer;
    
    delete[] buffer;
    std::cin.get();
}
```

---

### 래퍼런스



**포인터의 사용을 문법적으로 쉽게 만들어 주는 도구**

* 포인터와는 다르게 먼저 선언한 후 다른 변수를 참조하도록 할 수 없다.
* 선언할 때 직접 값을 할당할 수 없으며 이미 메모리를 차지하고 있는 다른 변수를 참조하도록 선언해야 한다. 

```c++
#include <iostream>

#define LOG(x) std::cout << x << std::end1

int main()
{
    int a = 5;
    int& ref = a;
    ref = 10;
    
    // 초기화 하지 않았기 때문에 오류가 생김
    // int& ref;
    
    // 값을 직접 할당할 수 없기 때문에 오류가 생김
    // int& ref = 10;
    
    std::cin.get();
}
```
