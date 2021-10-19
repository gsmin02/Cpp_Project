# 중간 정리 - 중요 내용
중요하다고 생각되는 부분만 따로 정리  
C와 공통되는 부분은 적고 C++을 배우면서 새롭게 느낀 부분 중심으로 작성  

## 문자열(string) 리터럴
- ◆ 문자열 리터럴에서는 문자열의 끝을 의미하는 NULL 문자가 제일 뒤에 자동적으로 붙여짐

## cast 연산자
- C 언어에서는 혼합연산 시 자료형의 크기가 큰 쪽으로 통일시켜 연산이 이루어짐(자동 형 변환(implicit arithmetic conversion))
- ◆ (자료형)값_이나_변수
    - (int)x, (char)ch, (double)sum
- 숫자 3은 int, (double)3은 일시적으로 double형 3.0

## 관계 연산자 + 논리 연산자
- C 언어에서는 다음과 같이 표현
    - ◆ if (score >= 90 && score < 95)

## &연산자 예
- ◆ 코드
```cpp
int a = 10;
printf("변수 a의 값=%d, 주소=%p\n", a, &a); 
```
- 결과
```
변수 a의 값=10, 주소=00EFF76C
```

## return문
- 결과 값을 호출한 함수로 반환
- ◆ return (수식이나 값);

## call by reference
- 코드
```cpp
#include <sttdio.h>
int num(int *pa, int *pb);
int main(void) {
    int a = 2, b = 5, c = 0;
    printf("sum() 호출 전 a=%d b=%d c=%d\n", a, b, c);
    ◆ c = sum(&a, &b);
    printf("sum() 호출 후 a=%d b=%d c=%d\n", a, b, c);
                                         // 4, 10, 14
    return 0;
}
int sum(int *pa, int *pb) {
    // a의 주소가 포인터로 pa로 전달됨
    *pa = *pa + 2;
    *pb = *pb + 5;
    return (*pa + *pb);
}
```
- 결과
```
sum() 호출 전 a=2 b=5 c=0
sum() 호출 후 a=4 b=10 c=14
```

## 기억 클래스: 정적(static) 변수
- ◆ static 변수의 특징
    1. 프로그램이 종료 될 때까지 값을 유지
    2. 처음 실행 시 한 번만 초기화되고 초기화 값이 없으면 0으로 초기화됨
    3. 스택이 아닌 정적 데이터 영역을 사용
    4. 지역 static 변수는 해당 블록 내에서만 접근 가능

## 구조체: C vs C++
- C
    - 변수의 모임
- C++
    - 변수와 함수의 모임
    - ◆ 차이점
        - struct은 public이 기본
        ```cpp
        struct Man{
        private:
            int age; // 멤버 변수
        public: // 기본 접근 속성
            int getAge() { return age; } // 멤버 함수
            void setAge(int a) { age = a; }
        };
        Man goo; //.cpp
        ```
        - class는 private이 기본
        ```cpp
        class Man{
            private: // 기본 접근 속성
                int age; // 멤버 변수
            public:
                int getAge() { return age; } // 멤버 함수
                void setAge(int a) { age = a; }
        };
        Man goo; // .cpp
        ```

## 다형성(polymorphism)
- ◆ 하나의 함수 이름(함수 중첩)이나 연산자(연산자 중첩)를 여러 목적으로 사용 (overloading)

## 멤버함수를 클래스 안에서 정의
- 코드
```cpp
class Dog{
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
- ◆ 클래스 다이어그램  
Dog  
──────  
-age : int  
──────  
+getAge()  
+setAge()  

## std namespace
```cpp
#include <iostream>
using std::cout; //  더 좋은 방법
using std::endl;
// 이제부터 cout은 std::cout을 참조
int main() {
    cout << "소프트웨어" << endl;
    return 0;
}
```

## 자동 inline 함수
- ◆ 멤버함수가 클래스 내부에서 정의되면 자동적으로 inline 함수가 된다.

## 일차원 배열의 이름 : 배열의 시작주소
- ◆ 배열의 이름은 그 배열의 시작 주소
```
goo1[0] = 00AFFD6C
goo1[1] = 00AFFD70
goo1[2] = 00ADDF74
goo1 = 00AFFD6C
goo2[0] = 00AFFD58
goo2[1] = 00AFFD5C
goo2[2] = 00AFFD60
goo2 = 00AFFD58

goo1 == & &goo1[0]
```

## 문자열과 문자형 배열
- 문자열은 문자형 배열에 두 가지 방법으로 초기화할 수 있음
    - char eng\[4\]={'A','B','C','\0'} // 문자의 모임
    - ◆ char eng\[4\]="ABC";

## 생성자 정의
- ◆ 멤버 함수 호출 시 자동으로 값 초기화 방법 3가지  
    1. 
        ```cpp
        Dog(){ age=1 }
        ```  
    2. 
        ```cpp
        Dog():age(1){ }
        ```  
    3. 
        ```cpp
        Dog():age{1}()
        ```
- 외부에서 정의  
    1. 
        ```cpp
        Dog::Dog() {
            age = 1;
        }
        ```


## 배열 복사는 strcpy() 사용
- 코드
```cpp
#define _CRT_SECURE_NO_WARNINGS // Visual Studio의 경우
#include <iostream>
#include <string> // or string.h (clang++, gcc 등 주로 온라인 컴파일러)

int main(void) {
    char s1[5];
    char s2[5] = "soft"; // 원본
    // s1 = s2; // error C3863: 배열 형식 'char [5]'은(는) 할당할 수 없습니다.
    strcpy(s1, s2); // ◆ s2 주소의 문자열을 널 문자를 만날 때까지 s1 주소로 복사
    std::cout << "s1=" << s1 << " s2=" s2 << std::endl;
    return 0;
}
```

## C++에서 변수를 초기화하는 방법
- ◆ 코드
```cpp
#include <iostream>
int main() {
    int x=1; // copy initialization, 비추
    int y(2); // direct initialization
    int z{3}; // Uniform initialization, C+11
    int z1{}; // Uniform initialization, 자동으로 0, C++11
    std::cout << x << y << z << z1;
}
```

## 종합 응용
- ◆ 코드
```cpp
#include <iostream>
#include <string>
using namespace std;

class Cat {
private:
    int age;
    double weight;
    string name;
public:
    int getAge();
    void setAge(int a);
    double getWeight();
    void setWeight(double a);
    string getName();
    void setName(string pName);

    void meow();
    Cat(int a);
    ~Cat();
};

int Cat::getAge() {
    return this->age;
}
void Cat::setAge(int a) {
    this->age = a;
}

double Cat::getWeight() {
    return this->weight;
}
void Cat::setWeight(double a) {
    this->weight = a;
}

string Cat::getName() {
    return this->name;
}
void Cat::setName(string pName) {
    this->name = pName;
}
void Cat::meow() {
    cout << "냐옹.\n";
}

Cat::Cat(int a) {
    this->age = a;
    cout << this << endl;
}
Cat::~Cat() {
    cout << "소멸";
}

int main() {
    Cat nabi(3);
    nabi.setAge(3);
    nabi.setWeight(3);
    nabi.setName("나비");
    cout << nabi.getName() << " 나이는 " << nabi.getAge() << "살이다.";
    nabi.meow();
    return 0;
}
```

# 중간 정리 - 기타
- 리터럴
- C vs C++ 차이점
- 이스케이프 시퀀스 \n \' \" \? %%
- 문자와 문자열 차이 'a' (1byte) "a" (2byte)
- &&(and) ||(or) !(not)
- a->b(포인터 구조체 변수 -> 멤버)
- 전달인자, 매개변수, 리턴 값
- 함수 정의, 호출, 선언
- 선언 == 원형 == prototype
- a와 b를 호출 X, a와 b의 "값"을 호출
- 지역 변수의 특징
- 객체지향 언어의 3가지 특징(캡슐화, 상속성, 다형성)
- 클래스와 객체의 차이점 (클래스 -> 객체 -> 인스턴스)
- 클래스 멤버의 접근 권한
- 멤버함수 외부에서 정의
- namespace (AA::add(1, 2), BB""add(2, 3))
- using (위치 지정 연산자 :: )
- 객체의 멤버 호출 장점 (재사용)
- this 포인터

## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일  

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
