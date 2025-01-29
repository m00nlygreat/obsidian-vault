## void main()

다트 코드가 실행되면 main() 함수가 실행된다.

## 함수

```dart
	이름 (파라미터) {}
```

## 세미콜론

formatter는 세미콜론을 자동으로 입력해주지 않는다. 세미콜론을 안쓰는 경우가 있기 때문

### Cascade operator

# 변수 (Variables)

- `String name = 'moon';` 과 같이 타입 지정할 수 있음
- 로컬 변수를 만들면 그냥 `var` 쓰면 됨
	- 타입은 픽스됨
	- 업데이트할 수 있음 (값을 변경할 수 있음)

## Dynamic

- 어떤 타입이든 될 수 있는 변수 타입
- `dynamic name;`과 같이 선언
	- 코드 내에서 타입이 확인되면 IDE가 타입에 대한 자동완성을 지원함.

## Null Safety

- 기본적으로 Null 값을 참조할 수 없도록 하는 것.
- `String? name = 'moon'`과 같이 선언하면 nullable을 표현할 수 있다
	- `name?.isNotEmpty;`와 같이 **null이 아니라면**을 표현할 수 있다

## `final` keyword

- `final String name = 'moon'` 수정할 수 없는 변수를 만든다.
	- 어차피 수정할 수 없으니 타입지정은 안해도 된다.

## `late` modifier

- `late final String name name;`
- 데이터 없이 변수를 생성하고자 할 때 late 수식어를 사용
	- API로부터 받아온다든지
- 값에 접근하기 전에 할당해야함

## `const` keyword

- TS/JS의 const는 final과 비슷하게 작동
- dart의 `const`는 compile-time constant를 생성
	- 따라서 컴파일 시 그 값을 알고 있어야 한다.

# Data types

## 이것들은 모두 class임

- String
- bool (`true`/`false`)
- num 
	- int
	- double

## Complex types

### list

```dart

void main() {
	List<int> numbers = [1,2,3,4];
}

```

#### collection if

```dart

var numbers = [1,2,3,4, if(true) 5]

```

### string interpolation

```dart

var name = 'moon';
var age = 37;
var string = 'hello, everyone my name is $name and I'm ${age+2}';

```

