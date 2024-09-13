# Dart Programming Language

# 1. Basic Syntax

- **Entry Point**

  ```dart
  void main() {
    // Your code here
  }
  ```

- **Printing to Console**
  ```dart
  print('Hello, Dart!');
  ```

# 2. Variables and Constants

## Variable Declaration

```dart
var name = 'Alice'; // Type inferred
String city = 'New York'; // Explicit type
```

## Constants

```dart
final String lastName = 'Doe'; // Runtime constant
const int maxItems = 10; // Compile-time constant
```

# 3. Data Types

## 3.1 Primitive Types

- `int`: Integer values
- `double`: Floating-point values
- `String`: Text values
- `bool`: Boolean values (true/false)

## 3.2 Collections

- **List**: Ordered collection
- **Set**: Unordered collection of unique items
- **Map**: Key-value pairs

# 4. Control Flow

## 4.1 Conditional Statements

```dart
if (age > 18) {
  print('Adult');
} else {
  print('Minor');
}

// Switch case
switch (day) {
  case 'Monday':
    print('Start of the week');
    break;
  default:
    print('Another day');
}
```

### if-else Conditional Statements

```dart
 var love = "god"
 var power
 if (love == "god"){
   power = "self"
}
print(love)
```

Or,

```dart
var love = "god"
var power
if (love == "god"){
  power = "self"
}
else {
   power = "depend"
}
print(love)
```

Or,

```dart
 var love = "god"
 var power = love == "god" ? "self" : "depend"
 print(love)
```

Or,

```dart
  var love
  var power = love ?? "depend"
  print(love)
```

## 4.2 Loops

```dart
// For loop
for (var i = 0; i < 5; i++) {
  print(i);
}

// For-in loop
for (var fruit in fruits) {
  print(fruit);
}

// While loop
while (condition) {
  // code
}

// Do-while loop
do {
  // code
} while (condition);
```

# 5. Functions

## Defining Functions

```dart
int add(int a, int b) {
  return a + b;
}

// Arrow syntax for single-expression functions
int multiply(int a, int b) => a * b;
```

## Optional Parameters

```dart
void greet(String name, [String greeting = 'Hello']) {
  print('$greeting, $name!');
}

void greetNamed({required String name, String greeting = 'Hello'}) {
  print('$greeting, $name!');
}
```

## Anonymous Functions (Lambdas)

```dart
var list = [1, 2, 3];
var squared = list.map((x) => x * x);
```

# 6. Collections

## Lists

```dart
List<String> fruits = ['Apple', 'Banana', 'Cherry'];
fruits.add('Date');
fruits.removeAt(0); // Removes 'Apple'
```

## Maps

```dart
Map<String, int> scores = {'Alice': 90, 'Bob': 85};
scores['Charlie'] = 95; // Add new entry
```

## Sets

```dart
Set<String> uniqueFruits = {'Apple', 'Banana', 'Apple'}; // 'Apple' will be added once
```

# 7. Classes and Objects

## Defining a Class

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age); // Constructor

  void introduce() {
    print('Hi, I am $name and I am $age years old.');
  }
}

// Creating an object
var person = Person('John', 30);
person.introduce();
```

## Getters and Setters

```dart
class Rectangle {
  double width;
  double height;

  Rectangle(this.width, this.height);

  double get area => width * height; // Getter
  set setWidth(double w) => width = w; // Setter
}
```

## Static Members

```dart
class MathUtils {
  static int add(int a, int b) => a + b;
}

var sum = MathUtils.add(5, 3);
```

## 7.1 Inheritance and Mixins

### Inheritance

```dart
class Animal {
  void speak() {
    print('Animal speaks');
  }
}

class Dog extends Animal {
  @override
  void speak() {
    print('Woof');
  }
}
```

### Mixins

```dart
mixin Flyer {
  void fly() {
    print('Flying');
  }
}

class Bird with Flyer {
  void chirp() {
    print('Chirp');
  }
}
```

# 9. Asynchronous Programming

### Future and Async/Await

```dart
Future<String> fetchData() async {
  // Simulate a network call
  await Future.delayed(Duration(seconds: 2));
  return 'Data loaded';
}

void loadData() async {
  String data = await fetchData();
  print(data);
}
```

## Stream

```dart
Stream<int> countStream() async* {
  for (var i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i; // Emit value
  }
}

void listenToStream() {
  countStream().listen((value) {
    print(value);
  });
}
```

# 10. Error Handling

- **Try-Catch**
  ```dart
  try {
    var result = 10 ~/ 0; // Integer division
  } catch (e) {
    print('Error: $e');
  } finally {
    print('This will always execute');
  }
  ```

# 11. Libraries and Packages

- **Importing Libraries**
  ```dart
  import 'dart:math'; // Math library
  import 'dart:convert'; // JSON encoding/decoding
  import 'package:http/http.dart' as http; // External package
  ```

# 12. Working with JSON

- **Encoding and Decoding JSON**

  ```dart
  import 'dart:convert';

  // Encoding
  var jsonString = jsonEncode({'name': 'John', 'age': 30});

  // Decoding
  var jsonData = jsonDecode(jsonString);
  print(jsonData['name']); // Output: John
  ```

# 13. Useful Dart Functions

- **String Manipulation**

  ```dart
  String str = 'Hello, Dart!';
  print(str.toUpperCase()); // HELLO, DART!
  print(str.substring(7, 11)); // Dart
  ```

- **List Operations**

  ```dart
  List<int> numbers = [1, 2, 3, 4, 5];
  print(numbers.reversed.toList()); // [5, 4, 3, 2, 1]
  ```

- **Map Operations**
  ```dart
  Map<String, int> ages = {'Alice': 30, 'Bob': 25};
  ages.forEach((key, value) {
    print('$key is $value years old');
  });
  ```

#### 14. **Advanced Features**

- **Extension Methods**

  ```dart
  extension StringExtensions on String {
    String get reversed => split('').reversed.join('');
  }

  void main() {
    print('Dart'.reversed); // traD
  }
  ```

- **Null Safety**

  ```dart
  String? nullableString; // Can be null
  String nonNullableString = 'Hello'; // Cannot be null

  // Null-aware operators
  var length = nullableString?.length; // Returns null if nullableString is null
  ```

- **Type Aliases**

  ```dart
  typedef IntList = List<int>;

  IntList numbers = [1, 2, 3];
  ```

#### 15. **Best Practices**

- **Use `const` for Compile-Time Constants**

  ```dart
  const pi = 3.14; // Use const for values that won't change
  ```

- **Use `final` for Runtime Constants**

  ```dart
  final currentTime = DateTime.now(); // Use final for values that are determined at runtime
  ```

- **Use `var` for Type Inference**

  ```dart
  var name = 'Alice'; // Use var when the type is obvious
  ```

- **Use `@override` for Overriding Methods**
  ```dart
  @override
  void speak() {
    print('Woof');
  }
  ```