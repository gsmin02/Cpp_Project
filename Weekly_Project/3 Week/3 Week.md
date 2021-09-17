## 세 수의 최댓값, 최솟값

```c
#include<iostream>
using std::cout;
using std::cin;
int main() {
	int num1, num2, num3, max, min;
	cout <<"세개의 다른 수를 입력하고 Enter를 누르세요=";
	cin >> num1; cin >> num2; cin >> num3;
	if (num1 > num2) { max = num1; min = num2; }
	else { max = num2; min = num1; }
	if (num3 > max) max = num3;
	if (num3 < min) min = num3;
	cout <<"최댓값="<< max <<", 최솟값="<< min <<"\n";
	return 0;
}
```

## switch~case문 계산기

```c
#include <iostream>
using std::cout;
using std::cin;
using std::endl;
int main() {
	char op;
	int num1, num2;
	cout <<"덧셈과 뺄셈만 가능합니다\n"<<endl;
	cout <<"계산하려는 수식(예:10+20)을 입력하세요:";
	cin >> num1; cin >> op; cin >> num2;
	switch (op)
	{
	case '+':
		cout <<"덧셈결과는 "<< num1 + num2 <<"입니다.\n"<<endl;
		break;
	case '-':
		cout <<"뺄셈결과는 "<< num1 - num2 <<"입니다.\n"<<endl;
		break;
	default:
		cout <<"다시 입력하세요\n"<<endl;
		break;
	}
}

```

## 100부터 1까지 5의 배수 출력 프로그램

```c
#include <iostream>
using std::cout;
using std::endl;
int main() {
	for (int i =100; i >=1; i--) {
		if (i % 5 ==0) {
			cout << i <<" ";
		}
	}
	return 0;
}
```

## for 문으로 C++ 스타일로 이름 10번 출력

```c
#include <iostream>
using std::cout;
using std::endl;
int main() {
	for (int i =1; i <=10; i++) {
		std::cout.width(2); //다음에 출력되는 하나(i)를 두칸에 출력
		std::cout << i <<" : 이름\n";
	}
}

```

## ASCII코드 표를 출력

```c
#include <iostream>
using std::cout;
using std::endl;
int main() {
	int i;
	for (i =0; i <128; i++) {
		cout << i <<"="<<char(i) <<"\t";
	}
	return 0;
}
```

## switch~case문 계산(반복)

```c
#include <iostream>
using std::cout;
using std::cin;
using std::endl;
int main() {
	char op;
	int num1, num2;
	for (; ; ) {
		cout <<"\n덧셈과 뺄셈만 가능합니다\n";
		cout <<"끝내려면 0+0을 입력하세요\n";
		cout <<"계산하려는 수식(예:10+20)을 입력하세요:";
		cin >> num1; cin >> op; cin >> num2;
		if (num1 ==0 && num2 ==0) {
			break;
		}
		switch (op) {
		case '+':
			cout <<"덧셈 결과는 "<< num1 + num2 <<"입니다.\n";
			break;
		case '-':
			cout <<"뺄셈 결과는 "<< num1 - num2 <<"입니다.\n";
			break;
		default:
			cout <<"다시 입력하세요\n";
			break;
		}
	}
}
```

## 임의의 개수의 수를 입력 받아 합과 평균 출력

```c
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int i, num, sum =0, total;
	cout <<"임의의 수의 평균을 구하는 프로그램입니다.\n";
	cout <<"계산하려는 수는 몇 개입니까==";
	cin >> total;
	for (i =1; i <= total; i++) {
		cout << i <<"번째 수를 입력하세요=";
		cin >> num;
		sum += num;
	}
	cout <<"합은"<< sum <<", 평균은 "<< (double)sum / total <<" 입니다.\n";
	return 0;
}
```

## if문 예제 1

```c
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int score;
	cout <<"당신의 점수를 입력하고 Enter를 누르세요=";
	cin >> score;
	// 첫 번째 방법
	if (score <60) cout <<"60점 미만이므로 재수강해야 합니다.\n";
	// 두 번째 방법
	if (score <60)
		cout <<"60점 미만이므로 재수강해야 합니다.\n";
	// 세 번째 방법
	if (score <60) {
		cout <<"60점 미만이므로 재수강해야 합니다.\n";
	}
	// 네 번째 방법
	if (score <60)
	{
		cout <<"60점 미만이므로 재수강해야 합니다.\n";
	}
	return 0;
}
```

## if문 예제2

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)) {
	int score;
	printf("당신의 점수를 입력하고 Enter를 누르세요=");
	scanf("%d", &score);
	if (score ==0) printf("1: 0점입니다.\n");
	if (!score) printf("2: 0점입니다.\n");
	if (score !=0) printf("1: 0점이 아닙니다.\n");
	if (score) printf("2: 0점이 아닙니다.\n");
	return 0;
}
```

## if문 예제 3

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int score;
	printf("당신의 점수를 입력하고 Enter를 누르세요=");
	scanf("%d", &score);
	if (score >=90 && score <95) printf("1:A\n");
	if (90 <= score <95) printf("2:A\n");
	return 0;
}
```

## if문 예제 4

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num;
	printf("주민등록번호 뒷 자리의 첫 번째 숫자를 입력하세요=");
	scanf("%d", &num);
	if (num ==1) printf("당신은 남성이군요!\n");
	if (num ==2) printf("당신은 여성이군요!\n");
	return 0;
}
```

## if~else문 예제 1

```c
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int num1, num2;
	cout <<"두 개의 다른 수를 입력하고 Enter를 누르세요=";
	cin >> num1; cin >> num2;
	if (num1 > num2) cout <<"두 수 중 더 큰 수는 "<< num1 <<"입니다.\n";
	if (num1 < num2) cout <<"두 수 중 더 큰 수는 "<< num2 <<"입니다.\n";
	// else cout << "두 수 중 더 큰 수는" << num2 << "입니다.\n";
	return 0;
}
```

## if~else문 예제 2

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int score;
	printf("당신의 점수를 입력하고 Enter를 누르세요=");
	scanf("%d", &score);
	if (score <60) printf("60점 미만이므로 재수강해야 합니다.\n");
	else printf("60점 이상이므로 Pass입니다.\n");
	return 0;
}
```

## if~else문 예제 3

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num1, num2, max;
	printf("두 개의 다른 수를 입력하고 Enter를 누르세요=");
	scanf("%d %d", &num1, &num2);
	if (num1 > num2) max = num1;
	else max = num2;
	//max=(num1>num2) ? num1 : num2;
	printf("더 큰 수는 %d입니다.\n", max);
	return 0;
}
```

## if~else문 예제 4

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	char ch;
	printf("키보드로 키 하나를 입력하세요=");
	scanf("%c", &ch);
	if (ch >='a'&& ch <='z') printf("영어 소문자 입니다.\n");
	else printf("영어 소문자가 아닙니다.\n");
	return 0;
}
```

## if~else문 예제 5

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int year;
	printf("2월이 29일까지 있어서 1년이 366일인 해를 윤년이라고 한다.\n");
	printf("연도가 평년인지 윤년인지를 출력해주는 프로그램입니다.\n");
	printf("알고 싶은 연도를 입력하세요 : ");
	scanf("%d", &year);
	if (year % 4 ==0 && year % 100 !=0 || year % 400 ==0)
		printf("%d년은 윤년입니다.\n", year);
	else
		printf("%d년은 평년입니다.\n", year);
	return 0;
}
```

## 다중 if~else문 1

```c
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int num;
	cout <<"당신의 주민등록번호 뒷 자리의 첫 번째 숫자를 입력하세요=";
	cin >> num;
	if (num ==1 || num ==3)
		cout <<"당신은 남성이군요!\n";
	else if (num ==2 || num ==4)
		cout <<"당신은 여성이군요!\n";
	else
		cout <<"당신은 대한민국 사람이 아니군요!\n";
	return 0;
}
```

## 다중 if~else문 2

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	char ch;
	printf("키보드로 키 하나를 입력하세요=");
	scanf("%c", &ch);
	if (ch >='a'&& ch <='z')
		printf("영어 소문자입니다.\n");
	else if (ch >='A'&& ch <='Z')
		printf("영어 대문자입니다.\n");
	else
		printf("영문자가 아닙니다.\n");
	return 0;
}
```

## 다중 if~else문 3

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int value;
	printf("1~3까지의 수를 입력하세요:");
	scanf("%d", &value);
	if (value ==1) printf("1을 입력하셨습니다.\n");
	else if (value ==2) printf("2를 입력하셨습니다.\n");
	else if (value ==3) printf("3을 입력하셨습니다.\n");
	else printf("잘못 입력하셨습니다.\n");
	return 0;
}
```

## 다중 if~else문 4

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num1, num2, num3, max;
	printf("세 개의 다른 수를 입력하고 Enter를 누르세요=");
	scanf("%d %d %d", &num1, &num2, &num3);
	if (num1 > num2) max = num1;
	else max = num2;
	if (num3 > max) max = num3;
	//else max = max;
	///max=(num1>num2) ? num1 : num2;
	///max=(num3>max) ? num3 : max;
	printf("입력받은 수는 %d, %d, %d이고,\n", num1, num2, num3);
	printf("최댓값은 %d입니다.\n", max);
	return 0;
}
```

## 다중 if~else문 5

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num1, num2, num3, max, min;
	printf("세개의 다른 수를 입력하고 Enter를 누르세요=");
	scanf("%d %d %d", &num1, &num2, &num3);
	if (num1 > num2) { max = num1; min = num2; }
	else { max = num2; min = num1; }
	if (num3 > max) max = num3;
	if (num3 < min) min = num3;
	printf("최댓값=%d, 최솟값=%d\n", max, min);
	return 0;
}
```

## 다중 if~else문 6

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num1, num2, num3, max, min;
	printf("세개의 다른 수를 입력하고 Enter를 누르세요=");
	scanf("%d %d %d", &num1, &num2, &num3);
	if (num1 > num2) { max = num1; min = num2; }
	else { max = num2; min = num1; }
	if (num3 > max) max = num3;
	if (num3 < min) min = num3;
	printf("최댓값=%d, 최솟값=%d\n", max, min);
	return 0;
}
```

## switch~case문 예제

```c
#include <iostream>
using std::cout;
using std::cin;
int main() {
	int value;
	cout <<"1~3까지의 수를 입력하세요:";
	cin >> value;
	switch (value) {
	case 1:
		cout <<"1을 입력하셨습니다.\n";
		break;
	case 2:
		cout <<"2를 입력하셨습니다.\n";
		break;
	case 3:
		cout <<"3을 입력하셨습니다.\n";
		break;
	default:
		cout <<"다시 입력하세요.\n";
		break;
	}
	return 0;
}
```

## 자신의 이름을 1000번 출력

```c
#include <iostream>
using std::cout;
int main() {
	int n;
	for (n =1; n <=1000; n++) {
		cout <<"이름 ";
	}
	return 0;
}

```

## 1부터 100까지 더하기

```c
#include <iostream>
using std::cout;
using std::endl;
int main(void)
{
	int n, sum =0; // 초기화를 하지 않으면 쓰레기값이 들어가서 이상한 값이 나옴
	for (n =1; n <=100; n++) {
		sum = sum + n;
	}
	cout << sum <<endl;
	return 0;
}
```

## for문 주의사항

```c
#include <stdio.h>
int main(void)
{
	int n, sum =0;
	for (n =1; n <=100; n++);
	sum = sum + n; //이 문장은 for문과 상관없는 문장. 한번만 실행됨
	printf("%d\n", sum);
	return 0;
}
```

## 두 수를 입력 받아 합과 평균 출력

```c
#define _CRT_SECURE_NO_WARNINGS //Visual Studio에서만 사용
#include <stdio.h>
int main(void)
{
	int num, sum =0;
	//누적하는변수 sum은 반드시초기화
	printf("1번째 수를 입력하세요=");
	scanf("%d", &num);
	sum = sum + num;
	printf("2번째 수를 입력하세요=");
	scanf("%d", &num);
	sum = sum + num;
	printf("합:%d,평균:%lf \n", sum, sum /2.);
	return 0;
}
```

## 수를 입력 받아 합과 평균 출력력

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void)
{
	int i, num, sum =0;
	for (i =1; i <=2; i++) {
		printf("%d번째 수를 입력하세요=", i);
		scanf("%d", &num);
		sum += num;
	}
	printf("합은%d,평균은%lf\n", sum, sum /2.0);
	return 0;
}
```

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void)
{
	int i, num, sum =0;
	for (i =1; i <=3; i++) {
		printf("%d번째 수를 입력하세요=", i);
		scanf("%d", &num);
		sum += num;
	}
	printf("합은%d,평균은%lf\n", sum, sum /3.0);
	return 0;
}
```

## 1부터 1000까지 점점 느리게 출력

```c
#include <stdio.h>
int main(void)
{
	int n, m;
	for (n =1; n <=1000; n++)
	{
		printf("%d ", n);
		for (m =1; m <= n *10000; m++);//점점 느리게 하는 부분
	}
	return 0;
}
```

## 2중 for문 예

```c
#include <stdio.h>
int main(void)
{
	int i, j;
	for (i =1; i <=10; i++) {
		for (j =0; j < i; j++) {
			printf("%3d", i);
		}
		printf("\n");
	}
	return 0;
}
```

## 문자 ‘q’를 입력 받을 때까지 계속 입력

```c
#include <stdio.h>
#include <conio.h>//_getche()
int main(void)
{
	char key;
	printf("키 하나를 누르세요. q를 누르면 종료=");
	do {
		key = _getche();
	} while (key !='q');
	printf("\n바이~~\n");
	return 0;
}
```

## 0부터 100점 사이의 점수를 입력받아 P/F 판단

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void)
{
	int score;
	printf("당신의 점수를 입력하고 Enter를 누르세요\n");
	do {
		printf("점수가 0에서 100사이의 값이 아니면 다시 입력 합니다=");
		scanf("%d", &score);
	} while (!(score >=0 && score <=100));
	if (score <60) printf("60점 미만이므로 재수강해야 합니다.\n");
	else printf("60점 이상이므로 Pass입니다.\n");
	return 0;
}
```

## 메뉴를 가지고 있는 프로그램의 기본 틀

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void)
{
	int menu;
	do {
		printf("\n메뉴\n");
		printf("1: 추가\n");
		printf("2: 삭제\n");
		printf("3: 저장\n");
		printf("원하는 작업을 선택하세요->");
		scanf("%d", &menu);
	} while (!(menu >=1 && menu <=3));
	printf("%d를 선택했습니다.\n");
	return 0;
}

```

## 1부터 어떤 수까지 더해야 10000이 넘는가?

```c
#include <stdio.h>
int main(void)
{
	int n =1, sum =0;
	while (1) { //for (; ;) {
		sum += n;
		if (sum >10000) break;
		++n;
	}
	printf("n=%d, sum=%d\n", n, sum);
	return 0;
}
```

## 1부터 100까지 홀수만 출력

```c
#include <stdio.h>
int main(void)
{
	int n;
	for (n =1; n <=100; n++)
	{
		if (n % 2 ==0) continue;
		printf("%3d ", n);
	}
	return 0;
}
```

## 함수 만들기 1

```c
#include <stdio.h>
void display() {
	printf("안녕");
}
int main() {
	display();
	return 0;
}
```

## 함수 만들기 2

```c
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

```c
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

```c
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

```c
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

```c
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

```c
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

## 출처
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
