# C++ 학습 정리

**[포텐업] 게임 개발자 양성 과정**

---

### 배열

**같은 유형의 데이터 여러 개를 저장하고 싶을 때 배열을 사용 **

배열 선언 시 배열의 크기만큼 연속된 메모리 주소가 할당된다.

```c++
#include <iostream>

int main()
{
	int example[5];
	example[0] = 1;
	example[4] = 10;

	std::cout << example[4] << std::endl;
	std::cout << example << std::endl;

	std::cin.get();
}
```



#### 배열 사용 시 자주 발생하는 오류 OutOfRange


**배열을 사용할 때 항상 배열의 범위 안에서 사용해야 한다.**

```c++
#include <iostream>

int main()
{
	int example[5];
	example[0] = 1;
	example[4] = 10;
	
	example[-1] = 3;
	example[5] = 20;

	std::cout << example[4] << std::endl;
	std::cout << example << std::endl;

	std::cin.get();
}
```



#### 배열과 포인터

**배열의 이름은 그 배열의 시작 주소를 의미( 즉, 포인터이므로 포인터로 받아서 포인터 연산이 가능하다.)**

포인터 변수에 배열 주소를 저장해 사용 가능하다.

```c++
#include <iostream>

int main()
{
	int example[5];
	example[0] = 1;
	example[4] = 10;

	int* ptr = example;
	*(ptr + 2) = 20;
	//*(int*)((char*)ptr + 8) = 20;

	std::cout << example[4] << std::endl;
	std::cout << example << std::endl;

	std::cin.get();
}
```



#### 배열의 동적 할당

아래 코드는 배열을 힙(Heap) 메모리에 생성하고, 생성한 메모리의 주소를 반환하는 과정을 보여준다.

```c++
#include <iostream>

int main()
{
	int example[5];

	//int length = 5;
	int length = sizeof(example) / sizeof(example[0]);
	for (int ix = 0; ix < length; ++ix)
	{
		example[ix] = 2;
	}

	int* another = new int[5];
	length = sizeof(another) / sizeof(another[0]);
	for (int ix = 0; ix < length; ++ix)
	{
		another[ix] = 2;
	}

	delete[] another;
	
	std::cin.get();
}
```

---

### 문자열

**문자가 연속으로 저장된 문자의 집합으로 문자를 배열로 저장한 것이다.**

**문자열을 저장할 때 사용하는 대표적인 타입 2가지 타입이 있다.**



#### const char* 타입

const char*의 경우 값을 바꾸지 못한다.

```c++
#include <iostream>

int main()
{
	const char* name = "Kwon";
	std::cout << name << "\n";

	std::cin.get();
}
```

이때 “Kwon”는 실제로 char 배열인데 이 배열의 시작 주소를 const char* 으로 저장하는 것이다. 또한 char 배열을 저장하기 위해 필요한 타입은 char* 인데 문자열 값을 그대로 저장할 때는 const char* 타입을 사용해야 한다.



#### char* 타입

char* = char[] 이다.

char* 타입으로 문자열을 저장하면, 실제로는 char 배열의 시작 주소를 저장한다.

4개의 문자를 넣을 때 5칸을 할당하고 마지막에 \0(NULL 문자)를 넣어줘야 한다.

```c++
#include <iostream>

int main()
{
	const char* name = "Ronnie";
	char name2[6] = { 'R', 'o', 'n', 'n', 'i', 'e' };
	std::cout << name2 << std::endl;

	std::cin.get();
}
```

위의 코드는 null문자를 문자열 끝에 추가해주지 않았기 때문에 제대로 출력되지 않는다. 따라서 아래와 같이 코드를 수정하면 정상적으로 결과가 나오는 것을 볼 수 있다.

```c++
#include <iostream>

int main()
{
	char* name = "Ronnie";
	char name2[7] = { 'R', 'o', 'n', 'n', 'i', 'e', '\0' };
	std::cout << name2 << "\n";

	std::cin.get();
}
```



#### const wchar_t* 타입

영어권 문자 뿐만 아니라 다른 나라의 문자(특히 동아시아)를 지원하기 위해 추가된 타입으로 char타입은 1바이트를 차지하는 반면 2바이트를 차지한다. 또한 문자열을 설정할 때는 문자열 리터럴 앞에 대문자 L을 추가해 L” “와 같은 형태로 작성해야 한다.

char 타입은 std::cout과 호환되고, wchar_t 타입은 std::wcout과 호환된다.

```c++
#include <iostream>

int main()
{
	const wchar_t* wideName = L"Ronnie";
	std::wcout << wideName << L"\n";

	std::cin.get();
}
```

---

### 스택과 힙



#### 스택 세그먼트

스택에 메모리 할당 시 연속적으로 한 단계씩 할당된다.

LIFO(Last In First Out)형 자료구조로 가장 늦게 들어온 데이터가 먼저 처리되며 메모리가 자동으로 관리되어 자동 메모리 라고도 불린다.



#### 스택 오버플로우

스택 세그먼트는 크기가 제한되어있는데 이 크기를 벗어나는 정도로 사용하면 스택 오버플로우가 발생한다.

```c++
int main()
{
	int stackOver[1000000000];
}
```

위와 같이 스택에 매우 큰 공간을 할당하려고 하면 프로그램 상황에 따라 스택 오버플로우가 발생할 수 있다.



#### 힙 세그먼트

동적으로 할당(실행중에 할당받는다.)되는 메모리를 관리하며 스택보다는 느리다. 하지만 스택에 비해 큰 데이터를 할당하는데 문제가 없다. 따러서 큰 배열이나 클래스를 할당할 때는 힙을 사용한다. new 연산자를 사용해 할당하는 것이 힙 세그먼트에 해당한다.

할당되는 메모리가 연속적이지 않으며 그 때 그 때 필요한 만큼의 빈 공간을 할당하는데 new와 delete는 항상 쌍으로 작성해 동적으로 할당한 메모리는 항상 delete/delete[] 연산자를 사용해 해제해야 한다. 할당된 메모리는 명시적으로 해제하지 않으면 프로그램이 종료될 때까지 유지되기 때문에 해제하지 않을 시 메모리 누수가 발생한다.

```c++
// int 타입을 저장할 수 있는 포인터 변수 선언.
int* number = new int;

// 10개의 int 타입을 저장할 수 있는 배열 포인터 변수 언언.
int* array = new int[10];

// 동적 메모리 해제.
delete number;
delete[] array;
```

---

### 클래스

**클래스는 데이터와 함수를 그룹으로 묶어주는 기능을 한다.**



#### Player 클래스 선언 및 활용

```c++
#include <iostream>

class Player
{
// 한정자/접근 제한자/가시성(Visibility).
// public/protected/private.
private: // 기본 설정. (외부 접근 X).
	int x, y;
	int speed;
};

int main()
{
	//int playerX, playerY;
	//int playerSpeed = 2;

	Player player;
	player.x = 5;
	player.speed = 1;

	Player player2;

	std::cin.get();
}
```

Player라는 이름의 클래스에 필요한 변수들을 그룹지어 선언해두면 사용하기 편리하며, 이것이 클래스다.

클래스는 기본적으로 private로 설정되기 때문에 가시성(visibility) 문제를 생각하면 한정자를 명시적으로 선언해줘야 한다.



#### 한정자 명시적 선언

```c++
#include <iostream>

class Player
{
public:
	int x, y;
	int speed;
};

int main()
{
	//int playerX, playerY;
	//int playerSpeed = 2;

	Player player;
	player.x = 5;
	player.speed = 1;

	std::cin.get();
}
```

- private은 자기 자신만 사용하는 함수 및 변수에 선언한다.
- protected는 자기 자신 및 자손(이 클래스를 상속한 클래스)에게 공개한다.
- public은 외부에 공개할 때 사용한다.





#### 생성자와 소멸자

**생성자**는 클래스의 이름과 똑같은 이름을 가진 함수이며, 반환 값이 없는 형태다. 클래스가 가지는 멤버 변수를 초기화하는 목적으로 많이 쓴다. 

파라미터를 전달 받을 수 있고 함수 오버로딩이 가능하다.



**소멸자**는 인스턴스가 삭제(소멸)될 때 호출되는 함수로 생성자와 마찬가지로 반환형이 없으며 앞에 ~를 붙이고 오버로딩이 불가능하다. 인스턴스가 사용했던 메모리와 값을 정리하는 목적으로 사용한다.

생성자와 달리 파라미터를 전달 받을 수 없고 void형으로만 선언이 가능하다.



#### 클래스와 배열



**객체 배열 선언**

```c++
#include <iostream>

class Player
{
public:
	Player()
		: x(0), y(0)
	{
		std::cout << "Player contructor call\n";
	}

	Player(int inX, int inY)
		: x(inX), y(inY)
	{
	}

	void ShowPosition()
	{
		std::cout << "x: " << x << "  " << "y: " << y << "\n";
	}

	int GetX() { return x; }
	int GetY() { return y; }
	void SetX(const int inX) { x = inX; }
	void SetY(const int inY) { y = inY; }

private:
	int x;
	int y;
};

int main()
{
	Player players[5];

	for (int ix = 0; ix < 5; ++ix)
	{
		players[ix].SetX(ix * 2);
		players[ix].SetY(ix * 3);
	}

	// Ranged Loop.
	for (Player& player : players)
	{
		player.ShowPosition();
	}
}
```

class로 선언한 Player 타입을 배열로 선언했다.

```
Player players[5];
```

배열 안에서 생성되는 객체는 다음 그림과 같은 형태가 된다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/array-img.png">

여기서 중요한 점은 객체가 배열 안에 존재한다는 것이다.



**객체 포인터 배열 선언**

객체 포인터 배열은 객체를 가리킬 수 있는 포인터로 구성된 배열이다.

```c++
#include <iostream>

class Player
{
public:
	Player()
		: x(0), y(0)
	{
		std::cout << "Player contructor call\n";
	}

	Player(int inX, int inY)
		: x(inX), y(inY)
	{
	}

	void ShowPosition()
	{
		std::cout << "x: " << x << "  " << "y: " << y << "\n";
	}

	int GetX() { return x; }
	int GetY() { return y; }
	void SetX(const int inX) { x = inX; }
	void SetY(const int inY) { y = inY; }


private:
	int x;
	int y;
};

int main()
{
	Player* players[5];

	for (int ix = 0; ix < 5; ++ix)
	{
		players[ix] = new Player(ix * 2, ix * 3);	// new 연산자를 사용한 객체 동적 생성.
	}

	for (Player* player : players)
	{
		player->ShowPosition();
	}

	for (int ix = 0; ix < 5; ++ix)
	{
		delete players[ix];		// 동적 할당한 객체 제거.
	}
}
```

위 코드는 main함수에서 객체 포인터 배열을 선언하고 있다.

```
Player* players[5];
```

배열 내부에는 Player 객체를 가리킬 수 있는 포인터 5개가 선언되어 있으며 이 때, 객체 배열과는 달리 선언하는 동시에 객체가 생성되지 않는다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/ptr-array-img.jpg">



**배열 안에서 객체 동적 할당**

```c++
for (int ix = 0; ix < 5; ++ix)
{
	players[ix] = new Player(ix * 2, ix * 3);	// new 연산자를 사용한 객체 동적 생성.
}
```

객체 포인터 선언 후 for 루프를 활용해 각각의 객체를 동적 할당을 통해 생성한다.

new 연산자로 생성된 객체의 주소를 각 배열의 포인터에 저장하고 있으며 생성된 객체는 다음 그림과 같이 저장된다.



또한 new 연산자를 통해 동적 할당된 객체는 제거하지 않으면 사용하지 않는데도 메모리가 남아 메모리 릭이 발생하므로 delete로 반드시 해제해야 한다.

```c++
for (int ix = 0; ix < 5; ++ix)
{
	delete players[ix];		// 동적 할당한 객체 제거.
}
```



#### this 포인터

멤버 함수 안에서 this라는 이름의 포인터 사용 가능하며 this는 자기 자신을 가리키는 포인터다.



#### friend 키워드

클래스에서 private로 선언된 멤버 변수 및 함수는 외부에서 접근이 허용되지 않지만 이에 예외를 두고 싶을 때 쓰는 키워드가 friend이다.

friend는 전역 함수 뿐만 아니라 다른 클래스에도 선언이 가능하다.



**friend 선언의 유용성 및 주의사항**

* private로 선언한 멤버 변수를 다른 클래스에서 접근해야 하는 상황이 빈번하게 발생할 수 있는데, 이 때 friend 키워드를 사용하면 해결이 가능하다.
* 하지만 이를 남용하게 되면 객체 지향 프로그래밍의 원리를 위배하는 결과가 나오기 때문에 주의해야 한다.



#### 전방 선언

한 클래스에서 다른 클래스를 포인터 변수로 사용할 때 해당 타입이 클래스라는 것을 컴파일러에게 알려주는 기능

**헤더 파일에 함수를 미리 선언하는 것** = **함수 전방 선언**

**(같은 원리로 클래스를 미리 선언하는 것을 클래스 전방 선언이라고 한다.)**

클래스 전방 선언 시 해당 클래스의 헤더를 포함시키지 않아도 되며 따라서 컴파일 시간을 단축할 수 있다.

클래스 전방 선언은 헤더 파일에서만 진행하며 cpp 파일에서는 필요한 클래스의 헤더를 포함(#include) 시켜서 사용한다.

```c++
#pragma once

// class Weapon;    // 여기에 전방 선언을 추가해도 됨.

class Player
{
public:
	Player();
	~Player();
	
	...
	
private:
	class Weapon* weapon = nullptr;    // 전방 선언.
};
```

Player.h



```c++
#include "Player.h"
#include "Weapon.h"    // 필요한 헤더 인클루드.
...
```

Player.cpp

---

### 복사 생성자

**같은 타입의 다른 인스턴스를 파라미터로 전달 받아 복사하는데 활용**

복사 생성자를 명시적으로 추가하지 않으면 기본 복사 생성자가 자동으로 추가된다.

```c++
#include <iostream>

class Player
{
public:
    // 생성자
	Player()
	{
		std::cout << "Player() call\n";
	}
	
    // 생성자 오버로딩
	Player(int number)
	{
		std::cout << "Player(int number) call\n";
	}
	
    // 복사 생성자
	Player(const Player& other)
	{
		std::cout << "Player(const Player& other) call\n";
	}
};

int main()
{
	Player player1;             // Player()
	Player player2(10);         // Player(int number)
	Player player3(player2);    // Player(const Player& other)
}
```



#### 깊은 복사

**기본 복사 생성자의 문제점은 다음과 같다.**

* 변수의 값을 그대로 대입한다.
* 값 타입의 데이터를 다룰 때는 자연스럽게 복사가 일어나기 때문에 문제가 없지만, 포인터 변수의 경우에는 문제가 된다.
* 포인터 변수도 단순히 값을 복사하기 때문에 결국 같은 주소를 저장하게 된다.
