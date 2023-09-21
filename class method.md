## 클래스의 메서드

### 1. 기본 생성자 (Default Constructor)
: 객체를 생성할 때 자동으로 호출되는 메서드로, 특별한 인자를 받지 않는 생성자를 뜻한다.


``` c++ 
MyClass() { }
```

### 2. 파라미터를 가진 생성자 (Parameterized Constructor)
: 하나 이상의 인자를 받는 생성자

``` c++
MyClass(int a, int b) { }
```


### 3. 복사 생성자 (Copy Constructor)
: 같은 타입의 다른 객체를 복사하여 새로운 객체를 생성할 때 사용

``` c++
MyClass(const MyClass& other) { }
```

### 4. 복사 대입 연산자 (Copy Assignment Operator)
: 같은 타입의 다른 객체의 값을 현재 객체에 복사할 때 사용

``` c++
MyClass& operator=(const MyClass& other) { }
```


### 5. 이동 생성자 (Move Constructor)
: 임시 객체(또는 다른 객체)의 자원을 현재 객체로 "이동"할 때 사용. C++11부터 도입됨.

``` c++
MyClass(MyClass&& other) { }
```

### 6. 이동 대입 연산자 (Move Assignment Operator)

임시 객체(또는 다른 객체)의 자원을 현재 객체로 "이동" 대입할 때 사용. C++11부터 도입됨.

``` c++
MyClass& operator=(MyClass&& other) { }
```

### 7. 소멸자 (Destructor)
: 객체가 소멸될 때 호출되는 메서드로, 객체의 자원을 정리하기 위해 사용

``` c++
~MyClass() { }
```

