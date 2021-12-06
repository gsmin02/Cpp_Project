
# 다형성

## 다형성의 종류

- C++에서 다형성을 실현하는 또 다른 방법으로 템플릿이 있다(인자 다형성).
- 코어션은 수식, 변수 등의 불일치가 생겼을 때 이를 해결해 주는 기능이다.
- 3+5.2와 같은 형 불일치 시 3(int 4byte)을 정확도가 더 높은 3.0(double 8byte)으로 형변환 시키는 것을 말하고 이러한 기능은 C 에도 있다.

# 템플릿

## 템플릿: 포괄적 함수(generic function)

- 템플릿은 인자(매개변수)를 통한 다형성을 제공한다.
- 함수 중첩은 기능이 같은 함수들을 같은 이름으로 사용할 수 있도록 한다.
- 함수의 매개변수의 형과 수로 구분이 되고, 코드 자체도 다르게 구성될 수 있다.
- 그러나, 코드는 전혀 바뀌지 않고 형만 다른 함수를 필요로 한다면 템플릿을 사용하는 것이 좋다.
- 이는 값 뿐만 아니라 형을 인자로 받는 함수로서 인자로 받은 형에 대하여 함수를 생성시키는 포괄적 함수(generic function)이다.

## 실매개변수 vs. 형식매개변수

- 함수들 간에 서로 데이터를 교환할 때 사용하는 것을 함수의 매개변수라고 함
- 실매개변수(actual parameter, argument)
  - 함수를 호출할 때 사용하는 매개변수
- 형식매개변수(formal parameter, parameter)
  - 함수 정의에서 사용하는 매개변수

## 실매개변수와 형식매개변수 예

```cpp
#include <stdio.h>
int add(int x, int y);
int main(void) {
    int sum;
    sum = add(5, 10);
    // 함수를 호출할 때 사용하는 매개변수인 5와 10은 실매개변수, argument
}
int add(int x, int y) { // 함수 정의시 사용하는 x와 y는 형식매개변수, parameter
    // x에 5, y에 10이 전달됨
    return(x + y);
}
```

- 실매개변수는 실제 값을 갖는 매개변수
- 형식매개변수는 실개매변수를 전달받기 위한 형식적인 매개변수
- 형식매개변수는 다른 어떤 변수명을 사용해도 됨
- add()함수는 다음과 같이 만들어도 됨

```cpp
    int add(int a, int b) { // 함수 정의시 사용하는 a와 b는 형식매개변수
        return(a + b);
    }
```

## 매개변수를 전달하는 방법 : 매우 중요

- C 언어에서는 기본적으로 값에 의한 호출(call by value)
- 실매개변수의 값을 형식매개변수로 전달
- 이 방법은 실매개변수를 형식매개변수로 전달할 뿐 함수 내부에서 형식매개변수가 변경되더라도 실매개변수는 변경되지 않음
- 형식매개변수가 변하면 실매개변수도 변하게 하려면 포인터를 이용하여 call by reference로 구현해야 함

값에 의한 호출 (call by value) | 주소에 의한 호출 (call by reference)
:---: | :---:
실매개변수의 값을 형식매개변수로 전달 | 실매개변수의 주소를 형식매개변수로 전달

## 포인터와 주소

- 메모리에는 위치를 구분하기 위해 순서대로 번호가 붙어있는데 이것을 메모리의 주소, 번지, address라 함
- int sum = 0;
  - 변수를 초기화하면서 선언하면, int형이므로 4바이트 메모리 공간이 확보되고 초기값으로 0이 할당됨
  - sum변수가 실제로 할당된 메모리의 주소를 알고 싶다면 &연산자를 사용하여 &sum이라고 하면 변수가 기억되어 있는 메모리 번지를 알 수 있음
- 메모리의 주소를 저장 하려면 일반 변수가 아닌 포인터를 사용
- 포인터라고만 해도 되지만 주소를 저장하는 변수이므로 포인터 변수라고도 함

## 포인터 선언

- 포인터도 변수이므로 사용하기 전에 선언해야 함
- 자료형과 변수명 사이에 구두점 *를 더 쓰면 됨
- 선언문에서 쓰는 *는 곱하기 연산자와 전혀 관계없는 구두점
- *는 자료형과 변수명 사이 아무데나 있어도 됨

## 참조 연산자 *

- 포인터는 일반적으로 일반 변수명 앞에 주소 연산자(&)를 사용해 해당 변수의 주소를 저장
- 포인터 px에는 변수 x의 주소가 들어있음
- px가 저장하고 있는 x의 주소로 가서 그 값인 10을 변수 y에 대입하려면 다음과 같이 하면 됨
- 포인터 앞에 \*를 찍어주면 되는데 이때 *는 참조 연산자
- 곱하기 연산자 *와 모양은 같지만 우선 순위가 높음

## C 언어세어 *(구두점 vs. 연산자)

- 선언문: 포인터를 선언(구두점)할 때
- 실행문: 주소로 가서 값을 가져올 때(연산자)
- *이 선언문에서 사용되는지 실행문에서 사용되는지에 따라서 다름
- 실행문에서 *는 포인터 변수에 저장된 주소로 가서 실제 데이터 값을 가져오는데 사용하는 참조 연산자로 간접 값(indirect value) 연산자, dereferencing 연산자라고도 함

## 참조자(reference) : 매우 중요

- C++에서만 가능
- A reference is an alternative name for an object (Bjarne Stroustrup).
- 참조자를 사용하려면 파일명이 .cpp이어야 함
- 변수의 별명
  - int & rx = x;
  - rx는 x를 참조하도록 초기화된 정수형 참조자
  - 참조자(rx)에 변화를 주면 그 타켓(x)도 변함

## 참조자(reference) 예

```cpp
#include<iostream>
using std::cout;
using std::endl;
int main(void) {
    int x = 10;
    int& rx = x; // rx는 x의 참조자
    cout << x << " " << rx << endl;
    rx = rx + 10;
    cout << x << " " << rx << endl; //참조자(rx)에 변화를 주면 그 타켓(x)도 변함
    x = x + 10;
    cout << x << " " << rx << endl; //타켓(x)에 변화를 주면 그 참조자(rx)도 변함
    return 0;
}
```

## call bt reference

- 형식매개변수가 변하면 실매개변수(a)도 변하게 하려면 주소 연산자와 포인터를 이용하여 call by reference로 구현해야 함
- 실매개변수의 주소로 함수를 호출
  - up(&a);
- 형식매개변수 pa는 주소를 저장해야 하므로 포인터로 선언
  - int *pa
- up 함수 내부에서 포인터 연산(*pa) 을 통해 main함수의 a값 변경

```cpp
// call by reference
#include <iostream>
using std::cout;
using std::endl;
void up(int *pa);
int main() {
    int a = 2;
    cout << a << endl;
    up(&a);
    cout << a << endl;
    return 0;
}
void up(int *pa) { //int *pa = &a
    *pa = *pa+1;
    cout << *pa << endl;
}
```

```cpp
// call by value
#include <iostream>
using std::cout;
using std::endl;
void up(int pa);
int main() {
    int a = 2;
    cout << a << endl;
    up(a); //up(2)
    cout << a << endl;
    return 0;
}
void up(int pa) { //int pa = 2
    pa = pa + 1;
    cout << pa << endl;
}
```

## call by reference

- 실매개변수의 주소를 형식매개변수로 전달
- 함수 호출할 때
  - swap(&a, &b)
  - 실매개변수는 변수의 주소를 전달
- 함수 정의 시
  - swap(int \*pa, int *pb)
  - 형식매개변수는 주소를 받아야 하므로 포인터변수로 받음
- 형식매개변수가 변하면 실매개변수도 변함
- return 값이 여러 개이거나 배열 전체를 전달하는 경우 사용

```cpp
void swap(int *, int *);//선언
int main(void) {
    int a=2,b=5;
    swap(&a,&b); //호출
    return 0;
}
void swap(int *pa, int *pb) {
//정의
}
```

# STL(Standerd Template Library)

## STL

- C++ 표준라이브러리의 일부분
- 자료구조 클래스와 알고리즘 등을 미리 만들어 놓은 라이브러리
- 반복자(iterator)를 가지고 동작하는 C++ 표준 라이브러리의 일부분
- 자주 사용되는 50여 개의 알고리즘과 다양한 자료구조들을 가지고 있음

## STL의 주요 구성 요소

- 컨테이너(container)
  - 객체들을 저장하는 객체나 클래스
  - vector, list, deque, string, map 등
- 반복자(iterator)
  - 컨테이너에 저장된 요소를 순회하고 접근하는 객체나 클래스
- 알고리즘(algorithm)
  - 데이터를 다루기 위한 함수
  - find, sort, search 등
- 함수 객체(function object), 함수자(functor)
  - 함수처럼 동작하는 객체로 operator() 연산자를 중첩한 클래스의 객체

## 컨테이너(container)

- 객체들을 저장하는 객체나 클래스
- 시퀀스 컨테이너(sequence container)
  - vector, deque, list
- 연관 컨테이너(associative container)
  - set, multiset, map, multimap
- 연속 메모리 기반 (contiquous-memory) 컨테이너
  - 데이터 여러개가 하나의 메모리 단위에 저장
  - 배열 기반 컨테이너(array-based container)
  - vector, string, deque
- 노드 기반(node-based) 컨테이너
  - 데이터 하나를 하나의 메모리 단위에 저장
  - list, set, multiset, map, multimap

## vector 컨테이너

```cpp
#include <iostream>
#include <vector>
using namespace std;
int main() {
    vector <int> x; //int x[10]와 차이
    // 여러 개 int형을 가지고 노는 배열 공간을 만들고 싶어요
    x.push_back(1);
    x.push_back(2);
    for(int i = 0 ; i < x.size() ; i++) {
        cout << x[i] << endl;
    }
    return 0;
} 
```

## 문자열 전용 컨테이너 : string 클래스

```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string str = "안녕!";
    cout << str << endl;
    str.push_back('H');
    str.push_back('i');
    cout << str << endl;
    for(int i = 0 ; i < str.size() ; i++) {
        cout << str[i];
    }
    return 0;
}
```

## vector container, iterator, algorithm, functor

```cpp
#include <iostream>
#include <vector> // vector container
#include <algorithm> // sort
#include <functional> // 함수자 less<>, greater<>
using namespace std;
int main() {
  vector<int> v(5); //vector container
  cout << v.size() << " : " << v.capacity() << endl; //5 :5
  //capacity는 할당된 메모리 공간의 크기, size는 저장된 데이터 요소의 개수
  for (int i = 0; i < v.size(); i++) cout << v[i] << ' '; //0 0 0 0 0
  cout << endl;
  for (int i = 0; i < v.size(); i++) v[i] = i + 1;
  for (int i = 0; i < v.size(); i++) cout << v[i] << ' '; //1 2 3 4 5
  cout << endl;
  for (int i = 0; i < 5; i++) v.push_back(10 - i);
  vector<int>::iterator iter; //iterator
  for (iter = v.begin(); iter != v.end(); iter++)cout << *iter << ' ';
  // 1 2 3 4 5 10 9 8 7 6
  sort(v.begin(), v.end()); cout << endl; //algorithm
  for (iter = v.begin(); iter != v.end(); iter++)cout << *iter << ' ';
  // 1 2 3 4 5 6 7 8 9 10
  sort(v.begin(), v.end(), greater<int>()); //functor
  cout << endl;
  for (iter = v.begin(); iter != v.end(); iter++)cout << *iter << ' ';
  // 10 9 8 7 6 5 4 3 2 1
  return 0;
}
```

# friend 함수

## friend함수와 friend클래스

- 클래스 내부의 멤버변수는 대부분 private으로 지정되어 외부에 대하여 감추어져 있다.
- 그러나 이러한 규칙을 깨고 특별히 외부에서 멤버변수들을 접근할 수 있도록 허용한 것이 friend함수와 friend클래스이다.
- 이는 비 객체지향적인 특징이지만 효율적인 프로그래밍을 위해 사용된다.
  - operator overloading시 사용(고급 문법)
- friend는 상대 함수나 클래스를 친구로 선언하여, 해당 클래스의 멤버함수는 아니지만 클래스의 멤버를 자유롭게 사용할 수 있게 하는 함수이다.
- 클래스 A에서 클래스(함수) B를 friend로 지정한 경우 클래스(함수) B는 클래스 A에 마음대로 접근할 수 있지만 A는 B에 접근할 수 없다.
- 클래스(함수) B는 클래스 A를 friend로 하지 않았기 때문이다.

## friend함수

- 현재 클래스에서 전역함수나 특정 클래스의 멤버함수를 friend로 지정한다.
- friend 지정은 public, private, protected 영역 어디라도 상관없다.
- friend함수는 상속하더라도 파생 클래스에 상속되지 않는다.

## friend 함수의 설정 형식

```cpp
class 클래스명 {
    ① friend 리턴형 함수명(매개변수 리스트);
    ② friend 리턴형 클래스명::함수명(매개변수리스트);
};
    ① 전역(외부)함수를 friend함수로 지정
    ② 다른 클래스의 멤버함수를 friend함수로 지정
```

## friend클래스

- 현재 클래스에서 다른 클래스를 friend로 지정
- 이렇게 되면 상대 클래스의 함수들은 현재 클래스의 모든 영역에 접근할 수 있음

# 예외처리

## 예외처리(exception handling, error handling)

- 에러(error)
  - 컴파일 에러 / 실행타임 에러(Run time error)
- 예외(오류) 처리
  - 실행 시간에 발생할 수 있는 오류 처리
- 코드에서 오류가 자주 발생하는 부분
  - 메모리를 할당했는데 메모리를 할당할 수 없는 경우
  - 포인터로 값을 출력하려 하는데 NULL포인터인 경우
  - 파일 열기
  - 소켓 통신
  - 프린팅
  - 사용자 입력
- 오류처리 방법
  - 무방비
  - 오류 발생을 알리고 종료
  - 오류 발생을 알리고 종료/저장 물어 봄
  - 코드에서 알아서 오류를 잡아내고 해결한 다음 정상적으로 프로그램 진행

## 예외처리 방법

- 오류가 발생할 가능성이 있는 코드에 대해 발생할 수 있는 모든 오류의 처리를 미리 해 둔다.
  - 발생할 수 있는 오류를 생각한다.
  - 처리 코드를 만든다.
- 여러가지 오류가 발생할 가능성이 있다면 각각의 오류에 대해 처리하는 코드를 만든다.
- 오류가 발생한 순간 바로 오류처리 코드로 이동할 수 있도록 한다.

## 예외처리 관련 키워드

- C++에서는 예외처리라는 내장된 오류처리 기법을 제공한다.
- 이를 이용하여 보다 쉽게 실행 오류에 대처할 수 있다
- 예외처리를 위한 키워드는 try, catch, throw로 다음과 같다.

키워드 | 의미
:---: | :---:
try | 예외를 감시하고자 하는 문장을 이 블록으로 묶음 main() 함수 전체에 포함할 수도 있음
throw | 예외가 발생했을 때 예외 발생을 알리고 던짐
catch | 예외를 받아 처리하는 블록

## 출처

C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"