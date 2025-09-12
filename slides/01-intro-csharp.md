# Introduction to C#
---
## What is C#?
- Modern, object-oriented programming language
- Developed by Microsoft
- Used for desktop, web, cloud, and automation

> Note: Emphasize C#'s versatility and strong typing.
---
## Basic Syntax
- Statements end with `;`
- Case-sensitive
- Uses `{}` for code blocks

```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello, World!");
    }
}
```
---
## Basic JS Syntax
- Statements end with `;`
- Case-sensitive
- Uses `{}` for code blocks

```js
    let a = 1;
    let b = 2;
    let c = x => 1 + 2 + x;
    c(3);
```
--
### Exercise
- Write a program that prints your name.

> Note: Walk through the structure of a C# program.
---
## Variables & Data Types
- `int`, `double`, `string`, `bool`
- Declaration and initialization

```csharp
int age = 30;
double price = 19.99;
string name = "Alice";
bool isActive = true;
```
--
### Exercise
- Declare variables for a book: title, author, price, isAvailable.
---
## Control Structures
- `if`, `else`, `switch`
- Loops: `for`, `while`, `foreach`

```csharp
for (int i = 0; i < 5; i++) {
    Console.WriteLine(i);
}
```
--
### Exercise
- Write a loop to print numbers 1-10.
---
## OOP Concepts
- Classes & Objects
- Properties & Methods
- Inheritance

```csharp
class Animal {
    public string Name { get; set; }
    public void Speak() {
        Console.WriteLine($"{Name} makes a sound.");
    }
}

class Dog : Animal {
    public void Bark() {
        Console.WriteLine("Woof!");
    }
}
```
--
### Exercise
- Create a `Car` class with properties and a method to display info.

> Note: Reinforce encapsulation and inheritance.