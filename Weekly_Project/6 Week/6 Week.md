# 클래스 멤버의 접근권한

## 정수(Integer) 클래스와 객체
- 정수를 다루기 위한 클래스 Integer
```c
class Intefet{ // Integer라는 이름의 class
    private: // 속성
        int val; // 멤버변수, private 속성
    public: // 이 줄 이하는 public속성
        int getVal(); // 멤버함수, 출력, getter
        int setVal(); // 멤버함수 , 입력, setter
}Val1; // ① 객체를 만드는(정의) 첫 번째 방법
Integer Val2; // ② 객체를 만드는 두 번째 방법
```

## 클래스 멤버의 접근 권한
- 멤버변수와 멤버함수를 선언하기 전에 그들의 속성(멤버의 액세스권한)을 지정
- 클래스 외부에서 멤버에 접근할 수 있는 권한
    - 전용(private)
        - 해당 클래스 내부에서만 접근할 수 있음
    - 범용(public)
        - 어디에서나 접근할 수 있음
    - 보호(protected)
        - private이지만 자식에게는 접근할 수 있도록 함

### private - 전용
- 데이터를 외부로부터의 잘못된 조작이나 사용에서 보호받기 위한 방법 제공
- 외부에서 직접적으로 접근할 수 없음
- 멤버변수는 주로 private로 선언
- 생략이 가능(멤버의 엑세스 권한이 없으면 private)
- 해당 클래스의 멤버함수만 접근 가능
```c
class Dog {
    private: // 생략 가능
        int age; // 멤버변수
    public:
        int getAge(); // 멤버함수
};
Dog coco; // 객체
```

### public - 범용
- 클래스 외부에서 멤버에 직접 접근 가능
- 멤버함수는 주로 public으로 선언
- public 멤버함수의 경우 private 멤버변수를 접근하는데 많이 사용
```c
class Dog {
    private: // 생략 가능
        int age; // 멤버변수
    public:
        int getAge(); // 멤버함수
};
Dog coco; // 객체
```

### protected - 보호
- 동일한 클래스의 멤버함수와 현재 클래스를 상속받아 생성된 파생(자식)클래스의 멤버함수만 직접 접근 가능
- 자신의 멤버함수와 자식의 멤버함수만 접근 가능
- 상속하지 않으면 private 속성과 같음

# 함수
- 함수란 특정한 작업을 하도록 만들어진 독립적인 단위 모듈
- 큰 프로그램 하나를 여러 개의 함수로 분할하여 구현하는 구조적 프로그래밍 방식의 기본
- 입력은 매개변수(parameter) 또는 전달인자(argument), 결과 값은 반환값 또는 리턴값(return value)

## 함수 정의, 호출, 선언
- 함수 정의
    - 함수 만들기
    - 이름, 매개변수, 리턴형, 기능
- 함수 호출
    - 함수 사용하기
    - 이름, 매개변수
- 함수 선언
    - 함수의 사용법
    - 이름, 매개변수, 리턴형
    - 컴파일러에게 함수에 대한 정보를 미리 줌

## return문
- 결과 값을 호출한 함수로 반환
- return문을 만나면 함수의 나머지 부분에 상관없이 함수의 실행을 종료하고 호출한 함수로 넘어감

# 멤버함수의 선언과 정의
- 클래스 내에 나타난 함수의 프로토타입(prototype)은 함수를 선언하는 것
    - int getAge();
- 실제 함수를 사용하기 위해서는 멤버함수에 대한 정의가 필요
- 멤버함수를 정의하는 2가지 방법
    - 클래스 안에서 정의
    - 클래스 밖에서 정의
    - 클래스 안에서 정의하는 경우는 클래스의 몸체가 비대해질 수 있으므로 잘 사용하지 않음
```c
class Dog {
    private: // 속성
        int age; // 멤버변수
    public:
        int getAge(); // 멤버 함수 선언
};
Dog coco; // 객체
```

## 멤버함수를 클래스 안에서 정의
```c
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
```

## 멤버함수를 클래스 외부에서 정의
- 리턴형 클래스명::멤버함수명(매개변수 리스트)
```c
class Dog {
    private:
        int age;
    public:
        int getAge(); // 멤버함수 getAge선언
        void setAge(int age); // 멤버함수 setAge선언
};

int Dog::getAge() // 멤버함수 getAge의 정의
{ // getAge()는 Dog클래스의 멤버함수
    return age;
}
void Dog::setAge(int a) // 멤버함수 setAge의 정의
{
    age = a;
}
```

## 범위 지정 연산자(scope resolution operator) '::'
- 멤버함수가 어느 클래스에 포함되어 있는지를 나타낼 때
- 함수 안에서 전역 변수를 접근할 때
    ```c
    #include <iostream>
    using std::cout;
    int a = 3; // 전역변수
    int main() {
        int a = 10; // 지역변수
        a = a + 10; cout << a << ","; // 지역변수 a, 20
        :: a = :: a + 3; cout << :: a; // 전역변수 a, 6
        return 0;
    }
    ```

## using과 namespace
- 기본
```c
#include<iostream>
int main() {
    std::cout<<"소프트웨어"<<std::end;;
    return 0;
}
```

- namespace
```c
#include <iostream>
using namespace std;
// 네임스페이스로 std 사용, 잘 쓰지 않음
int main() {
    cout << "소프트웨어" << endl;
    return 0;
}
```

- using
```c
#include <iostream>
using std::cout;
using std::endl;
int main() {
    cout << "소프트웨어" << endl;
    return 0;
}
```

## namespace
- 모든 식별자(변수, 함수 등의 이름)가 유일하도록 보장하는 코드 영역을 정의
    - aa.h
    ```c
    namespace AA {
        int add(int x, int y) {
            return x + y;
        }
    }
    ```
    - bb.h
    ```c
    namespace BB {
        int add(int x, int y) {
            return x + y + 1;
        }
    }
    ```
    - main
    ```c
    #include <iostream>
    #include "aa.h"
    #include "bb.h"
    int add(int x, int y) { return x + y + 2; }
    int main() {
        std::cout << AA::add(1, 2) << std::endl;
        std::cout << BB::add(1, 2) << std::endl;
        std::cout << ::add(1, 2); // 전역 namespace
        return 0;
    }
    ```

## std namespace
- cin, cout 등 C++ 표준 라이브러리의 네임스페이스

## using 지시문(directive)
- std 네임스페이스의 모든 것을 참조
- 컴파일러가 인식 못하는 이름의 경우 std namespace를 검사

# inline 함수
- C에서 #defice문에 의한 매크로 함수와 유사
- C++에서는 함수 선언이나 정의 앞에 inline 이라는 키워드를 사용하여 매크로 함수의 부작용을 없애면서 같은 기능을 수행
- inline 리턴형 함수명(매개변수 리스트)
    - inline int sum(int x, int y);
    - inline int add(int x, int y) { return (x + y); }
- inline 함수는 컴파일러에 의해 처리되며 텍스트가 아닌 함수 코드 블록의 복사본인 기계어 코드가 직접 삽입
- 함수이므로 매개변수의 데이터형을 확인할 수 있음
- 함수를 호출하고 값을 반환하는데 드는 시간상의 지체(overhead)를 줄일 수 있음

## inline 함수 예
```c
#include <iostream>
using std::cout;
#define sum(i, j) i+j
inline int iSum(int i, int j) {
    return i+j;
}
int add(int i, int j) {
    return i+j;
}
int main() {
    cout << sum(10, 20) / 2 << ",";
    cout << iSum(10, 20) / 2 << ",";
    cout << add(10, 20) / 2;
    return 0;
}
```

## inline 함수의 단점
- inline 함수를 사용하면 프로그램의 전반적인 실행속도가 빨라지지만 코드가 작은 함수일 때와 호출 빈도가 낮을 때 사용하는 것이 좋다.
- 아무리 작은 크기의 함수라도 여러 번 호출하게 되면 프로그램의 크기가 커져 실행 속도가 늦어지는 단점이 있음
- 함수의 코드크기가 큰 경우, inline 함수로 선언했다 할지라도 컴파일러가 일반 함수로 취급할 수 있음
- Visual C++에서도 한/두 줄의 짧은 실행문을 갖는 함수를 inline 함수로 취급하고 그 이상의 함수는 컴파일러가 판단하여 처리

## 자동 inline 함수
- 클래스 멤버함수의 정의부분이 짧으면(코드가 작은 함수) 보통 클래스 선언부 내에서 함수를 정의
- 이 경우 선언과 정의가 동시에 이루어짐
- 멤버함수가 클래스 내부에서 정의되면 자동적으로 inline함수가 됨
- 코드가 짧은 생성자와 소멸자가 대표적인 자동 inline 함수
    ```c
    class Dog{
        private:
            int age;
        public:
            int getAge() { return age; } // 멤버함수가 클래스 안에서 정의
            void setAge(int a) { age = a; } // 자동적으로 inline함수가 됨
    };
    ```

# 객체의 멤버호출
- 직접참조연산자: .
    - 일반 객체가 멤버(변수/함수)에 접근하기 위해 사용
- 간접참조연산자: ->
    - 포인터 객체가 멤버(변수/함수)에 접근하기 위해 사용
```c
class Dog {
    private: // 속성
        int age; // 멤버변수
    public:
        int getAge(); // 멤버함수
        void bark();
};
Dog happy, *pHappy; // 객체
```

## 객체의 멤버 호출
```c
#include <iostream>
using std::cout;
class Dog {
private:
    int age;
public:
    int getAge();
    void setAge(int a);
};
int Dog::getAge() { return age; }
void Dog::setAge(int a) { age = a; }

int main() {
    Dog happy; // Dog class의 happy객체 정의
    happy.setAge = 3;
    cout << happy.getAge;
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
