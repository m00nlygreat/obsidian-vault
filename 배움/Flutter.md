## How flutter works

- 플러터는 게임엔진(모든 픽셀을 연산하는)처럼 작동한다
- 각 플랫폼에 네이티브로 작성된 Runner 앱이 플러터 코드를 해석하여 화면을 렌더링
- Material, Cupertino 등의 네이티브와 비슷한 스타일 Theme을 만들어놓긴 했지만 근본적으로 네이티브가 아님

## Stream

```dart
Stream<int>.periodic(
	Duration(seconds: 1),
	(count) => count
)
```

- Stream 타입을 선언할 때는 `periodic` 메서드를 사용
	- Duration, Function을 argument로 주어야 한다