## 일반적인 C 출력 방법

```cpp
#include <stdio.h>
int main() {
	printf("소프트웨어\n");
	return 0;
}
```

## 평범한 C++ 출력 방법

```cpp
#include <iostream>
int main() {
	std::cout <<"소프트웨어"<<std::endl;
	return 0;
}
```

## 많이 쓰는 C++ 출력 방법

```cpp
#include <iostream>
using namespace std;
int main() {
	cout <<"소프트웨어"<<endl;
	return 0;
}
```

## 이상적인 C++ 출력 방법

```cpp
#include <iostream>
using std::cout;
using std::endl;
int main() {
	cout <<"소프트웨어"<<endl;
	return 0;
}
```

## C++ 입력 방법

```cpp
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int input;
	cout <<"숫자 하나 입력==>";
	cin >> input;
	cout <<"입력한 수는 =="<< input <<"입니다.";
	return 0;
}
```

## 여러 변수 값 출력

```cpp
#include <iostream>
#include<stdio.h>
using namespace std;
int main() {
	int num1, num2, num3;
	num1 =100;
	num2 =200;
	num3 = num1 + num2;
	printf("%d, %d, %d\n", num1, num2, num3); // C 출력 방식
	cout << num1 <<", "<< num2 <<", "<< num3; // C++ 출력 방식
	return 0;
}
```

## C 입력 방법

```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main() {
	int num;
	printf("숫자 하나를 입력하세요=");
	scanf("%d", &num);
	printf("입력받은 수는 %d입니다.\n", num);
	return 0;
}
```

## 나이 입력받아 출력

* C
```cpp
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main() {
	int age;
	printf("나이를 입력해주세요: ");
	scanf("%d", &age);
	printf("나이는 %d살입니다.\n", age);
	return 0;
}
```

* C++
```cpp
#include <iostream>
using std::cout;
using std::cin;
using std::endl;
int main() {
	int age;
	cout <<"나이를 입력해주세요 : ";
	cin >> age;
	cout <<"나이는 "<< age <<"살 입니다."<<endl;
	return 0;
}
```

## C 코드를 C++로 바꾸기

```cpp
#include <iostream>
int main() {
	int num1, num2;
	num1 =100;
	num2 =-300;
	std::cout <<"두 수의 합은 "<< num1 + num2 <<" 입니다."<<std::endl;
	return 0;
}
```

## 문자형 리터럴: C

```cpp
#include <stdio.h>
int main() {
	int a =10;
	printf("%c\n", 'a');
	printf("%d\n", a);
	return 0;
}

```

## 문자형 리터럴: C++

```cpp
#include <iostream>
using std::cout;
int main() {
	int a =10;
	cout <<'a'<<std::endl;
	cout << a <<std::endl;
	return 0;
}
```

## 문자 A와 문자열 A의 차이점

```cpp
#include <stdio.h>
int main() {
	printf("%c, %s\n", 'A', "A");
	return 0;
}
```

## 실수형의 저장 범위

```cpp
#include <stdio.h>
int main() {
	float f_num =15.12345678901234567890f;
	double d_num =15.12345678901234567890;
	printf("%f\n", f_num);
	printf("%23.20f\n", f_num);
	printf("%23.20f\n", d_num);
	return 0;
}
```

## 자료형의 크기

```cpp
#include <iostream>
#include <limits.h>
#include <float.h>//double, float 자료형을 쓰기 위함
using std::cout;
using std::endl;
int main() {
	cout <<"size of char : "<<sizeof(char) <<" bytes"<<endl <<endl;
	cout <<"size of int : "<<sizeof(int) <<" bytes"<<endl;
	cout <<"int max : "<< INT_MAX <<endl;
	cout <<"int min : "<< INT_MIN <<endl;
	cout <<"unsigned int max : "<< UINT_MAX <<endl <<endl;
	cout <<"size of short : "<<sizeof(short) <<" bytes"<<endl;
	cout <<"short max : "<< SHRT_MAX <<endl;
	cout <<"short min : "<< SHRT_MIN <<endl;
	cout <<"unsigned short max : "<< USHRT_MAX <<endl <<endl;
	cout <<"size of long : "<<sizeof(long) <<" bytes"<<endl <<endl;
	cout <<"size of float : "<<sizeof(float) <<" bytes"<<endl <<endl;
	cout <<"size of double : "<<sizeof(double) <<" bytes"<<endl;
	cout <<"double max : "<< DBL_MAX <<endl;
	cout <<"double min : "<< DBL_MIN <<endl;
	cout <<"size of long double : "<<sizeof(long double) <<" bytes";
	
```

## 변수를 상수화: const

```cpp
#include <stdio.h>
int main() {
	const int num =3;
	// num = num + 3; -> 상수화 했기 때문에 수정 불가
	printf("num=%d\n", num);
	return 0;
}
```

## #define문 예

```cpp
#include <stdio.h>
#define AA  2 // 상수 정의
#define sum3(i,j,k) ((i)+(j)+(k)) // 함수 정의
int main() {
	printf("%d\n", sum3(AA, 4, 6));
	printf("%d\n", sum3(AA, 4, 6) /2);
	printf("%f\n", sum3(1.2, 2.3, 3.4));
	printf("%d\n", AA);
	return 0;
}
```

## 산술연산자 예

```cpp
#include <stdio.h>
int main() {
	printf("5+2-3*2/2=%d\n", 5 +2 -3 *2 /2);
	printf("10/4=%d\n", 10 /4);
	printf("%f\n", 10 /4);
	printf("%f %f %f\n", 10 /4.0, 10.0 /4, 10.0 /4.0);
	printf("10%%4=%d\n", 10 % 4);
	return 0;
}
```

## 증가, 감소 연산자 예

```cpp
#include <stdio.h>
int main() {
	int a =10, b =10, c =20, d =20;
	int ap, bp, cm, dm;
	ap =++a; // a=a+1; ap=a; ap=11, a=11 
	printf("a=%d, ap=%d\n", a, ap);
	bp = b++; // bp=b; b=b+1; bp=10, b=11 
	printf("b=%d, bp=%d\n", b, bp);
	cm =--c; // c=c-1; cm=c; cm=19, c=19 
	printf("c=%d, cm=%d\n", c, cm);
	dm = d--; // dm=d; d=d-1; dm=20, d=19 
	printf("d=%d, dm=%d\n", d, dm);
	printf("%d\n", dm++);
	printf("%d\n", ++dm);
	return 0;
}
```

## cast 연산자 예

```cpp
#include <stdio.h>
int main() {
	int x =10, y =4;
	double z;
	printf("1:%d\n", 10 /4); // 2
	printf("2:%f\n", 10 /4); // 0.000000, 컴파일러에 따라 2.500000, 경고
	printf("3:%f %f %f\n", 10 /4.0, 10.0 /4, 10.0 /4.0);// 모두 2.500000
	printf("4:%d\n", x / y); // 2
	printf("5:%f\n", x / y); // 0.000000, 컴파일러에 따라 2.500000, 경고
	// warning C4477: 'printf' : 서식 문자열 '%f'에 'double' 형식의 인수가 
	// 필요하지만 variadic 인수 1의 형식이 'int'입니다.
	//warning: format specifies type 'double' but the argument has type 'int'
	z = x / y; // double형인 z에 2를 저장하면 소수점만 더 붙음
	printf("6:%f\n", z); // 2.000000
	z = (double)x / y; // 10.0 / 4
	printf("7:%f\n", z); // 2.500000
	z = x / (double)y; // 10 / 4.0
	printf("8:%f\n", z); // 2.500000 
	z = (double)x / (double)y;// 10.0 / 4.0
	printf("9:%f %lf\n", z, z); // 2.500000 2.500000 
	return 0;
}
```

## sizeof 연산자 예

```cpp
#include <stdio.h>
int main() {
	int x;
	int y[10];
	printf("%d\n", sizeof("I love you!")); // 12
	printf("%d\n", sizeof("대한")); // 5(Visual Studio - cp949) or 7(OnlineGDB - utf-8)
	printf("%d\n", sizeof(int)); // 4 
	printf("%d\n", sizeof(x)); // 4, sizeof x라고 써도 됨 
	printf("%d\n", sizeof(y)); // 40, sizeof y라고 써도 됨 
	return 0;
}
```

## 삼항 조건 연산자 예

```cpp
#include <stdio.h>
int main() {
	int i =2, j =4, min;
	printf("%d\n", (i < j) ? i : j);
	min = (i < j) ? i : j;
	printf("%d\n", min);
	if (i < j) min = i;
	else min = j;
	printf("%d\n", min);
	return 0;
}
```

## 혼합 대입 연산자 예

```cpp
#include <stdio.h>
int main() {
	int a =5;
	printf("%d\n", a);
	a = a +5; printf("%d\n", a);
	a +=5; printf("%d\n", a);
	a -=5; printf("%d\n", a);
	a *=5; printf("%d\n", a);
	a /=2; printf("%d\n", a);
	a *= a +5; printf("%d\n", a);
	//a = a*(a+5)
	return 0;
}
```

## 관계(비교) 연산자 예 1

```cpp
#include <stdio.h>
int main() {
	int a =10, b =20;
	printf("%d\n", 1 <2);
	printf("%d\n", 1 <=2);
	printf("%d\n", 1 >2);
	printf("%d\n", 1 >=2);
	printf("%d\n", a > b);
	printf("%d\n", 'A'>'B');
	printf("%d\n", 2.5 >3.5);
	return 0;
}
```

## 관계(비교) 연산자 예 2

```cpp
#include <stdio.h>
int main() {
	int a =10, b =20, c =10;
	printf("%d\n", 1 ==2);
	printf("%d\n", 1 !=2);
	printf("%d\n", a == b);
	printf("%d\n", a != b);
	printf("%d\n", a ==10);
	printf("%d\n", a == c);
	printf("%d\n", a = c);
	printf("%d\n", a =1);
	printf("%d\n", a =0);
	return 0;
}
```

## 논리 연산자와 short circuit rule： 연산 생략

```cpp
#include <stdio.h>
int main() {
	int a =5, b =0;
	printf("%d ", (7 ==7) && (8 !=3));  // 1 && 1
	printf("%d ", (7 >1) || (8 <1));  // 1 || 0
	printf("%d ", (2 ==1) && (3 ==3));// 0 && 1
	printf("%d ", !5); // 0이 아닌 수는 모두 참
	printf("%d ", (a && b)); // 5 && 0
	printf("%d ", (a || b)); // 5 || 0
	printf("%d\n", (!a));  // !5
	return 0;
}
```

## 관계 연산자 + 논리 연산자

```cpp
#include <stdio.h>
int main() {
	int score =92;
	printf("%d\n", 92 >=90 &&92 <95);// 1 && 1
	printf("%d\n", 90 <=92 <95);  // 1<95
	printf("%d\n", 97 >=90 &&97 <95);//1 && 0
	printf("%d\n", 90 <=97 <95);   // 1<95
	if (score >=90 && score <95) printf("A1\n");
	if (90 <= score <95) printf("A2\n");
	score =97;
	if (score >=90 && score <95) printf("A1\n");
	if (90 <= score <95) printf("A2\n"); // 97이 범위 내에 있지 않지만 범위 내에 있는 것처럼 참으로 인식, 논리적 오류
	return 0;
}
```

## 비트 연산자 예

```cpp
#include <stdio.h>
int main() {
	int a =0x1;    //2진수로 [0000 * 7] 0001, 16진수로 0000 0001
	int b =0x3;    //2진수로 [0000 * 7] 0011, 16진수로 0000 0003
	printf("%x\n", a & b);   // [0000 * 7] 0001
	printf("%x\n", a | b);   // [0000 * 7] 0011
	printf("%x\n", a ^ b);   // [0000 * 7] 0010
	printf("%x\n", a ^ b ^ b); // [0000 * 7] 0001
	printf("%x\n", ~a);    // [1111 * 7] 1110
	printf("%x\n", ~b);    // [1111 * 7] 1100
	return 0;
}
```

## 시프트 연산자 예

```cpp
#include <stdio.h>
int main() {
	printf("%d\n", 90 <<1); //180
	printf("%d\n", 90 *2); //180
	printf("%d\n", 90 <<2); //360
	printf("%d\n", 90 <<3); //720 
	printf("%d\n", 90 <<4);//1440 
	printf("%d\n", 90 >>1); //45
	printf("%d\n", 90 /2); //45
	printf("%d\n", 90 >>2); //22
	printf("%d\n", 90 >>3); //11
	return 0;
}
```

## & 연산자 예

```cpp
#include <stdio.h>
int main() {
	int a =10, b =20;
	printf("변수 a의 값=%d, 주소=%p\n", a, &a);
	printf("변수 b의 값=%d, 주소=%p\n", b, &b);
	return 0;
} // 지역 변수는 메모리의 스택이란 공간에 저장되는데 컴퓨터, OS, 컴파일러, 실행할 때마다 다름
```

## 출처
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
