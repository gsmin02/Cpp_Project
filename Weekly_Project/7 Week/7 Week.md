# 객체와 멤버호출

## private(protected)과 public 멤버의 접근 방법
- private protected
    - 외부에서 접근 불가
- public
    - 외부에서 접근 가능

```cpp
#include <iostream>
class Dog {
private:
    int age;
public:
    int getAge() {
        return age;
    }
    void setAge(int a) {
        age = a;
    }
};
int main() {
    Dog happy;
    happy.setAge(3);
    std::cout << happy.getAge();
    return 0;
}
```

## 객체의 멤버 호출
- 직접참조연산자 : .
    - 인반 객체가 멤버(변수/함수)에 접근하기 위해 사용
- 간접참조연산자 : ->
    - 포인터 객체가 멤버(변수/함수)에 접근하기 위해 사용

```cpp
class Dog{
private: // 속성
    int age; // 멤버변수
public:
    int getAge(); // 멤버함수
    void bark();
};
Dog happy, *pHappy; // 객체
```

- happy.age (age가 private이므로 작동하지 않음)
- happy.getAge() // 해피의 나이를 얻는다.
- happy.bark() // 해피가 짖는다.
- pHappy->getAge() // pHappy의 나이를 얻는다.
- pHappy->bark() // 포인터 객체 pHappy가 짖는다.

## 클래스와 객체 (인스턴스)
```cpp
#include <iostream>
using namespace std;
class Dog {
private:
    int age;
    double weight;
    string name;
public:
    int getAge() {
        return age;
    }
    void setAge(int a) {
        age = a;
    }
    double getWeight() {
        return weight;
    }
    void setWeight(double w) {
        weight = w;
    }
    string getName() {
        return name;
    }
    void setName(string n) {
        name = n;
    }
};

int main() {
    Dog happy;
    happy.setAge(3);
    happy.setWeight(3.5);
    happy.setName("해피");
    cout << happy.getName() << "는 " << happy.getAge() << "살, " << happy.getWeight() << "kg입니다.\n";
    return 0;
}
```

# 배열

## 배열
- 배열이란 연속적인 항목들이 동일한 크기의 순서를 갖고 나열되어 있는 데이터의 집합

## 일차원 배열
- 배열명 다음에 구두점 대괄호([])를 쓰며 대괄호 안에 배열의 크기를 나타내는 수를 하나 씀
    - 첨자(subscript) 또는 인덱스(index)
- 자료형 배열명\[첨자\];
- int score\[7\];
    - 배열명 만드는 규칙은 변수명 만드는 규칙과 동일
    - 배열 선언문에서 사용하는 첨자는 양의 정수이며 배열의 크기
    - score배열은 정수형 자료 7개를 저장할 수 있음
    - 7개의 공간을 배열의 원소(element)라 함

## 배열 원소 예
```cpp
#include <stdio.h>
int main(void) {
    int num[3]; // 배열 선언시 첨자의 값은 배열의 크기

    num[0] = 10; // 배열 원소(element)의 첨자는 순서
    num[1] = 20;
    num[2] = 30;
    // num[3] = 40; // 배열의 크기는 3개이고 num[3]는 4번째 원소이기 때문에 에러
    printf("%d, %d, %d ", num[0], num[1], num[2]);
    return 0;
}
```

## 일차원 배열 초기화
- 일차원 배열 초기화 방법
    - int score\[5\] = { 10, 20, 30, 40, 50 }; // int x = 10;
    - 변수 초기화오아 달리 원소가 많으므로 중괄호({})로 묶어 줌
    - score\[0\]에는 10이, score\[1\]에는 20 등이 차례대로 초기화됨
- 문자형 배열 초기화 방법
    - char name[ ] = {'G', 'o', 'o', ' ', ' S', ' ', 'M', '\0'};
    - 배열 선언과 함께 초기화까지 할 경우 원소의 개수 8은 생략 가능
    - 문자 배열의 마지막 원소는 반드시 널(NULL) 문자인 '\0'
    - 문자형 배열은 문자열과 관련이 있는데 C 언어에서 문자열은 항상 널 문자로 끝나기 때문
- 문자 배열은 무자열 형태로 초기화할 수도 있음
    - char name[ ] = "Goo S M";
    - 널 문자가 자동으로 마지막 원소에 할당됨
    - 원소의 개수는 8개

## 배열의 초기화
```cpp
#include <stdio.h>
int main(void) {
    int score[5] = { 10, 20, 30, 40, 50 };
    char name[] = {'G', 'o', 'o', ' ', 'S', ' ', 'M', '\0' };
    char name1[] = "Goo S M";
    printf("%d %d %d\n", score[0], score[1], score[4]);
    printf("%c%c%c%c%c\n", name[1], name[7], name[0], name[3], name[0]);
    printf("%c%c%c%c%c\n", name1p1[1] name1[7], name1[0], name1[3], name1[0]);
    return 0;
}
```

## 배열 초기화 방법
- 배열 원소가 초기화 데이터 수보다 많으면 나머지 원소들은 0으로 초기화됨
- 100개의 원소를 갖는 배열을 2개만 초기화하면 나머지 98개는 모두 0으로 자동 초기화
- 배열 원소의 수가 초기화한 데이터 수보다 적으면 "초기화 데이터가 너무 많다"라는 에러가 발생함
    - error C2078: 이니셜라이저가 너무 많습니다.
- 배열을 선언과 동시에 초기화한 경우와 선언 먼저하고 값을 대입한 경우인데 각 원소에는 같은 값이 할당됨

## 다차원 배열
- 다차원 배열은 2차원 배열, 3차원 배열 등 n차원 배열이 가능
- 일반적으로 3차원 이사의 배열은 이해하기 어려워서 잘 사용하지 않음
- 2차원 배열 x의 초기화는 두 가지 방법
    - int x\[3\]\[2\] = {1, 2, 3, 4, 5, 6};
    - int x\[3\]\[2\] = { {1, 2}, {3, 4}, {5, 6} };
- 2차원 배열도 물리적으로는 1차원적으로 저장
- 배열의 전체 크기는 선언시 사용한 첨자를 곱(3*2)하면 되고 마지막 원소는 x\[3\]\[2\]가 아니라 x\[2\]\[1\]인 것을 명심해야 함

## 문자열과 문자형 배열
- 문자열(string)은 두 개 이상의 문자 묶음
- 문자열 상수는 문자열 양쪽을 큰 따옴표(" ")로 감싸야 함
    - abc는 "abc"
    - 대한민국은 "대한민국"
- 문자열 상수는 각 문자가 한 바이트 씩 저장되므로 문자열 "ABC"는 ASCII코드 값(65 66 67 0)에 해당하는 2진수 메모리에 저장됨
- 문자열은 문자형 배열에 두 가지 방법으로 초기화할 수 있음
    - char eng\[4\] = {'A', 'B', 'C', '\0'}
    - char eng\[4\] = "ABC";
- 문자열 상수에서는 문자열의 끝을 의미하는 널 문자가 제일 뒤에 자동적으로 붙여짐
- 'a'는 문자로 1바이트에 저장되고, "a"는 문자열로 뒤에 널 문자가 있으므로 2바이트에 저장됨

## int형, char형 값 복사
```cpp
#include<iostream>
int main(void) {
    int x;
    int y = 10;
    char a, b = 'A';
    x = y;
    std::cout << "x=" << x << " y=" << y << std::endl;
    a = b;
    std::cout << "a=" << a << " b=" << b << std::endl;
    return 0;
}
```

## 배열 복사 - strcpy()
```cpp
#define _CRT_SECURE_NO_WARNINGS // Visual Studio의 경우
#include <iostream>
#include <string> // or string.h(Clang++, gcc 등 주로 온라인 컴파일러)

int main(void) {
    char s1[5];
    char s2[5] = "soft"; // 원본
    // s1 = s2; // error C3863: 배열 형식 'char [5]'은(는) 할당할 수 없습니다.
    strcpy(s1, s2); // s2 주소의 문자열을 널 문자를 만날 때까지 s1주소로 복사
    std::cout << "s1=" << s1 << " s2=" << s2 << std::endl;
    return 0;
}
```

## 문자열 복사: 배열 vs string
```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <string> //or string.h
int main(void) {
    char s1[5];
    char s2[5] = "soft";
    strcpy(s1, s2); //배열 복사
    std::cout << "s1=" << s1 << " s2=" << s2<< std::endl;
    return 0;
}
```
```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
int main(void) {
    std::string s1;
    std::string s2 = "soft";
    s1 = s2; //string형 복사는 그냥 대입
    //strcpy(s1, s2);
    std::cout << "s1=" << s1 << " s2=" << s2;
    return 0;
}
```

# 생성자와 소멸자

## 생성자와 소멸자
- 생성자(constructor)와 소멸자(destructor)라는 멤버함수는 사용자가 꼭 정의하지 않아도 되는 함수이다.
- 그렇다고 해서 존재하지 않는 것은 아니며 시스템 내부에서 언제다 객체의 생성과 소멸을 담당한다.
- 사용자가 이를 좀더 유용하게 사용하고자 하는 경우에만 가시화시켜 클래스 내부에 선언, 정의한다.

## 생성자(constructor)
- 일반 자료형(int, float, char 등)의 경우 컴파일러가 알아서 처리해 주지만 사용자 정의형인 클래스는 컴파일러가 아닌 다른 곳에서 객체를 초기화한다.
- 이 작업을 담당하는 함수가 바로 생성자이다.
- 생성자는 사용자가 특별히 지정하지 않아도 자동으로 호출되지만 멤버에 대한 초기화 자료를 지정하지 않으면 객체 멤버변수들은 쓰레기(garbage) 값을 갖는다.
- 즉, 생성자는 주로 멤버변수의 초기화를 한다.

## 생성자의 특징
- 생성자의 이름은 클래스명과 같다.
- 클래스의 객체가 생성될 때마다 자동으로 호출된다.
- 보통 객체가 메모리에 할당될 때 멤버변수의 초기화를 담당한다.
- 리턴형을 쓰지 않는다.
    - 리턴값이 존재하지 않으며 void형을 지정해도 안된다.
    - C/C++ 언어에서는 리턴값을 생략하면 int형인데 생성자는 예외이다.
- 생성되는 객체마다 초기화 값이 다를 수 있으므로 하나의 클래스에 여러 개의 생성자가 존재할 수 있다.
    - 매개변수는 달라야한다.
- 객체가 생기면서 자동 호출되며, 사용자가 호출할 수는 없다.
- 생성자가 반드시 있어야 하는 것은 아니지만 메모리는 초기화 한다는 의미에서 있는 것이 좋다.

## 생성자 예
```cpp
#include <iostream>
using std::cout;
class Dog{
private:
    int age;
public:
    Dog(int a) {
        age = a;
    }
    int getAge() {
        return age;
    }
    void setAge(int a) {
        age = a;
    }
};

int main() {
    Dog coco(4); // 4는 생성자로 넘어감
    Dog coco1{3}; // Uniform initialization
    Dog coco2 = Dog(2); // 비추
    Dog coco3 = 1; // 비추
    cout << coco.getAge() << coco1. getAge() << coco2.getAge() << coco3.getAge();
    return 0;
}
```
```cpp
#include <iostream>
using std::cout;
class Dog{
private:
    int age;
public:
    Dog(int a):age(a){}
    // Dog(int a):age{a}{}
    int getAge() {
        return age;
    }
    void setAge(int a) {
        age = a;
    }
}
```
- Dog 클래스에는 생성자가 없음
- Dog(){} 같은 생성자를 자동으로 만들어 줌
- 이를 implicitly generated constructor라 함
- 묵시적(자동)으로 만들어지는 생성자

## 소멸자(destructor)
- 클래스의 객체가 소멸될 때 자동으로 호출된다.
- 소멸자의 이름은 클래스명과 같고, 앞에 ~(title)를 붙인다.
- 클래스명이 Dog라면 소멸자 이름은 ~Dog()
- 하나의 클래스에 유일하다.
    - 생성자는 중첩이 가능하지만 소멸자 중첩은 불가능하다.
- 리턴형과 매개변수가 없다.
    - 리턴값이 존재하지 않으며 void형을 지정해도 안된다.
    - ~Dog();
- 사용자가 직접 호출할 수는 없다.

## 소멸자의 용도
- 객체가 소멸될 때 자동으로 호출되므로 객체가 소멸될 때 하고 싶은 코드를 작성한다.
- 소멸자는 사용한 메모리 공간이 더 이상 불필요하게 될 때 해당 메모리를 시스템이나 다른 객체에 반납하는 용도로 많이 사용하는 함수이다.
    - 한 객체가 사용한 메모리 공간을 해제하지 않으면 해당 공간은 다른 프로그램에서 사용할 수 없다.

## 소멸자 예
```cpp
#include <iostream>
using std:: cout;

class Dog{
private:
    int age;
public:
    Dog(int a) {
        age = a;
        cout << "멍\n";
    }
    ~Dog() {
        cout << "소멸\n";
    }
    int getAge();
    void setAge(int a);
};

int Dog::getAge() {
    return age;
}
void Dog::setAge(int a) {
    age = a;
}

int main() {
    Dog happy(5);
    cout << "main함수 시작\n";
    cout << happy.getAge();
    cout << "\nmain함수 끝\n";
    return 0;
}
```

# this 포인터

## this 포인터
- this 포인터는 자동적으로 시스템이 만들어 주는 포인터
- 멤버가 호출될 때 그 멤버가 속한 객체를 가르킨다.
- 객체를 통하여 멤버를 호출할 때 컴파일러는 객체의 포인터 즉 주소를 this포인터에 넣은 다음 멤버를 호출한다.
- this 포인터는 멤버를 호출한 객체의 const 포인터이다.
- 멤버함수를 수행하고 나서 그 결과로 객체 자신을 되돌릴 경우 return *this하고 하면 된다.
- 멤버함수에서 볼 때 this 포인터는 어떤 객체가 자신을 호출했는지 알고자 하는 경우 사용한다.
- 연산자 중첩에서 사용
- 클래스의 멤버함수 내에서 다른 클래스에 자기 자신을 매개변수로 넘길 때 사용

## this 포인터 예
```cpp
#include <iostream>
using std::cout;
class Dog{
private:
    int age;
public:
    Dog(int a) {
        this -> age = a;
    }
    ~Dog() {
        cout << "소멸";
    }
    int getAge();
    void setAge(int a);
};

int Dog::getAge() {
    return this -> age;
}
void Dog::setAge(int a) {
    this -> age = a;
}

int main() {
    Dog happy(5);
    cout << happy.getAge();
    return 0;
}
```
```cpp
#include <iostream>
using std::cout;
using std::endl;

class Dog{
private:
    int age;
public:
    Dog(int a);
    ~Dog();
    int getAge();
    void setAge(int a);
};

Dog::Dog(int a) {
    age = a;
    cout << this << endl;
}
Dog::~Dog() {
    cout << "소멸";
}
int Dog::getAge() {
    return age;
}
void Dog::setAge(int a) {
    age = a;
}

int main() {
    Dog happy(5), meri(3);
    cout << happy.getAge();
    cout << meri.getAge();
    return 0;
}
```

## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약   
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
