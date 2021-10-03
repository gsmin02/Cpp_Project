# 구조체

## 변수 / 배열 / 구조체 비교
### 변수
변수는 하나의 데이터형으로,   
한 번에 하나의 자료형 데이터를 한 번 넣을 수 있다   
### 배열
배열은 동일한 타입의 데이터들을 하나의 단위로 취급하고,   
한 번에 하나의 자료형 데이터를 여러 개 넣을 수 있다   
### 구조체
구조체는 다른 타입의 데이터들을 하나의 단위로 취급하고,   
한 번에 여러 개의 자료형을 여러 개 넣을 수 있다   

## 구조체
이미 정의된 서로 다른 자료형들을 요소로 하여 새로운 자료형을 만드는 것이다.   
사용하는 이유는 위와 같은 방식으로 그룹핑하게 되면 프로그래밍하기 편리한 자료들을 하나로 묶어 개발하기 수월해진다.   
배열은 동일한 자료형만 관리할 수 있지만 구조체는 다른 자료형을 묶어서 관리할 수 있다.   

## C의 구조체와 C++의 클래스

### C의 구조체
```c
struct Man { // 구조체 선언
	char name[7]; // 멤버
	int age; // 멤버
}; // ; 이전에 변수명을 넣으면 해당 이름으로 변수가 선언됨
struct Man struct_variable;
```
C의 구조체는 변수만 지정

### C++의 클래스
```c
class Man {
private:
    int age;
public:
    int getAge() { return age; }
    void setAge(int age) { int a = age; }
};
Man class_variable_and_function;
```
C++의 클래스는 변수와 함수 지정   

## 구조체 변수가 멤버에 접근하는 예

```c
struct Man {
    char name[10];
    int age;
    double weight;
};

struct Man Test1; // 일반 변수 선언
struct Man * Test2; // 포인터 변수 선언

Test1.age = 13; // 일반 변수는 멤버를 "."으로 접근
Test2->age = 7; // 포인터 변수는 멤버를 "->"로 접근
```

## Man형 구조체를 선언하고 변수를 만들어서 멤버에 접근

### C 스타일
```c
#include <stdio.h>
struct Man {
    char name[10];
    int age;
    double weight;
};
int main(void) {
    struct Man gildong, sunhee, comso[160];
    gildong.age = 20;
    sunhee.weight = 52.5;
    comso[0].age = 25;
    printf("%d %f %d\n", gildong.age, sunhee.weight, comso[0].age);
    return 0;
}
```

### C++ 스타일
```c
#include <iostream>
using std::cout;
using std::endl;
struct Man {
	char name[10];
	int age;
	double weight;
};
int main() {
	Man gildong, sunhee, comso[160];
	gildong.age = 20;
	sunhee.weight = 52.5;
	comso[0].age = 25;
	cout << gildong.age << " " << sunhee.weight << " " << comso[0].age << endl;
	return 0;
}
```

## 구조체와 레코드
다음과 같은 필드를 갖는 성적 레코드(record)를 관리하기 위한 구조체 score를 구현   
학번, 성명 등이 필드에 해당하며 구조체는 멤버로 된다.
```c
struct score {
    char hakbun[10];
    char name[10];
    int kor, eng, tot;
    double ave;
}
```

## 구조체 선언과 typedef

```c
typedef unsigned int uint; // unsigned int를 uint라는 새로운 자료형으로 정의
uint x; // unsigned int x와 같은 의미
typedef struct score SCORE; // SCORE라는 새로운 자료형이 생성된 것으로 "struct score" 또는 "SCORE" 둘 다 가능하다
```

## 구조체 변수의 초기화 멤버 값 대입

### C
```c
#include <stdio.h>
struct score {
    char hakbun[10];
    char name[10];
    int kor, eng, tot;
    double ave;
};
int main(void) {
    struct score h = { "202345678","하니",80,90 }; //초기화
    h.tot = h.kor + h.eng;
    h.ave = h.tot / 2.0;
    printf("%s %s %d %d %d %.2f\n", h.hakbun, h.name, h.kor, h.eng, h.tot, h.ave);
    return 0;//202345678 하니 80 90 170 85.00
}
```

### C++
```c
#include<iostream>
using namespace std;

struct score {
	char hakbun[10];
	char name[10];
	int kor, eng, tot;
	double ave;
};
int main() {
	score h = { "202345678","하니",80,90 }; //초기화
	h.tot = h.kor + h.eng;
	h.ave = h.tot / 2.0;
	cout << h.hakbun << " " << h.name << " " << h.kor << " " << h.eng << " " << h.tot << " ";
	cout << fixed;
	cout.precision(2);
	cout << h.ave << endl;
	return 0;//202345678 하니 80 90 170 85.00
}
```

## 구조체 변수들의 대입 연산

### C
```c
#include <stdio.h>
    typedef struct score {
    char hakbun[10];
    char name[10];
    int kor, eng, tot;
    double ave;
}SCORE;
int main(void)
{
    SCORE j, h = { "202345678", "하니",80,90 };
    h.tot = h.kor + h.eng;
    j = h;
    printf("%s %s %d %d %d\n", h.hakbun, h.name, h.kor, h.eng, h.tot);
    printf("%s %s %d %d %d\n", j.hakbun, j.name, j.kor, j.eng, j.tot);
    return 0;
}
```

### C++
```c
#include <iostream>
using std::cout;
using std::endl;
typedef struct score {
	char hakbun[10];
	char name[10];
	int kor, eng, tot;
	double ave;
}SCORE;
int main() {
	SCORE j, h = { "202345678", "하니",80,90 };
	h.tot = h.kor + h.eng;
	j = h;
	cout << h.hakbun << " " << h.name << " " << h.kor << " " << h.eng << " " << h.tot << endl;
	cout << j.hakbun << " " << j.name << " " << j.kor << " " << j.eng << " " << j.tot << endl;
	return 0;
}
```

# 객체지향 프로그래밍

## 구조적 프로그래밍 스타일(C언어)
간단하게 코드로 구현 시
### 기존 소스
```c
int main(void) {
    // 입력함수
    // 계산함수
    // 출력함수
    // 출력 기능 구현
    return 0;
}
```
### 구조화 된 소스
```c
int main(void) {
    input();
    compute();
    output();
    return 0;
}
input() { // 입력함수
    /* 입력 기능 구현 */
}
compute() { // 계산함수
    /* 계산 기능 구현 */
}
output() { // 출력함수
    /* 출력 기능 구현 */
}
```
이렇게 보면 기존 소스 부분이 더욱 보기 편할 수 있지만,   
프로젝트가 커지고 소스가 10줄, 100줄 이상 반복된다면,   
구조화가 된 소스가 훨씬 보기도 편하고 프로그래밍하기도 쉽다.   

## 구조적 프로그래밍(structured programming) 방법론
■ Pascal, C와 같은 언어로 프로그래밍하는 스타일   
■ 처리동작(명령, 연산)에 중점을 두어 프로그램을 작성   
■ 자료가 프로그램 전체에 노출   
■ 자료와 처리 동작을 변도로 구분하기 때문에 처리 동작과 자료 사이의 관계가 서로 밀접한 연관성을 갖지 못함   
■ 프로그램이 복잡해지면 디버깅 및 유지보수가 어려워짐   

## 객체지향
■ 우리가 살고 있는 세상은 거의 모든 사물이 객체(Object)로 이루어져 있음   
■ 실세계를 반영하는 프로그래밍   
■ 소프트웨어 확장 및 재사용 기회 증가   
■ 객체 지향(object oriented)   
    ● 문제의 모든 초점을 실세계에 존재하는 객체 중심으로 생각   
■ 객체지향 설계   
    ● 실세계의 실객체가 설계의 기초가 되는 설계기법   
■ 객체지향 언어   
    ● 실객체를 소프트웨어 객체로 쉽게 표현할 수 있도록 이와 관련된 많은 기능을 가지는 언어   
    ● C++, JAVA, C#, Object-C, Visual Basic.NET, Smalltalk, Ruby, Python   

## 객체지향 언어
■ 실객체를 소프트웨어 객체로 쉽게 표현할 수 있도록 이와 관련된 많은 기능을 가지는 언어   
### 순수 객체지향언어
● Eiffel, JADE, Ruby, Scala, Smalltalk   
### 절차적 프로그래밍 특징도 갖는 객체지향언어
● C++, JAVA, C#, Visual Basic.NET, Python   
### 객체지향 특징을 갖는 dynamic programming언어
● Python, Ruby, Perl 5, PHP 4   

## 객체
■ 객체는 자료와 이를 처리하는 동작인 연산(함수, method)을 하나로 묶어 만든 요소   
■ 프로그램을 구성하는 실체   
■ 객체란 자료를 표현하는 변수만을 가지는 것이 아니라 그 객체가 무엇을 할 수 있는가를 정의한 함수도 구성   
■ 인스턴스(Instance)   
    ● 어떤 클래스에서 생성된 객체 혹은 한 클래스에 속하는 각각의 객체   

## 클래스(class)
■ 각 객체의 속성을 정의하는 수단
■ 모든 객체는 사용 전에 객체의 속성을 기술하는 클래스를 정의한 수 이 클래스의 형으로 선언되어야 한다.   
■ 클래스는 객체의 타입(Object Type)이다.   
■ 클래스는 유사한 객체들이 갖는 동통된 데이터와 함수들을 정의한 객체의 기본 규격(specification)이다.   
■ ex) int x;   
■ ex) Man Test1;   

## 클래스와 객체
■ 클래스   
    ● 객체들의 공통적인 특성을 모아 놓은 것   
    ● 데이터와 데이터를 다루는 함수들을 모아 놓은 단위로서 자료 추상화를 지원   
■ 객체   
    ● 객체는 자신이 상태와 행동, 이름을 가지고 있는 것   

## ADT: 추상 자료형
■ Abstraction Data Type   
■ int, double 등이 아닌 사용자 정의 자료형   
■ C++에서는 클래스로 추상 자료형을 지원   
■ 자료에 대한 연산을 외부와 단절하는 개념   

## 상속(inheritance)
■ 파생 클래스가 기본 클래스의 정의된 속성(자료 및 연산)을 상속받는 것   
■ 상속을 이용하면 기존 프로그램의 재사용하기 수월하여 프로그램의 개반 비용과 복잡도를 줄일 수 있음   
■ 파생 클래스를 사용하면 자료형의 계층화도 가능   

## 다형성(polymorphism)
■ poly+morph: 많은 형태   
■ 유사한 기능은 하나의 이름(인터페이스)으로 복잡도를 감소시킴   
■ 하나의 함수 이름(함수 중첨)이나 연산자(연산자 중첩)를 여러 목적으로 사용   

## 클래스 선언(declaring a class) 객체 정의(defining an object)
```c
class 클래스명 {
    속성: // private이나 public, protected가 올 수 있음
        자료선언; // 맴버 변수
    속성:
        함수선언;
}객체변수; // 객체를 만드는(쩡의) 첫 번째 방법
클래스명 객체변수; // 객체를 만드는 구 번째 방법
```

## 클래스 멤버의 접근 권한
■ 멤버변수와 멤버함수를 선언하기 전에 그들의 속성(멤버의 액세스 권한)을 지정   
■ 클래스 외부에서 멤버에 접근할 수 있는 권한   
    ■ 전용(private)   
        ● 해당 클래스 내부에서만 접근 가능   
        ● 디폴트 속성으로 생략 가능   
    ■ 범용(public)   
        ● 어디에서나 접근 가능   
    ■ 보호(protected)   
        ● private이지만 자식에게는 접근 가능   

## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약   
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
