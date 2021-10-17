## 함수 만들기 1

```cpp
#include<stdio.h>
void display() {
	printf("안녕");
}
int main() {
	display();
	return 0;
}
```

## 함수 만들기 2

```cpp
#include <stdio.h>
void double_number(int x)
{
	printf("%d", x *2);
}
int main()
{
	double_number(3);
	return 0;
}
```

## 함수 만들기 3

```cpp
#include <stdio.h>
int double_number(int x)
{
	return x *2;
}
int main()
{
	double_number(3);
	return 0;
}
```

## 함수 만들기 4

```cpp
#include <stdio.h>
int add(int x, int y)
{
	return x + y;
}
int main()
{
	int x;
	x = add(2, 3);
	printf("%d", x);
	return 0;
}
```

## 함수 만들기 5

```cpp
#include <stdio.h>
char vending(int x)
{
	if (x ==1) return 'A';
	else return 'B';
}
int main()
{
	char x;
	x = vending(1);
	printf("%c\n", x);
	return 0;
}
```

## 함수 만들기 6

```cpp
#include <stdio.h>
const char* vending(int x)
{ //C++에서는 std::string 사용 가능
	if (x ==1) return "커피";
	else return "유자차";
}
int main()
{
	printf("%s\n", vending(1));
	return 0;
}
```

```cpp
#include <stdio.h>
char vending(int x)
{
	if (x ==1) return 'A';
	else return 'B';
}
int main()
{
	printf("%c\n", vending(1));
	return 0;
}
```

## C++에서 문자열

```cpp
// const char*
#include <iostream>
using namespace std;
const char* vending(int x)
{
	if (x ==1) return "커피";
	else return "유자차";
}
int main()
{
	cout << vending(1);
	return 0;
}
```

```cpp
// string
#include <iostream>
using namespace std;
string vending(int x)
{ //std::string
	if (x ==1) return "커피";
	else return "유자차";
}
int main()
{
	cout << vending(1);
	return 0;
}
```

## 함수의 정의와 선언(원형, prototype)

```cpp
#include <stdio.h>
void view(void);
int main(void) {
	printf("메인 함수 : view호출 전\n");
	view();
	printf("메인 함수 : view호출 후\n");
	return 0;
}
void view(void) {
	printf("view함수\n");
}
```

## 함수 선언, 정의, 호출

```cpp
#include <stdio.h>
void fun1(void); // 함수 선언 또는 원형
void fun2(void); // 함수 선언 또는 원형
int main(void) {
	printf("메인 함수 전\n");
	fun1(); // 함수 호출
	fun2(); // 함수 호출
	printf("메인 함수 후\n");
	return 0;
}
void fun1(void) { // 함수 정의
	printf("fun1()\n");
}
void fun2(void) { // 함수 정의
	printf("fun2()\n");
}
```

## 함수 만들기 1

```cpp
#include <stdio.h>
void display()
{
	printf("안녕");
}
int main()
{
	display();
	return 0;
}
```

```cpp
#include <stdio.h>
void display();
int main()
{
	display();
	return 0;
}
void display()
{
	printf("안녕");
}
```

## 함수 만들기 2

```cpp
#include <stdio.h>
void print_double_number(int x)
{
	printf("%d", x * 2);
}
int main()
{
	print_double_number(3);
	return 0;
}
```

### C++

```cpp
#include<iostream>
using std::cout;
void print_double_number(int x) {
	cout << x *2;
}
int main() {
	print_double_number(3);
	return 0;
}
```

## 함수 만들기 3

```cpp
#include <stdio.h>
int double_number(int x)
{
	return x *2;
}
int main()
{
	int x;
	x = double_number(3);
	printf("%d\n", x);
	printf("%d\n", double_number(3));
	return 0;
}
```

### C++

```cpp
#include <iostream>
using std::cout;
using std::endl;
int double_number(int x) {
	return x *2;
}
int main() {
	int x;
	x = double_number(3);
	cout << x <<endl;
	cout << double_number(3) <<endl;
	return 0;
}
```

## 함수 만들기 4

```cpp
#include <stdio.h>
int add(int x, int y)
{
	return x + y;
}
int main()
{
	int x;
	x = add(2, 3);
	printf("%d", x);
	return 0;
}
```

### C++

```cpp
#include <iostream>
using std::cout;
using std::endl;
int add(int x, int y) {
	return x + y;
}
int main() {
	int x;
	x = add(2, 3);
	cout << x <<endl;
	return 0;
}
```

## 함수 만들기 5

```cpp
#include <stdio.h>
char vending(int x)
{
	if (x ==1) return 'A';
	else return 'B';
}
int main()
{
	char x;
	x = vending(1);
	printf("%c\n", x);
	return 0;
}
```

### C++

```cpp
#include<iostream>
using std::cout;
using std::endl;
char vending(int x) {
	if (x ==1) return 'A';
	else return 'B';
}
int main() {
	char x;
	x = vending(1);
	cout << x <<endl;
	return 0;
}
```

## 함수 만들기 6

```cpp
#include <stdio.h>
const char* vending(int x)
{
	if (x ==1) return "커피";
	else return "유자차";
}
int main()
{
	printf("%s\n", vending(1));
	return 0;
}
```

### C++

```cpp
#include <iostream>
using std::cout;
using std::endl;
const char* vending(int x) {
	if (x ==1) return "커피";
	else return "유자차";
}
int main() {
	cout << vending(1) <<endl;
	return 0;
}
```

## 함수의 리턴값

```cpp
#include <stdio.h>
int add(int x, int y);//함수 선언
//int add(int,int);처럼 매개변수명은 생략 가능
int main(void)
{
	int sum;
	printf("메인 함수\n");
	add(5, 10); //함수를 호출하고 리턴값을 보관하지 않음
	//15가 리턴되었지만 사라짐
	sum = add(5, 10); //함수 호출 후 리턴 값을 sum에 저장
	printf("sum=%d\n", sum);
	printf("add(5,10)=%d\n", add(5, 10));//함수 호출 후 리턴값을 바로 출력
	return 0;
}
int add(int x, int y) //함수 정의
{ // x에 5, y에 10이 넘어옴
	int z;
	z = x + y;
	return(z); //위 세 줄 대신 return(x+y); 라고만 써도 됨
}
```

## 재귀 함수 예

```cpp
#include <stdio.h>
int sum(int n); // 함수 선언
int main(void) {
	int in =3, out;
	out = sum(in); // 함수 호출
	printf("\nin=%d,out=%d\n", in, out);
	return 0;
}
int sum(int n) { // 함수 정의
	printf("n=%d  ", n);
	if (n <=1) return(1);
	else return(n + sum(n -1));
}
```

## 실매개변수와 형식매개변수 예

```cpp
#include <stdio.h>
int sum(int a, int b); //함수 선언
int main(void)
{
	int a =2, b =5, result;
	double da =2.5, db =5.2;
	result = sum(2, 5);
	printf("%d\n", result);
	result = sum(a, b);
	printf("%d\n", result);
	result = sum(2.5, 5.2);
	printf("%d\n", result);
	result = sum(da, db);
	printf("%d\n", result);
	return 0;
}
int sum(int a, int b)
{
	return(a + b);
}
```

## call by value 예

```cpp
#include <stdio.h>
int sum(int x, int y);
int main(void)
{
	int a =2, b =5, c =0;
	printf("sum()호출 전 a=%d b=%d c=%d\n", a, b, c);
	c = sum(a, b);
	printf("sum()호출 후 a=%d b=%d c=%d\n", a, b, c); //2,5,14
	return 0;
}
int sum(int a, int b)
{
	a = a +2;
	b = b +5;
	printf("sum()함수 내 a=%d b=%d a+b=%d\n", a, b, a + b);
	return(a + b);
}
```

## call by reference

```cpp
#include <stdio.h>
int sum(int* pa, int* pb);
int main(void)
{
	int a =2, b =5, c =0;
	printf("sum()호출 전 a=%d b=%d c=%d\n", a, b, c);
	c = sum(&a, &b);
	printf("sum()호출 후 a=%d b=%d c=%d\n", a, b, c);
	//4,10,14
	return 0;
}
int sum(int* pa, int* pb)
{//a의 주소가 포인터 pa로 전달됨
	*pa =*pa +2;
	*pb =*pb +5;
	return(*pa +*pb);
}
```

## 반복되는 부분은 함수로 구현

```cpp
#include <stdio.h>
void add(int x, int y);
int main(void)
{
	int num1 =1, num2 =2, num3 =3;
	int num4 =4, num5 =5, num6 =6;
	add(num1, num2);
	add(num3, num4);
	add(num5, num6);
	return 0;
}
void add(int x, int y)
{
	printf("두 수 %d과 %d를 더한 결과는 %d입니다.\n", x, y, x + y);
}
```

## 모듈화 프로그래밍

```cpp
#include "score.h"
int main(void)
{
	int i, num, sum =0, total;
	int max = INT_MIN, min = INT_MAX;
	start();//함수 호출
	printf("계산하려는 수는 몇 개입니까=>");
	scanf("%d", &total);
	for (i =1; i <= total; i++) {
		printf("%d번째 수를 입력하세요=", i);
		scanf("%d", &num);
		sum += num;
		max = max_number(num, max);//함수 호출
		min = min_number(num, min);//함수 호출
	}
	printf("합:%d 평균:%.2f 최대값:%d 최소값:%d\n",
		sum, (double)sum / total, max, min);
	return 0;
}
void start(void)//함수 정의
{
	printf("┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓\n");
	printf("┃ 합, 평균, 최대값, 최소값  ┃\n");
	printf("┗━━━━━━━━━━━━━━━━━━━━━━━━━━━┛\n");
}
int max_number(int a, int b)//함수 정의
{
	return((a > b) ? a : b);
}
int min_number(int a, int b)//함수 정의
{
	return((a < b) ? a : b);
}
```

```cpp
//score.h의 내용
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <limits.h>
void start(void);//함수 선언
int max_number(int a, int b); //함수 선언
int min_number(int a, int b); //함수 선언
```

## 지역 변수의 유효범위

```cpp
#include <stdio.h>
int main(void)
{
	int k =10; //지역 변수
	printf("%d ", k); //10
	{
		int k =20; //지역 변수
		k +=10;
		printf("%d ", k); //30
	}
	k +=5;
	printf("%d ", k); //15
	return 0;
}
```

## auto변수

```cpp
#include <stdio.h>
int main(void)
{
	auto int a =1; //여기서 auto는 생략가능
	{
		int a =2; //auto 변수
		{
			int a =3; //auto 변수
			printf("%d ", a);
		}
		printf("%d ", a);
	}
	printf("%d ", a);
	return 0;
}
// auto변수: 함수나 블록을 진입하면 기억 영역이 확보되고, 벗어나면 기억 영역은 바로 소거됨
```

## auto변수와 static변수

```cpp
#include <stdio.h>
void sub(void);
int main(void)
{
	sub();
	sub();
	sub();
	return 0;
}
void sub(void)
{
	auto int x =10; //auto는 생략가능
	static int y =10; //실행시 이 문장은 실행하지 않음, 컴파일시 이미 결정됨
	printf("x=%d, y=%d\n", x, y);
	x++;
	y++;
}
```

### C++

```cpp
#include <iostream>
using std::cout;
using std::endl;
void sub(void);
int main() {
	sub();
	sub();
	sub();
	return 0;
}
void sub(void) {
	int x =10;
	static int y =10;
	cout <<"x="<< x <<", y="<< y <<endl;
	x++;
	y++;
}
```

## Man형 구조체를 선언하고 변수를 만들어서 멤버에 접근

```cpp
#include <stdio.h>
struct Man { //구조체 선언
	char name[10]; //멤버
	int age; //멤버
	double weight; //멤버
};
int main(void)
{
	struct Man gildong, sunhee, comso[160];
	gildong.age =20; //일반 구조체 변수의 멤버 참조
	sunhee.weight =52.5;
	comso[0].age =25;
	printf("%d %f %d\n",
		gildong.age, sunhee.weight, comso[0].age);
	return 0;
}
```

### C++

```cpp
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
	gildong.age =20;
	sunhee.weight =52.5;
	comso[0].age =25;
	cout << gildong.age <<" "<< sunhee.weight <<" "<< comso[0].age <<endl;
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
