
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

## 최종 코드

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

    delete[]pCat;
    // 할당 받은 메모리 해제, 배열로 할당받은 경우 delete 다음에 반드시 []를 써야 함
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

부모 suoerclass | 기본(Base)클래스 | B
:---: | :---: | :---:
 | inherits from ↑ 상속과정 |
자식 subclass | 파생(Derived) 클래스 | A

- A is a subclass of B
- B is a superclass of A

## 출처

C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약  
Computer S/W, [Induk Univ][googlelink]  
한성현 교수님 -  hsh@induk.ac.kr  
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[googlelink]: https://www.induk.ac.kr
