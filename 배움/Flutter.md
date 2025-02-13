## How flutter works

- 플러터는 게임엔진(모든 픽셀을 연산하는)처럼 작동한다
- 각 플랫폼에 네이티브로 작성된 Runner 앱이 플러터 코드를 해석하여 화면을 렌더링
- Material, Cupertino 등의 네이티브와 비슷한 스타일 Theme을 만들어놓긴 했지만 근본적으로 네이티브가 아님

# Provider

- Provider가 제공할 모델을 먼저 만들어야 한다. Provider는 이 클래스의 인스턴스를 하위 위젯트리에 전달한다. 여기서는 FishModel
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

### ChangeNotifierProvider

```dart
ChangeNotifierProvider(
	create: (context) {return FishModel(name: 'Salmon', number: 10,);}
	child: Widget(),
)
```

- rebuild가 필요없는 위젯에서는 of 메서드에 `listen: false`를 인자로 전달한다.

## MultiProvider

- Provider를 중첩하면 더러우니까 한 번에 만들자

```dart
MultiProvider(
	providers: [
		ChangeNotifierProvider(...),
		ChangeNotifierProvider(...)
	],
	child: Widget(),
)
```

## Riverpod

- Provider의 아나그램. Provider의 개발자 Remi가 새로 만들었다고 한다. 이유는
- Riverpod snippets 확장을 설치하자

### ProviderScope()

- 최상위 위젯트리에 위치

### ConsumerStatefulWidget

- Stateful widget 대신 씀

### StateProvider

- int, string, boolean, enum 등의 단순한 상태관리를 위한 위젯으로 NotifierProvier의 단순화 버전

```dart
// 별개의 파일에 작성한다. 아마도 파일이 분리된 위젯에서도 사용할 수 있게 하기 위해서인듯?

final counterProvider = StateProvider((ref) => 0); // 기본값의 의미가 있음.
```

- ref.read()
- ref.watch();
- Deprecate 될 예정이니 그냥 NotifierProvider를 사용하자

### NotifierProvider

