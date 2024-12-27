# C++ 학습 정리

**2024/12/27 [포텐업] 게임 개발자 양성 과정**

---

### 클래스 상속

**코드를 재활용하기 위해 활용한다. (코드 중복 방지)**

두개 이상의 클래스 선언 시 각 클래스의 필요 기능이 비슷해 코드가 중복으로 구현될 것 같을때 상속을 활용할 수 있다.

```c++
#include <iostream>

class Entity
{
public:
	Entity(float x, float y)
		: x(x), y(y)
	{
	}

	void Move(float xa, float ya)
	{
		x += xa;
		y += ya;
	}
	
protected:
	float x;
	float y;
};

class Player : public Entity
{
public:
	Player(const char* name, float x, float y)
		: Entity(x, y)
	{
		size_t length = strlen(name) + 1;
		this->name = new char[length];
		strcpy_s(this->name, length, name);
	}
	
	~Player()
	{
		delete[] name;
	}

	void PrintName()
	{
		std::cout << name << std::endl;
	}
	
private:
	char* name;
};

int main()
{
	std::cout << sizeof(Player) << std::endl;
	
	Player player = Player("Player", 2.0f, 0.0f);
	player.Move(5, 5);
	player.PrintName();

	std::cin.get();
}
```

위와 같이 Player는 Entity와 비슷하게 위치와 이동 기능을 포함하고 이름을 담는 변수가 추가된 형식이다.

이 때 Entity 클래스를 활용해 Player 클래스를 구현할 수 있다.



#### 상속 클래스의 생성 소멸

상속하는 클래스의 생성 순서

1. 메모리 공간의 할당. 이때 상속되는 클래스를 감안해서 메모리 공간을 할당한다.
2. 부모 클래스의 생성자 실행
3. 자식 클래스의 생성자 실행

생성과 달리 소멸은 자식 클래스의 소멸자가 먼저 실행되고, 부모 클래스의 소멸자가 실행된다.

---

### 상속 관계 (IS - A/HAS - A)



#### Is-A 관계의 상속

앞 예제에서 Player 클래스는 Entity 클래스를 상속했다. 해당 관계를 **Is-A** 관계라고 한다.

```c++
class Player : public Entity
```

Is-A 관계를 설명할 때는 보통 화살표로 표기하며 방향은 자식 클래스에서 부모 클래스를 향한다. (반대 방향은 성립하지 않는다.)

```
Player -> Entity
```

```c++
#include <iostream>

class Computer
{
public:
	void Process()
	{
		std::cout << "Process complex computations.\n";
	}
};

class Developer : public Computer
{
public:
	void Work()
	{
		Process();
	}
};

int main()
{
	Developer developer;
	developer.Work();
}
```

기능적으론 문제없지만 관계를 생각해 볼 때 자연스럽지 않다.



#### HasA 관계의 상속

대부분의 상속은 Is-A관계로 형성되지만 모든 상속이 그런 것은 아니다. 그것이 **Has-A** 관계다.

한 객체가 다른 객체를 소유할 때 사용한다.

```c++
#include <iostream>

class Computer
{
public:
	void Process()
	{
		std::cout << "Process complex computations.\n";
	}
};

class Developer
{
public:
	void Work()
	{
		computer.Process();
	}
	
private;
	Computer computer;
};

int main()
{
	Developer developer;
	developer.Work();
}
```

---

### 객체와 포인터의 관계



#### 객체 포인터

int 타입의 포인터는 int 타입 변수의 주소를 저장할 수 있다. 즉, 포인터의 타입을 객체의 타입(클래스)으로 선언하면 객체의 주소 값을 저장할 수 있다. 이를 상속 관계까지 확장하면 자식 객체를 부모 객체로 치환해 저장하는 것도 가능하다.

```c++
#include <iostream>

class Person
{
public:
	void Sleep()
	{
		std::cout << "Sleep\n";
	}
};

class Student : public Person
{
public:
	void Study()
	{
		std::cout << "Study\n";
	}
};

class PartTimeStudent : public Student
{
public:
	void Work()
	{
		std::cout << "Work\n";
	}
};

int main()
{
	Person* person1 = new Person();
	Person* person2 = new Student();
	Person* person3 = new PartTimeStudent();

	person1->Sleep();
	person2->Sleep();
	person3->Sleep();
}
```

* person1은 Person 클래스를 가리킨다.
* person2는 Student 클래스를 가리킨다.
* person3는 PartTimeStudent 클래스를 가리킨다.

```
PartTimeStudent -> Student -> Person
```



**객체 포인터는 자신이 가리키는 메모리 공간에 관계 없이 기본적으로 자신의 타입에 정의된 함수 및 변수에만 접근이 가능하다.**

---

### Virtual 함수 (다형성)

**다형성이란 하나의 포인터 객체가 여러 타입을 가질 수 있는 것을 의미한다.**

#### 가상 함수

상위 클래스가 가진 함수에 virtual 키워드를 추가하면 이를 상속하는 하위 클래스에서 오버라이드가 가능하다.

```c++
#include <iostream>

class Entity
{
public:
	virtual const char* GetName() { return "Entity"; }
};

class Player : public Entity
{
public:
	Player(const char* name)
	{
		size_t length = strlen(name) + 1;
		this->name = new char[length];
		strcpy_s(this->name, length, name);
	}

	~Player()
	{
		delete[] name;
	}

	virtual const char* GetName() override { return name; }

private:
	char* name;
};

int main()
{
	//Entity* entity = new Entity();
	//std::cout << entity->GetName() << "\n";

	//Player* player = new Player("RonnieJ");
	//std::cout << player->GetName() << "\n";

	Entity* entity = new Entity();
	std::cout << entity->GetName() << "\n";

	Entity* player = new Player("RonnieJ");
	std::cout << player->GetName() << "\n";

	delete entity;
	delete player;

	std::cin.get();
}
```

오버라이딩 시 기반 클래스의 가상 함수는 가려지는데 이때 기능을 완전히 대체하는 것이 아닌 기능을 더해 확장하고 싶을 때는 C++ 범위 연산자인 (::)를 활용해 기반 클래스의 가상 함수를 호출할 수 있다.

```c++
#include <iostream>

class Entity
{
public:
	virtual const char* GetName() { return "Entity"; }
	virtual void Print()
	{
		std::cout << "Entity\n";
	}
};

class Player : public Entity
{
public:
	Player(const char* name)
	{
		size_t length = strlen(name) + 1;
		this->name = new char[length];
		strcpy_s(this->name, length, name);
	}

	~Player()
	{
		delete[] name;
	}

	virtual const char* GetName() override { return name; }
	virtual void Print() override
	{
		Entity::Print();
		std::cout << name << "\n";
	}

private:
	char* name;
};

int main()
{
	Entity* entity = new Entity();
	entity->Print();

	Entity* player = new Player("RonnieJ");
	player->Print();

	delete entity;
	delete player;

	std::cin.get();
}
```



#### 가상 소멸자

**가상 함수와 마찬가지로 virtual 키워드가 필요한 소멸자이다.** (메모리 릭이 발생하지 않게 하려면 가상 함수 오버라이딩 사용 시 함께 사용해야 한다.)



#### 순수 가상 함수

**가상함수는 필요할 때만 재정의 하지만 순수 가상 함수는 반드시 재정의 해야 한다.**

순수 가상 함수는 내용을 가지지 않고, 선언만 존재하는데 내용을 가지지 않는 의미로 함수 구문 끝에 =0;을 붙인다. 따라서 이대로는 호출이 불가능 하다.

```c++
#include <iostream>

class Graphics
{
public:
	virtual void Draw() = 0;    // 순수 가상 함수.
};

class Line : public Graphics
{
public:
	virtual void Draw() override
	{
		std::cout << "Draw a line\n";
	}
};

class Circle : public Graphics
{
public:
	virtual void Draw() override
	{
		std::cout << "Draw a circle\n";
	}
};

class Rectangle : public Graphics
{
public:
	virtual void Draw() override
	{
		std::cout << "Draw a rectangle\n";
	}
};

int main()
{
	//Graphics* graphics = new Graphics();    // 오류.
	Graphics* line = new Line();
	Graphics* circle = new Circle();
	Graphics* rect = new Rectangle();
	
	line->Draw();
	circle->Draw();
	rect->Draw();
	
	delete line;
	delete circle;
	delete rect;
}
```



**추상 클래스**

순수 가상 함수를 가지는 클래스로 위 코드의 Graphics 클래스가 예시이다.

추상 클래스는 선언만 있고 본문이 없는 멤버 함수를 가지므로 그대로는 인스턴스를 생성할 수 없다. 실제로 위 코드 main 함수의 주석을 해제하면 오류가 발생한다.

이렇게 보면 추상 클래스는 의미가 없어보이지만, 설계 측면에서 객체 집합의 틀을 제공한다는 의미에서 중요하다.

위 예제를 보면 Line, Circle, Rectangle 등의 집합에서 필수로 제공해야 하는 Draw 함수의 구현을 Graphics 클래스를 통해 강제하는 것을 볼 수 있다.



**인터페이스**

C++ 은 인터페이스 문법이 없지만 인터페이스의 **"함수의 본문을 가지지 않고 선언만 제공하는 타입으로 그 자체로는 인스턴스를 생성할 수 없고, 반드시 파생 클래스 타입으로 생성해야 한다."**라는  특징이 추상 클래스의 특징과 매우 닮아있어 이를 순수 가상 함수를 활용해 구현한다.

---

### 연산자 오버로딩



