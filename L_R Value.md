## L-Value / R-Value

### L-Value(Left Value, 좌측 값)의 경우
- '이름'이 있으며 메모리에 지속적으로 위치하고 있는 객체 참조
- L-Value는 대입의 왼쪽과 오른쪽 모두에 나타날 수 있음.

Ex : 
``` 
int x;
// 'x'는 L-Value.
```


### R-Value(Right Value, 우측 값)의 경우
- 일반적으로 임시적인 값이나 반환값 등에 해당하며, 이름이 없거나 다른 곳에 할당되지 않는 객체를 참조.
- R-Value는 대입의 오른쪽에만 나타남.

Ex: 
```
int x = 5+3;
// '5+3'이 R-Value.
```


### 복사와 이동의 차이

#### 복사
: 객체의 내용을 다른 객체에 전달하는 것. 원본 객체는 변하지 않음.

#### 이동
: 객체의 리소스(동적 메모리 등)를 다른 객체로 옮기는 것. 이 과정중에 원본 객체는 해당된 리소스를 더 이상 소유하지 않게 된다.
대부분, 임시 객체로부터 리소스를 가져오는 경우에 사용함.

#### 복사 및 이동 관련 메서드들
- 복사 생성자(Copy Constructor) : 기존 객체로부터 새 객체 초기화
- 복사 대입 연산자(Copy Asssignment Operator) : 기존 객체의 내용을 다른 이미 생성된 객체에 복사한다.
- 이동 생성자(Move Constructor) : 임시 객체의 리소스를 새 객체로 이동시킴.
- 이동 대입 연산자(Move Assignment Operator) : 임시 객체의 리소스를 이미 생성된 객체로 이동시킴.

``` 
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec1 = {1, 2, 3, 4, 5};

    // 복사
    std::vector<int> vec2 = vec1;

    // 이동
    std::vector<int> vec3 = std::move(vec1); 

    // vec1은 사용할 수 없는 상태가 됨
    // vec3는 vec1의 모든 데이터를 소유
}
```
