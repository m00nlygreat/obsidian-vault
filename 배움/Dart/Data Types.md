## 이것들은 모두 class임

프로퍼티와 메서드들을 가지고 있음.

- String
- bool (`true`/`false`)
- num 
	- int
	- double

### string interpolation

```dart

var name = 'moon';
var age = 37;
var string = 'hello, everyone my name is $name and I\'m ${age+2}';

```

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

#### collection for

```dart

var oldFriends = ['악어', '토끼', '붕어'];
var newFriends = [
	'풍수',
	'지녕',
	for (f in oldFriends) "😎${f}",
];

```

### map

```dart
	Map<String, Object> player = {
		'name' : 'moon',
		age : 37,
	}
```

```dart
Map<List<int>, bool> yes_or_nos = {
	[1,2,3]: true,
	[2,3,3]: false,
}
```

- 니코는 key/value pair의 구조를 만들 때(API response를 받아오거나) Map 대신 class를 사용할 거라고 한다.

### set

```dart
Set<int> numbers = {1,2,3,4};
```

- 파이썬의 Set과 같다.

# 함수 (Functions)

```dart
void sayHello(String name) {
	print("Hello $name");
}
```
```dart
String sayHello(String name) {
	return "Hello $name";
}
```

### fat arrow syntax

```dart
String sayHello(String potato) => "Hello, $name";
```

JS의 arrow function과 같은 기능

## named parameters

```dart
String sayHello(
		{
			required String name, 
			required age, 
			String country = 'Korea'
		}
	) => return "Hello, $name. You are $age years old and you came from $country";

print(sayHello(
	name: 'agger', 
	age: 32,
	))
```

- 함수 선언부에 curly braces를 사용해 named parameter임을 밝히는 게 포인트
- named parameter에 기본값 제공 
- `requied` 키워드를 사용해 필수 파라미터를 밝힘

## optional positional parameters

- Positional parameters를 고수하면서도 optional한 parameter를 받을 수 있는데

```dart
String sayHello(
	String name, 
	int age, 
	[String? country = 'Korea],
) => "Hello $name, you are $age y/o and came from $country";

print(sayHello('Moon', 37));
```

## QQ operator (null-aware operator)

### `??`

```dart
String capitalizeName(String? name) => name?.toUpperCase() ?? 'moon'
```

- 좌항의 name 객체 호출에도 `?`를 붙이는 것에 유의 (null일 수 있음을 컴파일러에게 알려주는 것임)

### `??=`

```dart
String? name
name ??= 'moon' // name이 null이면 'moon'을 할당
```

## typedef

- 타입의 alias를 생성하는 기능
- 같은 타입이지만 다른 의미를 가질 때도 추상적인 의미로서 붙이면 좋음

```dart
typedef ListOfInts = List<int>;

ListOfInts reverseListOfNumbers(ListOfInts list) => list.reversed.toList();

void main() {
	print(reverseListofNumbers([1,2,3]));
}

```

```dart
typedef UserInfo = Map<String, String>;
String sayHi(Map<String, String> userInfo) => "Hi ${userInfo['name']}"

void main() {
pr
}
```



