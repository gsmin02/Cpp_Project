
# 최종 정리 - 중요 내용

중간 정리 이후 내용 중, 중요하다 생각되는 부분들을 따로 정리 및 작성

## 이항 연산자 중첩 : + 연산자

```cpp
#include <iostream>
using std::cout;
class Point {
    int x, y; // private변수
public:
    Point() { x = 0; y = 0; }
    Point(int xx, int yy) { x = xx; y = yy; }
    Point operator +(Point ob);
    int getX() { return x; }
    int getY() { return y; }
};
Point Point::operator +(Point ob) {
    Point temp;
    temp.x = x + ob.x;
    temp.y = y + ob.y;
    return temp;
}
int main() {
    Point ob1(3, 5), ob2(4, 6), ob3;
    cout << ob3.getX() << ", " << ob3.getY() << " ";
    ob3 = ob1 + ob2; // 이항연산자 + 호출
    cout << ob3.getX() << ", " << ob.getY();
    return 0;
}
```

## 상속 접근제어 속성에 따른 파생 클래스 멤버의 속성변화

- 상속 접근제어 속성에 따라 기본 클래스 멤버의 속성의 파생 클래스에서 어떻게 변하는지를 나타낸다.
- 일반적으로 public 상속이 제일 많이 이루어짐

속성 | private | protected | public
:---: | :---: | :---: | :---:
private | 상속불가 | 상속불가 | 상속불가
protected | private | protected | protected
public | private | protected | public

## protected 멤버 변수

```cpp
class A {
protected:
    int a, b;
public:
    void setAB(int i, int j) { a = i, b = j; }
};

class B:public A {
    int c;
public:
    void setC(int n) { c = n; }
    void showABC() { cout << a << b << c << endl; }
}
```

## 파생 클래스 생성자에서 기본 클래스 생성자에 매개변수 전달 형식

- ``` 파생클래스생성자(매개변수리스트):기본클래스생성자(매개변수리스트) { } ```

```cpp
class A {
    int a;
public:
    A(int i) {
        cout << "A의 생성자\n";
        a = i;
    }
    ~A() { cout << "A의 소멸자\n"; }
    void showA() { cout << a << '\n'; }
};
class B: public A {
    int b;
public:
    B(int i, int j):A(i) { // i는 클래스 생성자의 매개변수로 전달
        cout<<"B의 생성자\n";
        b = j;
    }
    ~B() { cout << "B의 소멸자\n"; }
    void showB() { cout << b << endl; }
};
```

## 상속에서 class diagram

- 이름 앞에 -는 private, #은 protected, +는 public

| Name |
| :---: |
| -name |
| +get_name  +print_name |
| ↑ |
| Phone |
| -phone |
| +get_phone  +print_phone |

## 오버로딩, 오버라이딩

- 오버로딩

```cpp
class A {
private:
    int age;
public:
    A() { age = 1; }
    A(int a) { age = a; }
};
```

- 오버라이딩

```cpp
class A {
public:
    virtual int SS(int i) { return (i * 2); }
};
class B: public A {
public:
    int SS(int i) { return (i * 3);}
}
```

## 정적(static) 멤버변수

```cpp
#include <iostream>
using std::cout;

class Point {
    int x;
    int y;
    static int count; // 선언
public:
    Point() { cout << ++count; }
    ~Point() { cout << --count; }
};
int Point::count = 0; // 정의
int main() {
    Point p1, p2, p3;
    return 0;
}
```

## 템플릿 구현 형식

```cpp
template <class 자료형이름> 리턴형 함수이름(배개변수리스트) {
    // 함수 코드
}
```

```cpp
template <class T> void SS(T x, T y) { // 여기서 T는 결정하지 않은 자료형
    // 함수 코드
}
```

## 템플릿 구현

```cpp
#include <iostream>
using std::cout;

template <class T> T Min(T n1, T n2) { //  자료형이 T, 리턴형, 매개변수가 모두 T 형
    return (n1 < n2 ? n1 : n2);
}
int main() {
    int min_i;
    min_i = Min(3, 6); // 매개변수 자료형이 정수형으로 T는 int형이 됨
    cout << min_i << ", ";
    
    double min_d;
    min_d = Min(10.3, 20.6); // 매개변수 자료형이 double형으로 T는 double형이 됨
    cout << min_d;
    return 0;
}
```

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
    return (x + y);
}
```

- 실매개변수는 실제 값을 갖는 매개변수
- 형식매개변수는 실매개변수를 전달받기 위한 형식적인 매개변수
- 형식매개변수는 다른 어떤 변수명을 사용해도 됨
- add()함수는 다음과 같이 만들어도 됨
  - ``` int add(int a, int b) { return (a + b); } ```

## 매개변수를 전달하는 방법 - 매우 중요

- C 언어에서는 기본적으로 값에 의한 호출(call by value)
- 실매개변수의 값을 형식매개변수로 전달
- 이 방법은 실매개변수를 형식매개변수로 전달할 뿐 함수 내부에서 형식매개변수가 변경되더라도 실매개변수는 변경되지 않음
- 형식매개변수가 변하면 실매개변수도 변하게 하려면 포인터를 이용하여 call by reference로 구현해야 함

값에 의한 호출 (call by value) | 주소에 의한 호출 (call by reference)
:---: | :---:
실매개변수의 값을 형식매개변수로 전달 | 실매개변수의 주소를 형식매개변수로 전달

## 참조자(reference) - 매우 중요

- C++에서만 가능
- A reference is an alternative name for an object (Bjarne Stroustrup).
- 참조자를 사용하려면 파일명이 .cpp이어야 함
- 변수의 별명
  - int & rx = x;
  - rx는 x를 참조하도록 초기화된 정수형 참조자
  - 참조자(rx)에 변화를 주면 그 타켓(x)도 변함

```cpp
#include <iostream>
using std::cout;
using std::endl;
int main(void) {
    int x = 10;
    int& rx = x; // rx는 x의 참조자
    cout << x << " " << rx << endl;
    rx = rx + 10;
    cout << x << " " << rx << endl; // 참조자(rx)에 변화를 주면 그 타겟도(x)로 변함
    x = x + 10;
    cout << x << " " << rx << endl; // 타겟(x)애 변화를 주면 그 참조자도(rx)도 변함
    return 0;
}
```

## call by reference - 매우 중요

- 포인터 사용 C, C++ 가능

```cpp
void up(int* a);
int main() {
    int a = 2;
    cout << a << endl;
    up(&a);
    cout << a << endl;
    return 0;
}
void up(int *a) {
    *a = *a + 1;
    cout << *a << endl;
}
```

- 참조자(reference)를 사용하는 방법 C++ 가능

```cpp
void up(int &a);
int main() {
    int a = 2;
    cout << a << endl;
    up(a);
    cout << a<< endl;
    return 0;
}
void up(int &a) {
    a = a + 1;
    cout << a << endl;
}
```

- 값(value)를 사용하는 방법 C, C++ 가능

```cpp
void up(int a);
int main() {
    int a = 2;
    cout << a << endl;
    up(a);
    cout << a<< endl;
    return 0;
}
void up(int a) {
    a = a + 1;
    cout << a << endl;
}
```

## 템플릿을 이용해 일반화된 클래스 구현 - 매우 중요

```cpp
#include <iostream>
using std::cout;
using std::endl;

template <class T1, class T2> class CCC {
    T1 x;
    T2 y;
public:
    CCC(T1 xx, T2 yy) { x = xx; y = yy; }
    void Print() { cout << x << ', ' << y << endl; }
};
int main() {
    CCC<int, int> C1(10, 20);
    CCC<double, double> c2(3.5, 5.5);
    CCC<char, const char*> c3('I', "Love You!");

    c1.Print();
    c2.Print();
    c3.Print();
    return 0;
}
```

## vector 컨테이너

```cpp
#include <iostream>
#include <vector>
using namespace std;
int main() {
    vector <int> x;
    x.push_back(1);
    x.push_back(2);
    for (int i = 0; i < x.size(); i++) {
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

    cout << str << endl; // 안녕!Hi
    for (int i = 0; i < str.size(); i ++) {
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

## 코드 1

```cpp
#include <iostream>
using namespace std;
class Cat {
private:
    int age;
    string name;
public:
    /*
    Cat(int age, string n) {
        this -> age = age;
        name = n;
        cout << name << "고양이 객체가 만들어졌어요.\n";
    }
    */
    Cat(int age, string n) {
        this -> age = age;
        name = n;
        cout << name << "고양이 객체가 만들어졌어요.\n";
    }
    Cat() { age = 1; name = "냥이"; }
    // 디폴트 생성자, 동적 할당된 배열 객체가 호출
    ~Cat() { cout << name << "객체 바이\n"; };
    int getAge() const;
    string getName() const;
    string setAge(int age);
    void setName(string pName);
    void meow() const;
    void cry(int x = 1);
};
void Cat::cry(int x) {
    for (int i = 0; i < x; i++) {
        cout << name << "야옹~~~";
    }
    cout << endl;
}
int Cat::getAge() const { return age; }
void Cat::setAge(int age) { this -> age = age; }
void Cat::setName(string pName) { name = pName; }
string Cat::getName() const { return name; }
coid Cat::meow() const { cout << name << "고양이가 울어요\n"; }

int main() {
    Cat nabi, yaong(2, "야옹"), *pNabi;
    int num, pAge;

    cout << nabi.getName() << " 출생 나이는 " << nabi.getAge() << " 살이다.\n";
    cout << yaong,getName() << " 출생 나이는 " << yaong.getAge() << " 살이다.\n";
    pNabi = &nabi;
    cout << pNabi -> getName() << " 출생 나이는 " << pNabi -> getAge() << " 살이다.\n";

    nabi.setName("Nabi");
    nabi.setAge(3);
    cout << nabi.getName() << " 나이는 " << nabi.getAge() << " 살이다.\n";

    yaong.meow();
    nabi.meow();
    nabi.cry();

    cout << "\n동적으로 생성할 고양이 수==";
    cin >> num;
    Cat* pCat = new Cat[num]; // 객체배열을 동적으로 메모리 할당, default 생성자 만들어야 함
    if (!pCat) { cout << "동적으로 메모리할당이 되지 않았습니다."; exit(1); }
    for (int i = 0; i < num; i++) {
        cout << "pCat[" << i <<"]" << " 객체의 나이ㄹㄹ 입력하십시오 : ";
        cin >> pAge;
        pCat[i].setAge(pAge);
    }
    for (int i = 0; i < num; i++) {
        cout << "pCat[" << i << "]" << " 객체의 나이는 " << pCat[i].getAge() << "입니다.\n";
    }

    cout << endl;

    delete[] pCat;
    // 할당 받은 메모리 해제, 배열로 할당받은 경우 delete 다음에 반드시 []를 써야 함
    return 0;
}
```

## 코드 2 - 가장 중요

```cpp
#include <iostream>
using std::cout;
using std::endl;
using std::string;

class Man {
    string name;
    int age;
public:
    Man(string n, int a) {
        name = n;
        age = a;
    }
    void m_show();
};
void Man::m_show() {
    cout << "이름 : " << name << endl;
    cout << "나이 : " << age << endl;
}
class Student : public Man {
    string ban;
    string hak;
public:
    Student(string n, int a, string b, string h) : Man(n, a) {
        ban = b;
        hak = h;
    }
    void s_show();
};
void Student::s_show() {
    m_show();
    cout << "반 : " << ban << endl;
    cout << "학번 : " << hak << endl;
}
class Teacher : public Man {
    string major;
    string subject;
public:
    Teacher(string n, int a, string m, string s) :Man(n , a) {
        major = m;
        subject = s;
    }
    void t_show();
};
void Teacher::t_show() {
    m_show();
    cout << "전공 : " << major << endl;
    cout << "담당과목: " << subject << endl;
}

int main() {
    Student gsm("구승민", 20, "A반", "202112401");
    Teacher hsh("한미소", 40, "전산", "C++프로그래밍");

    gsm.s_show();
    hsh.t_show();
    return 0;
}
```

# 최종 정리 - 기타 내용

## const 변수 사용법 4가지

- ``` const int x = 1; // 변수 x는 항상 초기값 1, 변경 불가 ```
- ``` int const y = 1; // 비추, const는 자료형 앞에 씀 ```
- ``` const int z{1}; // Uniform initialization, C++11 ```
- ``` constexpr int a = 5; // C++11부터 가능, compile-time constant ```

## const 멤버

- const로 지정된 함수에서는 멤버변수의 값을 변경할 수 없다.
  - 즉, 멤버를 참조만 하는 읽기 전용 함수(앞에서 get으로 시작하는 함수)가 된다.
- const형을 선언하고자 하면 멤버변수는 형 앞에 const를, 멤버함수는 함수의 괄호 다음에 const를 추가한다.
  - ``` const int age; // 멤버변수는 형 앞에 ```
  - ``` int getAge() const; // 멤버함수는 괄호 다음에 ```

```cpp
int getAge() const {
    return age;
}
```

## 포인터 선언 - 중요

- 포인터 변수는 자료형과 변수명 사이에 구두점 *를 더 쓰면 됨
  - ``` int *x; ```

## 참조 연산자 *

- 실행문에서 사용하는 *는 참조 연산자, 포인터의 주소로 가서 값을 가져옴
  - ``` y = *px; ```

## 동적 메모리를 사용하는 이유 - 중요

- 지역 변수는 자신의 지역({ }) 내에서만 유효한데, 전역변수처럼 프로그램이 끝날 때까지 값을 유지하고 싶은 경우
- 프로그램 작성시(컴파일시)는 필요한 메모리 공간의 크기를 모르겠고, 프로그램을 실행할 때(runtime) 메모리의 양을 결정해야 하는 경우
- 변수 선언 시 지역 변수가 저장되는 스택은 한정되어 있어서 너무 큰 크기는 할당 어려움

## new와 delete

- new는 메모리를 동적으로 할당하고, 할당된 메모리에 대한 주소를 반환하는 연산자이다.
  - malloc() 함수와 마찬가지로, 요구한 만큼의 메모리가 충분하지 않으면 new는 null 포인터를 반환한다.
  - ``` int *pi = new int; ```
  - ``` int \*pi = (int *)malloc(sizeof(int)); ```
- delete는 free()함수와 마찬가지로, 더 이상 필요 없는 메모리를 해제한다.
  - ``` delete pi; ```
  - ``` free(pi); ```
  - 해제하지 않으면 메모리 누수(leak)가 발생하여 다른 프로그램에서도 해당 메모리는 사용하지 못한다.

## 동적메모리 할당 - 중요

```cpp
int main() {
    int i, nl
    int *num; // 포인터 선언
    std::cin >> i;

    num = new int[i];
    if (num == NULL) exit(1); // 종료
    for (n = 0; n < i; n++) {
        std::cout << "숫자를 입력하십시오 : ";
        std::cin >> num[n]; // 포인터 이지만 배열로 사용
    }
    delete[] num; // 배열로 선언했기 때문에 배열 삭제
    return 0;
}
```

```cpp
int main() {
    Dog *dp; // 포인터 객체 선언
    dp = new Dog[10]; // 객체배열 동적 할당
    if (!dp) {
        std::cout << "메모리할당이 되지 않았습니다.";
        return 1;
    }
    for (int i = 0; i < 10; i++) {
        dp[i].setAge(i); // 포인터이지만 배열 입력, 배열의 이름은 그 배열의 시작주소
    }
    for (int i = 0; i < 10; i++) {
        std::cout << i << "번째 객체의 나이는 " << dp[i].getAge() << " 입니다. " << std::endl;
    }

    delete []dp;
    return 0;
}
```

## 함수 중첩

- 임의의 형의 두 매개변수 중 큰 값을 반환하는 Max()라는 함수를 작성하시오. 즉, Max()함수가 매개변수로 int, double, char 등을 모두 가질 수 있도록 함수를 중첩시키시오.

```cpp
int Max(int i, int j) {
    return i > j ? i : j;
}
double Max(double i, double j) {
    return i > j ? i : j;
}
char Max(char i, char j) {
    return i > j ? i : j;
}
```

## 함수 중첩(오버로딩)을 하는 2가지 경우

- 매개변수의 형이 다른 경우
- 매개변수의 개수가 다른 경우

## 생성자 중첩

- 일반적으로 중첩(오버로딩)을 가장 많이 사용하는 경우는 생성자 중첩이다
- 여러가지 방법으로 객체를 만들 수 있게 하기 위해 생성자 중첩을 많이 이용한다.

## 디폴트 인자

- ``` int add(int i = 1, int j = 2) ```
- 일단 디폴트 매개변수를 정의하기 시작하면 그 다음(오른쪽)의 매개변수들은 모두 디폴트 매개변수를 가져야 한다.
- 디폴트 인자를 갖는 생성자를 정의하는 경우 기본적으로 함수 중첩과 같은 효과가 있다.

## 연산자 중첩 형식

- operator라는 키워드를 사용하며, 그 형식은 다음과 같다.
- 단항연산자 중첩
  - ``` 리턴형 operator 연산자명(); // 전치, ++x ```
  - ``` 리턴형 operator 연산자명(int); // 후치, x++ ```
- 이항연산자 중첩
  - ``` 리턴형 operator 연산자명(매개변수); ```

## 전치 단항 연산자 중첩 - 중요

- 해당 클래스의 모든 멤버변수를 동시에 리턴

```cpp
class Point {
    int x;
    int y;
public:
    Point(int i , int j) { x = i; y = j; }
    int getX() { return x; }
    int getY() { return y; }
    Point operator ++() {
        ++x;
        ++y;
        return *this; // 중요
        // 객체를 모두 반환한다.
        // 즉, x, y 모두 리턴
    }
};
```

## 상속 : is-a, is_a, is a 관계

부모 superclass | 기본(Base)클래스 | B
:---: | :---: | :---:
. | inherits from ↑ 상속과정 |
자식 subclass | 파생(Derived) 클래스 | A

- A is a subclass of B
- B is a superclass of A

## static변수

- 정적 바인딩, ``` static int y = 10; ``` 에서 y의 초기값은 컴파일시 10으로 정해지며 실행시에 이 선언문은 실행하지 않음

## C++에서 새로 도입된 cast 연산자

```cpp
int main() {
    int x = 10, y = 4;

    cout << x / y << endl;
    cout << (double)x / y << endl; // 1
    cout << static_cast<double>(x) / y << endl; // 2
    return 0;
}
```

- 1과 2는 같은 소스임

## virtual 있을 때와 없을 때의 차이 - 중요

```cpp
#include <iostream>
using std::cout;

class Dot {
public:
    virtual void draw() { cout << "Dot::draw()\n"; }
    void print() {
        cout << "Dot 클래스\n";
        draw();
    }
};
class Line:public Dot {
public:
    void draw() { cout << "Line::draw()\n"; }
};
int main() {
    Line line;
    line.print();
    return 0;
}
```

## 예외처리

- C++에서는 예외처리라는 내장된 오류처리 기법을 제공한다.
- 이를 이용하여 보다 쉽게 실행 오류에 대처할 수 있다
- 예외처리를 위한 키워드는 try, catch, throw로 다음과 같다.

키워드 | 의미
:---: | :---:
try | 예외를 감시하고자 하는 문장을 이 블록으로 묶음 main() 함수 전체에 포함할 수도 있음
throw | 예외가 발생했을 때 예외 발생을 알리고 던짐
catch | 예외를 받아 처리하는 블록

```cpp
try { // 예외가 발생할 수 있는 코드
    throw 예외값;
}
catch(자료형) {
    // 예외 처리 블럭
}
catch(자료형) {
    // 예외 처리 블럭
}
```

- 하나 이상의 catch문장이 try문과 관련될 수 있다
- 어떤 catch 문장이 사용될 것인지는 예외값의 형에 따라 결정된다.
- catch에 명시된 자료형이 예외의 자료형과 일치한다면, 해당 catch 문장이 실행되며 다른 catch 문장들은 무시한다.

## 헤더파일 나누기

- 헤더파일 - 추가 - 새항목
- 클래스 선언은 헤더파일에 정의는 cpp파일에 하는 것이 일반적

## 출처

C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[googlelink]: https://www.induk.ac.kr
