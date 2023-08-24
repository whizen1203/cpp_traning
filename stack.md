## Stack은 아주 많이 사용되는 자료구조(중요)

직독직해로는 '쌓아놓은 더미'라는 의미.

### 후입선출(LIFO : Last-In First-Out)


#### 스택 vs 큐 vs 리스트

##### 공통점 : 
1. 선형자료구조의 형태를 취한다. 
2. 순서가 존재한다.


##### 차이점 : 
-리스트(List) : 읽기, 삽입(insert), 삭제(delete)를 리스트의 어느곳에서나 행함
-스택(Stack) : 삽입(insert), 삭제(delete)를 리스트의 한쪽 (Top)에서 행함
-큐(Queue) : 삽입(insert)는 리스트의 한쪽(rear)에서 하고, 삭제(delete)는 삽입의 반대쪽(front에서 행함)


#### 스택의 구조와 사용
자료 출력순서가 역순으로 이루어질 때 요긴하게 사용됨  ex) 되돌리기 기능

-상단(stack top) : 스택에서 입출력이 이루어지는 부분
-하단(stack bottom) : 반대쪽 바닥부분
-요소(element) : 스택에 저장되는 것들
-공백 스택(empty stack) : 공백상태의 스택
-포화 스택(full stack) : 포화상태인 스택


#### 시스템 스택(system stack) 함수 호출: 운영체제가 사용하는 스택

-복귀주소 기억 : 함수의 실행이 끝나면 자신을 호출한 함수로 되돌아감. 
##### '스택은 복귀할 주소를 기억하기 위해'
사용됨.

-활성 레코드(activation recode) : 시스템 스택에는 함수가 호출될 때마다 활성 레코드가 만들어지며, 그 활성 레코드에 복귀 주소가 저장됨.
이하 생성 정보 목록
1. 복귀 주소
2. 프로그램 카운터
3. 매개변수
4. 함수 내부에서 선언된 지역변수


#### 시스템 스택 대강 예시 
이미지 : 
![Stack][logo]
[logo] https://ifh.cc/g/BXVKgM.png

-사용예시 : Undo(되돌리기) 기능, 괄호검사, 계산기, 미로탐색


#### 스택 추상자료형
-스택은 후입선출(LIFO)의 접근 방법을 유지하는 0개 이상의 요소를 지닌 선형 리스트의 일종.

1. 스택 ADT(추상데이터 타입)
- 객체 : n개의 요소(element)들의 선형리스트

<table>
'연산'|기능
'init()'|스택을 초기화
'create()'|스택을 생성
'is_empty(s)|스택이 비어있는지 검사
is_full(s)| 스택이 가득차있는지 검사
push(e)|스택의 맨 위에 요소 e 추가
pop(s)| 스택의 맨 위 요소를 삭제
peek(s)| 스택의 맨 위 요소를 삭제하지 않고 반환
</table>


2. 스택의 연산 : 스택에 요소를 추가 / 삭제하는 연산과, 현재 스택 상태를 검사하는 연산들로 구성됨.

<table>
'연산'|기능
'top()'|스택 맨 위에 있는 데이터 값 변환
'push()'|스택에 데이터 삽입
'pop()'|스택에서 데이터 삭제하여 반환
'isempty()'|스택에 원소가 없으면 'True', 있으면 'False'값 반환
'isfull()'|스택에 원소가 없으면 'False', 있으면 'True'값 반환


#### 스택의 정적 / 동적 구현
-스택은 리스트와 마찬가지로 정적 / 동적의 2가지 방법으로 구현 가능.

##### 1. 스택의 정적 구현 : 1차원 배열 사용

1) 스택의 생성
- top : 가장 최근에 입력되었던 자료를 가리키는 변수
- stack[0]...stack[top] : 먼저 들어온 순으로 저장
- 공백 상태 : top = -1

``` c++
// 1차원 배열 사용

#define MAX_StackSize 100 //매크로 설정 MAX_StackSize를 100으로.

int stack[Max_StackSize]

// top의 초기 값은 스택이 비어있을 경우 -1이다.
int top = -1;

```


2)스택의 삽입(push)

``` c++
void push(int item)
{
	if (top >= Max_StackSize - 1) 
	{
	    stack_full();
	    return;
	}
	
	    stack[++top] = item;
	    // top ++; stack[top] = item;
}


// push (x)

if is_full(S)
	then error "overflow"
	else top <- top + 1     // <- == 유사코드(pseudocode) 할당(assign) 연산자. 
			   // 유사 코드에서는 프로그래밍 언어의 구체적인 문법을 따르지 않고 알고리즘의 로직을 설명하는 데에 초점을 둠. 표준 프로그래밍 언어와는 다르게, 간단하고 직관적인 표기법을 사용하기도 함.
			   // 예시로 제시된 코드에서 e <- data[top]는 e 변수에 data 배열의 top 번째 원소를 할당한다는 의미. 같은 방식으로 top <- top-1은 top의 값을 1 감소시킨다는 것을 나타냄.
			   // C++나 대부분의 프로그래밍 언어에서는 = 연산자를 사용해 변수에 값을 할당. 따라서, 유사 코드를 실제 코드로 변환할 때는 <-를 =로 바꿔함.
	    data[top] <- x
```


3) 스택의 삭제(Pop)

``` c++
int pop() 
{
    if (top == -1) return stack_empty();

    // int x; x = stack[yop]; top--; return x;
}


// pop()
if is_empty()
    then error "underflow"
else e <- data[top]
    top <- top-1
    return e
```


4) 스택의 검사(isempty / isfull)

``` c++
//스택이 비어있는지 검사하는 함수
int isempty()
{
    if (top < 0) return(1);
    
    else return(0);   
}

// 스택이 가득 차 있는지 검사하는 함수
int isfull()
{
    if (top >= Max_StackSize -1)  return(1);   // 여기에는 매크로가 안걸려 있지만, 위에서 매크로를 작성했으니 그냥 넘어감. Max_StackSize == 100
    
    else return(0);
}
```


##### 2. 스택의 동적 구현 : 연결 리스트 사용

- 장점 : 크기 제한 없음.
- 단점 : 구현이 복잡하고, 삽입 / 삭제 시간이 오래걸림.

1) 스택의 생성 
``` c++
// 요소의 타입
typedef int element;  // typedef == 자료형의 별칭 변경. int를 element로 변경.

typedef struct StackNode
{
    element item;
    struct StackNode *link;
} StackNode; // 연결된 스택 관련 데이터. struct StackNode에 StackNode라는 별칭을 부여한 것. 나중에 StackNode라는 이름만으로 struct StackNode를 가져와 쓸 수 있음.

typedef struct 
{
    StackNode * top;
} LinkedStackType;
```

2) 스택의 삽입
``` c
element pop(LinkedStackType * s)
{
    if ( is_empty(s) )
    {
        fprintf(stderr, "스택이 비어있음\n"); // fprintf는 printf와 다르게 지정된 파일(이 경우는 stderr)안에서 문자열을 출력함. 
				 // 지금 같은 경우는 stderr이 무슨 파일인지 지정하지 않아서 햇갈릴 수 있지만, stderr에 지정된 파일에 "스택이 비어있음\n"을 저장하는 방식.

        exit(1);
    }

    else 
    {
        StackNode * temp = s->top;	// -> == Arrow Operator. 포인터를 통해 구조체나 클래스 멤버에 접근할 대 사용함.
        int item = temp->item;
        s->top = s->top -> link;
        free(temp);			// free() 함수는 동적할당된 메모리를 해제할 때 사용함. 위에서 할당하고 사용했던 temp의 역할이 끝났기 때문에 temp의 메모리를 해제한 것.
        return item;
    }
}
```

3) 스택의 삭제
``` c
// 삭제 함수
element pop(LinkedStackType * s)
{
    if ( is_empty(s) ) 
    {
        fprintf(stderr, "스택이 비어있음\n");
        exif(1);
    }
    
    else
    {
        StackNode * temp = s->top;
        int item = temp->item;
        s->top = s->top->link;
        free(temp);
        return item;
    }
}
```


이하 스택 넣고(push) 빼기(pop) 간단 예시 코드
``` c++
#include <iostream>
#include <vector>
using namespace std;

// T 타입의 원소를 저장하는 스택 클래스
template <typename T>
class Stack {
private:
    vector<T> elements; // 스택의 원소들을 저장하는 벡터

public:
    // 스택이 비어있는지 확인하는 함수
    bool isEmpty() const {
        return elements.empty();
    }

    // 스택의 맨 위에 원소를 추가하는 함수
    void push(const T& element) {
        elements.push_back(element);
    }

    // 스택의 맨 위의 원소를 제거하는 함수
    void pop() {
        if (isEmpty()) {
            cerr << "스택이 비어있습니다." << endl;
            return;
        }
        elements.pop_back();
    }

    // 스택의 맨 위의 원소를 반환하는 함수
    T top() const {
        if (isEmpty()) {
            cerr << "스택이 비어있습니다." << endl;
            return T(); // 기본 생성된 값 반환
        }
        return elements.back();
    }
};

int main() {
    Stack<int> stack; // int 타입의 스택 객체 생성

    stack.push(10); // 스택에 10 추가
    stack.push(20); // 스택에 20 추가
    stack.push(30); // 스택에 30 추가

    // 스택의 맨 위의 원소 출력
    cout << "스택의 맨 위의 원소: " << stack.top() << endl; // 30 출력

    stack.pop(); // 스택의 맨 위의 원소 제거
    cout << "pop 후 스택의 맨 위의 원소: " << stack.top() << endl; // 20 출력

    stack.pop(); // 스택의 맨 위의 원소 제거
    cout << "다시 pop 후 스택의 맨 위의 원소: " << stack.top() << endl; // 10 출력

    stack.pop(); // 스택의 맨 위의 원소 제거

    // 스택이 비어있는지 확인
    if (stack.isEmpty()) {
        cout << "스택이 비어있습니다." << endl;
    }

    return 0;
}
```
