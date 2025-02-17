# 자료구조 학습 정리

**2025/01/06 [포텐업] 게임 개발자 양성 과정**

---

## 선형 자료구조

### 배열

스택에 해당되는 기본 배열

```c++
template<typename T, size_t size>
class Array
{
public:
	size_t Size() const
	{
		return size;
	}

	// 배열을 인덱스로 접근해 읽고, 쓰려면 레퍼런스로 반환해야 한다.
	T& operator[](size_t index)
	{
		if (index >= size)
		{
			// 디버그 모드에서만 동작한다.
			__debugbreak();
		}

		return data[index];
	}

	const T& operator[](size_t index) const
	{
		if (index >= size)
		{
			// 디버그 모드에서만 동작한다.
			__debugbreak();
		}
	
		return data[index];
	}

	T* Data()
	{
		return data;
	}

	const T* Data() const
	{
		return data;
	}

private:
	T data[size];
};

int main()
{
	Array<int, 5> data;

	memset(data.Data(), 0, data.Size() * sizeof(int));
	
	std::cin.get();
}
```

---

### 동적 배열

#### Vector(벡터)

**크기가 동적으로 변하는 배열, Array list라고 부르기도 한다.**

다양한 데이터가 배열의 형태로 저장된 연속체라고 할 수 있으며 삽입, 삭제, 접근 연산이 모두 index에 의해 이뤄지게 된다.

**벡터의 추상 자료형(ADT)**

- at(integer i) : index i에 대해서 데이터 값을 반환해준다.
  - operator[](int index);
- set(integer i, object o) : index i의 데이터를 o로 바꿔준다.
  - operator[](int index);
- insert/pushback/emplace(integer i, object o) : index i에 o를 삽입한다.
- earase(integer i) : index i에 있는 데이터를 제거해준다.
- size() : 벡터의 크기를 반환해준다.
- empty() : 벡터가 비었는지를 알려준다.

<img src= "https://github.com/KwonJeHan/Study-cpp/blob/main/img/Vector_arch.png">



#### 힙에 할당되어 자동으로 크기가 늘어나는 배열

```c++
#pragma once

#include <iostream>

template <typename T>
class Vector
{
public:
    Vector()
    {
				ReAllocate(2);
    }
    
    ~Vector()
    {
				if (data != nullptr)
				{
						delete[] data;
				}
    }

    void PushBack(const T& value)
    {
        if (size == capacity)
        {
            ReAllocate(capacity + capacity / 2);
        }

        data[size] = value;
        size++;
    }

    void PushBack(T&& value)
    {
        if (size <= capacity)
        {
            ReAllocate(capacity + capacity / 2);
        }

        data[size] = std::move(value);
        size++;
    }

    size_t Size() const
    {
        return size;
    }

    size_t Capacity() const
    {
        return capacity;
    }

    const T& operator[](size_t index) const
    {
        if (index >= size)
        {
            __debugbreak();
        }

        return data[index];
    }

    T& operator[](size_t index)
    {
        if (index >= size)
        {
            __debugbreak();
        }

        return data[index];
    }

private:
		void ReAllocate(size_t newCapacity)
    {
        // 1. allocate a new block of memory.
        // 2. copy/move old elements into new block.
        // 3. delete.

        T* newBlock = new T[newCapacity];

        if (newCapacity < size)
        {
            size = newCapacity;
        }

        for (size_t ix = 0; ix < size; ++ix)
        {
            // newBlock[ix] = data[ix];
            newBlock[ix] = std::move(data[ix]);
        }

        delete[] data;
        data = newBlock;
        capacity = newCapacity;
    }

    T* data = nullptr;
    size_t size = 0;
    size_t capacity = 0;
};
```



#### Vector Iterator

직접 만든 Vector 클래스를 순회할 수 있는 Iterator를 만들 수 있다



**Iterator 클래스를 포함한 Vector 클래스**

Vector.h

```c++
#pragma once

#include <iostream>

template<typename Vector>
class VectorIterator
{
public:
	using ValueType = typename Vector::ValueType;
	using PointerType = ValueType*;
	using ReferenceType = ValueType&;

public:
	VectorIterator(PointerType ptr)
		: ptr(ptr)
	{
	}

	VectorIterator& operator++()
	{
		++ptr;
		return *this;
	}

	VectorIterator& operator++(int)
	{
		VectorIterator iterator = *this;
		++(*this);
		return iterator;
	}

	VectorIterator& operator--()
	{
		ptr--;
		return *this;
	}

	VectorIterator& operator--(int)
	{
		VectorIterator iterator = *this;
		--(*this);
		return iterator;
	}

	ReferenceType operator[](int index)
	{
		return *(ptr + index);
	}

	PointerType operator->()
	{
		return ptr;
	}

	ReferenceType operator*()
	{
		return *ptr;
	}

	bool operator==(const VectorIterator& other) const
	{
		return ptr == other.ptr;
	}

	bool operator!=(const VectorIterator& other) const
	{
		return !(*this == other);
	}

private:
	PointerType ptr;
};

template<typename T>
class Vector
{
public:
	using ValueType = T;
	using Iterator = VectorIterator<Vector<T>>;
	
public:
	Vector()
	{
		// allocate 2 elements.
		Reallocate(2);
	}

	~Vector()
	{
		delete[] data;
	}

	void PushBack(const T& value)
	{
		if (size >= capacity)
		{
			Reallocate(capacity + capacity / 2);
		}

		data[size] = value;
		size++;
	}

	void PushBack(T&& value)
	{
		if (size >= capacity)
		{
			Reallocate(capacity + capacity / 2);
		}

		data[size] = std::move(value);
		size++;
	}

	void PopBack()
	{
		if (size > 0)
		{
			size--;
			data[size].~T();
		}
	}

	void Clear()
	{
		for (size_t ix = 0; ix < size; ++ix)
		{
			data[ix].~T();
		}

		size = 0;
	}

	const T& operator[](size_t index) const
	{
		if (index >= size)
		{
			// assert.
			__debugbreak();
		}

		return data[index];
	}

	T& operator[](size_t index)
	{
		if (index >= size)
		{
			// assert.
			__debugbreak();
		}

		return data[index];
	}

	size_t Size() const { return size; }

	 

private:
	void Reallocate(size_t newCapacity)
	{
		// 1. allocate a new block of memory.
		T* newBlock = new T[newCapacity];

		// when vector is downsizing we need to check if new capacity is less than size.
		// in this case vector could be overflow.
		if (newCapacity < size)
		{
			size = newCapacity;
		}

		// 2. copy/move ole elements into new block.
		for (size_t ix = 0; ix < size; ++ix)
		{
			//newBlock[ix] = data[ix];
			newBlock[ix] = std::move(data[ix]);
		}

		// 3. delete
		delete[] data;
		data = newBlock;
		capacity = newCapacity;
	}

private:
	T* data = nullptr;

	size_t size = 0;
	size_t capacity = 0;
};
```



Main.cpp

```c++
#include <iostream>
#include "Vector.h"

int main()
{
	Vector<int> values;
	values.PushBack(1);
	values.PushBack(2);
	values.PushBack(3);
	values.PushBack(4);
	values.PushBack(5);

	std::cout << "Not using iterators:\n";
	for (int ix = 0; ix < values.Size(); ++ix)
	{
		std::cout << values[ix] << std::endl;
	}

	std::cout << "Range-based for loop:\n";
	//foreach()
	for (int value : values)
	{
		std::cout << value << std::endl;
	}

	std::cout << "Iterator:\n";
	for (Vector<int>::Iterator it = values.begin(); it != values.end(); ++it)
	//for (auto it = values.begin(); it != values.end(); ++it)
	{
		std::cout << *it << std::endl;
	}

	std::cin.get();
}
```
