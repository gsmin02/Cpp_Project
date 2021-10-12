# 클래스 멤버의 접근권한

## 정수(Integer) 클래스와 객체
■ 정수를 다루기 위한 클래스 Integer
```c
class Intefet{ // Integer라는 이름의 class
    private: // 속성
        int val; // 멤버변수, private 속성
    public: // 이 줄 이하는 public속성
        int getVal(); // 멤버함수, 출력, getter
        int setVal(); // 멤버함수 , 입력, setter
}Val1; // ① 객체를 만드는(정의) 첫 번째 방법
Integer Val2; // ② 객체를 만드는 두 번째 방법
```

## 클래스 멤버의 접근 권한
- 멤버변수와 멤버함수를 선언하기 전에 그들의 속성(멤버의 액세스권한)을 지정
- 클래스 외부에서 멤버에 접근할 수 있는 권한
    - 전용(private)
        - 해당 클래스 내부에서만 접근할 수 있음
        - 디폴트 속성으로 생략 가능
    - 범용(public)
        - 어디에서나 접근할 수 있음
    - 보호(protected)
        - private이지만 자식에게는 접근할 수 있도록 함


# 함수

# 멤버함수의 선언과 정의

# inline 함수

# 객체의 멤버호출

## 출처
C++프로그래밍(21-2학기)한성현교수 강의 내용 변형 및 요약   
Computer S/W, [Induk Univ][googlelink]   
한성현 교수님 -  hsh@induk.ac.kr   
C/C++ 프로그래밍 | 송재철, 한성현, 김경신 공저 | 양서각 | 2007년 03월 03일

[id]: URL "Optional Title here"
[googlelink]: https://www.induk.ac.kr "Go google"
