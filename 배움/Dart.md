## void main()

다트 코드가 실행되면 main() 함수가 실행된다.

## 함수

```dart
	이름 (파라미터) {}
```

## 세미콜론

formatter는 세미콜론을 자동으로 입력해주지 않는다. 세미콜론을 안쓰는 경우가 있기 때문

### Cascade operator

## 변수 (Variables)

- `String name = 'moon';` 과 같이 타입 지정할 수 있음
- 로컬 변수를 만들면 그냥 `var` 쓰면 됨
	- 타입은 픽스됨
	- 업데이트할 수 있음 (값을 변경할 수 있음)

## Dynamic

- 어떤 타입이든 될 수 있는 변수 타입
- `dynamic name`과 같이 선언
	- 코드 내에서 타입이 확인되면 IDE가 타입에 대한 자동완성을 지원함.

## Null Safety

- 기본적으로 Null 값을 참조할 수 없도록 하는 것.
- `String? name = 'moon'`과 같이 선언하면 nullable을 표현할 수 있다
	- `name?.isNotEmpty;`와 같이 **null이 아니라면**을 표현할 수 있다




