# 구조체

## 변수 / 배열 / 구조체
변수 - 하나의 데이터형   
배열 - 동일한 타입의 데이터들을 하나의 단위로 취급   
구조체 - 다른 타입의 데이터들을 하나의 단위로 취급   

## C의 구조체와 C++의 클래스

### C의 구조체
```c
struct Man {
	char name[7];
	int age;
};
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


## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약   
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
