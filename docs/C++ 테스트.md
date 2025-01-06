### 1번

1. C++에서 참조(reference)와 포인터(pointer)의 차이를 설명하시오.

참조(Reference)는 선언만 먼저 하거나 값을 직접 할당하지 못한다.



### 2번

미리 컴파일된 헤더(Precompiled Header)를 사용하는 이유를 설명하시오(주관식)

컴파일 시간을 단축하기 위해 사용한다.



### 3번

다음 코드를 실행했을 때의 출력 결과를 예측하고, 그 이유를 설명하시오.

```c++
#include <iostream>

using namespace std;

void Modify(int &x)
{
	x *= 2;
}

int main()
{
	int number = 5;
	Modify(number);
	cout << number;

	return 0;
}

```

10이 출력되며 함수의 파라미터인 x가 number를 참조하며 x가 참조하는 값을 2배로 증가시키고 함수 종료와 함께 사라지지만 값은 number에 저장된다.



### 4번

다음의 스마트 포인터(Smart Pointer) 중에서 여러 소유자가 공유할 수 있고, 참조 횟수를 기반으로 관리되는 포인터의 종류는?

1. std::unique_ptr
2. std::weak_ptr
3. std::shared_ptr
4. raw pointer



3. std::shared_ptr



### 5번

다음 프로그램에서 발생할 수 있는 메모리 누수(Memery Leak)를 수정하세요.

```c++
#include <iostream>

int main()
{
    int *ptr = new int(10);
    std::cout << *ptr;
}
```



```c++
#include <iostream>

int main()
{
    int *ptr = new int(10);
    std::cout << *ptr;
    delete ptr;
}
```





### 6번

연산자 오버로딩을 통해 두 Vector2 객체를 더하는 코드를 작성하시오.

```cpp
#include <iostream>
using namespace std;

class Vector2
{
    int x, y;
public:
    Vector2(int x, int y) : x(x), y(y) {}
    void Display() { cout << "(" << x << ", " << y << ")\\n"; }
};

int main()
{
    Vector2 v1(1, 2), v2(3, 4);
    Vector2 v3 = v1 + v2;
    v3.Display(); // (4, 6)
}
```



```c++
```





### 7번

다음 코드의 출력 값을 적고, 그 이유를 간단히 설명하시오

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    virtual void Show() { cout << "Base\\n"; }
};

class Derived : public Base
{
public:
    virtual void Show() override { cout << "Derived\\n"; }
};

int main()
{
    Base *b = new Derived();
    b->Show();
    delete b;
}
```





### 8번

다음 코드를 실행하면, 형변환이 불가능한데도 형변환이 진행되며 “Derived2”가 출력 된다.

잘못된 부분을 찾아 코드를 수정하고, “Derived2”가 출력된 이유를 설명하시오.

```cpp
#include <iostream>

class Base
{
public:
	virtual ~Base() {}

	virtual void Show()	{ std::cout << "Base\\n"; }
};

class Derived1 : public Base
{
public:
	virtual void Show() override { std::cout << "Derived1\\n";	}
};

class Derived2 : public Base
{
public:
	virtual void Show() override { std::cout << "Derived2\\n";	}
};

int main()
{
	Base* b1 = new Derived2();

	Derived1* d = (Derived1*)b1;
	if (d != nullptr)
	{
		d->Show();
	}
	else
	{
		std::cout << "b1 can not be converted to Derived1 type.\\n";
	}
}
```







### 9번

다음 코드의 출력 결과를 작성하고, static 키워드의 역할을 설명하시오.

```cpp
#include <iostream>
using namespace std;

void Counter()
{
    static int count = 0;
    count++;
    cout << "Count: " << count << endl;
}

int main()
{
    counter();
    counter();
    counter();
    
    return 0;
}
```

Count: 1

Count: 2

Count: 3

count 변수가 함수 호출 시마다 초기화 되지 않고 값을 유지하도록 해준다.



### 10번

상속 계층 구조를 가지는 클래스의 인스턴스를 다운 캐스팅(Down Casting)할 때 사용해야 하는 형변환 연산자를 선택하시오.

1. static_cast
2. reinterpret_cast
3. const_cast
4. dynamic_cast



4. dynamic_cast



### 11번

dynamic_cast를 사용하는 대신, 커스텀 RTTI(RunTime Type Information)를 구현해 사용하는 이유를 설명하시오.

최근에 성능이 많이 개선되서 간헐적으로 사용하면 보통의 경우에는 문제가 되지 않을 수 있지만 게임 프로그래밍 환경과 같이 속도가 중요한 경우에 사용한다.