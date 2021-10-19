# 중간 정리
중요하다고 생각되는 부분만 따로 정리  
C와 공통되는 부분은 적고 C++을 배우면서 새롭게 느낀 부분 중심으로 작성  

## 문자열(string) 리터럴
- <span style="color=red;">※</span>문자열 리터럴에서는 문자열의 끝을 의미하는 NULL 문자가 제일 뒤에 자동적으로 붙여짐

## cast 연산자
- C 언어에서는 혼합연산 시 자료형의 크기가 큰 쪽으로 통일시켜 연산이 이루어짐(자동 형 변환(implicit arithmetic conversion))
- <span style="color=red;">※</span>(자료향)값_이나_변수
    - (int)x, (char)ch, (double)sum
- 숫자 3은 int, (double)3은 일시적으로 double형 3.0

## 관계 연산자 + 논리 연산자
- C 언어에서는 다음과 같이 표현
    - <span style="color=red;">※</span>if (score >= 90 && score < 95)

## &연산자 예
- 코드
```cpp
int a = 10;
printf("변수 a의 값=%d, 주소=%p\n", a, &a);
```
- 결과
```
변수 a의 값=10, 주소=00EFF76C
```



## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일  

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
