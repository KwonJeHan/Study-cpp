# C++ 학습 정리

**2025/01/03 [포텐업] 게임 개발자 양성 과정**

---

### lambda(람다)

람다 함수, 무명 함수 라고 부르며, 성격은 함수 객체와 같다.

함수 객체를 정의하지 않고 손쉽게 필요한 조건자 작성이 가능하다.

**람다 사용 방법**

```,c++
int main()
{
	[]  // lambda capture
	()  // 함수 정의
	{}  // 함수 본문
	(); // 함수 호출
}

// 람다 사용의 간단한 예시
int main()
{
	[](){ std::cout << "Hello World!\n"; }();
}
```



#### 캡처

**람다를 사용할 때 람다 외부에 정의돼 있는 함수를 람다 내부에서 사용하고 싶을 때 사용한다.**

참조나 복사로 전달이 가능하며 참조를 사용할 때는 '&'기호를 사용하고 복사로 전달할 때는 '변수 이름'을 사용한다.

람다의 '[](파라미터){식}'에서 맨 앞의 [] 사이에 캡처할 변수를 작성한다.

```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main()
{
	std::vector<int> moneyVector;
	moneyVector.emplace_back(100);
	moneyVector.emplace_back(4000);
	moneyVector.emplace_back(50);
	moneyVector.emplace_back(200);

	int totalMoney = 0;
	std::for_each(moneyVector.begin(), moneyVector.end(), 
		[&totalMoney](int money) { totalMoney += money; });
	std::cout << "Total Money : " << totalMoney << std::endl;

	std::cin.get();
	return 0;
}
```

---

### 함수 객체

**함수처럼 호출 가능한 객체**

함수 호출 연산자를 오버로딩한 클래스나 구조체로 함수 포인터보다 더 강력하고 유연하다.

클래스 또는 구조체에 operator()를 정의하고 함수 호출 연산자 ()를 오버로딩 하여 사용한다.

```c++
#include <iostream>

class Functor
{
public:
	void operator()(int x)
	{
		std::cout << "입력 값: " << x << "\n";
	}
};

int main()
{
	Functor functor; // 함수 객체 생성
	functor(5);      // 함수처럼 호출
	
	std::cin.get();
}
```

---

### 함수 포인터

**콜백(간접 호출) <-> 콜(직접 호출), 다른 함수의 주소를 저장하는 포인터이다.**

```c++
int Function()
{
	return 100;
}

int main()
{
	// FunctionPointer 함수 포인터 변수에 Function 함수 저장.
	// 함수를 함수 포인터에 저장할 때는 함수의 이름을 그대로 대입.
	int (*FunctionPointer)() = Function;
	
	// FunctionPointer 변수를 통해 함수 호출.
	// 포인터 타입이기 때문에 null 비교가 가능.
	if (FunctionPointer != nullptr)
	{
		FunctionPointer();	
	}
}
```



#### 다른 함수에 함수 포인터를 파라미터로 전달

다른 함수에 파라미터로 전달되는 함수를 콜백 함수라고 한다.

함수 포인터를 사용할 때 가장 유용한 경우가 바로 다른 함수에 파라미터로 함수를 전달하는 것이다.
