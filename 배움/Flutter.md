## How flutter works

- 플러터는 게임엔진(모든 픽셀을 연산하는)처럼 작동한다
- 각 플랫폼에 네이티브로 작성된 Runner 앱이 플러터 코드를 해석하여 화면을 렌더링
- Material, Cupertino 등의 네이티브와 비슷한 스타일 Theme을 만들어놓긴 했지만 근본적으로 네이티브가 아님

## Provider

- 먼저 `Provider()` 위젯으로 `MaterialApp()`을 감싸줌

```dart
Provider(
	create: (context) {return FishModel(name: 'Salmon', number: 10,);}
	child: Widget
)
```

하위 위젯에서는 `Provider.of<FishModel>(context).name` 의 형태로 데이터를 불러올 수 있다.

- of<T>() 는 T