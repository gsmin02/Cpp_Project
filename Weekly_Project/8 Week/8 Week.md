# 중간 정리
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

## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일  

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
