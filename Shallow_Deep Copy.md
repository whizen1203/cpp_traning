## 얕은 복사 (Shallow Copy)
: 얕은 복사는 객체의 멤버 변수들을 바로 복사하는 방식.
포인터 변수의 경우 포인터 값 자체만 복사하기 때문에, 두 객체는 같은 메모리 주소를 가리키게 됨. 
하나의 객체에서 동적 할당된 메모리의 내용을 변경하면 다른 객체에서도 동일한 변경이 반영됨. 
이로 인해 메모리 누수나 해제 문제가 발생할 수 있다.

``` cpp
class SimpleClass {
private:
    int* data;
public:
    SimpleClass(int val) {
        data = new int(val);
    }

    // 얕은 복사 생성자
    SimpleClass(const SimpleClass& other) : data(other.data) { }
};
```

## 깊은 복사 (Deep Copy)

깊은 복사는 객체가 포인터를 통해 동적 메모리에 접근하는 경우, 해당 메모리 영역까지 새로 할당받아 내용을 복사하는 방식. 
이렇게 하면 두 객체는 서로 다른 메모리 주소를 가리키게 되므로, 하나의 객체에서 동적 할당된 메모리의 내용을 변경해도 다른 객체에는 영향을 주지 않음.

``` cpp
class SimpleClass {
private:
    int* data;
public:
    SimpleClass(int val) {
        data = new int(val);
    }

    // 깊은 복사 생성자
    SimpleClass(const SimpleClass& other) {
        data = new int(*(other.data));
    }
};
```

깊은 복사의 주의점 
: 얕은 복사를 사용할 때는 주의가 필요하다. 두 객체가 같은 메모리 주소를 가리키기 때문에, 하나의 객체에서 메모리를 해제한 후 다른 객체에서 그 메모리에 접근하려고 하면 오류가 발생할 수 있기 때문에, 동적 메모리를 사용하는 경우 깊은 복사를 고려해야 한다.
