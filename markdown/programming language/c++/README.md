# 1. Introduction to C++

## What is C++?
C++ is a general-purpose programming language created by Bjarne Stroustrup at Bell Labs in the early 1980s. It is an extension of the C programming language and includes object-oriented features.

## History of C++
C++ was developed as an enhancement to the C language, adding features like classes, derived classes, and basic inheritance. Over the years, it has evolved with several standards, including C++98, C++03, C++11, C++14, C++17, and C++20.

## Features of C++
- Object-oriented
- Generic programming
- Low-level memory manipulation
- Rich library support
- High performance

# 2. Setting Up the Environment

#### Installing a C++ Compiler
You can use various compilers like GCC (GNU Compiler Collection), Clang, or MSVC (Microsoft Visual C++). For Windows, you can install MinGW or use Visual Studio.

## Choosing an IDE
Popular IDEs for C++ include:
- Visual Studio
- Code::Blocks
- CLion
- Eclipse CDT
- Dev-C++

# 3. Basic Syntax

## Hello World Program
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```

## Comments
```cpp
// This is a single-line comment
/*
This is a multi-line comment
*/
```

## Data Types
- `int`: Integer
- `float`: Floating-point number
- `double`: Double precision floating-point number
- `char`: Character
- `bool`: Boolean

## Variables and Constants
```cpp
int age = 25; // Variable
const float PI = 3.14; // Constant
```

# 4. Control Structures

## Conditional Statements
```cpp
if (age > 18) {
    cout << "Adult";
} else {
    cout << "Minor";
}
```

## Loops
```cpp
for (int i = 0; i < 5; i++) {
    cout << i << endl;
}

int j = 0;
while (j < 5) {
    cout << j << endl;
    j++;
}
```

# 5. Functions

## Function Declaration and Definition
```cpp
int add(int a, int b) {
    return a + b;
}
```

## Function Overloading
```cpp
int add(int a, int b);
double add(double a, double b);
```

## Inline Functions
```cpp
inline int square(int x) {
    return x * x;
}
```

## Recursion
```cpp
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

# 6. Object-Oriented Programming (OOP)

## Classes and Objects
```cpp
class Dog {
public:
    void bark() {
        cout << "Woof!" << endl;
    }
};

Dog myDog;
myDog.bark();
```

## Constructors and Destructors
```cpp
class Car {
public:
    Car() { cout << "Car created!" << endl; }
    ~Car() { cout << "Car destroyed!" << endl; }
};
```

## Inheritance
```cpp
class Animal {
public:
    void eat() { cout << "Eating..." << endl; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Woof!" << endl; }
};
```

## Polymorphism
```cpp
class Base {
public:
    virtual void show() { cout << "Base class" << endl; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived class" << endl; }
};
```

## Encapsulation and Abstraction
```cpp
class Account {
private:
    double balance;
public:
    void deposit(double amount) { balance += amount; }
    double getBalance() { return balance; }
};
```

# 7. Advanced Features

## Templates
```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

## Exception Handling
```cpp
try {
    throw runtime_error("Error occurred");
} catch (const exception& e) {
    cout << e.what() << endl;
}
```

## Standard Template Library (STL)
- Containers: `vector`, `list`, `map`, etc.
- Algorithms: `sort`, `find`, etc.

## Smart Pointers
```cpp
#include <memory>
std::unique_ptr<int> ptr(new int(5));
```

# 8. File Handling

## Reading from and Writing to Files
```cpp
#include <fstream>
std::ofstream outFile("example.txt");
outFile << "Hello, File!" << endl;
outFile.close();

std::ifstream inFile("example.txt");
std::string line;
while (getline(inFile, line)) {
    cout << line << endl;
}
inFile.close();
```

# 9. C++11 and Beyond

## New Features in C++11
- `auto` keyword
- Range-based for loops
- `nullptr`

## Lambda Expressions
```cpp
auto add = [](int a, int b) { return a + b; };
```

## Multithreading
```cpp
#include <thread>
void function() { /* code */ }
std::thread t(function);
t.join();
```
