# C++ 학습 정리

**2024/12/30 [포텐업] 게임 개발자 양성 과정**

---

### 형변환

C++ 은 네가지 형변환 방법을 제공한다.

* const_cast()
* static_cast()
* reinterpret_cast()
* dynamic_cast()



#### const cast

변수에 const 속성을 추가하거나 제거할 때 사용한다. 원칙적으로 사용할 일이 없어야 하지만 부득이하게 const 속성을 제거해야 할 때 사용한다.



#### static_cast()

C 형 변환의 제한된 버전으로 정확도의 손실이 발생하더라도 기본 데이터형 간의 변환을 수행한다.



#### reinterpret_cast()

어떤 데이터 타입이라도 다른 타입으로 변환이 가능하며 어떤 포인터 타입이라도 다른 포인터 타입으로 변환이 가능하다.

그만큼 강력하지만 안정성은 떨어진다.



#### dynamic_cast()

같은 상속 계층에 속한 타입끼리 형변환할 때 실행 시간에 타입을 검사한다.

실행 시간에 내부 객체의 타입 정보를 검사하기 때문에 형 변환이 적절하지 않다고 판단되면 포인터에 대해서는 nullptr을 반환하고, 레퍼런스에 대해서는 std::bad_cast 예외를 발생시킨다.

적어도 한 개 이상의 virtual 메소드가 있어야 한다. 아니면 컴파일 에러가 발생한다.



| **상황**                                                     | **형변환 방법**                           |
| ------------------------------------------------------------ | ----------------------------------------- |
| const 속성 제거                                              | const_cast()                              |
| 언어에서 허용하는 명시적 변환 (예: int를 double로, int를 bool로) | static_cast()                             |
| 사용자 정의 생성자나 변환 연산자에서 지원하는 명시적 변환    | static_cast()                             |
| 서로 관련 없는 타입의 객체끼리 변환                          | 불가능                                    |
| 같은 상속 계층에 있는 클래스 타입의 객체 포인터 사이의 변환  | dynamic_cast() 권장, static_cast()도 가능 |
| 같은 상속 계층에 있는 클래스 타입의 객체 레퍼런스 사이의 변환 | dynamic_cast() 권장, static_cast()도 가능 |
| 서로 관련 없는 타입의 포인터 사이의 변환                     | rereinterpret_cast() (위험할 수 있음)     |
| 서로 관련 없는 타입의 레퍼런스 사이의 변환                   | reinterpret_cast() (위험할 수 있음)       |
| 함수 포인터 사이의 변환                                      | reinterpret_cast()                        |

---

### RTTI

**RunTime Type Information의 약자로 번역하면 실시간 타입 정보라는 뜻이다.**

일반적으로 변수의 이름이나 구조체, 클래스의 타입은 컴파일러가 컴파일하는 동안에만 필요하기 때문에 컴파일 이후에는 정보가 남아있지 않다. 하지만 특정 객체의 정보(클래스의 이름, 어떤 클래스를 상속했는지 등)를 알아야 할 때가 있는데 이 때 필요한 것이 RTTI이다.



#### dymamic_cast와 typeid

* **dynamic_cast**
  * 시도하는 형변환 작업이 올바른지 검사
  * 포인터를 새로운 타입으로 형변환
* **typeid**
  * 객체에 대한 보다 자세한 정보를 제공
  * 객체의 타입에 대한 정보를 얻을 때 사용
  * 객체에 대한 모든 정보는 typeid가 반환하는 type_info에 저장
  * 다형성이 구현된 타입에만 적용이 된다. 즉, 적어도 하나의 가상 함수를 가진 클래스에만 적용해야 한다.



#### 표준 C++ RTTI의 단점

가장 큰 단점은 **성능**이다. 간헐적으로 사용할 경우 문제가 되지 않을 수 있지만, 게임 프로그래밍 환경처럼 속도가 중요한 경우 달갑지 않은 문제이다. 따라서 커스텀 RTTI 시스템을 구현해 사용한다.

---

### 템플릿(template)

형판, 틀, 패턴 등의 뜻을 가진다.



#### 함수 템플릿

비슷한 모양의 함수를 작성해야 할 때 매번 각 함수들을 직접 정의하지 않고 함수 템플릿을 선언해 사용한다.



**함수 템플릿 정의 방법**

* template 키워드 이후 <>괄호를 작성해 괄호 안에 템플릿으로 전달할 파라미터를 나열한다.
* 파라미터 목록에는 typename 키워드 다음에 함수 본문에서 사용할 타입의 이름을 작성하는데 보통 T 또는 Type을 많이 사용한다.
* 파라미터가 여러개인 경우 T1, T2, T3처럼 이름만 구분해서 지정해주면 된다.
* T로 정의된 부분은 실제 사용할 때 전달되는 타입에 따라 자동으로 변경된다.



```c++
#include <iostream>

template<typename T>
void Swap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}

void main()
{
	int number1 = 10;
	int number2 = 20;
	Swap(number1, number2);
	
	float number3 = 3.14f;
	float number4 = 5.12f;
	Swap(number3, number4);
	
	std::cout << "number1: " << number1 << ", number2: " << number2 << "\n";
	std::cout << "number3: " << number3 << ", number4: " << number4 << "\n";
}
```



#### 클래스 템플릿

하나의 특정 형 데이터들을 저장하는 클래스가 있을 때 다른 형의 데이터들을 저장해야되는 상황이 발생할 수도 있다. 이런 경우 클래스 템플릿을 사용하면 쉽게 해결할 수 있다.

클래스 선언 구문 위에 template<typename T>를 추가하고 기존에 선언했던 데이터형 부분을 T로 변경하면 템플릿 클래스를 작성할 수 있다.

```c++
#include <iostream>

template<typename T>
class Data
{
public:
	Data(T newData)
		: data(newData)
	{
	}

	void SetData(T newData)
	{
		data = newData;
	}

	T GetData() const { return data; }

private:
	T data;
};

int main()
{
	Data<int> data1 = Data<int>(0);
	data1.SetData(100);

	Data<float> data2 = Data<float>(3.1415f);

	std::cout << data1.GetData() << "\n";
	std::cout << data2.GetData() << "\n";
}
```

**템플릿은 그저 틀을 제공할 뿐, 그 자체로는 함수를 호출할 수 없다.**

---

### C 스타일 파일 입출력



#### 파일 열기 및 닫기



**파일 열기**

파일에 접근하려면 우선 파일을 열어야 한다(File Open)

파일을 연다는건 파일에 저장된 데이터를 읽고 쓰기 위한 준비를 한다는 의미



**파일 오픈 함수**

파일을 오픈할 때 fopen_s 함수를 사용한다.

첫 번째 파라미터로 입출력에 필요한 FILE 포인터를 전달하고, 두 번째 파라미터로 오픈할 파일의 이름(경로 및 확장자 포함)을 전달, 세 번째 파라미터로 파일을 어떻게 열 것인지 지정하는 모드를 전달한다.

```c++
errno_t fopen_s(FILE** stream, const char* filename, const char* mode);
```



**파일 이름**

오픈할 파일 이름으로 현재 위치 기준 상대 경로 혹은 절대 경로를 사용한다.

폴더 구분 문자로 /를 사용하거나 \\\를 사용한다. 또한 운영체제 별로 대소문자 구분이 다른데 윈도우의 경우 대소문자를 구분하지 않는다.



**모드**

파일을 어떤 방식으로 열 것인지 지정하는데 사용한다.

| 모드 | 설명                                                         |
| :--: | ------------------------------------------------------------ |
|  r   | 읽기 전용으로 파일을 연다. 이 모드로 파일을 열면 읽기만 가능하다. 파일을 찾지 못하면 오류가 반환(리턴)된다. |
|  w   | 데이터를 쓸 목적으로 파일을 열 때 사용한다. 이 모드로 연 파일은 쓰기만 가능하기 때문에 읽지는 못한다. 참고로, 윈도우는 쓰기 전용 속성이 없지만, 스트림은 쓰기 전용 상태로 열 수 있다. 파일이 없는 경우 새로 생성하며 파일이 있는 경우에는 기존 파일을 덮어쓴다. |
|  a   | 데이터를 추가할 목적으로 파일을 열 때 사용한다. 즉, 파일 끝에 데이터를 추가한다. 이 모드로 파일을 열면, 파일을 연 직후에 파일 포인터(File Position)가 파일의 끝 위치로 이동한다. 파일이 없는 경우 새로 생성한다. |
|  r+  | 읽고 쓰기가 가능하도록 파일을 연다. 파일이 없을 경우 에러를 반환한다. |
|  w+  | 읽고 쓰기가 가능하도록 파일을 연다. 파일이 없는 경우 생성한다. |
|  a+  | 읽기와 추가가 가능하도록 파일을 연다. 파일이 없는 경우 생성한다. |



**파일 형태**

fopen_s의 세 번째 파라미터 mode에는 오픈 모드 외에도 파일의 형태를 지정하는 플래그를 추가로 지정할 수 있다.

(열려는 파일이 텍스트 파일이면 t를, 바이너리(이진) 파일이면 b를 붙인다.)

- 바이너리 파일은 아무 변환을 하지 않고 그대로 읽는다.
- 텍스트 파일 모드로 파일을 열면 두 가지 변환을 진행한다.
  1. 개행 코드를 의미하는 CR/LF 조합은 LF로 변환해 읽히며 LF를 기록하면 CR/LF가 출력 된다. C 문자열 출력 함수들이 개행을 위해 LF(\n)을 사용하기 때문이다.
  2. 파일의 끝을 나타내는 Ctrl+Z(0x1A)는 EOF(-1)로 변환되어 읽힌다. 단 “a+” 모드로 열었을 때는 데이터를 끝 부분에 추가할 수 있도록 Ctrl+Z를 제거한다.

오픈 모드와 파일 형태가 mode 파라미터에 같이 전달되는데, 오픈 모드가 먼저 오고 파일 형태가 나중에 오는 형식으로 써야 한다. 단 +는 파일 형태 다음에 와도 상관 없다.

* “rt” : 텍스트 파일을 읽기 전용으로 읽는다.
* “wb” : 이진 파일을 쓰기 전용으로 연다.
* “r+b” : 이진 파일을 읽기, 쓰기가 가능하도록 연다. “rb+”도 가능.



**반환 값**

fopen_s 함수는 지정한 파일을 지정한 모드로 열고 입출력에 필요한 FILE 구조체를 생성한 후 그 포인터를 첫 번째 파라미터로 전달된 변수에 설정한다. (오류 발생 시 errno_t 타입의 오류 객체 반환)



**파일 닫기**

fopen_s로 파일 열기에 성공했으면 입출력 함수를 활용해 파일 내부 데이터에 접근할 수 있다. 파일을 모두 사용한 후에는 fclose 함수를 사용해 닫아야 한다.

```c++
int fclose(FILE* stream);
```



#### 파일 액세스



 **파일에 문자열 쓰기**

파일에 문자열을 쓸 때 fputs 함수를 사용한다.



**파일에서 문자열 읽기**

파일에서 문자열을 읽을 때 fgets 함수를 사용한다. 두 번째 파라미터는 2보다 큰 값이면 어떤 값을 설정해도 되지만 값이 너무 작으면 조금씩 자주 읽어야 하므로 성능에 영향을 줄 수 있다.



**feof 함수**

파라미터로 전달받은 스트림이 파일의 끝에 도달했는지 확인한다. (eof = End Of File)

따라서 이 함수가 true를 반환할 때 까지 반복해서 fgets 함수를 호출하면 파일의 끝까지 모든 내용을 읽을 수 있다.



**한 문자씩 읽고 쓰는 함수**

다음 두 함수는 스트림으로부터 한 무자씩 입출력한다.

```c++
int fgetc(FILE* stream);
int fputc(int character, FILE* stream);
```



**블록 단위로 읽고 쓰는 함수**

다음 두 함수는 블록 단위의 입출력이 필요할 때 사용할 수 있다.

```c++
size_t fread(void*  buffer, size_t elementSize, size_t elementCount, FILE*  stream);

size_t fwrite(void const* buffer, size_t elementSize, size_t elementCount, FILE* stream);
```

두 함수는 buffer에 저장된 bufferSize(elementSize) 크기의 메모리 블록 elementCount 개를 스트림으로 입출력하며 실제로 입출력한 길이를 반환한다. 대부분 지정한 크기만큼 입출력을 처리하지만, 파일의 끝 부분을 읽거나 디스크가 가득 찬 경우에는 더 작은 크기를 입출력할 수도 있다.



**fread/fwrite 함수를 활용한 파일 복사**

```c++
#include <iostream>

int main()
{
	char buffer[256];
	FILE* file = nullptr;
	fopen_s(&file, "Test.txt", "rb");
	if (file != nullptr)
	{
		FILE* newFile = nullptr;
		fopen_s(&newFile, "Test2.txt", "wb");
		if (newFile != nullptr)
		{
			while (!feof(file))
			{
				size_t readSize = fread(buffer, 1, 256, file);
				fwrite(buffer, 1, readSize, newFile);
			}

			fclose(newFile);
		}

		fclose(file);
	}
}
```



**포맷 지정 파일 입출력**

파일의 내용을 읽고 쓸 때 데이터가 일반 텍스트가 아니라 int, float, 문자열 등 다양하다면 fscanf, fprintf 함수를 사용해 포맷을 지정하여 입출력을 하면 된다. (사용 방법은 scanf, printf와 동일하지만 대상이 파일이라는 점만 다르다.)

```c++
int fscanf(FILE* stream, const char* format, ...);
int fprintf(FILE* stream, const char* format, ...);
```



#### 파일의 임의 접근

파일 스트림은 다음에 입출력을 진행할 파일의 위치를 항상 기억하고 있다.이 위치를 FP(FilePosition)라고 한다. 처음 파일을 열면 FP가 파일의 첫 부분을 가리키며 내용을 일거나 쓰면 액세스 한 만큼 FP가 자동으로 뒤로 이동하는데 이런 방식을 순차 접근이라고 한다.

**반면, 원하는 위치로 한 번에 이동하면서 읽는 방법을 임의 접근이라고 한다.**



**fseek 함수**

첫 번째 파라미터는 대상 스트림, 두 번째 파라미터 offset는 FP를 어디로 옮길 지 지정, 세 번째 파라미터 origin는 어느 위치를 기준으로 FP를 옮길 것인지 지정한다.

세 번째 파라미터에서 사용할 수 있는 값

1. SEEK_SET: 스트림 처음 위치 기준
2. SEEK_CUR: 현재 위치 기준 (방향에 따라 음수, 양수 모두 가능)
3. SEEK_END: 스트림의 끝 위치 기준 (offset이 음수여야 한다.)

```c++
int fseek(FILE* stream, long offset, int origin);
```



**ftell/rewind 함수**

**ftell 함수는 FP의 현재 위치를 반환한다.** 일반적으로는 파일의 전체 크기를 확인하기 위해 fseek(file, 0, SEEK_END) 함수를 사용해 파일의 끝 위치로 FP를 이동 시킨 후 ftell 함수를 통해 FP의 위치를 구하는 방식으로 활용한다.

**rewind는 FP를 다시 처음으로 되돌릴 때 사용한다.** rewind는 fseek(file, 0, SEEK_SET)과 동일한 기능을 제공한다.

---

### C++ 스타일 파일 입출력



#### offstream과 ifstream

파일 입출력에 사용되는 클래스로 char 타입을 대상으로 한다. (wifstream과 wofstream 클래스는 wchar_t 타입을 대상으로 하는 클래스)

(fstream 헤더 파일 에 선언되어 있으므로 헤더를 포함시켜야 한다.)



**파일 출력 예제**

```c++
#include <iostream>
#include <fstream>

int main()
{
	std::ofstream file;
	file.open("CPP_Test.txt");
	file << "String " << 132756 << " " << 3.141592 << "\n";
	file.close();
}
```



**파일 입력 예제**

```c++
#include <iostream>
#include <fstream>

int main()
{
	std::ifstream file("CPP_Test.txt");
	char stringData[256];
	int intData;
	float floatData;

	file >> stringData >> intData >> floatData;
	std::cout << stringData << " " << intData << " "  << floatData << "\n";
	file.close();
}
```



#### 파일 열기 확인

ifstream으로 파일을 읽을 때 파일이 없는 경우, 오류가 발생한다. 이를 위해 is_open 함수를 사용해 파일이 제대로 열렸는지 확인할 수 있다.

```c++
#include <iostream>
#include <fstream>

int main()
{
	std::ifstream file("Ronnie.txt");
	if (file.is_open())
	{
		std::cout << "파일 열기 성공\n";
	}
	else
	{
		std::cout << "파일 열기 실패\n";
	}
}
```

파일이 없기 때문에 "파일 열기 실패"가 출력된다.



#### 모드

파일을 열 때 사용하는 open 함수는 mode를 지정할 수 있다.

| **모드**         | **설명**                                                     |
| ---------------- | ------------------------------------------------------------ |
| ios_base::in     | 입력용으로 파일을 연다.                                      |
| ios_base::out    | 출력용으로 파일을 연다.                                      |
| ios_base::app    | 파일 끝에 데이터를 추가하는 모드로 파일을 연다. 데이터를 추가하는 것만 가능하다. |
| ios_base::ate    | 파일을 열자마자 FP를 파일의 끝 위치로 이동시킨다. FP를 임의의 위치로 이동 시킬 수 있다. |
| ios_base::trunc  | 파일이 이미 존재하는 경우, 데이터를 모두 지워 크기를 0으로 만든다. |
| ios_base::binary | 텍스트 모드가 아닌 바이너리 파일 모드로 연다.                |



#### read와 write 함수

파일을 읽고 쓸 때 사용한다.

```c++
basic_istremm& read(char *stream, streamsize size);
basic_ostream& write(const char *stream, streamsize size);
```



#### 임의 접근

FP를 임의의 위치로 이동시킬 때 두 가지 함수를 사용할 수 있다. 입력용, 출력용 FP를 따로 유지하기 위해 두 가지 함수가 있다.

첫 번째 파라미터는 어느 위치로 이동할 것인지를 나타내고 두 번째 파라미터는 이동의 기준점을 나타낸다.

두 번째 파라미터는 ios_base::beg, ios_base::cur, ios_base::end를 지정할 수 있으며 각각 파일의 시작 위치, 현재 위치, 파일의 끝 위치를 기준점으로 지정하는데 사용한다

```c++
basic_istream& seekg(off_type off, ios_base::seek_dir way);    // 입력용 임의 접근 함수.
basic_ostream& seekp(off_type off, ios_base::seek_dir way);    // 출력용 임의 접근 함수.
```



#### 파일의 현재 위치 반환 함수

C의 ftell과 같은 기능을 하며 각각 입력용, 출력용 함수를 구분해 제공된다.

```c++
pos_type tellg();
pos_type tellp();
```
