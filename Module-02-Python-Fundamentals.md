# Module 2: Python Fundamentals (Part 1/4)

## Lesson 1: Python Basics

---

# 1. Introduction to Python

## What is Python?

Python is a **high-level, interpreted programming language** created by **Guido van Rossum** in 1991.

It is one of the most popular programming languages because of:

* Simple syntax
* Easy readability
* Large community support
* Extensive libraries
* Cross-platform compatibility
* Dynamic typing
* Automatic memory management

### Applications of Python

Python is widely used in:

* Data Analytics
* Data Science
* Machine Learning
* Artificial Intelligence
* Web Development
* Automation
* Scientific Computing

---

# 2. Python in Data Analytics

Python is the most commonly used language in Data Analytics because of its powerful ecosystem.

## Important Libraries

### NumPy

Used for:

* Numerical computations
* Arrays
* Mathematical operations

Example:

```python
import numpy as np

arr = np.array([1,2,3])
```

---

### Pandas

Used for:

* Data manipulation
* Data cleaning
* Data analysis

Example:

```python
import pandas as pd

df = pd.read_csv("data.csv")
```

---

### Matplotlib

Used for:

* Data visualization
* Charts
* Graphs

Example:

```python
import matplotlib.pyplot as plt
```

---

### Seaborn

Used for:

* Advanced statistical visualizations
* Beautiful charts

Example:

```python
import seaborn as sns
```

---

### Scikit-Learn

Used for:

* Machine Learning
* Classification
* Regression
* Clustering

Example:

```python
from sklearn.linear_model import LinearRegression
```

---

# 3. Python Interpreter

## What is a Python Interpreter?

The Python Interpreter is a program that:

* Reads Python code
* Converts it into machine-understandable instructions
* Executes the code

It acts as a bridge between:

```text
Python Code
      ↓
Python Interpreter
      ↓
Computer Hardware
```

---

## Running a Python File

Python files use the extension:

```text
.py
```

Example:

```text
hello.py
```

Run it using:

```bash
python hello.py
```

or

```bash
python3 hello.py
```

Example:

```bash
python3 hello.py
```

Output:

```text
Hello World
```

---

# 4. Python Interactive Shell

## What is Interactive Mode?

Python provides an interactive environment where commands can be executed immediately.

Start it using:

```bash
python
```

or

```bash
python3
```

Example:

```python
>>> 10 + 5
15

>>> print("Hello")
Hello
```

---

## Advantages

* Immediate feedback
* Quick testing
* Experimentation
* Learning Python concepts

---

## Python Prompt

When Python starts:

```python
>>>
```

This symbol indicates:

```text
Python is ready to accept commands
```

---

# 5. Exiting Python Interpreter

Use:

```python
exit()
```

or

```python
quit()
```

Example:

```python
>>> exit()
```

Returns back to terminal.

---

# 6. Python Help System

Python provides a built-in help system.

Syntax:

```python
help(object)
```

Example:

```python
help(print)
```

Output:

```text
Information about print()
```

Useful for:

* Functions
* Modules
* Classes
* Objects

---

# 7. Jupyter Notebook

## What is Jupyter Notebook?

Jupyter Notebook is a:

> Web-based interactive development environment.

It combines:

* Code
* Documentation
* Visualizations
* Results

inside one document.

---

## Why Jupyter is Important for Data Analytics

Data Analysts frequently:

* Explore datasets
* Visualize data
* Document findings

Jupyter allows all of these in one place.

---

## Features

### 1. Cell-Based Execution

Execute code block-by-block.

```python
a = 10
```

Run only this cell.

---

### 2. Markdown Support

Write documentation directly inside notebook.

Example:

```markdown
# Data Analysis Report
```

---

### 3. Visualization Support

Graphs appear directly below code.

Example:

```python
plt.plot(x,y)
```

---

### 4. Multiple Language Support

Through kernels, Jupyter supports:

* Python
* R
* Julia
* Scala
* Others

---

# 8. Accessing Jupyter Notebook in Coursera Labs

Steps:

### Step 1

Login to Coursera

### Step 2

Open the course module

### Step 3

Click:

```text
Launch Lab
```

### Step 4

Jupyter Notebook environment opens automatically.

---

# 9. Creating a New Notebook

Inside Jupyter:

```text
New → Python 3
```

A new notebook opens.

---

# 10. Jupyter Notebook Structure

Notebook consists of **Cells**.

Three main types:

## Code Cell

Contains Python code.

Example:

```python
print("Hello")
```

---

## Markdown Cell

Contains formatted text.

Example:

```markdown
## Introduction
```

---

## Raw Cell

Used for special formatting and conversions.

Less commonly used.

---

# 11. Running Cells

Method 1:

```text
Shift + Enter
```

Method 2:

Click:

```text
Run
```

Output appears immediately below the cell.

---

# 12. Markdown Formatting

Markdown cells allow:

## Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
```

---

## Bold Text

```markdown
**Bold**
```

---

## Italics

```markdown
*Italic*
```

---

## Lists

```markdown
- Item 1
- Item 2
```

---

# 13. Notebook Management

## Save Notebook

Shortcut:

```text
Ctrl + S
```

or

```text
File → Save and Checkpoint
```

---

## Rename Notebook

Click notebook name at top.

Example:

```text
Untitled.ipynb
```

Change to:

```text
Python_Basics.ipynb
```

---

# 14. Kernel Management

## What is Kernel?

Kernel is the computational engine executing code.

---

### Restart Kernel

```text
Kernel → Restart
```

---

### Restart and Clear Output

```text
Kernel → Restart and Clear Output
```

---

### Restart and Run All

```text
Kernel → Restart and Run All
```

Useful when:

* Notebook becomes inconsistent
* Variables need resetting

---

# 15. Comments in Python

Comments improve readability and documentation.

---

## Single-Line Comment

Syntax:

```python
# This is a comment
```

Example:

```python
# Calculate total marks
total = 500
```

---

## Multi-Line Comment

Use triple quotes:

```python
"""
This is a
multi-line comment
"""
```

or

```python
'''
This is a
multi-line comment
'''
```

---

# 16. Commenting Best Practices

### Good

Explain:

```text
Why code exists
```

Example:

```python
# Convert age to integer because input() returns string
age = int(age)
```

---

### Bad

Explain obvious things.

```python
# Assign 5 to x
x = 5
```

This comment adds no value.

---

# Key Takeaways

### Python

* High-level interpreted language
* Created by Guido van Rossum
* Widely used in Data Analytics

### Python Interpreter

* Executes Python code
* Supports interactive shell

### Jupyter Notebook

* Combines code, text, outputs, and visualizations
* Uses cells
* Supports Markdown

### Comments

* Single-line → `#`
* Multi-line → Triple quotes
* Improve readability and maintainability

---

# Module 2: Python Fundamentals (Part 2/4)

## Lesson 1 & Lesson 2: Input/Output, Indentation, Python Semantics

---

# 1. Input Function

## What is Input?

The `input()` function allows a Python program to receive data from the user during execution.

### Syntax

```python
input(prompt)
```

Example:

```python
name = input("Enter your name: ")
```

Output:

```text
Enter your name: Alice
```

The value entered is stored in the variable `name`.

---

## Important Rule

`input()` ALWAYS returns a string (`str`).

Example:

```python
age = input("Enter age: ")
print(type(age))
```

Output:

```python
<class 'str'>
```

Even if the user enters:

```text
25
```

Python stores it as:

```python
"25"
```

---

# 2. Type Conversion

Since input always returns a string, numerical calculations require conversion.

---

## Integer Conversion

```python
age = int(input("Enter age: "))
```

Example:

```python
age = int(input("Enter age: "))
print(age + 1)
```

Input:

```text
20
```

Output:

```text
21
```

---

## Float Conversion

```python
salary = float(input("Enter salary: "))
```

Example:

```python
salary = float(input("Enter salary: "))
print(salary * 1.1)
```

---

## Common Conversion Functions

| Function | Converts To |
| -------- | ----------- |
| int()    | Integer     |
| float()  | Float       |
| str()    | String      |
| bool()   | Boolean     |

---

# 3. Print Function

## Purpose

Used to display output on screen.

### Syntax

```python
print(value)
```

Example:

```python
print("Hello Learner")
```

Output:

```text
Hello Learner
```

---

## Printing Variables

```python
x = 5

print(x)
```

Output:

```text
5
```

---

## Printing Multiple Values

```python
name = "Alice"
age = 30

print(name, age)
```

Output:

```text
Alice 30
```

---

# 4. Formatted Strings (f-Strings)

Introduced in Python 3.6+

Most preferred method of formatting output.

### Syntax

```python
f"text {variable}"
```

Example:

```python
name = "Alice"
age = 30

print(f"{name} is {age} years old")
```

Output:

```text
Alice is 30 years old
```

---

## Why Use f-Strings?

Advantages:

* Cleaner syntax
* More readable
* Faster than older formatting methods

Example:

```python
price = 100

print(f"Total price: ₹{price}")
```

Output:

```text
Total price: ₹100
```

---

# 5. Multi-Line Output

Use triple quotes.

```python
print("""
Welcome
to
Python
""")
```

Output:

```text
Welcome
to
Python
```

---

# 6. Combining Input and Print

Example:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print(f"In 10 years, {name} will be {age+10} years old.")
```

Input:

```text
Alice
20
```

Output:

```text
In 10 years, Alice will be 30 years old.
```

---

# 7. Best Practices for Input & Output

### Good Prompts

Bad:

```python
input()
```

Good:

```python
input("Enter your age: ")
```

---

### Always Validate Inputs

```python
age = int(input("Enter age: "))
```

---

### Prefer f-Strings

Instead of:

```python
print("Age =", age)
```

Use:

```python
print(f"Age = {age}")
```

---

# 8. Indentation in Python

## What is Indentation?

Indentation means spaces or tabs at the beginning of a line.

Unlike many languages:

Python uses indentation to define code blocks.

---

## Why Is Indentation Important?

Indentation determines:

* Scope
* Structure
* Program flow

Python treats indentation as syntax.

Incorrect indentation causes errors.

---

# 9. Standard Indentation Rule

Use:

```text
4 spaces
```

per indentation level.

Example:

```python
if x > 5:
    print("Greater")
```

---

# 10. Indentation with If Statements

Example:

```python
x = 10

if x > 5:
    print("Greater than 5")

print("Done")
```

Output:

```text
Greater than 5
Done
```

Notice:

```python
print("Done")
```

is outside the if block.

---

# 11. Indentation in Functions

Example:

```python
def greet(name):
    print("Hello")
    print(name)

greet("Alice")
```

Output:

```text
Hello
Alice
```

Everything inside function must be indented.

---

# 12. Indentation in Loops

Example:

```python
for i in range(3):
    print(i)

print("Loop Finished")
```

Output:

```text
0
1
2
Loop Finished
```

---

# 13. Nested Indentation

Example:

```python
for i in range(3):
    if i == 1:
        print("Middle")
```

Structure:

```text
For Loop
    If Block
        Print
```

Each level increases indentation.

---

# 14. Common Indentation Errors

## Missing Indentation

Wrong:

```python
if x > 5:
print("Hello")
```

Output:

```python
IndentationError
```

---

## Mixing Tabs and Spaces

Wrong:

```python
if x > 5:
<TAB>print("A")
<SPACES>print("B")
```

Avoid mixing.

---

## Inconsistent Indentation

Wrong:

```python
if x > 5:
    print("A")
       print("B")
```

---

# 15. Indentation Best Practices

### Use Four Spaces

```python
if condition:
    statement
```

---

### Be Consistent

Never mix:

* Tabs
* Spaces

---

### Use IDE Support

Modern IDEs:

* VS Code
* PyCharm
* Jupyter

automatically handle indentation.

---

# 16. Python Scalar Types

## What are Scalar Types?

Scalar types store a single value.

Python's main scalar types:

1. int
2. float
3. bool
4. str

---

# 17. Integer (int)

Stores whole numbers.

Examples:

```python
10
-5
0
```

---

### Type Checking

```python
x = 10

print(type(x))
```

Output:

```python
<class 'int'>
```

---

## Integer Operations

```python
10 + 5
10 - 5
10 * 5
```

---

### Division

```python
10 / 3
```

Output:

```python
3.333333
```

Returns float.

---

### Integer Division

```python
10 // 3
```

Output:

```python
3
```

---

### Modulus

```python
10 % 3
```

Output:

```python
1
```

---

### Exponentiation

```python
2 ** 3
```

Output:

```text
8
```

---

# 18. Float

Stores decimal numbers.

Examples:

```python
3.14
0.001
-4.5
```

---

### Scientific Notation

```python
2.5e-4
```

Means:

```text
0.00025
```

---

### Type Checking

```python
y = 3.14

print(type(y))
```

Output:

```python
<class 'float'>
```

---

# 19. Floating Point Precision Problem

Example:

```python
0.1 + 0.2 == 0.3
```

Output:

```python
False
```

Reason:

Computers store floating-point numbers approximately.

---

### Solution

Use:

```python
round()
```

Example:

```python
round(0.1 + 0.2, 2) == 0.3
```

Output:

```python
True
```

---

# 20. Boolean (bool)

Represents truth values.

Only two values:

```python
True
False
```

---

### Type Checking

```python
flag = True

print(type(flag))
```

Output:

```python
<class 'bool'>
```

---

### Boolean Operators

#### AND

```python
True and False
```

Output:

```python
False
```

---

#### OR

```python
True or False
```

Output:

```python
True
```

---

#### NOT

```python
not True
```

Output:

```python
False
```

---

# 21. String (str)

Sequence of characters.

Examples:

```python
"Python"
'Alice'
"123"
```

---

### Type Checking

```python
name = "Alice"

print(type(name))
```

Output:

```python
<class 'str'>
```

---

# 22. Type Conversion

Convert between scalar types.

Examples:

```python
int("10")
float("3.14")
str(100)
bool(1)
```

Outputs:

```python
10
3.14
"100"
True
```

---

# 23. Type Checking Functions

## type()

Returns exact type.

```python
type(10)
```

Output:

```python
<class 'int'>
```

---

## isinstance()

Checks if object belongs to a type.

```python
isinstance(10, int)
```

Output:

```python
True
```

---

# 24. Common Scalar Type Pitfalls

### Integer Division Returns Float

```python
10 / 2
```

Output:

```python
5.0
```

---

### Floating Point Errors

```python
0.1 + 0.2
```

May not equal exactly:

```python
0.3
```

---

### Input Returns String

```python
age = input()
```

Must convert before calculations:

```python
age = int(input())
```

---

# Key Takeaways

### Input & Print

* `input()` receives user input
* `print()` displays output
* Input always returns string
* Use type conversion when needed
* Prefer f-strings

### Indentation

* Defines code structure
* Python requires proper indentation
* Standard = 4 spaces

### Scalar Types

* `int`
* `float`
* `bool`
* `str`

### Important Functions

```python
type()
isinstance()
int()
float()
str()
bool()
round()
```

---

# Module 2: Python Fundamentals (Part 3/4)

## Lesson 2: Python Semantics – Objects, Attributes, Methods & Operators

---

# 1. Objects in Python

## What is an Object?

An object is an **instance of a class**.

Objects contain:

* Data → Attributes
* Behavior → Methods

A fundamental rule in Python:

> Everything in Python is an Object.

---

## Examples of Objects

```python
x = 10
name = "Alice"
price = 99.99
```

All three are objects.

---

## Checking Object Type

```python
name = "Alice"

print(type(name))
```

Output:

```python
<class 'str'>
```

Here:

```text
Class  → str
Object → "Alice"
```

---

# 2. Class vs Object

## Class

A class is a blueprint.

Example:

```text
Book Blueprint
 ├─ Title
 ├─ Author
 └─ Pages
```

---

## Object

Actual instance created from the blueprint.

Example:

```python
book1 = Book()
book2 = Book()
```

Each book becomes a separate object.

---

# 3. Creating a Class

## Basic Syntax

```python
class Book:
    pass
```

---

## Class with Constructor

```python
class Book:

    def __init__(self, title, author):

        self.title = title
        self.author = author
```

---

# 4. Constructor (**init**)

## Purpose

Automatically runs when an object is created.

Syntax:

```python
def __init__(self, parameters):
```

---

Example:

```python
class Book:

    def __init__(self, title, author):

        self.title = title
        self.author = author
```

Object Creation:

```python
book1 = Book("Python Basics", "John")
```

---

# 5. Accessing Object Attributes

Use dot notation.

Syntax:

```python
object.attribute
```

Example:

```python
print(book1.title)
```

Output:

```python
Python Basics
```

---

# 6. Methods in Objects

Methods are functions inside a class.

Example:

```python
class Book:

    def __init__(self, title, author):

        self.title = title
        self.author = author

    def get_citation(self):

        return f"{self.author} - {self.title}"
```

Usage:

```python
book1.get_citation()
```

Output:

```python
John - Python Basics
```

---

# 7. Built-in Python Objects

Python already provides many classes.

Examples:

```python
list
dict
str
int
float
tuple
set
```

---

### List Object

```python
numbers = [1,2,3]
```

---

### Dictionary Object

```python
student = {
    "name":"Alice",
    "age":21
}
```

---

### String Object

```python
name = "Alice"
```

---

# 8. Functions Are Objects Too

Python treats functions as objects.

Example:

```python
def greet():
    print("Hello")
```

Check type:

```python
print(type(greet))
```

Output:

```python
<class 'function'>
```

---

# 9. Object Identity

Each object has a unique memory identity.

Use:

```python
id()
```

Example:

```python
x = [1,2,3]
y = [1,2,3]

print(id(x))
print(id(y))
```

Different IDs:

```text
14012546
14014782
```

---

## Identity Comparison

```python
x is y
```

Output:

```python
False
```

Because both occupy different memory locations.

---

# 10. Mutable vs Immutable Objects

## Mutable

Can be modified after creation.

Examples:

```python
list
dictionary
set
```

Example:

```python
numbers = [1,2,3]

numbers.append(4)
```

Result:

```python
[1,2,3,4]
```

---

## Immutable

Cannot be modified after creation.

Examples:

```python
str
tuple
int
float
bool
```

Example:

```python
name = "Alice"
```

Cannot directly modify individual characters.

---

# 11. Attributes in Python

## What are Attributes?

Variables belonging to an object or class.

Example:

```python
book.title
book.author
```

---

# 12. Types of Attributes

Python provides:

### 1. Instance Attributes

Unique for each object.

### 2. Class Attributes

Shared among all objects.

---

# 13. Instance Attributes

Defined inside:

```python
__init__()
```

Example:

```python
class Book:

    def __init__(self,title,author):

        self.title = title
        self.author = author
```

Each object has its own values.

```python
book1 = Book("Python","John")
book2 = Book("AI","Mike")
```

---

# 14. Class Attributes

Shared by every object.

Example:

```python
class Book:

    category = "Programming"
```

Usage:

```python
print(Book.category)
```

Output:

```python
Programming
```

---

## Shared Across Objects

```python
book1.category
book2.category
```

Both return:

```python
Programming
```

---

# 15. Modifying Attributes

Instance attributes can be modified.

Example:

```python
book1.title = "Advanced Python"
```

Updated value:

```python
Advanced Python
```

---

# 16. Built-in Attribute Functions

---

## getattr()

Gets attribute value.

Syntax:

```python
getattr(object, attribute)
```

Example:

```python
getattr(car, "make")
```

Output:

```python
Toyota
```

---

## hasattr()

Checks existence.

Example:

```python
hasattr(car, "model")
```

Output:

```python
True
```

or

```python
False
```

---

## setattr()

Creates or updates attributes.

Example:

```python
setattr(car, "model", "Corolla")
```

Equivalent:

```python
car.model = "Corolla"
```

---

## delattr()

Deletes attribute.

Example:

```python
delattr(car, "model")
```

---

# 17. Property Decorators

Provide controlled access.

Useful for:

* Validation
* Security
* Data consistency

---

## Getter Property

```python
@property
def price(self):
    return self._price
```

---

## Setter Property

```python
@price.setter
def price(self,value):

    if value < 0:
        raise ValueError

    self._price = value
```

---

## Usage

```python
book.price = 100
```

---

## Validation Example

```python
book.price = -10
```

Output:

```python
ValueError
```

---

# 18. Methods in Python

## What is a Method?

A method is a function inside a class.

Methods define object behavior.

Example:

```python
book.get_info()
```

---

# 19. Types of Methods

Python has three major method types:

1. Instance Methods
2. Class Methods
3. Static Methods

---

# 20. Instance Methods

Most common method type.

First parameter:

```python
self
```

Example:

```python
class Book:

    def get_info(self):

        return self.title
```

Call:

```python
book.get_info()
```

---

# 21. Class Methods

Operate on the class itself.

Decorator:

```python
@classmethod
```

First parameter:

```python
cls
```

---

Example:

```python
class Book:

    total_books = 0

    @classmethod
    def get_total_books(cls):

        return cls.total_books
```

Usage:

```python
Book.get_total_books()
```

---

# 22. Alternate Constructor Example

```python
@classmethod
def from_string(cls,text):

    title, author = text.split(",")

    return cls(title,author)
```

Usage:

```python
book = Book.from_string(
    "Python,John"
)
```

Creates object directly from text.

---

# 23. Static Methods

Decorator:

```python
@staticmethod
```

No:

```python
self
cls
```

---

Example:

```python
class Book:

    @staticmethod
    def is_long(pages):

        return pages > 300
```

Usage:

```python
Book.is_long(500)
```

Output:

```python
True
```

---

# 24. Method Overriding

Subclass replaces parent method.

---

## Parent Class

```python
class Book:

    def __str__(self):

        return self.title
```

---

## Child Class

```python
class Ebook(Book):

    def __str__(self):

        return "EBook: " + self.title
```

---

Usage:

```python
ebook = Ebook()

print(ebook)
```

Output:

```python
EBook: Python
```

---

# 25. super()

Access parent implementation.

Example:

```python
super().__str__()
```

Used when extending parent behavior.

---

# 26. Operators in Python

Operators perform operations on operands.

Example:

```python
5 + 2
```

Operator:

```python
+
```

Operands:

```python
5 and 2
```

---

# 27. Arithmetic Operators

| Operator | Meaning          |
| -------- | ---------------- |
| +        | Addition         |
| -        | Subtraction      |
| *        | Multiplication   |
| /        | Division         |
| //       | Integer Division |
| %        | Modulus          |
| **       | Power            |

---

Example:

```python
10 + 5
10 - 5
10 * 5
10 / 5
10 // 3
10 % 3
2 ** 3
```

---

# 28. Comparison Operators

| Operator | Meaning       |
| -------- | ------------- |
| ==       | Equal         |
| !=       | Not Equal     |
| >        | Greater       |
| <        | Less          |
| >=       | Greater Equal |
| <=       | Less Equal    |

Example:

```python
10 > 5
```

Output:

```python
True
```

---

# 29. Logical Operators

## AND

```python
True and False
```

Output:

```python
False
```

---

## OR

```python
True or False
```

Output:

```python
True
```

---

## NOT

```python
not True
```

Output:

```python
False
```

---

# 30. Assignment Operators

Basic:

```python
x = 5
```

---

Compound:

```python
x += 5
x -= 5
x *= 5
x /= 5
```

---

# 31. Membership Operators

Check existence.

```python
in
not in
```

Example:

```python
"Python" in books
```

---

# 32. Identity Operators

Compare memory identity.

```python
is
is not
```

Example:

```python
x is y
```

---

## Difference Between == and is

### Equality

```python
x == y
```

Checks values.

---

### Identity

```python
x is y
```

Checks memory location.

---

Example:

```python
x = [1,2]
y = [1,2]
```

```python
x == y
```

Output:

```python
True
```

---

```python
x is y
```

Output:

```python
False
```

---

# 33. Operator Overloading

## What is Operator Overloading?

Changing operator behavior for custom classes.

---

Example:

```python
book1 + book2
```

can mean:

```text
Add prices of two books
```

---

## **add**()

Overloads +

```python
def __add__(self,other):

    return self.price + other.price
```

---

## **lt**()

Overloads <

```python
def __lt__(self,other):

    return self.pages < other.pages
```

---

## **eq**()

Overloads ==

```python
def __eq__(self,other):

    return (
        self.title == other.title
    )
```

---

# 34. Magic Methods

Special methods surrounded by double underscores.

Examples:

```python
__init__()
__str__()
__add__()
__eq__()
__lt__()
```

These power:

* Constructors
* Printing
* Comparisons
* Arithmetic
* Object behavior

---

# Best Practices

### Classes

* Use meaningful class names
* One responsibility per class

---

### Attributes

* Initialize inside `__init__`
* Use clear names

---

### Methods

* Keep methods focused
* Use docstrings
* Choose correct method type

---

### Operators

* Overload only when behavior is intuitive
* Avoid confusing implementations

---

# Key Takeaways

### Objects

* Everything in Python is an object
* Objects are instances of classes

### Attributes

* Store object data
* Instance vs Class attributes

### Methods

* Instance Methods → `self`
* Class Methods → `cls`
* Static Methods → Utility methods

### Operators

* Arithmetic
* Comparison
* Logical
* Assignment
* Membership
* Identity

### Advanced Concepts

* Property Decorators
* Operator Overloading
* Magic Methods
* Object Identity
* Mutable vs Immutable Objects

---

# Module 2: Python Fundamentals (Part 4/4)

## Lesson 3, 4 & 5: Control Flow, Functions, Lambda Functions & File Handling

---

# 1. Conditional Statements

## What are Conditional Statements?

Conditional statements allow a program to make decisions based on conditions.

Think of them as:

```text
IF something is true
    Do Task A
ELSE
    Do Task B
```

They control the flow of execution.

---

# 2. if Statement

## Syntax

```python
if condition:
    statement
```

Example:

```python
pages = 250

if pages > 100:
    print("Substantial Book")
```

Output:

```text
Substantial Book
```

---

# 3. if-else Statement

## Syntax

```python
if condition:
    statement1
else:
    statement2
```

Example:

```python
pages = 50

if pages > 100:
    print("Long Book")
else:
    print("Short Book")
```

Output:

```text
Short Book
```

---

# 4. elif Statement

Used when multiple conditions must be checked.

## Syntax

```python
if condition1:
    ...
elif condition2:
    ...
else:
    ...
```

Example:

```python
pages = 250

if pages < 100:
    print("Short")
elif pages < 300:
    print("Medium")
else:
    print("Long")
```

Output:

```text
Medium
```

---

# 5. Logical Operators in Conditions

## AND

Both conditions must be True.

```python
if pages > 200 and price < 30:
    print("Good Value")
```

---

## OR

At least one condition must be True.

```python
if pages > 300 or rating > 4:
    print("Recommended")
```

---

## NOT

Reverses a condition.

```python
if not available:
    print("Out of Stock")
```

---

# 6. Ternary Operator

Short form of if-else.

## Syntax

```python
value_if_true if condition else value_if_false
```

Example:

```python
book_type = "Ebook" if format == "digital" else "Physical"
```

---

# 7. Common Mistakes in Conditions

### Wrong

```python
if x = 10:
```

Assignment operator used.

---

### Correct

```python
if x == 10:
```

Comparison operator used.

---

# 8. Nested Conditional Statements

## What are Nested Conditionals?

An if statement inside another if statement.

Example:

```python
if category == "Programming":

    if pages > 500:
        print("Comprehensive Guide")
```

---

## Multi-Level Nesting

```python
if category == "Programming":

    if pages > 500:

        if price < 50:
            print("Best Buy")
```

---

# 9. Problems with Deep Nesting

Too much nesting causes:

* Reduced readability
* Difficult debugging
* Maintenance issues

Example:

```text
if
 └── if
      └── if
           └── if
```

Often called:

```text
Arrow Code
```

---

# 10. Alternative: Early Return

Instead of:

```python
if condition:

    if another_condition:
        return value
```

Use:

```python
if not condition:
    return

if not another_condition:
    return

return value
```

Cleaner and easier to read.

---

# 11. Best Practices for Conditionals

### Keep Conditions Simple

Good:

```python
if pages > 100:
```

Bad:

```python
if pages > 100 and price < 20 and author == "A" and ...
```

---

### Avoid Deep Nesting

Prefer:

* Logical operators
* Functions
* Early returns

---

# 12. Loops in Python

## What are Loops?

Loops repeat execution of code.

Used for:

* Processing data
* Iterating collections
* Automation

Python provides:

1. For Loop
2. While Loop

---

# 13. For Loop

Used when iterating over a sequence.

## Syntax

```python
for item in sequence:
    statement
```

Example:

```python
books = ["Python", "ML", "AI"]

for book in books:
    print(book)
```

Output:

```text
Python
ML
AI
```

---

# 14. range() Function

Generates a sequence of numbers.

Example:

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

---

## Important Rule

Last number is excluded.

```python
range(5)
```

Means:

```text
0 → 4
```

---

## Start and End Values

```python
for i in range(1,6):
    print(i)
```

Output:

```text
1
2
3
4
5
```

---

# 15. enumerate()

Adds index while looping.

Example:

```python
books = ["Python", "AI", "ML"]

for index, book in enumerate(books, start=1):
    print(index, book)
```

Output:

```text
1 Python
2 AI
3 ML
```

---

# 16. While Loop

Repeats while condition remains True.

## Syntax

```python
while condition:
    statement
```

---

Example:

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

Output:

```text
1
2
3
4
5
```

---

# 17. Infinite Loops

Example:

```python
while True:
    print("Running")
```

Runs forever.

Must be used carefully.

---

# 18. break Statement

Terminates loop immediately.

Example:

```python
while True:

    value = input()

    if value == "quit":
        break
```

---

# 19. continue Statement

Skips current iteration.

Example:

```python
for page in pages:

    if page < 200:
        continue

    print(page)
```

Only pages ≥ 200 are printed.

---

# 20. Nested Loops

Loop inside another loop.

Example:

```python
for category in categories:

    for length in lengths:

        print(category, length)
```

---

# 21. Choosing Between Loops

## Use For Loop

When iterations are known.

```python
for i in range(10):
```

---

## Use While Loop

When iterations are unknown.

```python
while user_input != "quit":
```

---

# 22. Functions in Python

## What is a Function?

Reusable block of code performing one task.

Benefits:

* Reusability
* Organization
* Readability
* Maintainability

---

# 23. Defining Functions

## Syntax

```python
def function_name():
    statements
```

---

Example:

```python
def greet():

    print("Hello")
```

---

# 24. Calling Functions

```python
greet()
```

Output:

```text
Hello
```

---

# 25. Function Parameters

Parameters are inputs to a function.

Example:

```python
def greet(name):

    return f"Hello {name}"
```

Call:

```python
greet("Alice")
```

Output:

```text
Hello Alice
```

---

# 26. Arguments vs Parameters

### Parameter

Defined in function.

```python
def greet(name):
```

`name` is parameter.

---

### Argument

Passed during function call.

```python
greet("Alice")
```

`Alice` is argument.

---

# 27. Return Statement

Returns result from a function.

Example:

```python
def square(x):

    return x * x
```

Usage:

```python
result = square(5)
```

Output:

```text
25
```

---

# 28. Default Parameters

Example:

```python
def create_book(title, pages=200):

    return title, pages
```

Call:

```python
create_book("Python")
```

Output:

```python
("Python", 200)
```

---

# 29. Keyword Arguments

Example:

```python
describe_book(
    year=2024,
    author="John",
    title="Python"
)
```

Order doesn't matter.

---

# 30. Multiple Return Values

Example:

```python
def get_book_info():

    return title, author, pages
```

Receive:

```python
title, author, pages = get_book_info()
```

Python returns a tuple.

---

# 31. Variable Scope

## Local Variables

Exist only inside function.

```python
def test():

    x = 10
```

Outside function:

```python
print(x)
```

Error.

---

## Global Variables

Defined outside functions.

```python
total_books = 0
```

Accessible throughout program.

---

# 32. Global Keyword

Allows modification of global variables.

Example:

```python
total_books = 0

def add_book():

    global total_books

    total_books += 1
```

---

# 33. Function Best Practices

### Good Function

```python
def calculate_discount(price, discount):
```

Clear and descriptive.

---

### Bad Function

```python
def cd(p,d):
```

Hard to understand.

---

### Rules

* One task per function
* Use meaningful names
* Add documentation
* Avoid unnecessary globals

---

# 34. Lambda Functions

## What is a Lambda Function?

Small anonymous function.

Also called:

```text
Anonymous Function
```

---

# 35. Lambda Syntax

```python
lambda arguments : expression
```

---

Regular Function:

```python
def square(x):

    return x*x
```

Lambda Equivalent:

```python
square = lambda x: x*x
```

---

# 36. Multiple Arguments

Example:

```python
add = lambda a,b: a+b
```

Usage:

```python
add(5,3)
```

Output:

```text
8
```

---

# 37. Lambda with sorted()

Example:

```python
sorted(
    books,
    key=lambda book: book.pages
)
```

Sorts by page count.

---

# 38. Lambda with map()

Transforms data.

Example:

```python
titles = list(
    map(
        lambda book: book.title,
        books
    )
)
```

---

# 39. Lambda with filter()

Filters data.

Example:

```python
long_books = list(
    filter(
        lambda book: book.pages > 300,
        books
    )
)
```

---

# 40. Lambda vs Regular Functions

| Lambda         | Regular             |
| -------------- | ------------------- |
| Anonymous      | Named               |
| One Expression | Multiple Statements |
| Short          | Detailed            |
| Quick Use      | Complex Logic       |

---

# 41. When to Use Lambda

Good for:

* map()
* filter()
* sorted()
* One-line operations

Avoid for:

* Complex business logic
* Large functions

---

# 42. File Handling

## Why File Handling?

Allows programs to:

* Store data
* Read data
* Save reports
* Process datasets

Critical for Data Analytics.

---

# 43. Opening Files

Traditional Method:

```python
file = open("books.txt","r")
```

Close:

```python
file.close()
```

---

# 44. Preferred Method: with

```python
with open("books.txt","r") as file:

    data = file.read()
```

Advantages:

* Automatic closing
* Safer
* Cleaner

---

# 45. File Modes

| Mode | Purpose      |
| ---- | ------------ |
| r    | Read         |
| w    | Write        |
| a    | Append       |
| r+   | Read + Write |
| rb   | Read Binary  |
| wb   | Write Binary |

---

# 46. Reading Entire File

```python
with open("books.txt","r") as file:

    content = file.read()
```

Loads entire file into memory.

Suitable for:

* Small files

---

# 47. Reading Line by Line

```python
with open("books.txt","r") as file:

    for line in file:

        print(line.strip())
```

Better for large files.

---

# 48. Working with CSV Files

CSV = Comma Separated Values

Example:

```python
import csv

with open("books.csv","r") as file:

    reader = csv.reader(file)

    for row in reader:
        print(row)
```

---

# 49. Working with JSON Files

JSON = JavaScript Object Notation

Example:

```python
import json

with open("books.json","r") as file:

    data = json.load(file)
```

---

# 50. Writing Files

## Write Mode

Creates or overwrites.

```python
with open("books.txt","w") as file:

    file.write("Python Basics")
```

---

# 51. Writing Multiple Lines

```python
books = [
    "Python",
    "AI",
    "ML"
]

with open("books.txt","w") as file:

    file.writelines(
        book + "\n"
        for book in books
    )
```

---

# 52. Append Mode

Adds content without deleting old content.

```python
with open("books.txt","a") as file:

    file.write("Data Science\n")
```

---

# 53. Writing CSV Files

```python
import csv

with open("books.csv","w") as file:

    writer = csv.writer(file)

    writer.writerow(
        ["Title","Pages"]
    )
```

---

# 54. Writing JSON Files

```python
import json

data = {
    "title":"Python"
}

with open("book.json","w") as file:

    json.dump(
        data,
        file,
        indent=4
    )
```

---

# 55. flush()

Forces data to disk immediately.

```python
file.flush()
```

Usually unnecessary when using:

```python
with open(...)
```

---

# 56. File Handling Best Practices

### Always Use

```python
with open(...)
```

---

### Choose Correct Mode

Read:

```python
"r"
```

Write:

```python
"w"
```

Append:

```python
"a"
```

---

### Be Careful with Write Mode

```python
"w"
```

overwrites existing files.

---

# Module 2 Final Revision Sheet

## Python Basics

* Interpreter
* Jupyter Notebook
* Input/Output
* Comments
* Indentation

---

## Data Types

* int
* float
* bool
* str

---

## OOP Concepts

* Objects
* Classes
* Attributes
* Methods
* Constructors
* Property Decorators

---

## Operators

* Arithmetic
* Comparison
* Logical
* Assignment
* Membership
* Identity
* Operator Overloading

---

## Control Flow

* if
* elif
* else
* Nested Conditions
* Ternary Operator

---

## Loops

* for
* while
* break
* continue
* enumerate
* range

---

## Functions

* Parameters
* Arguments
* Return Values
* Default Parameters
* Keyword Arguments
* Scope

---

## Lambda Functions

* Anonymous Functions
* map()
* filter()
* sorted()

---

## File Handling

* Read Files
* Write Files
* CSV Files
* JSON Files
* with Statement

---

# Module 2 Exam-Focused Topics (Most Important)

⭐ Input vs Print
⭐ Type Conversion (`int`, `float`, `str`, `bool`)
⭐ Indentation Rules
⭐ Scalar Types
⭐ Classes and Objects
⭐ Instance vs Class Attributes
⭐ Instance/Class/Static Methods
⭐ Operators and Operator Overloading
⭐ if-elif-else Statements
⭐ Nested Conditionals
⭐ For Loop vs While Loop
⭐ break and continue
⭐ Function Definition and Return Values
⭐ Lambda Functions
⭐ Reading Files
⭐ Writing Files
⭐ CSV and JSON Handling

---