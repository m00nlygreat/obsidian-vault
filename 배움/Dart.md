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



# Data types

## 이것들은 모두 class임

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
String sayHello(String potato) => return "Hello, $name";
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

# 클래스 (Classes)

```dart
class Player {
  late final String name; // constructor가 줄 것이므로 late
  late int xp = 1500;
  
  void sayHello(){
    print("Hi my name is $name with $xp");
  } // this는 필요없다.
  
  Player(String name, int xp) {
    this.name = name;
    this.xp = xp;
  }
}
```

### dart의 constructor

```dart
class Player {
  final String name; // 인스턴트 생성 즉시 할당되므로 late는 필요없는듯
  int xp = 1500;
  
  void sayHello(){
    print("Hi my name is $name with $xp");
  }
  
  Player(this.name, this.xp);
}
```

## named constructor / constructor parameters
```dart
class Player {
  final String name;
  int xp, age;
  String team;
  
  void sayHello(){
    print("Hi my name is $name from $team and $age y/o with $xp");
  } // this는 필요없다.

  Player.createBluePlayer({required String name, required int age}) :
	  this.name = name,
	  this.age = age,
	  this.team = 'blue',
	  this.xp = 0;
  Player.createRedPlayer(String name, int age) :
    this.name = name,
    this.age = age,
    this.team = 'red',
    this.xp = 0;
}

void main() {

  var moon = Player.createBluePlayer(name: 'moon', age:37,);
  var agger = Player.createRedPlayer('agger', 32);
  moon.sayHello();
  agger.sayHello();
}
```

- 기본적으로 positional parameters는 모두 required
- constructor 역시 기본적으로 함수이기에, named parameter 역시 동일한 방법을 사용

### JSON data로부터 인스턴스 만들기

```dart
class Player {
  final String name;
  int xp;
  String team;
  
  void sayHello(){
    print("Hi my name is $name from $team with $xp");
  }

  Player.fromJson(Map<String, dynamic> playerJson) :
    name = playerJson['name'],
    team = playerJson['team'],
    xp = playerJson['xp'];
  
 
}

void main() {
  var apiData = [
    {
      "name": "moon",
      "team": "red",
      "xp": 0,
    },
    {
      "name": "agger",
      "team": "blue",
      "xp": 0,
    },
  ];
  
  apiData.forEach((playerJson) {
    var player = Player.fromJson(playerJson);
    player.sayHello();
  });
}
```

## cascade notation

```dart
var moon = Player(name: "moon", xp: 1200, team: "red");
var potato = moon
  ..name = "hyung"
  ..xp = 150000
  ..team = "blue"
  ..sayHello();
```

- 앞에 object를 지칭하는 statement가 있으면 가능한 것 같다.
- 여기서는 그냥 `potato` 또는 `moon`만 써도 cascade notation을 쓸 수 있다.

## enums

```dart
enum Team { red, blue }
```

- 만든 enum은 타입처럼 쓸 수 있다.
- enum은 class처럼 멤버 변수를 갖거나 index, name과 같은 빌트인 멤버들이 있기도 하다.
	- [Enhanced Enums](https://dart.dev/language/enums#declaring-enhanced-enums) 참조
	- Enum은 따로 공부할 것

## abstract class

```dart
abstract class Human {
  void walk();
}

class Player extends Human {
  final String name;
  int xp;
  String team;
  
  void sayHello(){
    print("Hi my name is $name from $team with $xp");
  }

  Player({required this.name, required this.team, required this.xp});
  
  void walk(){
    print("$name walks");
    }
  
 
}

void main() {
  var moon = Player(name: 'moon', team: 'blue', xp: 15000);
  moon.sayHello();
  moon.walk();

}
```

- Human을 

## inheritance

```dart
class Human {
  final String name;
  int age;
  Human({required this.name, required this.age,});
  void sayHi(){
    print("Hi my name is $name and $age y/o");
  } 
}

enum Team { blue, red}

class Player extends Human {
  final Team team;
  
  Player({
    required this.team,
    required String name,
    required int age,
  }) : super(name: name, age: age);
  
  @override
  void sayHi(){
    super.sayHi();
    print("and I work for ${team.name}");
  }
}

void main() {
  var player = Player(team: Team.red, name: 'moon', age: 37,);
  player.sayHi();
}
```

- 익숙해지도록 다시 읽을 것
- Java나 Python의 클래스 상속을 보고 일반적인 문법은 어떻게 되는지 왜 해야 되는지 이해할 필요 있음

## mixins

- 생성자가 없는 클래스
	- 정해둔 값을 가지고 메서드나 프로퍼티를 가져오기 위해 사용

```dart
mixin class Tall { // 또는 그냥 mixin
	final double height = 180.5;
}

class Human with Tall {
  final String name;
  Human(this.name);
    
}

void main(){
  var human = Human('moon');
  print("I'm ${human.name} and I'm ${human.height}cm tall");
}

```
