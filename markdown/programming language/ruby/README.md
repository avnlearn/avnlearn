Sure! Here’s an in-depth tutorial on Ruby, covering its basics, object-oriented programming, and some advanced features.

### Introduction to Ruby

Ruby is a dynamic, open-source programming language with a focus on simplicity and productivity. It has an elegant syntax that is easy to read and write.

### Getting Started

1. **Installation**:

   - You can install Ruby using a version manager like `rbenv` or `RVM`, or you can download it from the [official Ruby website](https://www.ruby-lang.org/en/downloads/).

2. **Running Ruby**:
   - You can run Ruby scripts from the command line:
     ```bash
     ruby your_script.rb
     ```
   - You can also use the interactive Ruby shell (IRB):
     ```bash
     irb
     ```

### Basic Syntax

1. **Hello World**:

   ```ruby
   puts 'Hello, World!'
   ```

2. **Variables**:

   ```ruby
   name = "Alice"
   age = 30
   ```

3. **Data Types**:

   - **Numbers**: Integers and Floats
   - **Strings**: `"Hello"` or `'Hello'`
   - **Arrays**: `[1, 2, 3]`
   - **Hashes**: `{ key: 'value', key2: 'value2' }`

4. **Control Structures**:

   - **Conditional Statements**:

     ```ruby
     if age > 18
       puts "Adult"
     else
       puts "Minor"
     end
     ```

   - **Loops**:
     ```ruby
     5.times do
       puts "Hello"
     end
     ```

### Methods

Defining and calling methods in Ruby is straightforward:

```ruby
def greet(name)
  "Hello, #{name}!"
end

puts greet("Alice")
```

### Object-Oriented Programming

Ruby is a pure object-oriented language. Everything in Ruby is an object.

1. **Classes and Objects**:

   ```ruby
   class Dog
     def initialize(name)
       @name = name
     end

     def bark
       "Woof! My name is #{@name}."
     end
   end

   my_dog = Dog.new("Buddy")
   puts my_dog.bark
   ```

2. **Inheritance**:

   ```ruby
   class Animal
     def speak
       "I am an animal."
     end
   end

   class Cat < Animal
     def speak
       "Meow!"
     end
   end

   my_cat = Cat.new
   puts my_cat.speak
   ```

3. **Modules**:
   Modules are used for namespacing and mixins.

   ```ruby
   module Swimmable
     def swim
       "I can swim!"
     end
   end

   class Fish
     include Swimmable
   end

   goldfish = Fish.new
   puts goldfish.swim
   ```

### Advanced Features

1. **Blocks, Procs, and Lambdas**:

   - **Blocks**:

     ```ruby
     3.times { puts "Hello!" }
     ```

   - **Procs**:

     ```ruby
     my_proc = Proc.new { |x| x * 2 }
     puts my_proc.call(5)
     ```

   - **Lambdas**:
     ```ruby
     my_lambda = ->(x) { x * 2 }
     puts my_lambda.call(5)
     ```

2. **Error Handling**:

   ```ruby
   begin
     # Code that may raise an error
   rescue StandardError => e
     puts "Error: #{e.message}"
   end
   ```

3. **File I/O**:

   ```ruby
   File.open("example.txt", "w") do |file|
     file.puts "Hello, World!"
   end

   File.open("example.txt", "r") do |file|
     puts file.read
   end
   ```
