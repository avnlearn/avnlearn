# Dart Programming Language

# 1. Basic Syntax

## Entry Point

Every app requires the top-level main() function, where execution starts. Functions that don't explicitly return a value have the void return type.

```dart
void main() {
    // Your code here
}
```


```dart
print("Hello, Dart!");
var name = "Guddu Kumar";
print("Hello, $name");
print("Hello, ${name.toUpperCase()}");
print("Score, ${4 + 3}");
```

# 2. Variables and Constants

## Variable Declaration
### Type inferred


```dart
// Type inferred
var _int = 30101998;
var _double = 3010.1998;
var _String = 'India';
var _bool = true;
var _List = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Saturday'];
var _Set = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
var _Map = {
  'name': "Riya Mehta",
  'age': 20,
  'skill' : ['Programmer', 'Teacher']
};
```

### Explicit type (Data Types)
##### Primitive Types
- `int`: Integer values
- `double`: Floating-point values
- `String`: Text values
- `bool`: Boolean values (`true`/`false`)

##### Collections
- `List`: Ordered collection `[a_1, a_2, ...]`. [more](https://api.dart.dev/stable/3.5.3/dart-core/List-class.html)
- `Set` : Unordered collection of unique items `{a_1, a_2, ...}`. [more](https://api.dart.dev/stable/3.5.3/dart-core/Set-class.html)
- `Map` : Key-value pairs `{key_1 : value_1, key_2 : value_2, ...}`. [more](https://api.dart.dev/stable/3.5.3/dart-core/Map-class.html)


```dart
int number = 987654321;
double decimal = 3010.1998;
String country = 'India';
bool Isdeveloper = true;
List vowels = ['A', 'E', 'I', 'O', 'U'];
Set factor_of_180 = {2, 2, 5, 3, 3};
Map gifts = {
  // Key:    Value
  'first': 'partridge',
  'second': 'turtledoves',
  'fifth': 'golden rings'
};
Map nobleGases = {
  2: 'helium',
  10: 'neon',
  18: 'argon',
};
```

### Constants

- `final`: Runtime constant
- `const`: Compile-time constant


```dart
final String lastName = 'Doe';
const int pi = 3.1416;
```

### Nullable variables
A variable of type int can't have the value null:


```dart
int a = null; // INVALID.
```


```dart
int? a = null; // Valid.
int? a; // The initial value of a is null.
```


```dart
var a = null;
dynamic a = null;
```

### Type Aliases
You can create type aliases in Dart to simplify complex type definitions, making your code more readable.


```dart
typedef IntList = List<int>;

void main() {
  IntList numbers = [1, 2, 3, 4, 5];
  print(numbers); // Output: [1, 2, 3, 4, 5]
}

```

# 4. Operators
## Built-in Operators
Dart provides a variety of built-in operators, including:
* Arithmetic Operators: `+`, `-`, `*`,`/`, `~/` (integer division), `%` (modulus)
* Relational Operators: `==`, `!=`, `>`, `<`, `>=`, `<=`
* Logical Operators: `&&` (and), `||` (or), `!` (not)
* Assignment Operators: `=`, `+=`, `-=`, `*=`, `/=`, `%=`
* Bitwise Operators: `&`, `|`, `^`, `~`, `<<`, `>>`

# 5. Control Flow

## 5.1 `if` Conditional Statements
* Use `int, double, String, List, Set, Map` is compile-time error
* Use `dynamic` is runtime error
* **Notes :** Conditions is only assigned `bool` type

* `if` statement
    ```dart
    if (Conditions){
        // True Statements
    }
    ```
* `if-else` statement
    ```dart
    if (Conditions){
        // True Statements
    } else{
        // False Statment
    }
    ```
* `if-else if-else` statment
    ```dart
    if (Conditions_1){
        // Conditions_1 is True
    } else if (Conditions_2){
        // Conditons_1 is False and 
        // Conditons_2 is True
    } else if (Conditions_3){
        // Conditons_1 is False,
        // Conditons_2 is False and 
        // Conditons_3 is True
    } else {
        // All Conditions are False
    }
    ```
*
  ```dart
  variable = condition ? True_statement : False_statment;
  ```

## 5.2 `switch` Statement

```dart
switch (day) {
  case 'Monday':
    print('Start of the week');
    break;
  default:
    print('Another day');
}
```

## 5.3 Loops

### `while` Loop Statement
while loop check condition before iteration of the loop

```dart
while (condition) {
  // code
}
```
### `do-while` Loop Statement

do-while loop verifies the condition after the execution of the statements inside the loop

```dart
do {
  // code
} while (condition);
```

### `for` Loop Statement

```dart
for (var i = 0; i < 5; i++) {
  print(i);
}
```

```dart
// For-in loop
for (var fruit in fruits) {
  print(fruit);
}
```

## 5.4 Development only
```dart
assert(conditions)
```

# 6. Functions

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

## Functional Programming Features
Dart supports functional programming concepts, allowing you to treat functions as first-class citizens. You can pass functions as arguments, return them from other functions, and assign them to variables.


```dart
void main() {
  var add = (int a, int b) => a + b;
  var result = operate(5, 3, add);
  print(result); // Output: 8
}

int operate(int a, int b, int Function(int, int) operation) {
  return operation(a, b);
}

```

## Higher-Order Functions
Higher-order functions are functions that take other functions as parameters or return them. This is a powerful feature for creating more abstract and reusable code.


```dart
List<int> filter(List<int> list, bool Function(int) test) {
  List<int> result = [];
  for (var item in list) {
    if (test(item)) {
      result.add(item);
    }
  }
  return result;
}

void main() {
  var numbers = [1, 2, 3, 4, 5];
  var evenNumbers = filter(numbers, (n) => n.isEven);
  print(evenNumbers); // Output: [2, 4]
}

```

# 7. Object-Oriented Programming (OOP)

## Classes and Objects

### Defining a Class
A class is a blueprint for creating objects. An object is an instance of a class.


```dart
class Car {
  // Properties
  String color;
  String model;

  // Constructor
  Car(this.color, this.model);

  // Method
  void displayInfo() {
    print('Car model: $model, Color: $color');
  }
}

void main() {
  // Creating an object of the Car class
  Car myCar = Car('Red', 'Toyota');
  myCar.displayInfo(); // Output: Car model: Toyota, Color: Red
}
```

### Getters and Setters


```dart
class Rectangle {
  double width;
  double height;

  Rectangle(this.width, this.height);

  double get area => width * height; // Getter
  set setWidth(double w) => width = w; // Setter
}
```


### Static Members
Static members belong to the class itself rather than to any specific instance. They can be accessed without creating an instance of the class.


```dart
class MathUtils {
  static int add(int a, int b) {
    return a + b;
  }
}

void main() {
  int result = MathUtils.add(5, 3);
  print(result); // Output: 8
}

```

### Operator Overloading
Dart allows you to define how operators work with your custom classes.


```dart
class Vector {
  final double x;
  final double y;

  Vector(this.x, this.y);

  Vector operator +(Vector other) {
    return Vector(x + other.x, y + other.y);
  }

  Vector operator -(Vector other) {
    return Vector(x - other.x, y - other.y);
  }

  Vector operator *(double scalar) {
    return Vector(x * scalar, y * scalar);
  }

  Vector operator /(double scalar) {
    return Vector(x / scalar, y / scalar);
  }

  // Negation operator
  Vector operator -() {
    return Vector(-x, -y);
  }

  // Logical NOT operator (for demonstration)
  bool operator !() {
    return x == 0 && y == 0; // Returns true if the vector is (0, 0)
  }

  @override
  bool operator ==(Object other) {
    if (other is! Vector) return false;
    return x == other.x && y == other.y;
  }

  @override
  int get hashCode => x.hashCode ^ y.hashCode;

  // String Representation:  
  @override
  String toString() => 'Vector($x, $y)';
}

void main() {
  Vector v1 = Vector(2, 3);
  Vector v2 = Vector(4, 5);
  
  Vector sum = v1 + v2;
  Vector difference = v1 - v2;
  Vector scaled = v1 * 2;
  Vector divided = v1 / 2;

  print('Sum: $sum'); // Output: Sum: Vector(6.0, 8.0)
  print('Difference: $difference'); // Output: Difference: Vector(-2.0, -2.0)
  print('Scaled: $scaled'); // Output: Scaled: Vector(4.0, 6.0)
  print('Divided: $divided'); // Output: Divided: Vector(1.0, 1.5)
}

```

#### Index Operator (`[]` and `[]=`)
You can define the index operator to allow array-like access to your objects.


```dart
class Matrix {
  final List<List<int>> _data;

  Matrix(this._data);

  // Index operator for getting values
  int operator [](int index) {
    return _data[index];
  }

  // Index operator for setting values
  void operator []=(int index, List<int> value) {
    _data[index] = value;
  }

  int get length => _vectors.length;
}

void main() {
  Matrix matrix = Matrix([[1, 2], [3, 4]]);
  print(matrix[0]); // Output: [1, 2]
  matrix[1] = [5, 6];
  print(matrix[1]); // Output: [5, 6]
}

```

### Late Initialization
Dart provides the `late` keyword for variables that will be initialized later. This is useful for properties that cannot be initialized in the constructor.


```dart
class User {
  late String name; // Late initialization

  void setName(String newName) {
    name = newName;
  }
}

void main() {
  User user = User();
  user.setName('Alice');
  print(user.name); // Output: Alice
}

```

### Null Safety
Dart has built-in null safety, which helps prevent null reference errors. You can define nullable and non-nullable types.


```dart
class Person {
  String name; // Non-nullable
  int? age; // Nullable

  Person(this.name, [this.age]);
}

void main() {
  Person person1 = Person('Bob', 30);
  Person person2 = Person('Alice');

  print('${person1.name} is ${person1.age} years old.'); // Output: Bob is 30 years old.
  print('${person2.name} is ${person2.age ?? 'unknown'} years old.'); // Output: Alice is unknown years old.
}

```

### Metadata and Annotations
Dart allows you to use metadata (annotations) to provide additional information about classes, methods, or properties.


```dart
class Deprecated {
  const Deprecated();
}

@Deprecated()
class OldClass {
  void oldMethod() {
    print('This method is deprecated');
  }
}

void main() {
  OldClass old = OldClass();
  old.oldMethod(); // Output: This method is deprecated
}

```

## Inheritance
Inheritance allows a class to inherit properties and methods from another class.


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


```dart
class Vehicle {
  String brand;

  Vehicle(this.brand);

  void honk() {
    print('Beep! Beep!');
  }
}

class Bike extends Vehicle {
  int wheels;

  Bike(String brand, this.wheels) : super(brand);

  void displayInfo() {
    print('Bike brand: $brand, Wheels: $wheels');
  }
}

void main() {
  Bike myBike = Bike('Yamaha', 2);
  myBike.honk(); // Output: Beep! Beep!
  myBike.displayInfo(); // Output: Bike brand: Yamaha, Wheels: 2
}

```
## Composition
Composition is a design principle where a class is composed of one or more objects from other classes, rather than inheriting from them. This promotes greater flexibility and reusability.

```dart
class Engine {
  void start() {
    print('Engine started');
  }
}

class Car {
  final Engine engine;

  Car(this.engine);

  void start() {
    engine.start();
    print('Car started');
  }
}

void main() {
  var engine = Engine();
  var car = Car(engine);
  car.start(); // Output: Engine started
               //         Car started
}
```

## Encapsulation
Encapsulation is the bundling of data and methods that operate on that data within one unit, and restricting access to some of the object's components.

Encapsulation is the bundling of data (attributes) and methods that operate on that data within a single unit (class). It restricts direct access to some of the object's components, which is a means of preventing unintended interference and misuse.

### Access Modifiers
Dart provides access modifiers to control the visibility of class members:

* **Public**: Members are accessible from anywhere (default).
* **Private**: Members are accessible only within the same library. In Dart, you can make a member private by prefixing its name with an underscore (`_`).

```dart
class BankAccount {
  String _accountNumber; // Private property
  double _balance;

  BankAccount(this._accountNumber, this._balance);

  // Method to deposit money
  void deposit(double amount) {
    if (amount > 0) {
      _balance += amount;
      print('Deposited: \${amount}');
    }
  }

  // Method to get balance
  double get balance => _balance;
}

void main() {
  BankAccount account = BankAccount('123456', 1000.0);
  account.deposit(500.0);
  print('Current balance: \${account.balance}'); // Output: Current balance: $1500.0
}

```

## Polymorphism
Polymorphism allows methods to do different things based on the object it is acting upon.


```dart
class Animal {
  void sound() {
    print('Animal makes a sound');
  }
}

class Dog extends Animal {
  @override
  void sound() {
    print('Dog barks');
  }
}

class Cat extends Animal {
  @override
  void sound() {
    print('Cat meows');
  }
}

void main() {
  Animal myDog = Dog();
  Animal myCat = Cat();

  myDog.sound(); // Output: Dog barks
  myCat.sound(); // Output: Cat meows
}

```

## Abstract Classes
An abstract class cannot be instantiated and is meant to be subclassed.


```dart
abstract class Shape {
  void draw(); // Abstract method
}

class Circle extends Shape {
  @override
  void draw() {
    print('Drawing a Circle');
  }
}

class Square extends Shape {
  @override
  void draw() {
    print('Drawing a Square');
  }
}

void main() {
  Shape circle = Circle();
  Shape square = Square();

  circle.draw(); // Output: Drawing a Circle
  square.draw(); // Output: Drawing a Square
}

```

### Abstract Getters and Setters
You can define abstract getters and setters in abstract classes, allowing subclasses to provide specific implementations.


```dart
abstract class Shape {
  double get area; // Abstract getter
  set color(String c); // Abstract setter
}

class Rectangle implements Shape {
  double width;
  double height;
  String _color;

  Rectangle(this.width, this.height);

  @override
  double get area => width * height;

  @override
  set color(String c) {
    _color = c;
  }

  String get color => _color;
}

void main() {
  Rectangle rect = Rectangle(5, 10);
  rect.color = 'Red';
  print('Area: ${rect.area}, Color: ${rect.color}'); // Output: Area: 50.0, Color: Red
}

```

### Sealed Classes
Dart does not have built-in support for sealed classes, but you can simulate them using abstract classes and private constructors. This is useful for defining a limited set of subclasses.


```dart
abstract class Shape {
  const Shape();
}

class Circle extends Shape {
  final double radius;
  const Circle(this.radius);
}

class Square extends Shape {
  final double side;
  const Square(this.side);
}

// Only Circle and Square can be created
void main() {
  Shape shape = Circle(5);
  // Shape shape2 = Shape(); // This will cause an error
}

```

## Interfaces
In Dart, every class implicitly defines an interface. You can implement multiple interfaces in a class.


```dart
abstract class Animal {
  void sound();
}

abstract class Pet {
  void play();
}

class Dog implements Animal, Pet {
  @override
  void sound() {
    print('Dog barks');
  }

  @override
  void play() {
    print('Dog plays fetch');
  }
}

void main() {
  Dog myDog = Dog();
  myDog.sound(); // Output: Dog barks
  myDog.play();  // Output: Dog plays fetch
}

```

## Mixins
Mixins allow you to reuse a class’s code in multiple class hierarchies. You can use the `with` keyword to apply a mixin.


```dart
mixin Swimmer {
  void swim() {
    print('Swimming');
  }
}

mixin Flyer {
  void fly() {
    print('Flying');
  }
}

class Duck with Swimmer, Flyer {
  void quack() {
    print('Quack');
  }
}

void main() {
  Duck myDuck = Duck();
  myDuck.swim(); // Output: Swimming
  myDuck.fly();  // Output: Flying
  myDuck.quack(); // Output: Quack
}

```

### Constraints
You can create mixins that can only be applied to classes that extend a specific base class.


```dart
class Animal {
  void eat() {
    print('Eating');
  }
}

mixin CanFly on Animal {
  void fly() {
    print('Flying');
  }
}

class Bird extends Animal with CanFly {}

void main() {
  Bird bird = Bird();
  bird.eat(); // Output: Eating
  bird.fly(); // Output: Flying
}

```

## Generics
Generics allow you to create classes, methods, and interfaces that work with any data type while providing type safety.


```dart
class Box<T> {
  T item;

  Box(this.item);

  T getItem() {
    return item;
  }
}

void main() {
  Box<int> intBox = Box<int>(123);
  print(intBox.getItem()); // Output: 123

  Box<String> strBox = Box<String>('Hello');
  print(strBox.getItem()); // Output: Hello
}

```

## Extension Methods
Extension methods allow you to add new functionality to existing libraries or classes without modifying their source code.


```dart
extension StringExtensions on String {
  String get reversed {
    return split('').reversed.join('');
  }
}

void main() {
  String myString = 'Hello';
  print(myString.reversed); // Output: olleH
}

```

## Abstract Classes and Factory Constructors
Abstract classes can have factory constructors that return instances of subclasses.


```dart
abstract class Shape {
  factory Shape(String type) {
    if (type == 'circle') {
      return Circle();
    } else if (type == 'square') {
      return Square();
    }
    throw 'Unknown shape type';
  }

  void draw();
}

class Circle implements Shape {
  @override
  void draw() {
    print('Drawing a Circle');
  }
}

class Square implements Shape {
  @override
  void draw() {
    print('Drawing a Square');
  }
}

void main() {
  Shape shape1 = Shape('circle');
  shape1.draw(); // Output: Drawing a Circle

  Shape shape2 = Shape('square');
  shape2.draw(); // Output: Drawing a Square
}

```

# 8. Collections

# 9. Asynchronous Programming

## Future and Async/Await
Dart supports asynchronous programming using `Future` and `Stream`. This is essential for handling operations like I/O without blocking the main thread.


```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2)); // Simulate a network call
  return 'Data fetched';
}

void main() async {
  print('Fetching data...');
  String data = await fetchData();
  print(data); // Output: Data fetched
}

```

## Stream
Streams allow you to handle a sequence of asynchronous events. You can listen to a stream and react to new data as it arrives.


```dart
Stream<int> countStream() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i; // Yielding values to the stream
  }
}

void main() async {
  await for (var value in countStream()) {
    print(value); // Output: 1, 2, 3, 4, 5 (one per second)
  }
}

```

# 10. Error Handling

## Try-Catch


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

## Importing Libraries


```dart
import 'dart:math'; // Math library
import 'dart:convert'; // JSON encoding/decoding
import 'package:http/http.dart' as http; // External package
```
