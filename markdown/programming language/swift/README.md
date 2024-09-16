### 1. Introduction to Swift

Swift is a powerful and intuitive programming language developed by Apple for iOS, macOS, watchOS, and tvOS app development. It is designed to be easy to use and is known for its performance and safety.

### 2. Setting Up Your Environment

To start programming in Swift, you need to set up your development environment:

- **Xcode**: Download and install Xcode from the Mac App Store. Xcode is the official IDE for Swift development.
- **Playgrounds**: You can use Swift Playgrounds for experimenting with Swift code in a more interactive way.

### 3. Basic Syntax

#### Hello World

```swift
print("Hello, World!")
```

#### Variables and Constants

- **Variables**: Use `var` to declare a variable.
- **Constants**: Use `let` to declare a constant.

```swift
var name = "John"
let age = 30
```

#### Data Types

Swift has several built-in data types:

- **Int**: Integer values
- **Double**: Floating-point values
- **String**: Text values
- **Bool**: Boolean values

```swift
var score: Int = 100
var pi: Double = 3.14
var greeting: String = "Hello"
var isActive: Bool = true
```

### 4. Control Flow

#### Conditional Statements

```swift
let score = 85

if score >= 90 {
    print("Grade: A")
} else if score >= 80 {
    print("Grade: B")
} else {
    print("Grade: C")
}
```

#### Loops

- **For Loop**:

```swift
for i in 1...5 {
    print(i)
}
```

- **While Loop**:

```swift
var count = 5
while count > 0 {
    print(count)
    count -= 1
}
```

### 5. Functions

Functions are reusable blocks of code.

```swift
func greet(name: String) -> String {
    return "Hello, \(name)!"
}

let message = greet(name: "Alice")
print(message)
```

### 6. Optionals

Optionals are a powerful feature in Swift that allows variables to have a "no value" state.

```swift
var optionalName: String? = nil
optionalName = "Bob"

if let name = optionalName {
    print("Name is \(name)")
} else {
    print("Name is nil")
}
```

### 7. Collections

#### Arrays

```swift
var fruits = ["Apple", "Banana", "Cherry"]
fruits.append("Date")
print(fruits[0]) // Output: Apple
```

#### Dictionaries

```swift
var ages = ["Alice": 30, "Bob": 25]
ages["Charlie"] = 35
print(ages["Alice"]!) // Output: 30
```

### 8. Object-Oriented Programming

#### Classes and Structures

```swift
class Person {
    var name: String
    var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
    
    func introduce() -> String {
        return "Hi, I'm \(name) and I'm \(age) years old."
    }
}

let person = Person(name: "Alice", age: 30)
print(person.introduce())
```

### 9. Protocols and Extensions

#### Protocols

Protocols define a blueprint of methods, properties, and other requirements.

```swift
protocol Greetable {
    func greet() -> String
}

class Dog: Greetable {
    func greet() -> String {
        return "Woof!"
    }
}
```

#### Extensions

Extensions add functionality to existing classes, structures, or protocols.

```swift
extension Int {
    func squared() -> Int {
        return self * self
    }
}

let number = 4
print(number.squared()) // Output: 16
```

### 10. Error Handling

Swift uses `do-catch` blocks for error handling.

```swift
enum FileError: Error {
    case fileNotFound
}

func readFile(name: String) throws {
    throw FileError.fileNotFound
}

do {
    try readFile(name: "test.txt")
} catch {
    print("Error: \(error)")
}
```
