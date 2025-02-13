## How flutter works

- 플러터는 게임엔진(모든 픽셀을 연산하는)처럼 작동한다
- 각 플랫폼에 네이티브로 작성된 Runner 앱이 플러터 코드를 해석하여 화면을 렌더링
- Material, Cupertino 등의 네이티브와 비슷한 스타일 Theme을 만들어놓긴 했지만 근본적으로 네이티브가 아님

## Provider

- Provider가 제공할 모델을 먼저 만들어야 한다. Provider는 ㅇ
- 먼저 `Provider()` 위젯으로 `MaterialApp()`을 감싸줌

```dart
Provider(
	create: (context) {return FishModel(name: 'Salmon', number: 10,);}
	child: Widget
)
```

하위 위젯에서는 `Provider.of<FishModel>(context).name` 의 형태로 데이터를 불러올 수 있다.

- `of<T>(context)` 는 context를 거슬러 올라가 T에 해당하는 인스턴스를 찾아서 반환하는 메서드

### ChangeNotifier

- Provider로 전달할 인스턴스의 클래스에 mixin으로 첨부할 수 있는 기능
- 인스턴스가 변경되었을 때 위젯들에게 변경을 전파한다
- addListner(), removeListener(), notifyListers()
- 수동으로 Listner를 관리해야 하고, 여러 불편한 점이 있기 때문에, ChangeNotifierProvider를 사용하자

