# 함수 중첩

## 다형성(polymorphism)의 종류

- 다형성은 다른 유형의 엔터티에 단일 인터페이스를 제공하거나 사용하는 것
- 단일 기호의 여러 유형을 나타냄

## 함수 중첩(function overloading)

- 함수 오버로딩
- 다형성을 구현하는 한 가지 방법
- C에서는 기능이 같은데도 처리하는 자료형에 따라 다른 이름의 함수를 사용함
- 수의 절대값을 구하는 함수
  - ``` abs() // int, abs(-4)=4 ```
  - ``` labs() // long, labs(-3l)=3 ```
  - ``` fabs() // float, fabs(-3.6f)=3.6 ```
- 다형성을 제공하는 C++에서는 하나의 함수 이름을 중첩해서 사용 가능하다.
- 하나의 함수명을 여러 개의 유사 목적으로 사용할 수 있다.

## C의 경우 함수 중첩 불가능

- 두 개의 정수형 매개변수를 받아들여 더하는 함수

```cpp
int add_i(int i, int j) {
    return (i + j);
}
```

- 두 개의 실수형 매개변수를 받아들여 더하는 함수

```cpp
float add_f(float i, float j) {
    return (i + j);
}
```

- 두 개의 double형 매개변수를 받아들여 더하는 함수

```cpp
double add_d(double i, double j) {
    return (i + j);
}
```

## C++은 함수 중첩 가능

- 앞의 세 함수 add_i, add_f, add_d는 같은 작업을 구행하지만 매개변수의 자료형에 따라 각각 다른 이름을 부여하고 있다.

- C++ 에서는 함수 중첩을 이용하여 프로그램을 이해하기 쉽게 작성할 수 있다.
  - 즉, 다음과 같이 같은 이름을 부여할 수 있다.

- 컴파일러가 매개변수의 입력 자료형에 따라서 자동적으로 해당 함수를 연결해준다.

```cpp
int add(int i, int j) {
    return (i + j);
}
float add(float i, float j) {
    return (i + j);
}
double add(double i, double j) {
    return (i + j);
} // C++ function overloading
```

## 함수중첩을 하는 2가지 경우

- 매개변수의 형이 다른 경우

```cpp
#include <iostream>
int add(int i, int j) {
    return (i + j);
}
float add(float i, float j) {
    return (i + j);
}
double add(double i, double j) {
    return (i + j);
}
int main() {
    std::cout << add(1, 2) << std::endl;
    std::cout << add(1.3f, 2.6f) << std::endl;
    std::cout << add(6.5, 3.8) << std::endl;
    return 0;
}
```

- 매개변수의 개수가 다른 경우

```cpp
#include <iostream>
int add(int i, int j) {
    return (i + j);
}
int add(int i, int j, int k) {
    return (i + j + k);
}
int add(int i, int j, int k, int l) {
    return (i + j + k + l);
}
int main()
{
    std::cout << add(1, 2) << std::endl;
    std::cout << add(1, 2, 3) << std::endl;
    std::cout << add(1, 2, 3, 4) << std::endl;
    return 0;
}
```

# 생성자 중첩

## 생성자 중첩

- 클래스의 멤버함수도 중첩이 가능하고, 생성자도 물론 중첩이 가능하다.
- 하지만 소멸자는 중첩이 불가능하다.
- 생성자 함수도 매개변수를 가질 수 있기 때문에 매개변수의 수나 자료형에 따라 여러 개의 생성자 함수를 중첩할 수 있다.
- 생성자 함수를 중첩시키는 것은 객체에 초기값을 다양하게 주는 선택 기회를 제공하는 것이다.

# 디폴트 인자(매개변수)

## 디폴트 인자(default parameter, default argument)

- 디폴트 매개변수
- int add(int, int); //매개변수 2개
- C++에서는 함수를 호출할 때 별도의 매개변수를 전달하지 않아도 기본적인 값을 전달하도록 함수 원형을 선언할 때 디폴트 값을 지정할 수 있다.
- 해당 매개변수가 주어지지 않으면 디폴트 인자 값이 할당된다.
- 모든 매개변수에 디폴트 값을 줄 필요는 없으며 필요한 곳에만 준다.
- 디폴트 매개변수의 사용은 함수 중첩의 축약형이다.
- 디폴트 매개변수를 갖는 함수를 만들 때, main()함수 전에 함수 선언을 하면 선언부에만 디폴트 인자를 지정해야 한다.
  - ``` int add(int i = 1, int j = 2); // 선언부에 디폴트 인자 작성 ```
- 일단 디폴트 매개변수를 정의하기 시작하면 그 다음(오른쪽)의 매개변수들은 모두 디폴트 매개변수를 가져야 한다.
  - ``` int add(int i = 1, int j); // 오류 ```

## 출처

C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"