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

![Variables](Dart/Variables.md)

# Data types

![Data Types](Dart/Data%20Types.md)

# 클래스 (Classes)

![Classes](Dart/Classes.md)

# 비동기 프로그래밍

## Stream

```dart
Stream<int>.periodic(
	Duration(seconds: 1),
	(count) => count
)
```

- Stream 타입을 선언할 때는 `periodic` 메서드를 사용
	- Duration, Function을 argument로 주어야 한다

```dart
Stream<T> optionalMap<T>(Stream<T> source, [T Function(T)? convert]) async* {
  if (convert == null) {
    yield* source;
  } else {
    await for (var event in source) {
      yield convert(event);
    }
  }
}
```