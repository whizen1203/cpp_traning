## 복사 대입 연산자 (Copy Assignment Operator)
: 이미 생성된 객체에 대해 다른 객체의 값을 복사하여 대입할 때 호출됨.
복사 대입 연산자는 한 객체의 내용을 다른 객체에 복사할 때 사용되는 연산자. 
복사 생성자와는 달리 이미 생성된 객체에 다른 객체의 내용을 복사할 때 사용. 
복사 대입 연산자는 = 연산자를 오버로딩하여 정의할 수 있다.

**줄여서 '대입 연산자'라고 부름.**

기본적으로 컴파일러는 클래스에 대해 복사 대입 연산자를 암시적으로 제공. 
이 암시적 복사 대입 연산자는 얕은 복사(shallow copy)를 수행하기 때문에, 동적 메모리 할당이나 특별한 자원 관리가 필요한 경우에는 복사 대입 연산자를 직접 정의


``` cpp
class MyClass {
private:
    int* data;
public:
    MyClass(int value) {
        data = new int(value);
    }

    // 복사 대입 연산자
    MyClass& operator=(const MyClass& other) {
        if (this == &other) // 자기 자신에 대한 대입을 막기 위한 검사
            return *this;

        delete data; // 기존에 가지고 있던 자원을 해제
        data = new int(*(other.data)); // 깊은 복사 수행

        return *this;
    }

    ~MyClass() {
        delete data;
    }
};
```

예시:

cpp
Copy code
class MyClass {
private:
    int* data;
public:
    MyClass(int value) {
        data = new int(value);
    }

    // 복사 대입 연산자
    MyClass& operator=(const MyClass& other) {
        if (this == &other) // 자기 자신에 대한 대입을 막기 위한 검사
            return *this;

        delete data; // 기존에 가지고 있던 자원을 해제
        data = new int(*(other.data)); // 깊은 복사 수행

        return *this;
    }

    ~MyClass() {
        delete data;
    }
};

### 주의점
1. 자기 대입 (Self-Assignment): 자기 자신에 대한 대입을 처리할 수 있도록 코드를 작성해야 한다. 위 예시의 경우, if (this == &other) 조건문이 이 역할을 맡는다.
2. 자원 해제: 복사 대입을 수행하기 전에 객체가 이미 가지고 있던 자원을 적절히 해제해야 한다. 위 예시에서는 delete data;가 이 역할을 한다.


## 복사 생성자 (Copy Constructor)
: 객체가 생성될 때 다른 객체로부터 초기화되는 경우에 호출됨. **보통은 '복사 연산자'라고 부름.**

예: MyClass obj2 = obj1;
