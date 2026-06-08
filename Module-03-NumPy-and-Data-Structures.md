# Module 03: Fundamental Data Structures and NumPy

## Learning Objectives

After completing this module, you will be able to:

* Understand immutable and mutable data structures in Python.
* Create and manipulate tuples, strings, lists, dictionaries, and sets.
* Apply indexing and slicing techniques effectively.
* Use built-in methods for common data manipulation tasks.
* Understand the fundamentals of NumPy arrays and their advantages.
* Perform numerical computations efficiently using NumPy.
* Work with array indexing, slicing, broadcasting, and mathematical functions.
* Select appropriate data structures based on application requirements.

---

# Immutable Data Structures

Immutable objects cannot be modified after creation. Instead of changing an existing object, any modification creates a new object.

Python's most commonly used immutable data structures include:

* Tuples
* Strings
* Frozen Sets

Immutability improves:

* Data integrity
* Program safety
* Memory optimization
* Performance in specific scenarios

---

# Tuples

## What is a Tuple?

A tuple is an ordered and immutable sequence of elements.

Unlike lists, tuples cannot be modified after creation.

### Characteristics

* Ordered
* Immutable
* Allows duplicate values
* Can contain mixed data types
* Supports indexing and slicing
* Can be nested

---

## Creating Tuples

### Empty Tuple

```python
empty_tuple = ()
```

### Tuple with Elements

```python
book = ("Python", "Guido", 1991, 850)
```

### Single Element Tuple

```python
single = (10,)
```

The comma is mandatory.

Without the comma:

```python
single = (10)
```

Python treats it as an integer.

---

## Accessing Tuple Elements

Tuples use zero-based indexing.

```python
book = ("Python", "Guido", 1991, 850)

print(book[0])
print(book[1])
```

Output:

```python
Python
Guido
```

---

## Negative Indexing

Negative indices access elements from the end.

```python
book[-1]
```

Output:

```python
850
```

```python
book[-2]
```

Output:

```python
1991
```

---

## Tuple Unpacking

Tuple unpacking assigns tuple elements to variables.

```python
book = ("Python", "Guido", 1991, 850)

title, author, year, pages = book
```

Now:

```python
title  -> Python
author -> Guido
year   -> 1991
pages  -> 850
```

### Benefits

* Cleaner code
* Easy variable assignment
* Useful for function returns

---

## Nested Tuples

Tuples can contain other tuples.

```python
nested = (
    1,
    2,
    ("A", "B"),
    [3, 4]
)
```

Accessing nested elements:

```python
nested[2][0]
```

Output:

```python
A
```

---

## Tuple Immutability

Once created, tuples cannot be modified.

```python
numbers = (1, 2, 3)

numbers[0] = 10
```

Output:

```python
TypeError
```

Because tuples are immutable.

---

## Tuple Concatenation

Tuples can be combined.

```python
t1 = (1, 2)
t2 = (3, 4)

result = t1 + t2
```

Output:

```python
(1, 2, 3, 4)
```

A new tuple is created.

---

## Tuple Repetition

```python
t = ("Python",)

print(t * 3)
```

Output:

```python
('Python', 'Python', 'Python')
```

---

## Tuple vs List

| Feature              | Tuple   | List            |
| -------------------- | ------- | --------------- |
| Mutable              | No      | Yes             |
| Syntax               | ()      | []              |
| Performance          | Faster  | Slightly slower |
| Memory Usage         | Lower   | Higher          |
| Dictionary Key Usage | Allowed | Not Allowed     |

---

## Common Use Cases

### Coordinates

```python
point = (10, 20)
```

### RGB Values

```python
color = (255, 255, 255)
```

### Returning Multiple Values

```python
def get_user():
    return ("John", 25)
```

### Dictionary Keys

```python
locations = {
    (10, 20): "Home"
}
```

---

# Tuple Methods

Because tuples are immutable, they provide fewer methods than lists.

---

## count()

Returns the number of occurrences.

```python
numbers = (1, 2, 2, 3, 2)

numbers.count(2)
```

Output:

```python
3
```

---

## index()

Returns the first occurrence position.

```python
colors = ("red", "green", "blue")

colors.index("green")
```

Output:

```python
1
```

---

## index() with Range

```python
values = (10, 20, 30, 40, 30, 50)

values.index(30, 3, 6)
```

Output:

```python
4
```

---

## len()

Returns number of elements.

```python
book = ("Python", "Guido", 1991, 850)

len(book)
```

Output:

```python
4
```

---

## max()

Returns largest value.

```python
numbers = (1, 5, 9, 2)

max(numbers)
```

Output:

```python
9
```

---

## min()

Returns smallest value.

```python
min(numbers)
```

Output:

```python
1
```

---

## sorted()

Returns a sorted list.

```python
scores = (90, 70, 85)

sorted(scores)
```

Output:

```python
[70, 85, 90]
```

Descending order:

```python
sorted(scores, reverse=True)
```

Output:

```python
[90, 85, 70]
```

### Important

`sorted()` returns a list, not a tuple.

---

# Strings

## What is a String?

A string is an immutable sequence of characters.

Strings are used to store textual information.

Examples:

```python
"Python"
'Python'
```

Both are valid.

---

## Characteristics

* Ordered
* Immutable
* Supports indexing
* Supports slicing
* Supports concatenation
* Supports repetition

---

## Creating Strings

### Single Quotes

```python
name = 'Python'
```

### Double Quotes

```python
name = "Python"
```

### Triple Quotes

```python
paragraph = """
Python is powerful.
Python is easy.
"""
```

Useful for multiline text.

---

## String Concatenation

```python
first = "John"
last = "Doe"

full = first + " " + last
```

Output:

```python
John Doe
```

---

## String Repetition

```python
word = "Python"

print(word * 3)
```

Output:

```python
PythonPythonPython
```

---

## String Length

```python
text = "Python"

len(text)
```

Output:

```python
6
```

---

## String Indexing

```python
text = "Python"

text[0]
```

Output:

```python
P
```

```python
text[2]
```

Output:

```python
t
```

---

## Negative Indexing

```python
text[-1]
```

Output:

```python
n
```

```python
text[-2]
```

Output:

```python
o
```

---

## String Slicing

Syntax:

```python
string[start:end:step]
```

Examples:

```python
text = "Python Programming"

text[0:6]
```

Output:

```python
Python
```

---

```python
text[7:]
```

Output:

```python
Programming
```

---

```python
text[::-1]
```

Output:

```python
gnimmargorP nohtyP
```

---

## Case Conversion Methods

### upper()

```python
"python".upper()
```

Output:

```python
PYTHON
```

### lower()

```python
"PYTHON".lower()
```

Output:

```python
python
```

### capitalize()

```python
"python".capitalize()
```

Output:

```python
Python
```

---

## Searching Strings

### find()

```python
text = "Python is awesome"

text.find("awesome")
```

Returns index position.

### count()

```python
text.count("o")
```

Counts occurrences.

### in Operator

```python
"Python" in text
```

Returns:

```python
True
```

---

## replace()

```python
text = "Python is cool"

text.replace("cool", "awesome")
```

Output:

```python
Python is awesome
```

---

## String Immutability

Invalid:

```python
text = "Python"

text[0] = "J"
```

Output:

```python
TypeError
```

Correct approach:

```python
text = "J" + text[1:]
```

Output:

```python
Jython
```

---

## Why Strings Are Immutable

Benefits:

* Better performance
* Safer programs
* Hashable
* Can be dictionary keys
* Memory optimization

---

## Key Takeaways

* Tuples are immutable ordered collections.
* Strings are immutable sequences of characters.
* Tuple methods are limited because tuples cannot be modified.
* Strings support powerful text manipulation features.
* Both tuples and strings support indexing and slicing.
* Immutable structures improve safety and reliability in programs.


# Mutable Data Structures

Unlike immutable structures, mutable data structures can be modified after creation. Elements can be added, removed, updated, or rearranged without creating a completely new object.

Python's major mutable data structures include:

* Lists
* Dictionaries
* Sets

Mutable structures are extremely useful when working with changing datasets, user input, file processing, data analysis, and machine learning workflows.

---

# Lists

## What is a List?

A list is an ordered and mutable collection of elements.

Lists are among the most frequently used data structures in Python because of their flexibility and ease of use.

### Characteristics

* Ordered
* Mutable
* Allows duplicate values
* Supports mixed data types
* Supports indexing and slicing
* Supports nesting

---

## Creating Lists

### Empty List

```python
empty_list = []
```

---

### List with Elements

```python
numbers = [1, 2, 3, 4, 5]
```

---

### Mixed Data Type List

```python
mixed = [1, "Python", 3.14, True]
```

---

### Using list() Constructor

```python
letters = list("Python")
```

Output:

```python
['P', 'y', 't', 'h', 'o', 'n']
```

---

## Accessing List Elements

Lists use zero-based indexing.

```python
fruits = ["apple", "banana", "orange"]

print(fruits[0])
```

Output:

```python
apple
```

---

```python
print(fruits[1])
```

Output:

```python
banana
```

---

## Negative Indexing

```python
fruits[-1]
```

Output:

```python
orange
```

---

```python
fruits[-2]
```

Output:

```python
banana
```

---

## Modifying Elements

Lists are mutable.

```python
numbers = [1, 2, 3, 4, 5]

numbers[2] = 30
```

Output:

```python
[1, 2, 30, 4, 5]
```

---

## List Concatenation

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

combined = list1 + list2
```

Output:

```python
[1, 2, 3, 4, 5, 6]
```

---

## Nested Lists

Lists can contain other lists.

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Visual representation:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

---

## Accessing Nested Elements

```python
matrix[1][2]
```

Output:

```python
6
```

Explanation:

```text
matrix[1]     -> [4, 5, 6]
matrix[1][2]  -> 6
```

---

## Common Built-in Functions

### len()

```python
numbers = [1, 2, 3, 4, 5]

len(numbers)
```

Output:

```python
5
```

---

### max()

```python
max(numbers)
```

Output:

```python
5
```

---

### min()

```python
min(numbers)
```

Output:

```python
1
```

---

### sum()

```python
sum(numbers)
```

Output:

```python
15
```

---

## List vs Tuple

| Feature      | List            | Tuple       |
| ------------ | --------------- | ----------- |
| Mutable      | Yes             | No          |
| Syntax       | []              | ()          |
| Performance  | Slightly Slower | Faster      |
| Memory Usage | Higher          | Lower       |
| Modification | Allowed         | Not Allowed |

---

# List Slicing

## What is Slicing?

Slicing allows extraction of a subset of list elements.

General syntax:

```python
list[start:end:step]
```

Where:

* start = inclusive
* end = exclusive
* step = increment

---

## Basic Slicing

```python
numbers = [0,1,2,3,4,5,6,7,8,9]

numbers[2:7]
```

Output:

```python
[2,3,4,5,6]
```

---

## Slice from Beginning

```python
numbers[:5]
```

Output:

```python
[0,1,2,3,4]
```

---

## Slice Until End

```python
numbers[5:]
```

Output:

```python
[5,6,7,8,9]
```

---

## Entire List Copy

```python
numbers[:]
```

Output:

```python
[0,1,2,3,4,5,6,7,8,9]
```

---

## Negative Index Slicing

### Last Five Elements

```python
numbers[-5:]
```

Output:

```python
[5,6,7,8,9]
```

---

### Excluding Last Three

```python
numbers[:-3]
```

Output:

```python
[0,1,2,3,4,5,6]
```

---

## Step Parameter

### Every Second Element

```python
numbers[::2]
```

Output:

```python
[0,2,4,6,8]
```

---

### Odd Elements

```python
numbers[1::2]
```

Output:

```python
[1,3,5,7,9]
```

---

## Reverse a List

```python
numbers[::-1]
```

Output:

```python
[9,8,7,6,5,4,3,2,1,0]
```

---

## Slicing Nested Lists

```python
matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
]

matrix[:2]
```

Output:

```python
[
 [1,2,3],
 [4,5,6]
]
```

---

### Using List Comprehension

```python
[row[:2] for row in matrix]
```

Output:

```python
[
 [1,2],
 [4,5],
 [7,8]
]
```

---

## Slice Assignment

Slicing can modify lists.

```python
numbers = [1,2,3,4,5]

numbers[2:4] = [20,30]
```

Output:

```python
[1,2,20,30,5]
```

---

## Deleting Using Slices

```python
numbers = [1,2,3,4,5]

del numbers[2:4]
```

Output:

```python
[1,2,5]
```

---

## Indexing vs Slicing

### Indexing

Returns a single element.

```python
numbers[2]
```

Output:

```python
2
```

---

### Slicing

Returns a list.

```python
numbers[2:5]
```

Output:

```python
[2,3,4]
```

---

# List Methods

Python lists provide powerful built-in methods for modification and analysis.

Most list methods modify the original list directly.

---

## append()

Adds one element to the end.

```python
fruits = ["apple", "banana"]

fruits.append("cherry")
```

Output:

```python
['apple', 'banana', 'cherry']
```

---

## extend()

Adds multiple elements.

```python
numbers = [1,2,3]

numbers.extend([4,5])
```

Output:

```python
[1,2,3,4,5]
```

---

## insert()

Adds an element at a specific index.

```python
colors = ["red", "blue"]

colors.insert(1, "green")
```

Output:

```python
['red', 'green', 'blue']
```

---

## remove()

Removes first matching value.

```python
numbers = [1,2,2,3]

numbers.remove(2)
```

Output:

```python
[1,2,3]
```

---

## pop()

Removes and returns an element.

```python
fruits = ["apple", "banana", "orange"]

item = fruits.pop(1)
```

Output:

```python
banana
```

Remaining list:

```python
['apple', 'orange']
```

---

## clear()

Removes all elements.

```python
numbers = [1,2,3]

numbers.clear()
```

Output:

```python
[]
```

---

## index()

Returns position of first occurrence.

```python
colors = ["red", "green", "blue"]

colors.index("blue")
```

Output:

```python
2
```

---

## count()

Returns frequency.

```python
numbers = [1,2,2,3,2]

numbers.count(2)
```

Output:

```python
3
```

---

## sort()

Sorts list in ascending order.

```python
numbers = [5,2,9,1]

numbers.sort()
```

Output:

```python
[1,2,5,9]
```

---

### Descending Sort

```python
numbers.sort(reverse=True)
```

Output:

```python
[9,5,2,1]
```

---

## reverse()

Reverses order.

```python
fruits.reverse()
```

---

## copy()

Creates a shallow copy.

```python
original = [1,2,3]

copied = original.copy()
```

---

## Shallow Copy Example

```python
copied[0] = 100
```

Result:

```python
original = [1,2,3]
copied   = [100,2,3]
```

The original remains unchanged.

---

# Dictionaries

## What is a Dictionary?

A dictionary is a mutable collection of key-value pairs.

Instead of using numeric indices like lists, dictionaries use keys to access values.

---

## Characteristics

* Mutable
* Fast lookup
* Key-value structure
* Keys must be unique
* Keys must be immutable
* Values can be any datatype

---

## Creating Dictionaries

### Using Curly Braces

```python
person = {
    "name": "John",
    "age": 30
}
```

---

### Using dict() Constructor

```python
car = dict(
    brand="Toyota",
    model="Corolla",
    year=2020
)
```

---

### Empty Dictionary

```python
data = {}
```

---

## Accessing Values

Using keys:

```python
person["name"]
```

Output:

```python
John
```

---

## Using get()

```python
person.get("age")
```

Output:

```python
30
```

Safer because it avoids KeyError.

---

## Default Values

```python
person.get("city", "Not Found")
```

Output:

```python
Not Found
```

---

## Modifying Dictionaries

### Add New Pair

```python
person["city"] = "New York"
```

### Update Existing Value

```python
person["age"] = 31
```

---

## Dictionary Mutability

Because dictionaries are mutable:

```python
person["occupation"] = "Engineer"
```

can be added anytime after creation.

---

## Why Dictionaries Are Important

Dictionaries are among the most important structures in:

* Data Analysis
* APIs
* JSON Processing
* Machine Learning
* Configuration Files
* Database Records

They provide extremely fast lookups and intuitive organization of data.


# Dictionary Methods and Operations

Python dictionaries include several built-in methods that make data retrieval, modification, and inspection efficient.

---

## Removing Elements

### del Statement

Removes a key-value pair permanently.

```python
person = {
    "name": "John",
    "age": 30
}

del person["age"]
```

Output:

```python
{'name': 'John'}
```

---

### pop()

Removes a key and returns its value.

```python
person = {
    "name": "John",
    "age": 30
}

age = person.pop("age")
```

Output:

```python
age = 30
```

Dictionary becomes:

```python
{'name': 'John'}
```

---

### popitem()

Removes and returns the most recently inserted item.

```python
car = {
    "brand": "Toyota",
    "model": "Corolla",
    "year": 2020
}

car.popitem()
```

Output:

```python
('year', 2020)
```

---

### clear()

Removes all elements.

```python
car.clear()
```

Output:

```python
{}
```

---

## Dictionary Views

Python provides special methods to inspect dictionary contents.

---

### keys()

Returns all keys.

```python
car = {
    "brand": "Toyota",
    "model": "Corolla",
    "year": 2020
}

car.keys()
```

Output:

```python
dict_keys(['brand', 'model', 'year'])
```

---

### values()

Returns all values.

```python
car.values()
```

Output:

```python
dict_values(['Toyota', 'Corolla', 2020])
```

---

### items()

Returns key-value pairs as tuples.

```python
car.items()
```

Output:

```python
dict_items([
    ('brand', 'Toyota'),
    ('model', 'Corolla'),
    ('year', 2020)
])
```

---

## Iterating Through Dictionaries

### Iterating Over Keys

```python
for key in car:
    print(key)
```

Output:

```python
brand
model
year
```

---

### Iterating Over Values

```python
for value in car.values():
    print(value)
```

Output:

```python
Toyota
Corolla
2020
```

---

### Iterating Over Key-Value Pairs

```python
for key, value in car.items():
    print(key, value)
```

Output:

```python
brand Toyota
model Corolla
year 2020
```

---

## Nested Dictionaries

A dictionary can contain other dictionaries.

```python
students = {
    "student1": {
        "name": "John",
        "grade": "A"
    },
    "student2": {
        "name": "Alice",
        "grade": "B"
    }
}
```

Accessing nested values:

```python
students["student1"]["name"]
```

Output:

```python
John
```

---

## Dictionary Merging

### Using Double Asterisk Operator

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4}

merged = {**dict1, **dict2}
```

Output:

```python
{
 'a': 1,
 'b': 2,
 'c': 3,
 'd': 4
}
```

---

### Using Pipe Operator (Python 3.9+)

```python
merged = dict1 | dict2
```

Produces the same result.

---

## Common Applications of Dictionaries

### Configuration Storage

```python
config = {
    "host": "localhost",
    "port": 8080
}
```

---

### Counting Frequencies

```python
word_count = {
    "python": 15,
    "data": 8,
    "numpy": 5
}
```

---

### JSON-like Structures

```python
user = {
    "id": 101,
    "name": "John",
    "email": "john@example.com"
}
```

---

### Caching Results

```python
cache = {
    "result_1": 100
}
```

---

# Sets

## What is a Set?

A set is an unordered collection of unique elements.

Sets are designed for:

* Membership testing
* Removing duplicates
* Mathematical set operations
* Fast lookups

---

## Characteristics of Sets

* Unordered
* Mutable
* Unique elements only
* No indexing
* Fast membership testing
* Supports mathematical operations

---

## Creating Sets

### Using Curly Braces

```python
fruits = {"apple", "banana", "orange"}
```

---

### Using set() Constructor

```python
numbers = set([1, 2, 3, 4])
```

---

### Empty Set

```python
empty_set = set()
```

Important:

```python
{}
```

creates an empty dictionary, not a set.

---

## Removing Duplicates Automatically

```python
numbers = {1, 2, 2, 3, 3, 4}
```

Output:

```python
{1, 2, 3, 4}
```

Duplicate values are removed automatically.

---

## Adding Elements

### add()

Adds one element.

```python
colors = {"red", "green"}

colors.add("blue")
```

Output:

```python
{'red', 'green', 'blue'}
```

---

### update()

Adds multiple elements.

```python
colors.update(["yellow", "orange"])
```

Output:

```python
{'red', 'green', 'blue', 'yellow', 'orange'}
```

---

## Removing Elements

### remove()

Removes a specific element.

```python
numbers = {1, 2, 3, 4}

numbers.remove(3)
```

Output:

```python
{1, 2, 4}
```

Raises KeyError if element doesn't exist.

---

### discard()

Safer version of remove().

```python
numbers.discard(10)
```

No error is raised.

---

### pop()

Removes an arbitrary element.

```python
numbers.pop()
```

Since sets are unordered, the removed value is unpredictable.

---

## Frozen Sets

A frozen set is an immutable version of a set.

```python
fs = frozenset([1, 2, 3])
```

Attempting modification:

```python
fs.add(4)
```

Produces:

```python
AttributeError
```

---

## Why Frozen Sets Exist

Frozen sets:

* Are immutable
* Are hashable
* Can be dictionary keys
* Can be members of other sets

Example:

```python
locations = {
    frozenset([1, 2]): "A"
}
```

---

## Membership Testing

Sets are extremely fast for membership checks.

```python
colors = {"red", "green", "blue"}

"green" in colors
```

Output:

```python
True
```

---

## Common Set Applications

### Removing Duplicates

```python
emails = [
    "a@gmail.com",
    "b@gmail.com",
    "a@gmail.com"
]

unique_emails = set(emails)
```

---

### Fast Searching

```python
allowed_users = {
    "john",
    "alice",
    "bob"
}
```

Membership lookup is extremely efficient.

---

### Finding Unique Values

```python
unique_numbers = set(numbers)
```

---

### Database Deduplication

Sets are commonly used for:

* Duplicate record removal
* Unique user detection
* Unique product IDs
* Email cleaning

---

# Set Operations

Python supports mathematical set operations directly.

These operations are heavily used in:

* Data Analysis
* Machine Learning
* Database Processing
* Data Cleaning

---

## Union

Combines all unique elements.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

set1.union(set2)
```

Output:

```python
{1, 2, 3, 4, 5}
```

---

### Union Operator

```python
set1 | set2
```

Produces identical output.

---

## Intersection

Returns common elements.

```python
set1.intersection(set2)
```

Output:

```python
{3}
```

---

### Intersection Operator

```python
set1 & set2
```

---

## Difference

Elements present in first set but not second.

```python
set1 - set2
```

Output:

```python
{1, 2}
```

---

### Difference Method

```python
set1.difference(set2)
```

---

## Symmetric Difference

Elements present in either set but not both.

```python
set1 ^ set2
```

Output:

```python
{1, 2, 4, 5}
```

---

### Method Form

```python
set1.symmetric_difference(set2)
```

---

## Subset

Checks whether one set is completely contained in another.

```python
A = {1, 2}
B = {1, 2, 3, 4}

A.issubset(B)
```

Output:

```python
True
```

---

## Superset

Checks whether one set completely contains another.

```python
B.issuperset(A)
```

Output:

```python
True
```

---

## Disjoint Sets

Sets having no common elements.

```python
A = {1, 2}
B = {5, 6}

A.isdisjoint(B)
```

Output:

```python
True
```

---

## Update Operations

### update()

Modifies set in-place.

```python
set1.update(set2)
```

Equivalent to union assignment.

---

### intersection_update()

Keeps only common elements.

```python
set1.intersection_update(set2)
```

---

## Real-World Example: Email Deduplication

```python
emails = [
    "user1@example.com",
    "user2@example.com",
    "user1@example.com",
    "user3@example.com"
]

unique_emails = set(emails)
```

Output:

```python
{
 'user1@example.com',
 'user2@example.com',
 'user3@example.com'
}
```

This is one of the most common uses of sets in data processing pipelines.

---

# Summary of Mutable Data Structures

| Structure  | Ordered | Mutable | Duplicate Values | Key Feature        |
| ---------- | ------- | ------- | ---------------- | ------------------ |
| List       | Yes     | Yes     | Allowed          | Sequential storage |
| Dictionary | No*     | Yes     | Values Allowed   | Key-value mapping  |
| Set        | No      | Yes     | Not Allowed      | Unique elements    |

* Modern Python preserves insertion order in dictionaries, but conceptually dictionaries are key-value stores rather than sequential collections.

# NumPy

## Introduction to NumPy

NumPy (Numerical Python) is the foundational library for numerical computing in Python.

It provides:

* High-performance multidimensional arrays
* Mathematical functions
* Linear algebra operations
* Statistical functions
* Random number generation
* Broadcasting capabilities

NumPy is the backbone of many popular libraries including:

* Pandas
* Scikit-Learn
* TensorFlow
* PyTorch
* SciPy

---

## Why NumPy?

Python lists are flexible but inefficient for numerical computation.

NumPy provides:

### Faster Computation

Operations are implemented in optimized C code.

### Lower Memory Usage

Arrays consume significantly less memory than Python lists.

### Vectorized Operations

Operations are performed on entire arrays without explicit loops.

### Broadcasting

Allows arithmetic between arrays of different shapes.

### Integration

Works seamlessly with scientific and machine learning libraries.

---

## Importing NumPy

The standard convention:

```python
import numpy as np
```

The alias `np` is universally used in Python code.

---

# NumPy Arrays

## What is a NumPy Array?

A NumPy array is a homogeneous multidimensional collection of elements.

Homogeneous means:

All elements must have the same datatype.

Example:

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
```

---

## Python List vs NumPy Array

### Python List

```python
numbers = [1, 2, 3, 4]
```

Can contain:

```python
mixed = [1, "Python", 3.14]
```

---

### NumPy Array

```python
arr = np.array([1, 2, 3, 4])
```

All elements share the same datatype.

---

## Creating Arrays

### From Python Lists

```python
arr = np.array([1, 2, 3, 4, 5])
```

Output:

```python
array([1, 2, 3, 4, 5])
```

---

## Using arange()

Creates evenly spaced values.

```python
np.arange(5)
```

Output:

```python
array([0, 1, 2, 3, 4])
```

---

```python
np.arange(2, 10)
```

Output:

```python
array([2,3,4,5,6,7,8,9])
```

---

```python
np.arange(0, 20, 2)
```

Output:

```python
array([0,2,4,6,8,10,12,14,16,18])
```

---

## Creating Arrays of Zeros

```python
np.zeros(5)
```

Output:

```python
array([0., 0., 0., 0., 0.])
```

---

### 2D Zeros Array

```python
np.zeros((3,4))
```

Output:

```python
[
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]
]
```

---

## Creating Arrays of Ones

```python
np.ones(5)
```

Output:

```python
array([1.,1.,1.,1.,1.])
```

---

### 2D Ones Array

```python
np.ones((2,3))
```

Output:

```python
[
 [1. 1. 1.]
 [1. 1. 1.]
]
```

---

## Using linspace()

Creates evenly spaced values between two numbers.

```python
np.linspace(0, 1, 5)
```

Output:

```python
array([
 0.00,
 0.25,
 0.50,
 0.75,
 1.00
])
```

---

### Why linspace?

Useful for:

* Plotting
* Simulations
* Numerical methods
* Machine learning

---

## Random Arrays

### Uniform Distribution

```python
np.random.rand(3,3)
```

Example Output:

```python
[
 [0.23 0.87 0.44]
 [0.15 0.66 0.78]
 [0.91 0.32 0.54]
]
```

Values range between:

```text
0 and 1
```

---

# Array Attributes

NumPy arrays contain useful metadata.

---

## shape

Returns dimensions.

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])

arr.shape
```

Output:

```python
(2, 3)
```

Meaning:

```text
2 Rows
3 Columns
```

---

## ndim

Returns number of dimensions.

```python
arr.ndim
```

Output:

```python
2
```

---

### Examples

```python
np.array([1,2,3]).ndim
```

Output:

```python
1
```

---

```python
np.array([[1,2],[3,4]]).ndim
```

Output:

```python
2
```

---

## size

Returns total elements.

```python
arr.size
```

Output:

```python
6
```

Because:

```text
2 × 3 = 6
```

---

## dtype

Returns datatype.

```python
arr.dtype
```

Output:

```python
dtype('int64')
```

Depending on system architecture.

---

# Accessing Array Elements

## One-Dimensional Arrays

```python
arr = np.array([10,20,30,40,50])
```

---

### First Element

```python
arr[0]
```

Output:

```python
10
```

---

### Third Element

```python
arr[2]
```

Output:

```python
30
```

---

### Last Element

```python
arr[-1]
```

Output:

```python
50
```

---

# Two-Dimensional Arrays

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])
```

---

### Access Specific Element

```python
arr[1,2]
```

Output:

```python
6
```

Explanation:

```text
Row Index = 1
Column Index = 2
```

---

### Access Entire Row

```python
arr[0]
```

Output:

```python
array([1,2,3])
```

---

### Access Entire Column

```python
arr[:,1]
```

Output:

```python
array([2,5])
```

---

# Array Slicing

NumPy slicing follows:

```python
array[start:end:step]
```

---

## Basic Slicing

```python
arr = np.array([0,1,2,3,4,5,6,7,8,9])

arr[2:7]
```

Output:

```python
array([2,3,4,5,6])
```

---

## Every Second Element

```python
arr[::2]
```

Output:

```python
array([0,2,4,6,8])
```

---

## Reverse Array

```python
arr[::-1]
```

Output:

```python
array([9,8,7,6,5,4,3,2,1,0])
```

---

# Two-Dimensional Slicing

```python
arr = np.array([
 [1,2,3],
 [4,5,6],
 [7,8,9]
])
```

---

### First Two Rows

```python
arr[:2]
```

Output:

```python
[
 [1,2,3],
 [4,5,6]
]
```

---

### Specific Columns

```python
arr[:,1:]
```

Output:

```python
[
 [2,3],
 [5,6],
 [8,9]
]
```

---

### Extract Subarray

```python
arr[:2,1:]
```

Output:

```python
[
 [2,3],
 [5,6]
]
```

---

# Modifying Arrays

Arrays are mutable.

```python
arr = np.array([1,2,3,4,5])

arr[2] = 100
```

Output:

```python
array([1,2,100,4,5])
```

---

## Slice Assignment

```python
arr[2:4] = 10
```

Output:

```python
array([1,2,10,10,5])
```

The scalar value is automatically broadcast across the slice.

---

# Reshaping Arrays

A major advantage of NumPy.

---

## reshape()

Changes dimensions without changing data.

```python
arr = np.arange(12)
```

Output:

```python
array([
 0,1,2,3,
 4,5,6,7,
 8,9,10,11
])
```

---

### Convert to 3 × 4 Matrix

```python
arr.reshape(3,4)
```

Output:

```python
[
 [0,1,2,3],
 [4,5,6,7],
 [8,9,10,11]
]
```

---

### Why Reshape?

Extensively used in:

* Machine Learning
* Deep Learning
* Computer Vision
* Data Processing

because algorithms expect specific dimensions.

---

# Array Concatenation

Combining arrays.

```python
a = np.array([1,2,3])
b = np.array([4,5,6])
```

---

## concatenate()

```python
np.concatenate((a,b))
```

Output:

```python
array([1,2,3,4,5,6])
```

---

# Splitting Arrays

## split()

```python
arr = np.array([1,2,3,4,5,6])

np.split(arr, 2)
```

Output:

```python
[
 array([1,2,3]),
 array([4,5,6])
]
```

---

# Advantages of NumPy Arrays

### Performance

Much faster than Python lists.

### Memory Efficiency

Stores data compactly.

### Mathematical Computation

Supports vectorized calculations.

### Broadcasting

Reduces loops.

### Machine Learning Ready

All major ML frameworks expect NumPy-style arrays.

---

# Key Takeaways

* NumPy is the foundation of scientific computing in Python.
* Arrays are homogeneous and efficient.
* Arrays support indexing, slicing, reshaping, and concatenation.
* Array attributes like shape, size, dtype, and ndim provide useful information.
* NumPy is significantly faster than Python lists for numerical computation.
* Understanding arrays is essential before learning Pandas, Machine Learning, and Deep Learning.

# NumPy Data Types (DTypes)

## Introduction

One of NumPy's biggest advantages is its extensive datatype system.

Unlike Python, which automatically manages object types, NumPy allows precise control over memory usage and computation.

NumPy datatypes are commonly called **DTypes**.

Understanding DTypes is important because they affect:

* Memory consumption
* Processing speed
* Numerical precision
* Storage efficiency

---

## Common NumPy Data Types

### Integer Types

| Type  | Size   |
| ----- | ------ |
| int8  | 8-bit  |
| int16 | 16-bit |
| int32 | 32-bit |
| int64 | 64-bit |

Example:

```python
import numpy as np

arr = np.array([1, 2, 3], dtype=np.int32)
```

---

### Unsigned Integers

Unsigned integers only store positive values.

| Type   | Range                 |
| ------ | --------------------- |
| uint8  | 0 to 255              |
| uint16 | 0 to 65535            |
| uint32 | Larger positive range |

Example:

```python
arr = np.array([10, 20, 30], dtype=np.uint8)
```

---

### Floating Point Types

| Type    | Precision |
| ------- | --------- |
| float16 | Low       |
| float32 | Medium    |
| float64 | High      |

Example:

```python
arr = np.array([1.5, 2.8, 3.7], dtype=np.float64)
```

---

### Complex Numbers

Used in:

* Signal Processing
* Physics
* Electrical Engineering

Available Types:

```python
np.complex64
np.complex128
```

Example:

```python
arr = np.array([1+2j, 3+4j])
```

---

### Boolean Type

Stores:

```python
True
False
```

Example:

```python
arr = np.array([True, False, True])
```

---

### String Type

```python
arr = np.array(["Python", "NumPy"])
```

---

# Specifying Datatypes

You can explicitly define a datatype.

### Integer Example

```python
arr = np.array([1, 2, 3], dtype=np.int32)
```

Output:

```python
array([1,2,3], dtype=int32)
```

---

### Float Example

```python
arr = np.array([1,2,3], dtype=np.float64)
```

Output:

```python
array([1.,2.,3.])
```

---

# Checking Datatypes

Use:

```python
arr.dtype
```

Example:

```python
arr = np.array([1,2,3])

print(arr.dtype)
```

Output:

```python
int64
```

(May vary depending on operating system.)

---

# Type Conversion

## astype()

Converts one datatype into another.

### Integer → Float

```python
arr = np.array([1,2,3])

new_arr = arr.astype(np.float64)
```

Output:

```python
array([1.,2.,3.])
```

---

### Float → Integer

```python
arr = np.array([1.9, 2.5, 3.7])

arr.astype(np.int32)
```

Output:

```python
array([1,2,3])
```

Notice:

```text
Decimal values are truncated.
```

---

# Automatic Type Promotion

NumPy automatically chooses the safest datatype during operations.

Example:

```python
a = np.array([1,2,3], dtype=np.int32)

b = np.array([1.5,2.5,3.5], dtype=np.float64)

c = a + b
```

Output datatype:

```python
float64
```

Reason:

```text
float64 can safely store both integers and decimals.
```

---

# Memory Usage

Different datatypes consume different amounts of memory.

## itemsize

Returns memory used per element.

### int8

```python
arr = np.array([1,2,3], dtype=np.int8)

arr.itemsize
```

Output:

```python
1
```

1 byte per element.

---

### int64

```python
arr = np.array([1,2,3], dtype=np.int64)

arr.itemsize
```

Output:

```python
8
```

8 bytes per element.

---

## Why This Matters

Dataset:

```text
10 Million Numbers
```

Using:

```text
int8  → 10 MB
int64 → 80 MB
```

Huge memory difference.

---

# Choosing Appropriate Datatypes

General Guidelines:

### Use int8/int16

When values are small.

Example:

```python
Age
Temperature
Ratings
```

---

### Use int32/int64

When values can become large.

Example:

```python
Population
Sales Records
IDs
```

---

### Use float32

Machine Learning commonly uses:

```python
float32
```

because it balances:

* Precision
* Speed
* Memory

---

### Use float64

Scientific calculations requiring high precision.

---

# Structured Arrays

NumPy supports database-like records.

Example:

```python
student_dtype = np.dtype([
    ('name', 'U20'),
    ('grade', 'f4')
])
```

---

Creating Structured Data:

```python
students = np.array([
    ("John", 85.5),
    ("Alice", 92.0)
], dtype=student_dtype)
```

Output:

```python
[
 ('John', 85.5),
 ('Alice', 92.0)
]
```

---

Accessing Fields

```python
students['name']
```

Output:

```python
['John', 'Alice']
```

---

```python
students['grade']
```

Output:

```python
[85.5, 92.0]
```

---

# Handling Missing Values

Real-world datasets often contain missing values.

NumPy uses:

```python
np.nan
```

which stands for:

```text
Not a Number
```

Example:

```python
arr = np.array([1, 2, np.nan, 4])
```

---

## Checking for NaN

```python
np.isnan(arr)
```

Output:

```python
[
 False,
 False,
 True,
 False
]
```

---

# Best Practices

### Choose Smallest Possible Datatype

Improves memory efficiency.

### Avoid Overflow

Small integer types can overflow.

Example:

```python
np.int8(127) + 1
```

Produces unexpected results.

---

### Balance Precision and Speed

More precision:

```text
Higher Memory
Slower Processing
```

Less precision:

```text
Lower Memory
Faster Processing
```

Choose according to the application.

---

# Arithmetic with NumPy

One of NumPy's greatest strengths is performing arithmetic on entire arrays simultaneously.

This concept is called:

```text
Vectorized Computation
```

No loops required.

---

## Element-Wise Addition

```python
A = np.array([1,2,3])

B = np.array([4,5,6])

A + B
```

Output:

```python
array([5,7,9])
```

Calculation:

```text
1+4 = 5
2+5 = 7
3+6 = 9
```

---

## Element-Wise Subtraction

```python
A - B
```

Output:

```python
array([-3,-3,-3])
```

---

## Element-Wise Multiplication

```python
A * B
```

Output:

```python
array([4,10,18])
```

---

## Element-Wise Division

```python
A / B
```

Output:

```python
array([
 0.25,
 0.40,
 0.50
])
```

---

## Power Operation

```python
A ** 2
```

Output:

```python
array([1,4,9])
```

---

## Square Root

```python
np.sqrt(A)
```

Output:

```python
array([
 1.0,
 1.414,
 1.732
])
```

---

## Exponential

```python
np.exp(A)
```

Output:

```python
[
 e¹,
 e²,
 e³
]
```

Numerical values:

```python
[
 2.718,
 7.389,
 20.085
]
```

---

# Scalar Operations

A scalar is a single number.

Example:

```python
A = np.array([1,2,3])
```

---

### Add Scalar

```python
A + 5
```

Output:

```python
array([6,7,8])
```

---

### Multiply Scalar

```python
A * 2
```

Output:

```python
array([2,4,6])
```

---

### Divide Scalar

```python
A / 2
```

Output:

```python
array([
 0.5,
 1.0,
 1.5
])
```

---

# Broadcasting

Broadcasting is one of NumPy's most powerful features.

It allows operations between arrays of different shapes.

Example:

```python
A = np.array([
 [1,2,3],
 [4,5,6]
])

B = np.array([10,20,30])

A + B
```

Output:

```python
[
 [11,22,33],
 [14,25,36]
]
```

NumPy automatically expands B across rows.

Without broadcasting, explicit loops would be required.

---

# Why Broadcasting Is Important

Benefits:

* Faster execution
* Less memory usage
* Cleaner code
* No manual loops

Broadcasting is heavily used in:

* Machine Learning
* Deep Learning
* Data Analysis
* Scientific Computing

---

# Comparison Operations

NumPy supports element-wise comparisons.

```python
A = np.array([1,2,3])

B = np.array([1,4,2])
```

---

### Equality

```python
A == B
```

Output:

```python
[
 True,
 False,
 False
]
```

---

### Greater Than

```python
A > B
```

Output:

```python
[
 False,
 False,
 True
]
```

---

### Less Than

```python
A < B
```

Output:

```python
[
 False,
 True,
 False
]
```

These comparisons create Boolean arrays.

---

# Key Takeaways

* NumPy provides fine-grained datatype control.
* Datatypes affect memory, speed, and precision.
* `astype()` converts datatypes.
* `itemsize` reveals memory consumption.
* NumPy performs arithmetic element-wise.
* Vectorized operations eliminate explicit loops.
* Broadcasting allows operations between arrays of different shapes.
* Comparison operations produce Boolean arrays for filtering and analysis.

# Boolean Operations in NumPy

Boolean operations are extremely important in data analysis because they allow us to filter and select data based on conditions.

---

## Boolean Arrays

A Boolean array contains only:

```python
True
False
```

Example:

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

arr > 3
```

Output:

```python
array([False, False, False, True, True])
```

---

## Logical AND

Use:

```python
np.logical_and()
```

Example:

```python
a = np.array([True, True, False, False])

b = np.array([True, False, True, False])

np.logical_and(a, b)
```

Output:

```python
array([ True, False, False, False])
```

Both values must be True.

---

## Logical OR

Use:

```python
np.logical_or()
```

Example:

```python
np.logical_or(a, b)
```

Output:

```python
array([ True, True, True, False])
```

At least one value must be True.

---

## Logical NOT

Use:

```python
np.logical_not()
```

Example:

```python
np.logical_not(a)
```

Output:

```python
array([False, False, True, True])
```

Reverses Boolean values.

---

## Combined Conditions

Example:

```python
arr = np.array([10, 20, 30, 40, 50])

(arr > 20) & (arr < 50)
```

Output:

```python
array([False, False, True, True, False])
```

Useful for filtering datasets.

---

# Universal Functions (ufuncs)

Universal Functions (ufuncs) are highly optimized NumPy functions that operate element-wise on arrays.

Benefits:

* Faster execution
* Vectorized computation
* No loops required

---

## np.add()

Equivalent to:

```python
a + b
```

Example:

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

np.add(a,b)
```

Output:

```python
array([5,7,9])
```

---

## np.subtract()

```python
np.subtract(a,b)
```

Output:

```python
array([-3,-3,-3])
```

---

## np.multiply()

```python
np.multiply(a,b)
```

Output:

```python
array([4,10,18])
```

---

## np.divide()

```python
np.divide(a,b)
```

Output:

```python
array([
0.25,
0.40,
0.50
])
```

---

## np.power()

```python
np.power(a,2)
```

Output:

```python
array([1,4,9])
```

---

## Why Use ufuncs?

Advantages:

* Written in C
* Much faster than loops
* Supports broadcasting
* Supports multidimensional arrays

---

# Indexing and Slicing Arrays

NumPy indexing is similar to Python lists but significantly more powerful.

---

## 1-D Array Indexing

```python
arr = np.array([1,2,3,4,5])
```

### First Element

```python
arr[0]
```

Output:

```python
1
```

---

### Last Element

```python
arr[-1]
```

Output:

```python
5
```

---

## 2-D Array Indexing

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])
```

Access row 2 column 3:

```python
arr[1,2]
```

Output:

```python
6
```

Remember:

```text
Index starts from 0
```

---

## Access Entire Row

```python
arr[0]
```

Output:

```python
array([1,2,3])
```

---

# Slicing Arrays

Syntax:

```python
array[start:end:step]
```

---

## Basic Slice

```python
arr = np.array([0,1,2,3,4,5,6,7,8,9])

arr[2:7]
```

Output:

```python
array([2,3,4,5,6])
```

---

## Every Second Element

```python
arr[::2]
```

Output:

```python
array([0,2,4,6,8])
```

---

## Reverse Array

```python
arr[::-1]
```

Output:

```python
array([9,8,7,6,5,4,3,2,1,0])
```

---

# Slicing 2-D Arrays

Example:

```python
arr = np.array([
    [1,2,3],
    [4,5,6],
    [7,8,9]
])
```

---

### Select First Two Rows

```python
arr[:2]
```

Output:

```python
[
 [1,2,3],
 [4,5,6]
]
```

---

### Select Specific Columns

```python
arr[:,1:]
```

Output:

```python
[
 [2,3],
 [5,6],
 [8,9]
]
```

---

### Select Subarray

```python
arr[:2,1:]
```

Output:

```python
[
 [2,3],
 [5,6]
]
```

---

# Modifying Arrays with Slicing

You can update multiple values at once.

Example:

```python
arr = np.array([1,2,3,4,5])

arr[2:4] = 10
```

Output:

```python
array([1,2,10,10,5])
```

Value is automatically broadcast.

---

# Boolean Indexing

Boolean indexing is one of the most important NumPy concepts.

It selects elements based on conditions.

---

## Example

```python
arr = np.array([1,2,3,4,5])

mask = arr > 2

mask
```

Output:

```python
array([
False,
False,
True,
True,
True
])
```

---

## Apply Mask

```python
arr[mask]
```

Output:

```python
array([3,4,5])
```

---

## Direct Method

```python
arr[arr > 2]
```

Output:

```python
array([3,4,5])
```

---

## Multiple Conditions

```python
arr[(arr > 2) & (arr < 5)]
```

Output:

```python
array([3,4])
```

---

# Fancy Indexing

Fancy indexing uses arrays of indices.

---

## Example

```python
arr = np.array([10,20,30,40,50])

arr[[1,3,4]]
```

Output:

```python
array([20,40,50])
```

Selected positions:

```text
1 → 20
3 → 40
4 → 50
```

---

## Repeated Indices

```python
arr[[0,0,1]]
```

Output:

```python
array([10,10,20])
```

---

# np.ix()

Used for selecting rows and columns simultaneously.

Example:

```python
arr = np.array([
 [1,2,3],
 [4,5,6],
 [7,8,9]
])

arr[np.ix_([0,2],[0,2])]
```

Output:

```python
[
 [1,3],
 [7,9]
]
```

Selected:

```text
Rows: 0,2
Columns: 0,2
```

---

# Multi-Dimensional Fancy Indexing

Example:

```python
arr = np.arange(10)

indices = np.array([
 [1,3],
 [5,7]
])

arr[indices]
```

Output:

```python
[
 [1,3],
 [5,7]
]
```

---

# np.where()

Returns positions where a condition is True.

Example:

```python
arr = np.array([1,2,3,4,5])

np.where(arr > 3)
```

Output:

```python
(array([3,4]),)
```

Meaning:

```text
Values greater than 3 occur at indices:
3 and 4
```

---

## Conditional Replacement

```python
np.where(arr > 3, 100, 0)
```

Output:

```python
array([0,0,0,100,100])
```

Syntax:

```python
np.where(condition, true_value, false_value)
```

---

# np.argwhere()

Returns coordinates of matching values.

Example:

```python
arr = np.array([1,2,3,4,5])

np.argwhere(arr > 3)
```

Output:

```python
[
 [3],
 [4]
]
```

Useful for locating values in multidimensional arrays.

---

# Masked Arrays

Real-world datasets often contain:

* Missing values
* Invalid values
* Corrupted values

NumPy provides Masked Arrays.

---

## Creating Masked Array

```python
import numpy.ma as ma

arr = np.array([1,2,3,4,5])

mask = [False, False, True, False, True]

masked = ma.masked_array(arr, mask=mask)
```

Output:

```python
[1 2 -- 4 --]
```

Masked values are hidden.

---

## Benefits

Used when:

* Dataset contains missing entries
* Scientific measurements have errors
* Data cleaning is required

---

# Key Takeaways

* Boolean operations work element-wise.
* `logical_and()`, `logical_or()`, and `logical_not()` are important logical functions.
* Universal Functions (ufuncs) provide optimized mathematical operations.
* NumPy supports powerful indexing and slicing techniques.
* Boolean indexing enables condition-based filtering.
* Fancy indexing selects custom positions.
* `np.where()` and `np.argwhere()` locate matching values.
* Masked arrays help manage missing or invalid data.

---

# NumPy Functions and Statistical Analysis

NumPy provides:

* Mathematical Functions
* Statistical Functions
* Aggregation Functions
* Array Manipulation Functions
* Linear Algebra Functions
* Random Number Functions

These functions form the foundation of data analysis, machine learning, and scientific computing.

# Essential Reading Summary: Immutable Data Structures

Immutable data structures are objects whose contents cannot be changed after creation. Once an immutable object is created, its values remain fixed throughout the program's execution.

## Advantages of Immutable Data Structures

- Prevent accidental modification of data.
- Improve program reliability and predictability.
- Can be safely shared across multiple functions.
- Often more memory efficient.
- Can be used as dictionary keys (if all elements are immutable).

## Types of Immutable Data Structures Covered

### Tuples

- Ordered collection of elements.
- Defined using parentheses `()`.
- Can contain mixed data types.
- Supports indexing, slicing, unpacking, concatenation, and repetition.
- Cannot be modified after creation.

Example:

```python
book = ("Python", "John Doe", 2024)
```

### Strings

- Sequence of characters.
- Defined using single, double, or triple quotes.
- Immutable by design.
- Support indexing, slicing, searching, and replacement.

Example:

```python
name = "Python"
```

## When to Use Immutable Structures

Use tuples when:

- Data should remain constant.
- Returning multiple values from functions.
- Storing coordinates, RGB values, configurations.

Use strings when:

- Working with textual data.
- Processing user input.
- Performing text analysis.

---

# Essential Reading Summary: Mutable Data Structures

Mutable data structures allow their contents to be modified after creation.

## Advantages of Mutable Data Structures

- Dynamic modification of data.
- Efficient updates.
- Suitable for changing datasets.
- Useful in data analysis and machine learning.

## Types of Mutable Data Structures Covered

### Lists

- Ordered collection.
- Defined using square brackets `[]`.
- Supports indexing and slicing.
- Elements can be modified.

Example:

```python
numbers = [1, 2, 3, 4]
```

### Dictionaries

- Store data as key-value pairs.
- Defined using curly braces `{}`.
- Fast lookup using keys.

Example:

```python
person = {
    "name": "John",
    "age": 25
}
```

### Sets

- Unordered collection of unique elements.
- Automatically removes duplicates.

Example:

```python
unique_numbers = {1, 2, 3}
```

## When to Use Mutable Structures

Use Lists when:

- Order matters.
- Data changes frequently.

Use Dictionaries when:

- Fast lookups are required.
- Data naturally fits key-value relationships.

Use Sets when:

- Removing duplicates.
- Performing mathematical set operations.

---

# Essential Reading Summary: NumPy Library

NumPy (Numerical Python) is the foundational library for numerical computing in Python.

## Why NumPy?

Compared to Python Lists:

- Faster execution.
- Less memory usage.
- Supports multidimensional arrays.
- Vectorized operations.
- Broadcasting support.
- Large collection of mathematical functions.

## Major Features

### Array Creation

```python
np.array()
np.arange()
np.linspace()
np.zeros()
np.ones()
```

### Mathematical Operations

```python
np.sum()
np.mean()
np.sqrt()
np.square()
np.exp()
np.log()
```

### Statistical Functions

```python
np.mean()
np.median()
np.var()
np.std()
```

### Array Manipulation

```python
reshape()
transpose()
concatenate()
split()
```

### Random Number Generation

```python
np.random.rand()
np.random.randn()
np.random.randint()
```

### Linear Algebra

```python
np.dot()
np.linalg.det()
```

## Applications of NumPy

- Data Analysis
- Machine Learning
- Artificial Intelligence
- Scientific Computing
- Image Processing
- Deep Learning
- Financial Modeling

---

# Comparison Tables

## Tuple vs List

| Feature | Tuple | List |
|----------|--------|--------|
| Mutable | No | Yes |
| Syntax | () | [] |
| Memory Usage | Lower | Higher |
| Speed | Faster | Slower |
| Can be Dictionary Key | Yes | No |
| Modification | Not Allowed | Allowed |

---

## List vs Set

| Feature | List | Set |
|----------|--------|--------|
| Ordered | Yes | No |
| Duplicates Allowed | Yes | No |
| Indexing | Yes | No |
| Mutable | Yes | Yes |
| Membership Testing | Slower | Faster |

---

## Dictionary vs Set

| Feature | Dictionary | Set |
|----------|------------|------|
| Structure | Key-Value Pairs | Unique Values |
| Lookup Speed | Very Fast | Very Fast |
| Keys Required | Yes | No |
| Values Stored | Yes | No |

---

## Python List vs NumPy Array

| Feature | Python List | NumPy Array |
|----------|-------------|-------------|
| Speed | Slower | Faster |
| Memory Usage | Higher | Lower |
| Homogeneous Data | No | Yes |
| Mathematical Operations | Limited | Extensive |
| Broadcasting | No | Yes |
| Multidimensional Support | Limited | Excellent |

---

# Module 3 Cheatsheet

## Tuple

```python
t = (1, 2, 3)

t[0]
len(t)
t.count(2)
t.index(3)
```

## String

```python
s = "Python"

s.upper()
s.lower()
s.replace()
s.find()
s.count()
s.split()
```

## List

```python
lst.append()
lst.extend()
lst.insert()
lst.remove()
lst.pop()
lst.sort()
lst.reverse()
lst.copy()
```

## Dictionary

```python
d.get()
d.keys()
d.values()
d.items()
d.pop()
```

## Set

```python
s.add()
s.remove()
s.discard()
s.union()
s.intersection()
s.difference()
```

## NumPy

```python
np.array()
np.arange()
np.linspace()
np.zeros()
np.ones()
np.reshape()
np.mean()
np.sum()
np.std()
```

---

# Frequently Used Methods Quick Reference

## Tuple Methods

| Method | Purpose |
|----------|----------|
| count() | Count occurrences |
| index() | Find index |

---

## String Methods

| Method | Purpose |
|----------|----------|
| upper() | Convert to uppercase |
| lower() | Convert to lowercase |
| find() | Find substring |
| replace() | Replace substring |
| split() | Split string |
| join() | Join strings |

---

## List Methods

| Method | Purpose |
|----------|----------|
| append() | Add element |
| extend() | Add multiple elements |
| insert() | Insert at position |
| remove() | Remove value |
| pop() | Remove by index |
| clear() | Empty list |
| sort() | Sort elements |
| reverse() | Reverse list |

---

## Dictionary Methods

| Method | Purpose |
|----------|----------|
| get() | Safe retrieval |
| keys() | Get keys |
| values() | Get values |
| items() | Get key-value pairs |
| pop() | Remove key |

---

## Set Methods

| Method | Purpose |
|----------|----------|
| add() | Add element |
| remove() | Remove element |
| discard() | Remove safely |
| union() | Combine sets |
| intersection() | Common elements |
| difference() | Unique elements |

---

# Important Interview Questions

## Tuples

### Q1. Why are tuples immutable?

Immutability improves performance, safety, and allows tuples to be used as dictionary keys.

### Q2. Can a tuple contain mutable objects?

Yes.

Example:

```python
t = ([1, 2], 3)
```

The tuple is immutable but the list inside it can change.

---

## Strings

### Q3. Why does string modification create a new object?

Strings are immutable. Every modification produces a new string.

---

## Lists

### Q4. Difference between append() and extend()?

append():

```python
lst.append([4,5])
```

Result:

```python
[1,2,3,[4,5]]
```

extend():

```python
lst.extend([4,5])
```

Result:

```python
[1,2,3,4,5]
```

---

## Dictionaries

### Q5. Why must dictionary keys be immutable?

Python uses hashing for fast lookups.

Mutable objects can change their hash value.

---

## Sets

### Q6. Why are sets useful?

- Remove duplicates
- Fast membership testing
- Mathematical set operations

---

## NumPy

### Q7. Why is NumPy faster than Python Lists?

Because NumPy:

- Uses contiguous memory.
- Uses optimized C implementations.
- Supports vectorized operations.

### Q8. What is broadcasting?

Broadcasting automatically expands smaller arrays to perform arithmetic with larger arrays.

Example:

```python
arr + 10
```

Adds 10 to every element.

### Q9. Difference between reshape() and transpose()?

reshape():

Changes dimensions.

transpose():

Swaps axes.

---

# Module 3 Key Takeaways

1. Tuples and Strings are immutable.
2. Lists, Dictionaries, and Sets are mutable.
3. Lists support indexing and slicing.
4. Dictionaries provide fast key-value access.
5. Sets automatically eliminate duplicates.
6. NumPy arrays are faster and more memory efficient than Python lists.
7. Broadcasting eliminates many explicit loops.
8. Boolean indexing is essential for data filtering.
9. NumPy provides powerful statistical, mathematical, and linear algebra functions.
10. Data Structures and NumPy form the foundation of Data Analytics, Machine Learning, and Scientific Computing in Python.

---

# End of Module 3
**Fundamental Data Structures and NumPy in Python**