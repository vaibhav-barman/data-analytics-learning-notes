# Pandas Series

## Introduction

A **Pandas Series** is a **one-dimensional labeled array** provided by the Pandas library. It is one of the most fundamental data structures in data analysis and acts as the building block for DataFrames.

A Series can store:

* Integers
* Floating-point numbers
* Strings
* Boolean values
* Mixed data types

Each element in a Series consists of:

1. **Index (Label)**
2. **Value**

Think of a Series as a smarter version of a Python list because it contains labels (indexes) along with values.

---

## Why Pandas Series is Important

Before Pandas existed, analysts relied heavily on:

* Python Lists
* Dictionaries
* NumPy Arrays

These structures lacked many features needed for real-world data analysis such as:

* Label-based indexing
* Missing value handling
* Fast filtering
* Statistical operations

Pandas Series solves these problems efficiently.

---

## Importing Pandas

Before creating a Series, Pandas must be imported.

```python
import pandas as pd
```

### Why use `pd`?

`pd` is simply an alias.

Instead of writing:

```python
pandas.Series()
```

we write:

```python
pd.Series()
```

which is shorter and easier.

---

# Creating a Series

---

## Creating Series from a List

### Syntax

```python
pd.Series(data)
```

### Example

```python
import pandas as pd

numbers = [10, 20, 30, 40, 50]

s = pd.Series(numbers)

print(s)
```

### Output

```python
0    10
1    20
2    30
3    40
4    50
dtype: int64
```

---

### Understanding the Output

```python
0    10
1    20
2    30
3    40
4    50
```

Left side:

```python
0
1
2
3
4
```

are indexes.

Right side:

```python
10
20
30
40
50
```

are values.

Pandas automatically generates indexes starting from 0.

---

## Creating Series with Custom Index

Instead of default numerical indexes, we can assign meaningful labels.

### Example

```python
s = pd.Series(
    [10,20,30,40,50],
    index=["A","B","C","D","E"]
)

print(s)
```

### Output

```python
A    10
B    20
C    30
D    40
E    50
dtype: int64
```

---

### Advantages

Custom indexes make data easier to understand.

Instead of:

```python
s[1]
```

you can use:

```python
s["B"]
```

which is more meaningful.

---

## Creating Series from Dictionary

A dictionary naturally contains:

```python
Key : Value
```

Pandas converts:

```python
Key → Index
Value → Data
```

### Example

```python
data = {
    "A":10,
    "B":20,
    "C":30
}

s = pd.Series(data)

print(s)
```

### Output

```python
A    10
B    20
C    30
dtype: int64
```

---

### Why Dictionary-Based Creation is Useful

Many real-world datasets already exist in key-value format.

Examples:

```python
{
   "January": 12000,
   "February": 15000,
   "March": 18000
}
```

can directly become a Series.

---

# Accessing Elements

There are multiple methods.

---

## Access by Label

### Example

```python
s["B"]
```

### Output

```python
20
```

Because index B contains value 20.

---

## Access by Position

### Example

```python
s[1]
```

### Output

```python
20
```

Position starts from 0.

---

## Slicing

Works similar to Python Lists.

### Example

```python
s[1:4]
```

### Output

```python
B    20
C    30
D    40
```

Notice:

```python
4
```

is excluded.

---

# Series Attributes

Attributes help us inspect the structure of a Series.

---

## 1. index

Returns all index labels.

### Example

```python
print(s.index)
```

### Output

```python
Index(['A','B','C','D','E'])
```

---

## 2. values

Returns underlying values.

### Example

```python
print(s.values)
```

### Output

```python
array([10,20,30,40,50])
```

---

## 3. dtype

Returns data type.

### Example

```python
print(s.dtype)
```

### Output

```python
int64
```

Possible data types:

```python
int64
float64
object
bool
```

---

# Series Operations

One major strength of Pandas is vectorized operations.

Instead of loops:

```python
for i in data:
    ...
```

operations occur automatically.

---

## Addition

### Example

```python
s1 = pd.Series([1,2,3,4,5])
s2 = pd.Series([10,20,30,40,50])

s1 + s2
```

### Output

```python
0    11
1    22
2    33
3    44
4    55
```

Element-wise addition occurs.

---

## Scalar Multiplication

### Example

```python
s1 * 2
```

### Output

```python
0     2
1     4
2     6
3     8
4    10
```

Every value is multiplied by 2.

---

# Filtering Series

Filtering is one of the most important EDA operations.

---

## Example

```python
s = pd.Series([10,20,30,40,50])

s[s > 30]
```

### Output

```python
3    40
4    50
```

---

### How it Works

Step 1:

```python
s > 30
```

Produces:

```python
False
False
False
True
True
```

Step 2:

Pandas returns only rows where condition is True.

---

# Applying Functions

The `apply()` method applies a function to every element.

---

## Using Lambda Function

### Example

```python
s = pd.Series([1,2,3,4])

s.apply(lambda x: x**2)
```

### Output

```python
0     1
1     4
2     9
3    16
```

---

### What Happened?

Each value was squared:

```python
1² = 1
2² = 4
3² = 9
4² = 16
```

---

## Why Apply is Powerful

Useful for:

* Currency conversion
* Data transformation
* Feature engineering
* Text cleaning

Examples:

```python
uppercase
lowercase
square
cube
discount calculation
tax calculation
```

---

# Handling Missing Values

Real-world datasets almost always contain missing values.

Pandas represents them as:

```python
NaN
```

(Not a Number)

---

## Creating Series with Missing Values

```python
import numpy as np

s = pd.Series([10,20,np.nan,40])
```

Output:

```python
0    10
1    20
2    NaN
3    40
```

---

## Detect Missing Values

### isnull()

```python
s.isnull()
```

Output:

```python
0    False
1    False
2     True
3    False
```

---

## Remove Missing Values

### dropna()

```python
s.dropna()
```

Output:

```python
0    10
1    20
3    40
```

Notice:

```python
Index 2
```

was removed.

---

# Mixed Data Types

A Series can hold multiple types.

### Example

```python
s = pd.Series([
    10,
    "Python",
    3.14,
    True
])

print(s)
```

### Output

```python
0       10
1   Python
2     3.14
3     True
dtype: object
```

---

## Why dtype becomes Object

Since all values have different types:

```python
Integer
String
Float
Boolean
```

Pandas uses:

```python
object
```

to store them together.

---

# Real-World Applications of Series

### Stock Market

```python
Day → Stock Price
```

```python
Monday     150
Tuesday    153
Wednesday  149
```

---

### Sales Data

```python
Month → Revenue
```

```python
Jan  120000
Feb  150000
Mar  175000
```

---

### Sensor Data

```python
Time → Temperature
```

```python
10AM  32°C
11AM  34°C
12PM  36°C
```

---

# Interview Questions

### What is a Pandas Series?

A one-dimensional labeled array capable of storing any data type.

---

### Difference Between List and Series?

| List                      | Series              |
| ------------------------- | ------------------- |
| No labels                 | Has labels          |
| Basic operations          | Advanced operations |
| No built-in filtering     | Powerful filtering  |
| No missing value handling | Handles NaN         |

---

### What is NaN?

Represents missing data in Pandas.

---

### Difference Between Series and DataFrame?

| Series         | DataFrame            |
| -------------- | -------------------- |
| 1-D            | 2-D                  |
| Single Column  | Multiple Columns     |
| Building Block | Collection of Series |

---

# Key Takeaways

* Series is a one-dimensional labeled array.
* Can be created from lists, dictionaries, arrays.
* Supports custom indexing.
* Provides fast filtering and operations.
* Handles missing values efficiently.
* Supports mixed data types.
* Forms the foundation of Pandas DataFrames.
* One of the most important structures in Exploratory Data Analysis (EDA).

# Pandas DataFrame

## Introduction

A **Pandas DataFrame** is a **two-dimensional labeled data structure** that organizes data into rows and columns, similar to:

* Excel spreadsheets
* SQL tables
* Google Sheets
* Database tables

It is the most important data structure in Pandas and is used in almost every Data Science, Data Analysis, Machine Learning, and AI project.

A DataFrame can store:

* Numerical data
* Text data
* Boolean values
* Dates and timestamps
* Missing values

All within the same table.

---

## Why DataFrames Are Important

Real-world datasets rarely consist of a single column.

For example:

| Name  | Age | City     |
| ----- | --- | -------- |
| John  | 28  | New York |
| Alice | 34  | London   |
| Alex  | 42  | Paris    |

This type of structured tabular data cannot be efficiently handled using a single Series.

A DataFrame solves this problem by storing multiple Series together.

---

## Relationship Between Series and DataFrame

Think of a DataFrame as a collection of Series.

### Example

```python
Name Column
-----------
John
Alice
Alex
```

is a Series.

```python
Age Column
----------
28
34
42
```

is another Series.

Combining them creates a DataFrame.

| Name  | Age |
| ----- | --- |
| John  | 28  |
| Alice | 34  |
| Alex  | 42  |

---

# Importing Pandas

```python
import pandas as pd
```

---

# Creating a DataFrame

There are multiple ways to create DataFrames.

---

## Method 1: Dictionary of Lists

Most common method.

### Syntax

```python
pd.DataFrame(dictionary)
```

### Example

```python
data = {
    "Name": ["John","Alice","Alex"],
    "Age": [28,34,42],
    "City": ["New York","London","Paris"]
}

df = pd.DataFrame(data)

print(df)
```

### Output

```python
    Name   Age      City
0   John   28   New York
1  Alice   34     London
2   Alex   42      Paris
```

---

## Understanding the Structure

### Columns

```python
Name
Age
City
```

represent features.

### Rows

```python
John
Alice
Alex
```

represent records.

### Index

```python
0
1
2
```

represents row labels.

---

# Method 2: List of Dictionaries

Sometimes data comes row-by-row.

### Example

```python
data = [
    {"Name":"John","Age":28,"City":"New York"},
    {"Name":"Alice","Age":34,"City":"London"},
    {"Name":"Alex","Age":42,"City":"Paris"}
]

df = pd.DataFrame(data)

print(df)
```

### Output

```python
    Name   Age      City
0   John   28   New York
1  Alice   34     London
2   Alex   42      Paris
```

---

## When to Use This Method

Useful when:

* Reading JSON data
* Processing API responses
* Collecting user inputs
* Parsing web data

Because JSON naturally resembles a list of dictionaries.

---

# Creating DataFrame with Custom Index

Instead of default indexes:

```python
0
1
2
```

we can create meaningful labels.

### Example

```python
data = {
    "Name":["John","Alice","Alex"],
    "Age":[28,34,42]
}

df = pd.DataFrame(
    data,
    index=["Person1","Person2","Person3"]
)

print(df)
```

### Output

```python
         Name   Age
Person1 John   28
Person2 Alice  34
Person3 Alex   42
```

---

## Advantages

Custom indexes make datasets easier to understand.

Instead of:

```python
df.loc[1]
```

you can use:

```python
df.loc["Person2"]
```

which is more descriptive.

---

# Understanding DataFrame Components

A DataFrame consists of:

```text
Rows
Columns
Index
Values
Data Types
```

Example:

| Index | Name  | Age | City   |
| ----- | ----- | --- | ------ |
| 0     | John  | 28  | NY     |
| 1     | Alice | 34  | London |

---

# Accessing Columns

Columns are the most commonly accessed part of a DataFrame.

---

## Method 1: Square Brackets

### Example

```python
df["Name"]
```

### Output

```python
0     John
1    Alice
2     Alex
```

Notice:

The result is a **Series**, not a DataFrame.

---

## Method 2: Dot Notation

### Example

```python
df.Name
```

Output:

```python
0     John
1    Alice
2     Alex
```

---

## Which Method is Better?

Recommended:

```python
df["Name"]
```

because it works with:

* Spaces
* Special characters
* Reserved keywords

while dot notation sometimes fails.

---

# Accessing Multiple Columns

### Example

```python
df[["Name","Age"]]
```

### Output

```python
    Name   Age
0   John   28
1  Alice   34
2   Alex   42
```

Notice:

Multiple columns return a DataFrame.

---

# Accessing Rows

Pandas provides two major methods:

```python
loc
iloc
```

---

# loc (Label-Based Indexing)

Uses labels.

Think:

```python
loc = location by label
```

---

## Single Row

```python
df.loc[0]
```

Output

```python
Name        John
Age           28
City    New York
```

Returns a Series.

---

## Multiple Rows

```python
df.loc[0:1]
```

Output

```python
    Name   Age      City
0   John   28   New York
1  Alice   34     London
```

---

## Custom Index Example

```python
df.loc["Person2"]
```

returns:

```python
Name    Alice
Age        34
```

---

# iloc (Integer-Based Indexing)

Uses row position.

Think:

```python
i = integer
```

---

## First Row

```python
df.iloc[0]
```

Output

```python
Name        John
Age           28
City    New York
```

---

## First Two Rows

```python
df.iloc[0:2]
```

Output

```python
    Name   Age      City
0   John   28   New York
1  Alice   34     London
```

---

## Difference Between loc and iloc

| loc               | iloc              |
| ----------------- | ----------------- |
| Uses labels       | Uses positions    |
| loc["A"]          | iloc[0]           |
| Inclusive slicing | Exclusive slicing |

Example:

```python
df.loc[0:2]
```

includes row 2.

But:

```python
df.iloc[0:2]
```

excludes row 2.

---

# Adding New Columns

One of the most common DataFrame operations.

---

## Example

```python
df["Country"] = [
    "USA",
    "UK",
    "France"
]
```

Output

| Name  | Age | City   | Country |
| ----- | --- | ------ | ------- |
| John  | 28  | NY     | USA     |
| Alice | 34  | London | UK      |
| Alex  | 42  | Paris  | France  |

---

## Why Add Columns?

During EDA we often create:

* New features
* Derived values
* Calculated metrics
* Categories

Example:

```python
Salary Category
Tax Amount
Profit Margin
Age Group
```

---

# DataFrame Summary Functions

Before analysis we must understand the dataset.

Two important methods:

```python
describe()
info()
```

---

# describe()

Provides statistical summary.

### Example

```python
df.describe()
```

Output

```python
             Age
count    3.000000
mean    34.666667
std      7.023769
min     28.000000
25%     31.000000
50%     34.000000
75%     38.000000
max     42.000000
```

---

## Meaning of Each Statistic

### count

Number of values.

### mean

Average.

### std

Standard deviation.

### min

Smallest value.

### 25%

First Quartile (Q1).

### 50%

Median.

### 75%

Third Quartile (Q3).

### max

Largest value.

---

# info()

Provides structural information.

### Example

```python
df.info()
```

Output

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries
Data columns (total 3 columns):

Name    3 non-null object
Age     3 non-null int64
City    3 non-null object
```

---

## Why info() is Important

Shows:

* Number of rows
* Number of columns
* Missing values
* Memory usage
* Data types

Used heavily in EDA.

---

# Applying Functions

We can transform entire columns using apply().

---

## Example

```python
df["Age"] = df["Age"].apply(
    lambda x: x + 1
)
```

Output

```python
29
35
43
```

---

## What Happened?

Each value was incremented by 1.

```python
28 → 29
34 → 35
42 → 43
```

---

## Common Uses

```python
Currency Conversion
Age Group Creation
Tax Calculation
Discount Calculation
Text Cleaning
```

---

# Handling Missing Values

Real-world data is rarely perfect.

Example:

| Name  | Age |
| ----- | --- |
| John  | 28  |
| Alice | NaN |
| Alex  | 42  |

---

# Detect Missing Values

## isnull()

```python
df.isnull()
```

Output

```python
      Name    Age
0    False  False
1    False   True
2    False  False
```

---

# Counting Missing Values

```python
df.isnull().sum()
```

Output

```python
Name    0
Age     1
```

---

# Removing Missing Values

## dropna()

```python
df.dropna()
```

Output

```python
Name    Age
John     28
Alex     42
```

The row containing NaN is removed.

---

# Example Workflow in EDA

Suppose a CSV file is loaded.

```python
df = pd.read_csv("employees.csv")
```

Typical steps:

```python
df.head()
df.info()
df.describe()
df.isnull().sum()
df.dropna()
```

This is the starting point of almost every data analysis project.

---

# Real-World Applications

### Employee Database

| Employee | Salary | Department |
| -------- | ------ | ---------- |
| John     | 50000  | HR         |
| Alice    | 70000  | IT         |

---

### Student Records

| Student | Marks | Grade |
| ------- | ----- | ----- |
| Sam     | 85    | A     |
| Tom     | 70    | B     |

---

### Sales Dataset

| Product | Price | Quantity |
| ------- | ----- | -------- |
| Laptop  | 60000 | 5        |
| Phone   | 30000 | 10       |

---

# Interview Questions

### What is a DataFrame?

A two-dimensional labeled tabular data structure in Pandas.

---

### Difference Between Series and DataFrame?

| Series          | DataFrame        |
| --------------- | ---------------- |
| One-dimensional | Two-dimensional  |
| Single column   | Multiple columns |
| Simpler         | More powerful    |

---

### What does describe() do?

Returns statistical summary of numerical columns.

---

### What does info() do?

Returns structural information such as:

* rows
* columns
* dtypes
* non-null values

---

### Difference Between loc and iloc?

| loc            | iloc             |
| -------------- | ---------------- |
| Label-based    | Position-based   |
| Uses row names | Uses row numbers |

---

# Key Takeaways

* DataFrame is the core structure of Pandas.
* Organizes data into rows and columns.
* Can be created from dictionaries, lists, JSON-like structures.
* Supports custom indexes.
* Columns can be accessed using brackets or dot notation.
* Rows can be accessed using loc and iloc.
* New columns can be added easily.
* describe() provides statistical summaries.
* info() provides structural summaries.
* Handles missing values efficiently.
* Forms the foundation of Exploratory Data Analysis and Machine Learning workflows.

# Indexing a DataFrame

## Introduction

Indexing is one of the most important concepts in Pandas because it allows us to:

* Access specific rows
* Access specific columns
* Extract subsets of data
* Filter records
* Retrieve data efficiently

Without indexing, working with large datasets becomes extremely difficult.

Consider the DataFrame below:

| Index | Name  | Age | City     |
| ----- | ----- | --- | -------- |
| A     | John  | 28  | New York |
| B     | Alice | 34  | London   |
| C     | Alex  | 42  | Paris    |
| D     | Sam   | 30  | Tokyo    |

This DataFrame will be used throughout this chapter.

---

# Creating a Sample DataFrame

```python
import pandas as pd

data = {
    "Name":["John","Alice","Alex","Sam"],
    "Age":[28,34,42,30],
    "City":["New York","London","Paris","Tokyo"]
}

df = pd.DataFrame(
    data,
    index=["A","B","C","D"]
)

print(df)
```

Output:

```text
    Name   Age      City
A   John   28   New York
B  Alice   34     London
C   Alex   42      Paris
D    Sam   30      Tokyo
```

---

# Types of Indexing in Pandas

Pandas supports multiple indexing methods:

```text
1. Column Indexing
2. Label-Based Indexing (loc)
3. Integer-Based Indexing (iloc)
4. Boolean Indexing
5. Conditional Indexing
```

Each method serves a different purpose.

---

# Column Indexing

Column indexing is used to retrieve one or more columns.

---

## Selecting a Single Column

### Syntax

```python
df["column_name"]
```

### Example

```python
df["Name"]
```

Output:

```text
A     John
B    Alice
C     Alex
D      Sam
Name: Name, dtype: object
```

---

### What is Returned?

A single column returns a:

```text
Pandas Series
```

because a column itself is essentially a Series.

---

## Selecting Multiple Columns

### Syntax

```python
df[["column1","column2"]]
```

Notice:

```python
[["Name","Age"]]
```

Double brackets are required.

---

### Example

```python
df[["Name","Age"]]
```

Output:

```text
    Name   Age
A   John   28
B  Alice   34
C   Alex   42
D    Sam   30
```

---

### What is Returned?

Multiple columns return a:

```text
DataFrame
```

because more than one column is selected.

---

# Label-Based Indexing (loc)

One of the most powerful indexing techniques.

---

## What is loc?

`loc` stands for:

```text
Location by Label
```

It retrieves data using:

* Row labels
* Column labels

---

## Syntax

```python
df.loc[row_label]
```

---

## Selecting a Single Row

### Example

```python
df.loc["B"]
```

Output:

```text
Name    Alice
Age        34
City    London
```

---

### Explanation

The label:

```python
"B"
```

corresponds to:

```text
Alice
34
London
```

Therefore the entire row is returned.

---

## Selecting Multiple Rows

### Example

```python
df.loc["A":"C"]
```

Output:

```text
    Name   Age      City
A   John   28   New York
B  Alice   34     London
C   Alex   42      Paris
```

---

### Important Note

Unlike Python slicing:

```python
0:3
```

Pandas `loc` is:

```text
Inclusive
```

Meaning:

```python
"A":"C"
```

includes:

```text
A
B
C
```

---

# Selecting Rows and Columns Together

### Syntax

```python
df.loc[
    row_selection,
    column_selection
]
```

---

### Example

```python
df.loc[
    "A":"C",
    ["Name","Age"]
]
```

Output:

```text
    Name   Age
A   John   28
B  Alice   34
C   Alex   42
```

---

### Why Use This?

Allows precise extraction of data.

Instead of retrieving entire rows:

```python
df.loc["A":"C"]
```

you can retrieve only the required columns.

---

# Integer-Based Indexing (iloc)

Sometimes labels are unknown or unimportant.

In such cases, use:

```text
iloc
```

---

## What is iloc?

`iloc` stands for:

```text
Integer Location
```

It accesses data using numerical positions.

---

### Row Positions

```text
A → 0
B → 1
C → 2
D → 3
```

---

## Selecting a Single Row

### Example

```python
df.iloc[1]
```

Output:

```text
Name    Alice
Age        34
City    London
```

---

Because:

```text
Position 1 = Row B
```

---

## Selecting Multiple Rows

### Example

```python
df.iloc[0:3]
```

Output:

```text
    Name   Age      City
A   John   28   New York
B  Alice   34     London
C   Alex   42      Paris
```

---

### Important Difference

`iloc` follows normal Python slicing.

```python
0:3
```

returns:

```text
0
1
2
```

and excludes:

```text
3
```

---

# Selecting Specific Rows and Columns

### Example

```python
df.iloc[
    0:3,
    0:2
]
```

Output:

```text
    Name   Age
A   John   28
B  Alice   34
C   Alex   42
```

---

### Understanding Positions

Rows:

```text
0
1
2
```

Columns:

```text
0 → Name
1 → Age
```

Therefore only Name and Age are selected.

---

# loc vs iloc

This is a common interview question.

| loc               | iloc              |
| ----------------- | ----------------- |
| Uses labels       | Uses positions    |
| Label-based       | Integer-based     |
| loc["B"]          | iloc[1]           |
| Inclusive slicing | Exclusive slicing |

---

### Example

#### loc

```python
df.loc["A":"C"]
```

Returns:

```text
A
B
C
```

---

#### iloc

```python
df.iloc[0:3]
```

Returns:

```text
0
1
2
```

Equivalent rows:

```text
A
B
C
```

but slicing rules differ internally.

---

# Boolean Indexing

Boolean indexing is one of the most powerful features in Pandas.

Instead of selecting rows by label or position, we select rows based on conditions.

---

## Example

```python
df["Age"] > 30
```

Output:

```text
A    False
B     True
C     True
D    False
```

This creates a Boolean mask.

---

### Applying the Mask

```python
df[df["Age"] > 30]
```

Output:

```text
    Name   Age    City
B  Alice   34  London
C   Alex   42   Paris
```

---

### What Happened?

Step 1:

```python
df["Age"] > 30
```

creates:

```text
False
True
True
False
```

Step 2:

Rows with:

```text
True
```

are returned.

---

# Conditional Indexing

Boolean indexing becomes more useful when combined with conditions.

---

## Example: City Equals London

```python
df[df["City"] == "London"]
```

Output:

```text
    Name   Age    City
B  Alice   34  London
```

---

## Example: Age Greater Than 35

```python
df[df["Age"] > 35]
```

Output:

```text
    Name   Age   City
C   Alex   42  Paris
```

---

# Combining Conditions

---

## AND Condition

Use:

```python
&
```

### Example

```python
df[
    (df["Age"] > 30)
    &
    (df["City"] == "London")
]
```

Output:

```text
    Name   Age    City
B  Alice   34  London
```

---

## OR Condition

Use:

```python
|
```

### Example

```python
df[
    (df["Age"] > 35)
    |
    (df["City"] == "Tokyo")
]
```

Output:

```text
    Name   Age   City
C   Alex   42  Paris
D    Sam   30  Tokyo
```

---

# Selecting Specific Columns After Filtering

Example:

Retrieve only names of people living in London.

```python
df.loc[
    df["City"] == "London",
    "Name"
]
```

Output:

```text
B    Alice
```

---

### Why This Is Useful

Suppose a dataset has:

```text
100 columns
```

You may only need:

```text
Name
Salary
Department
```

Filtering with column selection makes analysis faster and cleaner.

---

# Real-World Example

Employee Dataset:

| Employee | Salary | Department |
| -------- | ------ | ---------- |
| John     | 50000  | HR         |
| Alice    | 80000  | IT         |
| Alex     | 90000  | IT         |

Find IT employees:

```python
df[df["Department"] == "IT"]
```

Find employees earning above 70000:

```python
df[df["Salary"] > 70000]
```

Find IT employees earning above 70000:

```python
df[
    (df["Department"] == "IT")
    &
    (df["Salary"] > 70000)
]
```

---

# Common Mistakes

---

## Mistake 1

Using `and`

```python
df[
    (df["Age"] > 30)
    and
    (df["Salary"] > 50000)
]
```

❌ Wrong

---

### Correct

```python
df[
    (df["Age"] > 30)
    &
    (df["Salary"] > 50000)
]
```

✅ Correct

---

## Mistake 2

Forgetting Parentheses

```python
df[
    df["Age"] > 30
    &
    df["Salary"] > 50000
]
```

❌ Wrong

---

### Correct

```python
df[
    (df["Age"] > 30)
    &
    (df["Salary"] > 50000)
]
```

✅ Correct

---

# Interview Questions

### What is DataFrame Indexing?

The process of accessing rows, columns, or subsets of data from a DataFrame.

---

### Difference Between loc and iloc?

| loc         | iloc           |
| ----------- | -------------- |
| Label-based | Position-based |
| Uses names  | Uses numbers   |

---

### What is Boolean Indexing?

Selecting rows based on True/False conditions.

---

### What is a Boolean Mask?

A Series of:

```text
True
False
```

values used for filtering.

---

### Which Indexing Method is Used Most in EDA?

Usually:

```python
loc
Boolean Indexing
```

because most analysis requires condition-based filtering.

---

# Key Takeaways

* Indexing is used to access and manipulate DataFrame data.
* Single column selection returns a Series.
* Multiple column selection returns a DataFrame.
* `loc` uses labels.
* `iloc` uses numerical positions.
* `loc` slicing is inclusive.
* `iloc` slicing is exclusive.
* Boolean indexing enables condition-based filtering.
* Conditions can be combined using `&` and `|`.
* Indexing is one of the most frequently used Pandas skills in Exploratory Data Analysis.

# Selection in a DataFrame

## Introduction

After learning how indexing works in Pandas, the next important skill is **selection**.

Selection refers to extracting:

* Specific columns
* Specific rows
* Specific subsets
* Filtered records
* Random samples
* Top or bottom records

Selection is one of the most frequently used operations during:

* Exploratory Data Analysis (EDA)
* Data Cleaning
* Machine Learning
* Reporting

A DataFrame may contain hundreds of columns and millions of rows. Selection allows us to retrieve only the data we need.

---

# Creating a Sample DataFrame

Throughout this chapter we will use the following DataFrame:

```python
import pandas as pd

data = {
    "Name":["Alice","Bob","Charlie","David","Emma"],
    "Age":[25,35,42,29,38],
    "City":["New York","London","Tokyo","Paris","London"],
    "Salary":[50000,70000,90000,60000,80000]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
      Name  Age      City  Salary
0    Alice   25  New York   50000
1      Bob   35    London   70000
2  Charlie   42     Tokyo   90000
3    David   29     Paris   60000
4     Emma   38    London   80000
```

---

# Types of Selection

Pandas provides multiple ways to select data:

```text
1. Single Column Selection
2. Multiple Column Selection
3. Row Selection
4. Row and Column Subset Selection
5. Boolean Selection
6. Query Selection
7. Membership Selection (isin)
8. Random Sampling
9. Largest and Smallest Values
```

---

# Selecting a Single Column

A single column can be selected using either:

### Method 1

```python
df["Age"]
```

### Method 2

```python
df.Age
```

---

## Output

```text
0    25
1    35
2    42
3    29
4    38
Name: Age
```

---

## Return Type

Selecting a single column returns:

```text
Pandas Series
```

because a column itself is a Series.

---

# Bracket Notation vs Dot Notation

Both work:

```python
df["Age"]
```

```python
df.Age
```

---

### Recommended

Use:

```python
df["Age"]
```

because:

* Works with spaces
* Works with special characters
* Safer and more consistent

---

# Selecting Multiple Columns

Often we need more than one column.

---

## Method 1

```python
df[["Name","Salary"]]
```

---

## Output

```text
      Name  Salary
0    Alice   50000
1      Bob   70000
2  Charlie   90000
3    David   60000
4     Emma   80000
```

---

### Important

Notice the double brackets:

```python
[["Name","Salary"]]
```

Why?

Outer brackets:

```text
DataFrame Selection
```

Inner brackets:

```text
List of Column Names
```

---

## Return Type

Selecting multiple columns returns:

```text
DataFrame
```

---

# Selecting Columns with loc

Another approach:

```python
df.loc[:, ["Name","Salary"]]
```

---

### Explanation

```python
:
```

means:

```text
All Rows
```

while

```python
["Name","Salary"]
```

means:

```text
Selected Columns
```

---

# Selecting Rows with loc

The `loc` method uses labels.

---

## Selecting One Row

```python
df.loc[2]
```

Output:

```text
Name      Charlie
Age            42
City        Tokyo
Salary      90000
```

---

## Selecting Multiple Rows

```python
df.loc[1:3]
```

Output:

```text
    Name  Age    City  Salary
1    Bob   35  London   70000
2 Charlie 42   Tokyo   90000
3  David 29   Paris   60000
```

---

### Important

`loc` slicing is:

```text
Inclusive
```

So:

```python
1:3
```

includes:

```text
1
2
3
```

---

# Selecting Rows with iloc

`iloc` uses numerical positions.

---

## Selecting One Row

```python
df.iloc[2]
```

Output:

```text
Name      Charlie
Age            42
City        Tokyo
Salary      90000
```

---

## Selecting Multiple Rows

```python
df.iloc[1:4]
```

Output:

```text
    Name  Age    City  Salary
1    Bob   35  London   70000
2 Charlie 42   Tokyo   90000
3  David 29   Paris   60000
```

---

### Important

`iloc` slicing follows Python rules:

```python
1:4
```

returns:

```text
1
2
3
```

and excludes:

```text
4
```

---

# Subset Selection

Often we need specific rows and columns together.

---

## Using loc

```python
df.loc[
    1:3,
    ["Name","Salary"]
]
```

Output:

```text
      Name  Salary
1      Bob   70000
2  Charlie   90000
3    David   60000
```

---

## Using iloc

```python
df.iloc[
    1:4,
    [0,3]
]
```

Output:

```text
      Name  Salary
1      Bob   70000
2  Charlie   90000
3    David   60000
```

---

## Why Use Subset Selection?

Instead of retrieving:

```text
All rows
All columns
```

we retrieve:

```text
Only required data
```

which improves:

* Performance
* Readability
* Analysis speed

---

# Boolean Selection

One of the most powerful selection methods.

---

## Example

Select people older than 35.

```python
df[df["Age"] > 35]
```

Output:

```text
      Name  Age    City  Salary
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

## How It Works

Step 1

```python
df["Age"] > 35
```

returns:

```text
False
False
True
False
True
```

Step 2

Rows with:

```text
True
```

are selected.

---

# Selecting Specific Columns After Filtering

Example:

Select only Name and Salary where Salary > 60000.

```python
df.loc[
    df["Salary"] > 60000,
    ["Name","Salary"]
]
```

Output:

```text
      Name  Salary
1      Bob   70000
2  Charlie   90000
4     Emma   80000
```

---

# Multiple Conditions

---

## AND Condition

```python
df[
    (df["Age"] > 35)
    &
    (df["Salary"] > 70000)
]
```

Output:

```text
      Name  Age   City  Salary
2  Charlie  42  Tokyo   90000
4     Emma  38 London   80000
```

---

## OR Condition

```python
df[
    (df["City"] == "London")
    |
    (df["Salary"] > 85000)
]
```

Output:

```text
      Name  Age    City  Salary
1      Bob   35  London   70000
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# Query Method

The `query()` method provides a cleaner syntax for filtering.

---

## Example

```python
df.query(
    "Age > 35 and City != 'Tokyo'"
)
```

Output:

```text
   Name  Age    City  Salary
4  Emma   38  London   80000
```

---

## Advantages

For complex conditions:

```python
df.query(...)
```

is often easier to read than:

```python
df[
    (...)
    &
    (...)
]
```

---

# Membership Selection with isin()

Sometimes we need to filter multiple values.

---

## Example

Select people from London or Tokyo.

```python
df[
    df["City"].isin(
        ["London","Tokyo"]
    )
]
```

Output:

```text
      Name  Age    City  Salary
1      Bob   35  London   70000
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

## Why Use isin()?

Instead of writing:

```python
(df["City"]=="London")
|
(df["City"]=="Tokyo")
```

we simply write:

```python
df["City"].isin(
    ["London","Tokyo"]
)
```

which is cleaner.

---

# Random Sampling

Useful when working with huge datasets.

---

## Selecting Random Rows

```python
df.sample(n=2)
```

Output (random):

```text
    Name  Age    City  Salary
0  Alice  25  New York 50000
4   Emma  38  London   80000
```

---

### Each Execution Gives Different Results

Running again may return different rows.

---

# Sampling by Fraction

Instead of fixed rows:

```python
df.sample(frac=0.4)
```

returns:

```text
40% of dataset
```

randomly selected.

---

# Selecting Largest Values

Often used in business analytics.

---

## Top Salaries

```python
df.nlargest(
    2,
    "Salary"
)
```

Output:

```text
      Name  Salary
2  Charlie  90000
4     Emma  80000
```

---

### Use Cases

Finding:

* Top customers
* Top products
* Top performers
* Highest revenue

---

# Selecting Smallest Values

---

## Youngest Employees

```python
df.nsmallest(
    2,
    "Age"
)
```

Output:

```text
    Name  Age
0  Alice 25
3  David 29
```

---

### Use Cases

Finding:

* Lowest sales
* Lowest revenue
* Youngest employees
* Cheapest products

---

# Advanced Selection Using eval()

The `eval()` method evaluates expressions directly.

---

## Example

```python
df.eval(
    "Salary > 70000"
)
```

Output:

```text
0 False
1 False
2 True
3 False
4 True
```

---

## Creating New Columns

```python
df["HighSalary"] = df.eval(
    "Salary > 70000"
)
```

Output:

```text
      Name  Salary  HighSalary
0    Alice  50000     False
1      Bob  70000     False
2  Charlie  90000      True
3    David  60000     False
4     Emma  80000      True
```

---

# Real-World EDA Examples

---

## Find High Income Customers

```python
df[df["Salary"] > 75000]
```

---

## Find Employees in London

```python
df[df["City"] == "London"]
```

---

## Find Top 5 Earners

```python
df.nlargest(
    5,
    "Salary"
)
```

---

## Create Random Testing Dataset

```python
df.sample(
    frac=0.2
)
```

---

# Common Mistakes

## Forgetting Double Brackets

Wrong:

```python
df["Name","Salary"]
```

❌

Correct:

```python
df[["Name","Salary"]]
```

✅

---

## Using and Instead of &

Wrong:

```python
(df["Age"] > 35)
and
(df["Salary"] > 70000)
```

❌

Correct:

```python
(df["Age"] > 35)
&
(df["Salary"] > 70000)
```

✅

---

## Missing Parentheses

Wrong:

```python
df["Age"] > 35 &
df["Salary"] > 70000
```

❌

Correct:

```python
(df["Age"] > 35)
&
(df["Salary"] > 70000)
```

✅

---

# Interview Questions

### Difference Between loc and iloc?

| loc         | iloc           |
| ----------- | -------------- |
| Label-based | Position-based |
| Uses names  | Uses numbers   |

---

### Difference Between Selection and Filtering?

Selection:

```text
Choosing rows or columns
```

Filtering:

```text
Selecting rows based on conditions
```

---

### What Does query() Do?

Allows SQL-like filtering using strings.

---

### What Does isin() Do?

Checks whether values belong to a specified list.

---

### What Does sample() Do?

Returns random records from a DataFrame.

---

# Key Takeaways

* Selection is used to retrieve specific data from a DataFrame.
* Single column selection returns a Series.
* Multiple column selection returns a DataFrame.
* `loc` uses labels.
* `iloc` uses positions.
* Boolean selection enables condition-based retrieval.
* `query()` provides readable filtering syntax.
* `isin()` simplifies multi-value filtering.
* `sample()` retrieves random records.
* `nlargest()` and `nsmallest()` quickly identify top and bottom values.
* Selection is one of the most important skills in Exploratory Data Analysis (EDA).

# Filtering a DataFrame

## Introduction

Filtering is one of the most important operations in Pandas and Data Analysis.

While selection helps us retrieve rows and columns, filtering allows us to retrieve only the rows that satisfy specific conditions.

In real-world datasets, we rarely analyze all records. Instead, we filter data to answer questions such as:

* Which customers spent more than ₹10,000?
* Which employees are older than 40?
* Which products belong to a specific category?
* Which records contain missing values?
* Which transactions happened during a specific date range?

Filtering helps reduce large datasets into meaningful subsets.

---

# Creating a Sample DataFrame

Throughout this chapter, we will use the following DataFrame:

```python
import pandas as pd

data = {
    "Name":["Alice","Bob","Charlie","David","Emma"],
    "Age":[25,35,42,29,38],
    "City":["New York","London","Tokyo","Paris","London"],
    "Salary":[50000,70000,90000,60000,80000]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
      Name  Age      City  Salary
0    Alice   25  New York   50000
1      Bob   35    London   70000
2  Charlie   42     Tokyo   90000
3    David   29     Paris   60000
4     Emma   38    London   80000
```

---

# What is Filtering?

Filtering means:

```text
Keeping only rows that satisfy a condition
```

Example:

```text
Age > 35
```

Only rows where age is greater than 35 will be returned.

---

# Boolean Filtering

The most common filtering method in Pandas is Boolean Filtering.

A condition returns:

```text
True
or
False
```

Rows with:

```text
True
```

are selected.

Rows with:

```text
False
```

are removed.

---

# Single Condition Filtering

## Example

Select people older than 35.

```python
df[df["Age"] > 35]
```

---

## Step 1

Pandas evaluates:

```python
df["Age"] > 35
```

Output:

```text
0    False
1    False
2     True
3    False
4     True
```

---

## Step 2

Rows with True are selected.

Output:

```text
      Name  Age    City  Salary
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# Comparison Operators Used in Filtering

| Operator | Meaning               |
| -------- | --------------------- |
| >        | Greater than          |
| <        | Less than             |
| >=       | Greater than or equal |
| <=       | Less than or equal    |
| ==       | Equal                 |
| !=       | Not equal             |

---

## Examples

### Greater Than

```python
df[df["Salary"] > 70000]
```

---

### Less Than

```python
df[df["Age"] < 30]
```

---

### Equal To

```python
df[df["City"] == "London"]
```

---

### Not Equal To

```python
df[df["City"] != "London"]
```

---

# Filtering with Multiple Conditions

Real-world analysis often requires multiple conditions.

Pandas supports:

```text
AND
OR
NOT
```

operations.

---

# AND Condition

Use:

```python
&
```

Both conditions must be True.

---

## Example

Age greater than 35 AND salary greater than 70000.

```python
df[
    (df["Age"] > 35)
    &
    (df["Salary"] > 70000)
]
```

Output:

```text
      Name  Age    City  Salary
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

## Important Rule

Every condition must be enclosed inside parentheses.

Correct:

```python
(df["Age"] > 35)
&
(df["Salary"] > 70000)
```

Wrong:

```python
df["Age"] > 35 &
df["Salary"] > 70000
```

---

# OR Condition

Use:

```python
|
```

At least one condition must be True.

---

## Example

People from London OR Salary greater than 85000.

```python
df[
    (df["City"] == "London")
    |
    (df["Salary"] > 85000)
]
```

Output:

```text
      Name  Age    City  Salary
1      Bob   35  London   70000
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# NOT Condition

Use:

```python
~
```

NOT reverses True and False.

---

## Example

People NOT living in London.

```python
df[
    ~(df["City"] == "London")
]
```

Output:

```text
      Name  Age      City  Salary
0    Alice   25  New York   50000
2  Charlie   42     Tokyo   90000
3    David   29     Paris   60000
```

---

# Filtering Using isin()

Suppose we want multiple specific values.

Instead of writing:

```python
(df["City"]=="London")
|
(df["City"]=="Tokyo")
```

we use:

```python
df["City"].isin(
    ["London","Tokyo"]
)
```

---

## Example

```python
df[
    df["City"].isin(
        ["London","Tokyo"]
    )
]
```

Output:

```text
      Name  Age    City  Salary
1      Bob   35  London   70000
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# Why isin() is Useful

Without isin():

```python
(city == London)
|
(city == Tokyo)
|
(city == Paris)
|
(city == Delhi)
```

With isin():

```python
city.isin(
    ["London","Tokyo","Paris","Delhi"]
)
```

Cleaner and faster.

---

# String-Based Filtering

Pandas provides string methods through:

```python
.str
```

accessor.

---

# startswith()

Filter names beginning with A.

```python
df[
    df["Name"].str.startswith("A")
]
```

Output:

```text
    Name  Age      City  Salary
0  Alice   25  New York   50000
```

---

# endswith()

```python
df[
    df["Name"].str.endswith("e")
]
```

Output:

```text
      Name
0    Alice
2  Charlie
```

---

# contains()

Find names containing "ar".

```python
df[
    df["Name"].str.contains("ar")
]
```

Output:

```text
      Name
2  Charlie
```

---

# Query Method

The query() method provides a SQL-like syntax.

---

## Example

```python
df.query(
    "Age > 35"
)
```

Output:

```text
      Name  Age    City  Salary
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# Multiple Conditions with Query

```python
df.query(
    "Age > 35 and Salary > 70000"
)
```

Output:

```text
      Name  Age    City  Salary
2  Charlie   42   Tokyo   90000
4     Emma   38  London   80000
```

---

# Advantages of query()

Traditional filtering:

```python
df[
    (df["Age"] > 35)
    &
    (df["Salary"] > 70000)
]
```

Query:

```python
df.query(
    "Age > 35 and Salary > 70000"
)
```

More readable.

---

# Filtering with loc

Filtering can be combined with column selection.

---

## Example

Select Name and Salary where Salary > 70000.

```python
df.loc[
    df["Salary"] > 70000,
    ["Name","Salary"]
]
```

Output:

```text
      Name  Salary
2  Charlie   90000
4     Emma   80000
```

---

# Filtering Missing Values

Missing values are represented by:

```python
NaN
```

(Not a Number)

---

## Example Dataset

```python
import numpy as np

df = pd.DataFrame({
    "Name":["Alice","Bob","Charlie"],
    "Salary":[50000,np.nan,90000]
})
```

---

# Detect Missing Values

```python
df.isnull()
```

Output:

```text
    Name  Salary
0  False   False
1  False    True
2  False   False
```

---

# Remove Missing Values

```python
df.dropna()
```

Output:

```text
      Name  Salary
0    Alice 50000
2  Charlie 90000
```

---

# Remove Missing Values from Specific Columns

```python
df.dropna(
    subset=["Salary"]
)
```

Only checks Salary column.

---

# Filtering with between()

Useful for ranges.

---

## Example

Find people aged between 30 and 40.

```python
df[
    df["Age"].between(30,40)
]
```

Output:

```text
    Name  Age    City  Salary
1    Bob   35  London   70000
4   Emma   38  London   80000
```

---

## Equivalent Expression

```python
(df["Age"] >= 30)
&
(df["Age"] <= 40)
```

but `between()` is cleaner.

---

# Complex Conditions with eval()

The eval() method evaluates expressions efficiently.

---

## Example

```python
df.eval(
    "(Age > 35) & (Salary > 70000)"
)
```

Output:

```text
0    False
1    False
2     True
3    False
4     True
```

---

# Creating New Boolean Columns

```python
df["HighSalary"] = df.eval(
    "Salary > 70000"
)
```

Output:

```text
      Name  Salary  HighSalary
0    Alice   50000       False
1      Bob   70000       False
2  Charlie   90000        True
3    David   60000       False
4     Emma   80000        True
```

---

# Real-World EDA Filtering Examples

---

## High Income Customers

```python
customers[
    customers["Income"] > 100000
]
```

---

## Failed Students

```python
students[
    students["Marks"] < 40
]
```

---

## Products from Specific Categories

```python
products[
    products["Category"].isin(
        ["Electronics","Books"]
    )
]
```

---

## Transactions Above ₹50,000

```python
transactions[
    transactions["Amount"] > 50000
]
```

---

## Employees in HR Department

```python
employees[
    employees["Department"] == "HR"
]
```

---

# Common Mistakes

## Using and Instead of &

Wrong:

```python
(df["Age"] > 35)
and
(df["Salary"] > 70000)
```

❌

Correct:

```python
(df["Age"] > 35)
&
(df["Salary"] > 70000)
```

✅

---

## Using or Instead of |

Wrong:

```python
condition1 or condition2
```

❌

Correct:

```python
condition1 | condition2
```

✅

---

## Forgetting Parentheses

Wrong:

```python
df["Age"] > 35 &
df["Salary"] > 70000
```

❌

Correct:

```python
(df["Age"] > 35)
&
(df["Salary"] > 70000)
```

✅

---

# Interview Questions

### What is Filtering?

Selecting rows that satisfy a condition.

---

### Difference Between Selection and Filtering?

Selection:

```text
Choosing rows or columns
```

Filtering:

```text
Choosing rows based on conditions
```

---

### Why Use isin()?

To check membership in multiple values.

---

### Why Use query()?

Cleaner syntax for complex filters.

---

### What Does between() Do?

Checks whether values lie within a specified range.

---

### What Does dropna() Do?

Removes rows containing missing values.

---

# Key Takeaways

* Filtering extracts rows satisfying specific conditions.
* Boolean indexing is the foundation of filtering.
* Use `&`, `|`, and `~` for AND, OR, and NOT operations.
* `isin()` simplifies multi-value filtering.
* String methods enable text-based filtering.
* `query()` provides SQL-like filtering syntax.
* `between()` simplifies range filtering.
* `dropna()` helps remove incomplete records.
* Filtering is one of the most important operations in Exploratory Data Analysis (EDA).
* Almost every real-world data analysis project relies heavily on filtering.

# Operations on a DataFrame

## Introduction

Once data is loaded into a Pandas DataFrame, we often need to perform operations such as:

* Mathematical calculations
* Data transformations
* Creating new columns
* Applying custom functions
* Grouping and aggregating data
* Combining multiple DataFrames

These operations form the backbone of data analysis and are heavily used in:

* Exploratory Data Analysis (EDA)
* Data Cleaning
* Feature Engineering
* Machine Learning
* Business Analytics

Pandas provides powerful built-in functions to perform these operations efficiently.

---

# Sample DataFrames

Throughout this chapter, we will use the following DataFrames.

```python
import pandas as pd

df1 = pd.DataFrame({
    "A":[1,2,3],
    "B":[4,5,6]
})

df2 = pd.DataFrame({
    "A":[10,20,30],
    "B":[40,50,60]
})

print(df1)

print(df2)
```

Output:

```text
df1

   A  B
0  1  4
1  2  5
2  3  6

df2

    A   B
0  10  40
1  20  50
2  30  60
```

---

# Types of DataFrame Operations

Pandas supports:

```text
1. Arithmetic Operations
2. Scalar Operations
3. Applying Functions
4. Element-wise Operations
5. Grouping
6. Aggregation
7. Merging
8. Joining
```

---

# Arithmetic Operations Between DataFrames

DataFrames can be added, subtracted, multiplied, and divided.

Pandas performs these operations element-by-element.

---

## Addition

```python
df1 + df2
```

Output:

```text
    A   B
0  11  44
1  22  55
2  33  66
```

---

## How Addition Works

Pandas matches:

* Rows using indexes
* Columns using column names

Then performs:

```text
1 + 10 = 11
4 + 40 = 44

2 + 20 = 22
5 + 50 = 55

3 + 30 = 33
6 + 60 = 66
```

---

# Subtraction

```python
df2 - df1
```

Output:

```text
    A   B
0   9  36
1  18  45
2  27  54
```

---

# Multiplication

```python
df1 * df2
```

Output:

```text
    A    B
0  10  160
1  40  250
2  90  360
```

---

# Division

```python
df2 / df1
```

Output:

```text
      A     B
0 10.0 10.00
1 10.0 10.00
2 10.0 10.00
```

---

# Alignment Behavior

One powerful feature of Pandas is automatic alignment.

Example:

```python
df1 = pd.DataFrame({
    "A":[1,2]
})

df2 = pd.DataFrame({
    "B":[10,20]
})
```

Adding:

```python
df1 + df2
```

Output:

```text
    A   B
0 NaN NaN
1 NaN NaN
```

---

### Why?

Because:

```text
Column A does not exist in df2
Column B does not exist in df1
```

Pandas aligns labels before calculations.

---

# Scalar Operations

A scalar is a single value.

Examples:

```text
10
5
100
0.5
```

---

## Multiply Entire DataFrame

```python
df1 * 2
```

Output:

```text
   A   B
0  2   8
1  4  10
2  6  12
```

---

## Add Constant

```python
df1 + 5
```

Output:

```text
   A   B
0  6   9
1  7  10
2  8  11
```

---

## Divide Entire DataFrame

```python
df1 / 2
```

Output:

```text
     A    B
0  0.5  2.0
1  1.0  2.5
2  1.5  3.0
```

---

# Why Scalar Operations Matter

Used for:

* Normalization
* Scaling
* Currency conversion
* Unit conversion
* Feature engineering

Example:

```python
salary / 1000
```

Converts:

```text
₹50000 → 50
₹70000 → 70
```

---

# Applying Functions to Columns

One of the most useful Pandas capabilities.

---

## Example

```python
df1["C"] = df1["A"].apply(
    lambda x: x**2
)
```

Output:

```text
   A  B  C
0  1  4  1
1  2  5  4
2  3  6  9
```

---

## What Happened?

For each value:

```text
1² = 1
2² = 4
3² = 9
```

Results stored in new column C.

---

# Using Custom Functions

Instead of lambda:

```python
def square(x):
    return x*x
```

Apply:

```python
df1["A"].apply(square)
```

Output:

```text
0    1
1    4
2    9
```

---

# Why Apply Functions?

Used for:

* Data transformations
* Feature creation
* Cleaning text
* Formatting values
* Mathematical calculations

---

# Element-Wise Operations

Sometimes we want to apply a function to every value in the DataFrame.

For this purpose:

```python
applymap()
```

is used.

---

## Example

```python
df1.applymap(
    lambda x: x * 10
)
```

Output:

```text
    A   B
0  10  40
1  20  50
2  30  60
```

---

## How It Works

Every element is processed.

```text
1 → 10
2 → 20
3 → 30
4 → 40
5 → 50
6 → 60
```

---

# Difference Between apply() and applymap()

| Method     | Works On      |
| ---------- | ------------- |
| apply()    | Row or Column |
| applymap() | Every Element |

---

## Example

```python
df["Age"].apply(...)
```

Column operation.

---

```python
df.applymap(...)
```

Entire DataFrame operation.

---

# Grouping Data

Grouping is one of the most powerful analytical operations in Pandas.

It allows us to:

```text
Split
Apply
Combine
```

---

## Sample Data

```python
df = pd.DataFrame({
    "Category":["A","A","B","B"],
    "Value":[10,20,30,40]
})
```

Output:

```text
  Category  Value
0    A       10
1    A       20
2    B       30
3    B       40
```

---

# GroupBy Operation

```python
grouped = df.groupby("Category")
```

Groups become:

```text
A → [10,20]

B → [30,40]
```

---

# Calculating Mean

```python
df.groupby("Category").mean()
```

Output:

```text
          Value
Category
A           15
B           35
```

---

### Calculation

Category A:

```text
(10 + 20) / 2 = 15
```

Category B:

```text
(30 + 40) / 2 = 35
```

---

# Sum Aggregation

```python
df.groupby("Category").sum()
```

Output:

```text
          Value
Category
A           30
B           70
```

---

# Count Aggregation

```python
df.groupby("Category").count()
```

Output:

```text
          Value
Category
A            2
B            2
```

---

# Multiple Aggregations

Instead of one operation:

```python
df.groupby(
    "Category"
).agg(
    ["mean","sum","count"]
)
```

Output:

```text
         Value
         mean sum count

A         15  30   2
B         35  70   2
```

---

# Why GroupBy Is Important

Used in:

* Sales Analysis
* Customer Analytics
* Financial Reports
* Business Intelligence
* KPI Dashboards

Examples:

```text
Average salary by department

Total sales by city

Number of customers by state
```

---

# Merging DataFrames

Real-world data is often spread across multiple tables.

Merge combines them.

---

## DataFrame 1

```python
df1 = pd.DataFrame({
    "ID":[1,2,3],
    "Name":["Alice","Bob","Charlie"]
})
```

---

## DataFrame 2

```python
df2 = pd.DataFrame({
    "ID":[1,2,4],
    "Salary":[50000,60000,70000]
})
```

---

# Outer Merge

```python
pd.merge(
    df1,
    df2,
    on="ID",
    how="outer"
)
```

Output:

```text
   ID    Name   Salary
0   1   Alice   50000
1   2   Bob     60000
2   3   Charlie   NaN
3   4   NaN     70000
```

---

## Why NaN Appears?

ID 3:

```text
Exists in df1
Missing in df2
```

ID 4:

```text
Exists in df2
Missing in df1
```

---

# Types of Merge

| Merge Type | Meaning               |
| ---------- | --------------------- |
| inner      | Common records only   |
| left       | All left records      |
| right      | All right records     |
| outer      | All records from both |

---

# Joining DataFrames

Join is similar to merge.

Main difference:

```text
Join works primarily using indexes
```

---

## Example

```python
df1.join(
    df2,
    how="outer"
)
```

---

Output:

```text
      A     B
0   data  data
1   data  data
2   data  NaN
3   NaN   data
```

---

# Merge vs Join

| Merge         | Join         |
| ------------- | ------------ |
| Uses columns  | Uses indexes |
| More flexible | Simpler      |
| SQL-like      | Index-based  |

---

# Handling Missing Values After Merge

After combining datasets:

```text
Missing values are common
```

represented as:

```text
NaN
```

---

## Replace Missing Values

```python
df.fillna(0)
```

Output:

```text
NaN → 0
```

---

# Real-World Examples

---

## Employee Salary Analysis

```python
employees.groupby(
    "Department"
)["Salary"].mean()
```

---

## Monthly Sales

```python
sales.groupby(
    "Month"
)["Revenue"].sum()
```

---

## Customer Segmentation

```python
customers.groupby(
    "City"
).count()
```

---

## Combining Customer and Order Data

```python
pd.merge(
    customers,
    orders,
    on="CustomerID"
)
```

---

# Common Mistakes

## Forgetting Assignment

Wrong:

```python
df["Age"].apply(
    lambda x: x+1
)
```

Result not saved.

---

Correct:

```python
df["Age"] = df["Age"].apply(
    lambda x: x+1
)
```

---

## Using applymap on a Series

Wrong:

```python
df["Age"].applymap(...)
```

❌

Correct:

```python
df["Age"].apply(...)
```

✅

---

## Merging on Wrong Key

Wrong:

```python
pd.merge(
    df1,
    df2,
    on="Name"
)
```

if Name doesn't exist in both.

Always verify merge keys.

---

# Interview Questions

### What is apply()?

Applies a function to a Series or DataFrame axis.

---

### What is applymap()?

Applies a function to every element in a DataFrame.

---

### What is GroupBy?

A technique used to split data into groups and perform calculations on each group.

---

### Difference Between Merge and Join?

Merge uses columns.

Join uses indexes.

---

### What Happens When Labels Don't Match During Arithmetic Operations?

Pandas aligns labels and produces NaN where matches are unavailable.

---

# Key Takeaways

* DataFrames support arithmetic operations like addition, subtraction, multiplication, and division.
* Scalar operations apply calculations to every value.
* `apply()` transforms rows or columns.
* `applymap()` transforms every element.
* `groupby()` is one of the most powerful analysis tools in Pandas.
* Aggregations include mean, sum, count, min, max, and more.
* `merge()` combines DataFrames using common columns.
* `join()` combines DataFrames using indexes.
* Pandas automatically aligns data using labels.
* These operations form the foundation of real-world data analysis and EDA.

# Descriptive Statistics for Numerical Data

## Introduction

When working with data, one of the first goals is to understand:

* What is the typical value?
* How spread out is the data?
* Is the data symmetric or skewed?
* Are there any outliers?
* What does the overall distribution look like?

These questions are answered using **Descriptive Statistics**.

Descriptive statistics summarize and describe the important characteristics of numerical data without making predictions or inferences.

They form the foundation of:

* Exploratory Data Analysis (EDA)
* Data Science
* Machine Learning
* Business Analytics
* Research and Statistics

---

# What Are Descriptive Statistics?

Descriptive statistics are numerical measures used to summarize data.

They are generally divided into three categories:

```text
1. Measures of Central Tendency
2. Measures of Dispersion
3. Measures of Shape
```

---

## Measures of Central Tendency

Describe the center of the data.

Examples:

* Mean
* Median
* Mode

---

## Measures of Dispersion

Describe how spread out the data is.

Examples:

* Range
* Variance
* Standard Deviation
* Interquartile Range (IQR)

---

## Measures of Shape

Describe the distribution pattern.

Examples:

* Skewness
* Kurtosis

---

# Sample Dataset

Throughout this chapter, we will use:

```python
data = [2, 4, 5, 7, 12]
```

---

# Measures of Central Tendency

Central tendency refers to the "center" or "typical value" of a dataset.

---

# Mean

The **Mean** is commonly called the average.

It is calculated as:

\text{Mean}=\frac{\sum x}{n}

Where:

* Σx = Sum of all values
* n = Number of observations

---

## Example

Dataset:

```text
2, 4, 5, 7, 12
```

Calculation:

```text
(2 + 4 + 5 + 7 + 12) / 5

= 30 / 5

= 6
```

Mean:

```text
6
```

---

# Python Example

```python
import numpy as np

data = [2,4,5,7,12]

np.mean(data)
```

Output:

```text
6.0
```

---

# Advantages of Mean

* Easy to calculate
* Uses all observations
* Most widely used average

---

# Disadvantages of Mean

Highly affected by outliers.

Example:

```text
2, 4, 5, 7, 100
```

Mean becomes:

```text
23.6
```

which does not represent the data well.

---

# Median

The Median is the middle value after sorting.

---

## Steps

1. Arrange data in ascending order.
2. Find middle value.

---

## Example

```text
2, 4, 5, 7, 12
```

Middle value:

```text
5
```

Median:

```text
5
```

---

# Median for Even Number of Values

Dataset:

```text
2, 4, 6, 8
```

Middle values:

```text
4 and 6
```

Median:

```text
(4 + 6)/2 = 5
```

---

# Python Example

```python
np.median(data)
```

Output:

```text
5.0
```

---

# Advantages of Median

* Resistant to outliers
* Suitable for skewed data
* Useful in salary and income analysis

---

# Example with Outlier

Dataset:

```text
2, 4, 5, 7, 100
```

Mean:

```text
23.6
```

Median:

```text
5
```

Median better represents the center.

---

# Mode

Mode is the most frequently occurring value.

---

## Example

Dataset:

```text
2, 4, 4, 5, 7
```

Mode:

```text
4
```

because it appears most often.

---

# Types of Mode

### No Mode

```text
1,2,3,4,5
```

Every value occurs once.

---

### Unimodal

```text
1,2,2,3,4
```

One mode.

---

### Bimodal

```text
1,2,2,3,3,4
```

Two modes.

---

### Multimodal

Multiple repeating values.

---

# Python Example

```python
from scipy import stats

stats.mode(data)
```

Output:

```text
ModeResult(mode=5, count=2)
```

---

# Summary of Central Tendency

| Measure | Meaning             |
| ------- | ------------------- |
| Mean    | Average             |
| Median  | Middle Value        |
| Mode    | Most Frequent Value |

---

# Measures of Dispersion

Central tendency tells us where data is centered.

Dispersion tells us:

```text
How spread out is the data?
```

---

# Range

The simplest measure of spread.

Formula:

\text{Range}=\text{Maximum}-\text{Minimum}

---

## Example

Dataset:

```text
2,4,5,7,12
```

Maximum:

```text
12
```

Minimum:

```text
2
```

Range:

```text
12 - 2 = 10
```

---

# Python Example

```python
max(data) - min(data)
```

Output:

```text
10
```

---

# Limitations of Range

Only uses:

* Maximum
* Minimum

Ignores all other values.

---

# Variance

Variance measures the average squared deviation from the mean.

It quantifies spread around the average.

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"s^2=\frac{\sum (x_i-\bar{x})^2}{n-1}"}}

---

# Understanding Variance

Steps:

1. Calculate mean
2. Subtract mean from every value
3. Square differences
4. Compute average

---

## Example

Dataset:

```text
2,4,5,7,12
```

Mean:

```text
6
```

Differences:

```text
-4
-2
-1
1
6
```

Squares:

```text
16
4
1
1
36
```

Total:

```text
58
```

Variance:

```text
58 / 4 = 14.5
```

---

# Python Example

```python
np.var(data, ddof=1)
```

Output:

```text
14.5
```

---

# Why Squaring?

Squaring:

* Removes negative signs
* Gives larger penalties to large deviations

---

# Standard Deviation

Standard deviation is the square root of variance.

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"s=\sqrt{s^2}"}}

---

## Example

Variance:

```text
14.5
```

Standard deviation:

```text
√14.5 ≈ 3.81
```

---

# Python Example

```python
np.std(data, ddof=1)
```

Output:

```text
3.81
```

---

# Why Standard Deviation Is Important

Unlike variance:

```text
Variance → squared units

Standard Deviation → original units
```

Therefore easier to interpret.

---

# Interquartile Range (IQR)

IQR measures the spread of the middle 50% of data.

Formula:

IQR=Q_3-Q_1

Where:

* Q1 = 25th percentile
* Q3 = 75th percentile

---

# Example

Dataset:

```text
1,2,3,4,5,6,7,8,9
```

Q1:

```text
3
```

Q3:

```text
7
```

IQR:

```text
7 - 3 = 4
```

---

# Why IQR Is Important

Unlike range:

```text
IQR ignores extreme values
```

Therefore:

```text
More robust to outliers
```

---

# Python Example

```python
Q1 = np.percentile(data,25)
Q3 = np.percentile(data,75)

IQR = Q3 - Q1
```

---

# Measures of Shape

Shape describes how the distribution looks.

Main measures:

```text
1. Skewness
2. Kurtosis
```

---

# Skewness

Skewness measures asymmetry.

---

# Positive Skew

Characteristics:

```text
Long tail on right side
```

Example:

```text
Income Distribution
```

Visualization:

```text
|
|***
|****
|*****
|******
|**************
---------------->
```

---

# Negative Skew

Characteristics:

```text
Long tail on left side
```

Visualization:

```text
**************
******
*****
****
***
---------------->
```

---

# Symmetric Distribution

Perfectly balanced.

Example:

```text
Normal Distribution
```

Visualization:

```text
      *
    *****
  *********
*************
  *********
    *****
      *
```

---

# Interpreting Skewness

| Value | Interpretation |
| ----- | -------------- |
| 0     | Symmetric      |
| > 0   | Right Skewed   |
| < 0   | Left Skewed    |

---

# Python Example

```python
from scipy.stats import skew

skew(data)
```

---

# Kurtosis

Kurtosis measures:

```text
Tail heaviness
```

and likelihood of extreme values.

---

# High Kurtosis

Characteristics:

```text
Heavy tails
More outliers
```

---

# Low Kurtosis

Characteristics:

```text
Light tails
Fewer outliers
```

---

# Normal Distribution Kurtosis

Reference value:

```text
3
```

---

# Interpreting Kurtosis

| Kurtosis | Meaning     |
| -------- | ----------- |
| > 3      | Heavy Tails |
| = 3      | Normal      |
| < 3      | Light Tails |

---

# Python Example

```python
from scipy.stats import kurtosis

kurtosis(data)
```

---

# Boxplots

A Boxplot summarizes:

* Minimum
* Q1
* Median
* Q3
* Maximum
* Outliers

all in one visualization.

---

## Components

```text
Minimum

Q1

Median

Q3

Maximum
```

---

# Advantages of Boxplots

* Detect outliers
* Compare distributions
* Show skewness
* Summarize data quickly

---

# Creating a Boxplot

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(data=data)

plt.show()
```

---

# Outlier Detection Using IQR

A common EDA task is detecting outliers.

---

## Lower Bound

Q_1-1.5(IQR)

---

## Upper Bound

Q_3+1.5(IQR)

---

Values outside these bounds are considered outliers.

---

# Example

Dataset:

```text
10,12,13,15,16,18,100
```

Clearly:

```text
100
```

is an outlier.

---

# Detecting Outliers in Python

```python
Q1 = np.percentile(data,25)
Q3 = np.percentile(data,75)

IQR = Q3 - Q1

lower = Q1 - 1.5*IQR
upper = Q3 + 1.5*IQR

outliers = [
    x for x in data
    if x < lower or x > upper
]
```

---

# Descriptive Statistics Using Pandas

Pandas provides a single function:

```python
df.describe()
```

---

# Example

```python
import pandas as pd

df = pd.DataFrame({
    "Age":[25,30,35,40,45]
})

df.describe()
```

Output:

```text
count
mean
std
min
25%
50%
75%
max
```

---

# What describe() Provides

| Statistic | Meaning            |
| --------- | ------------------ |
| count     | Number of records  |
| mean      | Average            |
| std       | Standard deviation |
| min       | Minimum            |
| 25%       | Q1                 |
| 50%       | Median             |
| 75%       | Q3                 |
| max       | Maximum            |

---

# Real-World Applications

---

## Salary Analysis

```text
Mean Salary
Median Salary
Salary Variability
```

---

## Sales Analysis

```text
Average Revenue
Revenue Spread
Sales Outliers
```

---

## Customer Analytics

```text
Average Spending
Spending Distribution
```

---

## Risk Analysis

```text
Volatility
Variance
Standard Deviation
```

---

# Common Mistakes

## Using Mean for Highly Skewed Data

Wrong choice:

```text
Income Data
```

Better:

```text
Median
```

---

## Ignoring Outliers

Outliers can significantly affect:

* Mean
* Variance
* Standard Deviation

---

## Confusing Variance and Standard Deviation

Variance:

```text
Squared Units
```

Standard Deviation:

```text
Original Units
```

---

# Interview Questions

### What is Mean?

Average of all values.

---

### Difference Between Mean and Median?

Mean uses all values.

Median uses middle value.

Median is more resistant to outliers.

---

### What is Standard Deviation?

Measure of spread around the mean.

---

### Why Is IQR Useful?

It ignores extreme values and focuses on the middle 50%.

---

### What Does Positive Skew Mean?

Distribution has a longer right tail.

---

### What Does Kurtosis Measure?

Tail heaviness and likelihood of extreme values.

---

# Key Takeaways

* Descriptive statistics summarize numerical data.
* Mean, median, and mode describe the center of data.
* Range, variance, standard deviation, and IQR describe spread.
* Skewness measures asymmetry.
* Kurtosis measures tail heaviness.
* Boxplots summarize distributions and detect outliers.
* IQR is commonly used for outlier detection.
* `describe()` provides a quick statistical summary.
* Descriptive statistics form the foundation of Exploratory Data Analysis (EDA).

# Descriptive Statistics for Categorical Data

## Introduction

Not all data is numerical.

Many real-world datasets contain values such as:

```text
Male / Female

Red / Blue / Green

Satisfied / Unsatisfied

Electronics / Clothing / Books
```

These are known as **Categorical Variables**.

Unlike numerical data, we cannot calculate:

* Mean
* Median
* Standard Deviation

for categorical variables.

Instead, we use specialized descriptive statistical techniques designed specifically for categories.

---

# What is Categorical Data?

Categorical data represents characteristics or labels that place observations into groups.

Examples:

| Person | Gender |
| ------ | ------ |
| A      | Male   |
| B      | Female |
| C      | Male   |

Here:

```text
Male and Female
```

are categories.

---

# Types of Categorical Data

Categorical data is divided into three major types.

---

## Nominal Data

Categories have no natural ordering.

Examples:

```text
Red
Blue
Green
Yellow
```

or

```text
India
USA
Canada
Australia
```

Order does not matter.

---

## Ordinal Data

Categories have a meaningful order.

Examples:

```text
Poor
Average
Good
Excellent
```

or

```text
High School
Bachelor's
Master's
PhD
```

Order matters.

However:

```text
Difference between categories is not measurable
```

---

## Binary Data

Contains only two categories.

Examples:

```text
Yes / No

True / False

Pass / Fail

Male / Female
```

Binary data is extremely common in machine learning and statistics.

---

# Why Analyze Categorical Data?

Categorical analysis helps answer questions such as:

```text
What category appears most often?

How frequently does each category occur?

Are two categorical variables related?

Which category dominates the dataset?
```

---

# Frequency Distribution

The most important concept in categorical analysis is:

```text
Frequency Distribution
```

A frequency distribution counts how many times each category appears.

---

## Example Dataset

Customer Satisfaction Survey:

```text
Good
Excellent
Average
Good
Poor
Good
Excellent
Average
Good
Excellent
```

---

# Counting Frequencies

| Satisfaction | Count |
| ------------ | ----- |
| Poor         | 1     |
| Average      | 2     |
| Good         | 4     |
| Excellent    | 3     |

---

# Interpretation

We can immediately see:

```text
Good is the most common response.
```

This gives us a quick understanding of customer sentiment.

---

# Relative Frequency

Raw counts are useful.

But percentages are often more informative.

Relative Frequency is calculated as:

\text{Relative Frequency}=\frac{\text{Category Count}}{\text{Total Count}}

---

## Example

Total Responses:

```text
10
```

Good Responses:

```text
4
```

Relative Frequency:

```text
4 / 10

= 0.4

= 40%
```

---

# Complete Relative Frequency Table

| Satisfaction | Count | Percentage |
| ------------ | ----- | ---------- |
| Poor         | 1     | 10%        |
| Average      | 2     | 20%        |
| Good         | 4     | 40%        |
| Excellent    | 3     | 30%        |

---

# Why Relative Frequency Matters

Counts can be misleading for large datasets.

Example:

```text
Dataset A: 100 observations

Dataset B: 10,000 observations
```

Percentages make comparisons easier.

---

# Mode for Categorical Data

Mean and Median often do not make sense for categories.

The primary measure of central tendency is:

```text
Mode
```

---

## Definition

Mode is the category that appears most frequently.

---

## Example

Dataset:

```text
Poor
Average
Good
Good
Good
Excellent
```

Mode:

```text
Good
```

because it appears most often.

---

# Why Mode Is Important

The mode tells us:

```text
Most Popular Category

Most Common Customer Choice

Most Frequent Outcome
```

---

# Example: Product Categories

Dataset:

```text
Electronics
Electronics
Books
Clothing
Electronics
Books
```

Mode:

```text
Electronics
```

---

# Creating Categorical Data in Pandas

```python
import pandas as pd

data = pd.Series([
    "Poor",
    "Average",
    "Good",
    "Good",
    "Excellent",
    "Good"
])
```

---

# Frequency Distribution in Pandas

```python
data.value_counts()
```

Output:

```text
Good         3
Poor         1
Average      1
Excellent    1
```

---

# Relative Frequency in Pandas

```python
data.value_counts(normalize=True)
```

Output:

```text
Good         0.50
Poor         0.17
Average      0.17
Excellent    0.17
```

---

# Finding the Mode

```python
data.mode()
```

Output:

```text
Good
```

---

# Example Dataset for Analysis

Suppose we have customer feedback data.

| Customer | Satisfaction |
| -------- | ------------ |
| 1        | Poor         |
| 2        | Average      |
| 3        | Good         |
| 4        | Excellent    |
| 5        | Good         |

---

# Satisfaction Distribution

After counting:

| Rating    | Frequency |
| --------- | --------- |
| Poor      | 10        |
| Average   | 30        |
| Good      | 40        |
| Excellent | 20        |

Total:

```text
100 customers
```

---

# Percentage Distribution

| Rating    | Percentage |
| --------- | ---------- |
| Poor      | 10%        |
| Average   | 30%        |
| Good      | 40%        |
| Excellent | 20%        |

---

# Interpretation

Most customers are:

```text
Good (40%)
```

Therefore:

```text
Overall customer experience is positive.
```

---

# Contingency Tables

Sometimes we need to study the relationship between two categorical variables.

For example:

```text
Product Category

and

Customer Satisfaction
```

---

# What is a Contingency Table?

A contingency table displays frequencies for combinations of two categorical variables.

---

## Example

| Category    | Good | Average | Poor |
| ----------- | ---- | ------- | ---- |
| Electronics | 20   | 10      | 5    |
| Clothing    | 15   | 12      | 3    |
| Books       | 10   | 8       | 2    |

---

# Interpretation

We can see:

```text
Electronics has the highest number of Good ratings.
```

This helps identify patterns across categories.

---

# Creating Contingency Tables in Pandas

```python
pd.crosstab(
    df["Category"],
    df["Satisfaction"]
)
```

Output:

```text
Frequency table of both variables
```

---

# Why Contingency Tables Are Useful

They help answer questions such as:

```text
Which product category receives the best ratings?

Which category receives the most complaints?

How do customer preferences vary?
```

---

# Marginal Frequencies

Marginal frequencies are row totals and column totals.

---

## Example

| Category    | Good | Average | Total |
| ----------- | ---- | ------- | ----- |
| Electronics | 20   | 10      | 30    |
| Clothing    | 15   | 5       | 20    |
| Total       | 35   | 15      | 50    |

---

# Row Marginals

Represent totals for each row.

Example:

```text
Electronics = 30
Clothing = 20
```

---

# Column Marginals

Represent totals for each column.

Example:

```text
Good = 35

Average = 15
```

---

# Conditional Proportions

Conditional proportions help us understand relationships more clearly.

Formula:

P(A|B)=\frac{Frequency(A\cap B)}{Frequency(B)}

---

# Example

Electronics products:

```text
50 total
```

Good ratings:

```text
20
```

Conditional Proportion:

```text
20 / 50

= 0.40

= 40%
```

---

# Why Conditional Proportions Matter

Raw counts can be misleading.

Conditional proportions normalize the data.

This allows fair comparison across categories.

---

# Calculating Conditional Proportions in Pandas

```python
contingency_table.div(
    contingency_table.sum(axis=1),
    axis=0
)
```

This converts counts into proportions.

---

# Visualization of Categorical Data

Tables are useful.

Visualizations are often easier to interpret.

Common plots include:

```text
Bar Charts

Pie Charts

Heatmaps
```

---

# Bar Charts

Bar charts display category frequencies.

Example:

```text
Good       ██████████████

Average    ████████

Poor       ███

Excellent  ███████
```

---

# Why Bar Charts Are Useful

They help compare categories quickly.

Best for:

* Frequencies
* Counts
* Percentages

---

# Creating a Bar Plot

```python
data.value_counts().plot(kind="bar")
```

---

# Pie Charts

Pie charts show category proportions.

Example:

```text
Good       40%
Average    30%
Poor       10%
Excellent  20%
```

---

# Creating a Pie Chart

```python
data.value_counts().plot(
    kind="pie",
    autopct="%1.1f%%"
)
```

---

# Heatmaps

Heatmaps are useful for contingency tables.

Color intensity represents frequency.

---

## Example

| Category    | Good   | Average |
| ----------- | ------ | ------- |
| Electronics | Dark   | Light   |
| Clothing    | Medium | Medium  |

Darker colors indicate higher counts.

---

# Creating a Heatmap

```python
import seaborn as sns

sns.heatmap(
    contingency_table,
    annot=True
)
```

---

# Example: Product Satisfaction Dataset

Suppose we generate:

```python
100 products
```

across:

```text
Electronics

Clothing

Books
```

with satisfaction ratings:

```text
Poor

Average

Good

Excellent
```

---

# Analysis Workflow

### Step 1

Create frequency distribution.

```python
df["Satisfaction"].value_counts()
```

---

### Step 2

Find mode.

```python
df["Satisfaction"].mode()
```

---

### Step 3

Create contingency table.

```python
pd.crosstab(
    df["Category"],
    df["Satisfaction"]
)
```

---

### Step 4

Compute conditional proportions.

```python
contingency.div(
    contingency.sum(axis=1),
    axis=0
)
```

---

### Step 5

Visualize using heatmap.

```python
sns.heatmap(contingency)
```

---

# Real-World Applications

---

## Customer Feedback Analysis

Determine:

```text
Most common customer rating
```

---

## Market Research

Analyze:

```text
Brand Preference
```

---

## Survey Analysis

Understand:

```text
Public Opinion
```

---

## Healthcare

Analyze:

```text
Disease Categories

Treatment Categories

Patient Satisfaction
```

---

# Common Mistakes

---

## Using Mean on Nominal Data

Incorrect:

```text
Average Color

Average Gender
```

These concepts do not exist.

---

## Ignoring Percentages

Counts alone may mislead.

Always consider relative frequencies.

---

## Confusing Frequency and Probability

Frequency:

```text
Observed Count
```

Probability:

```text
Expected Likelihood
```

---

# Interview Questions

### What is categorical data?

Data representing groups or categories.

---

### Types of categorical data?

* Nominal
* Ordinal
* Binary

---

### What is a frequency distribution?

A table showing category counts.

---

### What is the mode?

Most frequently occurring category.

---

### What is a contingency table?

A table showing relationships between two categorical variables.

---

### Why are conditional proportions useful?

They normalize data and allow fair comparison.

---

# Key Takeaways

* Categorical data represents labels or groups.
* Three major types are nominal, ordinal, and binary.
* Frequency distributions summarize category counts.
* Relative frequencies convert counts into percentages.
* Mode is the primary measure of central tendency.
* Contingency tables analyze relationships between categorical variables.
* Marginal frequencies provide row and column totals.
* Conditional proportions normalize category comparisons.
* Bar charts, pie charts, and heatmaps are the most common visualizations.
* Categorical data analysis is essential for surveys, customer analytics, market research, and business intelligence.

# Data Relationship: Correlation and Covariance

## Introduction

In Exploratory Data Analysis (EDA), one of the most important objectives is understanding how variables are related.

Questions like:

```text
Does study time affect exam scores?

Does age affect salary?

Does temperature affect ice cream sales?

Does advertising spend affect revenue?
```

can be answered using:

1. Covariance
2. Correlation

These techniques help measure the relationship between two variables.

---

# Why Study Relationships?

Suppose we have the following data:

| Study Hours | Exam Score |
| ----------- | ---------- |
| 2           | 40         |
| 4           | 55         |
| 6           | 70         |
| 8           | 85         |
| 10          | 95         |

As study hours increase:

```text
Exam scores also increase.
```

This indicates a positive relationship.

Correlation and covariance help quantify such relationships mathematically.

---

# Covariance

## Definition

Covariance measures how two variables change together.

It tells us whether:

```text
Both variables increase together

Both variables decrease together

One increases while the other decreases
```

---

# Covariance Formula

Cov(X,Y)=\frac{\sum (X_i-\bar X)(Y_i-\bar Y)}{n-1}

Where:

| Symbol | Meaning                |
| ------ | ---------------------- |
| X      | First Variable         |
| Y      | Second Variable        |
| X̄     | Mean of X              |
| Ȳ      | Mean of Y              |
| n      | Number of Observations |

---

# Understanding Covariance

The formula compares:

```text
How far X is from its mean

How far Y is from its mean
```

and checks whether they move in the same direction.

---

# Positive Covariance

If:

```text
X increases

Y increases
```

or

```text
X decreases

Y decreases
```

Covariance becomes positive.

Example:

| Study Hours | Marks |
| ----------- | ----- |
| 1           | 20    |
| 2           | 40    |
| 3           | 60    |
| 4           | 80    |

Both move together.

Result:

```text
Positive Covariance
```

---

# Negative Covariance

If:

```text
X increases

Y decreases
```

Covariance becomes negative.

Example:

| Speed | Travel Time |
| ----- | ----------- |
| 20    | 10          |
| 40    | 5           |
| 60    | 3           |
| 80    | 2           |

Higher speed results in lower travel time.

Result:

```text
Negative Covariance
```

---

# Zero Covariance

If two variables have no linear relationship:

```text
Covariance ≈ 0
```

Example:

```text
Shoe Size

Exam Marks
```

Usually unrelated.

---

# Interpreting Covariance

| Covariance Value | Meaning                 |
| ---------------- | ----------------------- |
| Positive         | Variables move together |
| Negative         | Variables move opposite |
| Zero             | No linear relationship  |

---

# Problem with Covariance

Covariance depends on units.

Example:

```text
Salary measured in Rupees

Salary measured in Dollars
```

Covariance changes dramatically.

Therefore:

```text
Covariance cannot be compared across datasets.
```

This leads us to Correlation.

---

# Correlation

## Definition

Correlation is a standardized measure of relationship between variables.

It tells:

```text
Direction of relationship

Strength of relationship
```

---

# Pearson Correlation Coefficient

The most commonly used correlation measure is:

```text
Pearson Correlation
```

Formula:

r=\frac{Cov(X,Y)}{\sigma_X\sigma_Y}

Where:

| Symbol   | Meaning                 |
| -------- | ----------------------- |
| r        | Correlation Coefficient |
| Cov(X,Y) | Covariance              |
| σX       | Standard Deviation of X |
| σY       | Standard Deviation of Y |

---

# Correlation Range

Unlike covariance:

```text
Correlation always lies between

-1 and +1
```

---

# Correlation Scale

| Correlation  | Meaning                      |
| ------------ | ---------------------------- |
| +1           | Perfect Positive Correlation |
| +0.7 to +1   | Strong Positive              |
| +0.3 to +0.7 | Moderate Positive            |
| 0 to +0.3    | Weak Positive                |
| 0            | No Correlation               |
| -0.3 to 0    | Weak Negative                |
| -0.7 to -0.3 | Moderate Negative            |
| -1 to -0.7   | Strong Negative              |
| -1           | Perfect Negative Correlation |

---

# Perfect Positive Correlation

When:

```text
X increases

Y increases proportionally
```

Example:

| X | Y |
| - | - |
| 1 | 2 |
| 2 | 4 |
| 3 | 6 |
| 4 | 8 |

Result:

```text
r = +1
```

---

# Perfect Negative Correlation

When:

```text
X increases

Y decreases proportionally
```

Example:

| X | Y |
| - | - |
| 1 | 8 |
| 2 | 6 |
| 3 | 4 |
| 4 | 2 |

Result:

```text
r = -1
```

---

# No Correlation

Example:

| Shoe Size | Salary |
| --------- | ------ |
| 7         | 50000  |
| 9         | 60000  |
| 8         | 40000  |
| 10        | 70000  |

No meaningful pattern.

Result:

```text
r ≈ 0
```

---

# Visual Understanding of Correlation

## Strong Positive Correlation

```text
•
  •
    •
      •
         •
```

---

## Strong Negative Correlation

```text
         •
      •
   •
 •
•
```

---

## No Correlation

```text
•      •
    •
       •
 •
         •
```

---

# Step-by-Step Correlation Example

Suppose:

| X | Y |
| - | - |
| 2 | 3 |
| 4 | 5 |
| 6 | 7 |
| 8 | 9 |

---

## Step 1

Calculate Mean

For X:

```text
(2+4+6+8)/4

= 5
```

For Y:

```text
(3+5+7+9)/4

= 6
```

---

## Step 2

Calculate Covariance

Using covariance formula.

Suppose result is:

```text
Cov(X,Y) = 6.67
```

---

## Step 3

Calculate Standard Deviations

Suppose:

```text
σX = 2.58

σY = 2.58
```

---

## Step 4

Calculate Correlation

```text
r = 6.67/(2.58 × 2.58)

≈ 1
```

Meaning:

```text
Perfect Positive Correlation
```

---

# Correlation Using NumPy

## Create Sample Data

```python
import numpy as np

x = np.array([1,2,3,4,5])

y = np.array([2,4,6,8,10])
```

---

# Covariance Using NumPy

```python
np.cov(x,y)
```

Output:

```text
Covariance Matrix
```

Example:

```text
[[2.5 5.0]
 [5.0 10.0]]
```

---

# Correlation Using NumPy

```python
np.corrcoef(x,y)
```

Output:

```text
[[1.0 1.0]
 [1.0 1.0]]
```

Perfect positive relationship.

---

# Correlation Using Pandas

Create DataFrame:

```python
import pandas as pd

df = pd.DataFrame({
    "X":x,
    "Y":y
})
```

---

# Covariance Matrix

```python
df.cov()
```

Output:

```text
Covariance matrix
```

---

# Correlation Matrix

```python
df.corr()
```

Output:

```text
Correlation matrix
```

---

# What is a Correlation Matrix?

When multiple numerical variables exist:

```text
Age

Salary

Experience

Education
```

we compute pairwise correlations.

---

## Example

| Variable   | Age  | Salary | Experience |
| ---------- | ---- | ------ | ---------- |
| Age        | 1.00 | 0.45   | 0.70       |
| Salary     | 0.45 | 1.00   | 0.65       |
| Experience | 0.70 | 0.65   | 1.00       |

---

# Interpretation

Age vs Experience:

```text
0.70

Strong Positive Relationship
```

Age vs Salary:

```text
0.45

Moderate Positive Relationship
```

---

# Correlation Heatmap

One of the most common EDA visualizations.

```python
import seaborn as sns

sns.heatmap(
    df.corr(),
    annot=True
)
```

---

# Why Use Heatmaps?

They quickly show:

```text
Strong Positive Relationships

Strong Negative Relationships

Weak Relationships
```

without reading large tables.

---

# Covariance vs Correlation

| Feature               | Covariance | Correlation |
| --------------------- | ---------- | ----------- |
| Measures Relationship | Yes        | Yes         |
| Shows Direction       | Yes        | Yes         |
| Shows Strength        | Difficult  | Easy        |
| Standardized          | No         | Yes         |
| Range                 | Unlimited  | -1 to +1    |
| Unit Dependent        | Yes        | No          |
| Easy to Interpret     | No         | Yes         |

---

# Limitations of Correlation

Correlation is powerful but dangerous when misunderstood.

---

## Correlation ≠ Causation

The biggest mistake.

Example:

```text
Ice Cream Sales ↑

Drowning Incidents ↑
```

Correlation exists.

But:

```text
Ice Cream does NOT cause drowning.
```

Actual cause:

```text
Hot Weather
```

which increases both.

---

# Example of True Causation

| Study Time | Score  |
| ---------- | ------ |
| More       | Higher |
| Less       | Lower  |

Here:

```text
Study Time directly influences score.
```

Correlation likely reflects causation.

---

# Correlation Only Detects Linear Relationships

Consider:

```text
Y = X²
```

Relationship exists.

But Pearson correlation may underestimate it because:

```text
Relationship is nonlinear.
```

---

# Effect of Outliers

Correlation is sensitive to extreme values.

Example:

| X   | Y |
| --- | - |
| 1   | 2 |
| 2   | 4 |
| 3   | 6 |
| 100 | 1 |

Single outlier can distort results.

---

# Real-World Applications

---

## Finance

Relationship between:

```text
Stock A

Stock B
```

---

## Marketing

Relationship between:

```text
Advertising Spend

Sales Revenue
```

---

## Healthcare

Relationship between:

```text
Weight

Blood Pressure
```

---

## Education

Relationship between:

```text
Study Hours

Exam Scores
```

---

# Interview Questions

### What is covariance?

Measures how two variables change together.

---

### What is correlation?

Standardized measure of relationship strength and direction.

---

### Range of correlation?

```text
-1 to +1
```

---

### Difference between covariance and correlation?

Correlation is standardized and easier to interpret.

---

### What does correlation of 0 mean?

No linear relationship.

---

### Does correlation imply causation?

No.

Correlation only indicates association.

---

### Why use correlation instead of covariance?

Because correlation is unit-independent and comparable across datasets.

---

# Key Takeaways

* Covariance measures how two variables move together.
* Positive covariance means variables move in the same direction.
* Negative covariance means variables move in opposite directions.
* Correlation standardizes covariance.
* Correlation ranges from -1 to +1.
* Positive correlation indicates variables increase together.
* Negative correlation indicates inverse relationships.
* Correlation matrices help analyze multiple variables.
* Heatmaps are commonly used to visualize correlations.
* Correlation does not imply causation.
* Correlation is one of the most important tools in Exploratory Data Analysis and Feature Selection.

# Univariate Analysis

## Introduction

After cleaning and understanding a dataset, the first step in Exploratory Data Analysis (EDA) is usually:

```text
Analyze one variable at a time
```

This process is called:

```text
Univariate Analysis
```

The word can be broken into:

```text
Uni = One

Variate = Variable
```

Meaning:

```text
Study of a single variable independently
```

---

# What is Univariate Analysis?

## Definition

Univariate Analysis is a statistical technique used to analyze and summarize a single variable.

It focuses on understanding:

* Distribution
* Central Tendency
* Spread
* Shape
* Outliers

of one variable at a time.

---

# Why Univariate Analysis?

Before building models or finding relationships between variables, we need to understand each feature individually.

Questions answered by univariate analysis:

```text
What is the average value?

How spread out is the data?

Are there outliers?

Is the data normally distributed?

Is the data skewed?
```

---

# Example Dataset

| Student | Age |
| ------- | --- |
| A       | 18  |
| B       | 20  |
| C       | 22  |
| D       | 21  |
| E       | 19  |

Here we analyze only:

```text
Age
```

This is univariate analysis.

---

# Objectives of Univariate Analysis

The main objectives are:

### Understand Data Distribution

```text
Normal?

Skewed?

Uniform?

Bimodal?
```

---

### Identify Outliers

```text
Extremely large values

Extremely small values
```

---

### Summarize Data

Using statistics such as:

* Mean
* Median
* Mode

---

### Measure Variability

Using:

* Range
* Variance
* Standard Deviation
* IQR

---

# Types of Variables in Univariate Analysis

---

## Numerical Variables

Examples:

```text
Age

Salary

Height

Weight

Income
```

For numerical data we use:

* Mean
* Median
* Variance
* Histograms
* Boxplots

---

## Categorical Variables

Examples:

```text
Gender

Department

City

Education Level
```

For categorical data we use:

* Frequency Tables
* Mode
* Bar Charts
* Pie Charts

---

# Measures of Central Tendency

These describe the center of data.

---

## Mean

Average value.

Formula:

\bar X=\frac{\sum X}{n}

---

### Example

Data:

```text
10, 20, 30, 40, 50
```

Mean:

```text
150 / 5

= 30
```

---

## Median

Middle value after sorting.

Data:

```text
10,20,30,40,50
```

Median:

```text
30
```

---

## Mode

Most frequent value.

Data:

```text
10,20,20,30,40
```

Mode:

```text
20
```

---

# Measures of Dispersion

Dispersion tells how spread out data is.

---

## Range

Formula:

Range=Maximum-Minimum

Example:

```text
10,20,30,40,50
```

Range:

```text
50 - 10

= 40
```

---

## Variance

Measures average squared deviation from mean.

s^2=\frac{\sum (X_i-\bar X)^2}{n-1}

---

## Standard Deviation

Square root of variance.

genui{"math_block_widget_always_prefetch_v2":{"content":"s=\sqrt{s^2}"}}

---

### Interpretation

Small SD:

```text
Data clustered near mean
```

Large SD:

```text
Data highly spread out
```

---

## Interquartile Range (IQR)

Measures spread of middle 50% data.

Formula:

IQR=Q_3-Q_1

Where:

```text
Q1 = 25th Percentile

Q3 = 75th Percentile
```

---

# Shape of Distribution

Univariate analysis also studies data shape.

Important measures:

* Skewness
* Kurtosis

---

# Skewness

Measures asymmetry of data.

---

## Symmetric Distribution

Left and right sides look similar.

Example:

```text
Normal Distribution
```

```text
      /\
     /  \
    /    \
```

Skewness:

```text
≈ 0
```

---

## Positive Skew

Long tail toward right.

```text
   /\
  /  \
 /    \_____
```

Characteristics:

```text
Mean > Median
```

Examples:

* Income
* House Prices
* Wealth Distribution

---

## Negative Skew

Long tail toward left.

```text
 _____
/     \
       \
        \
```

Characteristics:

```text
Mean < Median
```

Examples:

* Easy Exams
* High Scoring Tests

---

# Kurtosis

Measures tail heaviness.

---

## High Kurtosis

```text
Heavy Tails

More Outliers
```

---

## Low Kurtosis

```text
Light Tails

Fewer Outliers
```

---

## Normal Kurtosis

Typical bell-shaped distribution.

---

# Percentiles and Quantiles

Percentiles divide data into 100 equal parts.

---

## Common Percentiles

| Percentile | Meaning |
| ---------- | ------- |
| 25th       | Q1      |
| 50th       | Median  |
| 75th       | Q3      |

---

# Why Percentiles Matter

Example:

```text
90th Percentile Salary
```

means:

```text
90% of people earn less than that value
```

---

# Frequency Distribution (Categorical Data)

Suppose:

| Satisfaction |
| ------------ |
| Good         |
| Good         |
| Average      |
| Excellent    |
| Good         |

Frequency Table:

| Category  | Count |
| --------- | ----- |
| Good      | 3     |
| Average   | 1     |
| Excellent | 1     |

---

# Visualization in Univariate Analysis

Visualization is crucial because numbers alone often hide patterns.

---

# Histogram

Most important plot for numerical data.

Shows:

```text
Distribution

Shape

Spread
```

Example:

```text
      ███
    ███████
  ███████████
    ███████
      ███
```

Looks approximately normal.

---

# What Histograms Reveal

### Distribution Shape

* Normal
* Skewed
* Uniform
* Bimodal

---

### Spread

Wide histogram:

```text
High Variability
```

Narrow histogram:

```text
Low Variability
```

---

### Outliers

Extreme isolated bars indicate potential outliers.

---

# Density Plot

A smooth version of histogram.

Shows probability density of data.

Useful for:

```text
Understanding distribution shape
```

---

# Box Plot

One of the most powerful EDA tools.

Shows:

* Minimum
* Q1
* Median
* Q3
* Maximum
* Outliers

---

## Structure of Boxplot

```text
|----|====|====|----|

Min   Q1 Med  Q3 Max
```

---

# Reading Boxplots

---

## Median

Middle line inside box.

---

## Box

Represents:

```text
Middle 50% Data
```

---

## Whiskers

Represent spread outside IQR.

---

## Dots Outside

Represent:

```text
Potential Outliers
```

---

# Outlier Detection

One major goal of univariate analysis.

---

## What is an Outlier?

An observation significantly different from most data.

Example:

```text
10
12
15
18
20
200
```

Here:

```text
200
```

is an outlier.

---

# Why Outliers Matter

They can:

* Distort Mean
* Distort Variance
* Affect Machine Learning Models
* Cause Incorrect Conclusions

---

# Z-Score Method

Most common outlier detection technique.

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"Z=\frac{X-\mu}{\sigma}"}}

Where:

| Symbol | Meaning            |
| ------ | ------------------ |
| X      | Observation        |
| μ      | Mean               |
| σ      | Standard Deviation |

---

# Z-Score Interpretation

| Z Score | Meaning           |
| ------- | ----------------- |
| 0       | Exactly Mean      |
| 1       | One SD Above Mean |
| -1      | One SD Below Mean |
| 3       | Extreme Value     |
| -3      | Extreme Value     |

---

# Outlier Rule

If:

```text
|Z| > 3
```

then observation is usually treated as an outlier.

---

# Python Example

```python
from scipy import stats

z_scores = stats.zscore(df["Age"])

outliers = df[abs(z_scores) > 3]
```

---

# Practical Workflow

When analyzing a numerical feature:

### Step 1

Calculate:

```python
df["Age"].describe()
```

---

### Step 2

Check skewness.

```python
df["Age"].skew()
```

---

### Step 3

Check kurtosis.

```python
df["Age"].kurt()
```

---

### Step 4

Plot histogram.

```python
df["Age"].hist()
```

---

### Step 5

Plot boxplot.

```python
sns.boxplot(df["Age"])
```

---

### Step 6

Detect outliers.

```python
stats.zscore()
```

---

# Real-World Applications

---

## Employee Salaries

Analyze:

```text
Salary Distribution

Salary Outliers

Average Salary
```

---

## Healthcare

Analyze:

```text
Age

Blood Pressure

Heart Rate
```

---

## Finance

Analyze:

```text
Stock Returns

Trading Volume

Revenue
```

---

## Education

Analyze:

```text
Exam Scores

Attendance

Study Hours
```

---

# Interview Questions

### What is univariate analysis?

Analysis of a single variable.

---

### Why is it important?

It helps understand data distribution before advanced analysis.

---

### What are the major statistics used?

* Mean
* Median
* Mode
* Variance
* Standard Deviation
* IQR

---

### Which plots are commonly used?

* Histogram
* Density Plot
* Box Plot
* Bar Chart

---

### How are outliers detected?

Using:

* Z-score
* IQR Method
* Boxplots

---

### What does skewness measure?

Asymmetry of distribution.

---

### What does kurtosis measure?

Tail heaviness and likelihood of outliers.

---

# Key Takeaways

* Univariate analysis studies one variable at a time.
* It is the first step of Exploratory Data Analysis.
* Numerical variables are analyzed using descriptive statistics and plots.
* Categorical variables are analyzed using frequencies and proportions.
* Histograms reveal distribution shape.
* Boxplots reveal spread and outliers.
* Skewness measures asymmetry.
* Kurtosis measures tail heaviness.
* Z-score helps detect outliers.
* Understanding each variable individually is critical before performing correlation analysis, feature engineering, or machine learning.

# Bivariate Analysis

## Introduction

After understanding individual variables through **Univariate Analysis**, the next step in Exploratory Data Analysis (EDA) is studying relationships between variables.

This process is called:

```text
Bivariate Analysis
```

Breaking the word:

```text
Bi = Two

Variate = Variables
```

Meaning:

```text
Analysis of two variables together
```

---

# What is Bivariate Analysis?

## Definition

Bivariate Analysis is the statistical study of the relationship between two variables.

It helps answer questions like:

```text
Does age affect income?

Does study time affect exam scores?

Does advertising spend affect sales?

Does customer satisfaction vary by department?
```

The goal is to determine:

* Whether a relationship exists
* Strength of relationship
* Direction of relationship
* Nature of relationship

---

# Why Bivariate Analysis?

Univariate analysis tells us about a single variable.

Bivariate analysis tells us:

```text
How one variable changes when another changes.
```

This is extremely important for:

* Feature selection
* Predictive modeling
* Hypothesis testing
* Business decision-making

---

# Types of Bivariate Analysis

The method used depends on variable types.

| Variable 1  | Variable 2  | Analysis Method            |
| ----------- | ----------- | -------------------------- |
| Numerical   | Numerical   | Correlation, Covariance    |
| Numerical   | Categorical | Boxplots, Group Statistics |
| Categorical | Categorical | Contingency Tables         |

---

# Numerical vs Numerical Analysis

Examples:

```text
Age vs Salary

Height vs Weight

Study Hours vs Marks
```

Most common techniques:

* Correlation
* Covariance
* Scatter Plots

---

# Correlation Analysis

Correlation measures:

```text
Strength

and

Direction

of relationship
```

between two variables.

---

## Correlation Scale

| Correlation  | Interpretation    |
| ------------ | ----------------- |
| +1           | Perfect Positive  |
| +0.7 to +1   | Strong Positive   |
| +0.3 to +0.7 | Moderate Positive |
| 0            | No Correlation    |
| -0.3 to -0.7 | Moderate Negative |
| -0.7 to -1   | Strong Negative   |
| -1           | Perfect Negative  |

---

# Example

| Study Hours | Marks |
| ----------- | ----- |
| 2           | 40    |
| 4           | 55    |
| 6           | 70    |
| 8           | 85    |

Observation:

```text
As study hours increase,
marks also increase.
```

Positive correlation exists.

---

# Covariance Analysis

Covariance measures whether variables move together.

Positive covariance:

```text
Age ↑

Salary ↑
```

Negative covariance:

```text
Speed ↑

Travel Time ↓
```

---

# Correlation Matrix

When multiple numerical variables exist:

```text
Age

Income

Experience

Education
```

we create a correlation matrix.

Example:

| Variable   | Age  | Income | Experience |
| ---------- | ---- | ------ | ---------- |
| Age        | 1.00 | 0.45   | 0.70       |
| Income     | 0.45 | 1.00   | 0.65       |
| Experience | 0.70 | 0.65   | 1.00       |

---

# Interpretation

Age vs Experience:

```text
0.70

Strong positive relationship
```

Income vs Age:

```text
0.45

Moderate positive relationship
```

---

# Numerical vs Categorical Analysis

Examples:

```text
Salary vs Department

Income vs Education Level

Marks vs Gender
```

Goal:

```text
Compare numerical distributions
across categories.
```

---

# Example Dataset

| Employee | Department | Salary |
| -------- | ---------- | ------ |
| A        | HR         | 50000  |
| B        | HR         | 52000  |
| C        | IT         | 90000  |
| D        | IT         | 95000  |

Question:

```text
Does salary differ by department?
```

This is a bivariate problem.

---

# Group-wise Statistics

We can compute:

```python
df.groupby("Department")["Salary"].mean()
```

Output:

| Department | Avg Salary |
| ---------- | ---------- |
| HR         | 51000      |
| IT         | 92500      |

---

# Interpretation

```text
IT employees earn more on average.
```

This reveals a relationship between:

```text
Department

and

Salary
```

---

# Categorical vs Categorical Analysis

Examples:

```text
Department vs Satisfaction

Gender vs Purchase Decision

Education vs Employment Status
```

Most common technique:

```text
Contingency Table
```

---

# Contingency Table

Example:

| Department | High | Medium | Low |
| ---------- | ---- | ------ | --- |
| HR         | 50   | 30     | 20  |
| Sales      | 40   | 35     | 25  |
| IT         | 70   | 20     | 10  |

---

# Interpretation

We can observe:

```text
IT has highest number of
high satisfaction employees.
```

---

# Creating Contingency Tables

```python
pd.crosstab(
    df["Department"],
    df["Satisfaction"]
)
```

---

# Key Techniques in Bivariate Analysis

The course highlights three major techniques:

---

## 1. Correlation Analysis

Measures strength of linear relationships.

Used for:

```text
Numerical vs Numerical
```

---

## 2. Covariance Analysis

Measures joint variation.

Used for:

```text
Numerical vs Numerical
```

---

## 3. Contingency Tables

Measure relationships between categories.

Used for:

```text
Categorical vs Categorical
```

---

# Visualization in Bivariate Analysis

Numbers alone are difficult to interpret.

Visualization makes relationships obvious.

Common plots:

* Scatter Plots
* Box Plots
* Heatmaps

---

# Scatter Plot

Most important bivariate visualization.

Used for:

```text
Numerical vs Numerical
```

---

## Example

Age vs Income

```text
•
   •
      •
         •
            •
```

Relationship becomes visible immediately.

---

# Why Scatter Plots?

Scatter plots help identify:

* Correlation
* Trends
* Clusters
* Outliers

---

# Strong Positive Relationship

```text
•
  •
    •
      •
         •
```

Variables increase together.

---

# Strong Negative Relationship

```text
         •
      •
   •
 •
•
```

One increases while the other decreases.

---

# No Relationship

```text
•     •
   •
       •
 •
         •
```

Random distribution.

---

# Box Plots

Used for:

```text
Numerical vs Categorical
```

Example:

```text
Salary vs Department
```

---

# Why Boxplots?

They help compare:

* Median
* Spread
* Outliers

across categories.

---

# Example

HR Salary Distribution

```text
|----|====|====|----|
```

IT Salary Distribution

```text
|-------|========|========|-------|
```

Comparison becomes easy.

---

# Heatmaps

Heatmaps are widely used for:

```text
Correlation Matrices

Contingency Tables
```

---

# Correlation Heatmap

Example:

|            | Age | Income | Experience |
| ---------- | --- | ------ | ---------- |
| Age        | 1.0 | 0.4    | 0.7        |
| Income     | 0.4 | 1.0    | 0.6        |
| Experience | 0.7 | 0.6    | 1.0        |

Color intensity indicates relationship strength.

---

# Contingency Heatmap

Example:

| Department | High      | Medium | Low    |
| ---------- | --------- | ------ | ------ |
| HR         | Dark      | Medium | Light  |
| Sales      | Medium    | Dark   | Medium |
| IT         | Very Dark | Light  | Light  |

Darker cells represent higher frequencies.

---

# Correlation Matrix in Python

```python
df.corr()
```

---

# Visualizing Correlation Matrix

```python
import seaborn as sns

sns.heatmap(
    df.corr(),
    annot=True
)
```

---

# Covariance Matrix in Python

```python
df.cov()
```

---

# Contingency Table in Python

```python
pd.crosstab(
    df["Department"],
    df["Satisfaction"]
)
```

---

# Scatter Plot in Python

```python
plt.scatter(
    df["Age"],
    df["Income"]
)
```

---

# Practical Bivariate Workflow

---

## Step 1

Identify variable types.

```text
Numerical?

Categorical?
```

---

## Step 2

Choose correct technique.

| Variable Types | Technique   |
| -------------- | ----------- |
| Num vs Num     | Correlation |
| Num vs Cat     | Boxplot     |
| Cat vs Cat     | Crosstab    |

---

## Step 3

Calculate statistics.

```python
df.corr()
df.cov()
pd.crosstab()
```

---

## Step 4

Visualize.

```python
Scatter Plot

Heatmap

Box Plot
```

---

## Step 5

Interpret results.

Ask:

```text
Relationship exists?

Positive or negative?

Strong or weak?

Business meaning?
```

---

# Real-World Applications

---

## Education

Analyze:

```text
Study Hours

vs

Exam Marks
```

---

## Finance

Analyze:

```text
Risk

vs

Return
```

---

## Marketing

Analyze:

```text
Advertising Spend

vs

Revenue
```

---

## HR Analytics

Analyze:

```text
Department

vs

Employee Satisfaction
```

---

## Healthcare

Analyze:

```text
Weight

vs

Blood Pressure
```

---

# Limitations

---

## Correlation Does Not Mean Causation

Example:

```text
Ice Cream Sales ↑

Drowning Incidents ↑
```

Both increase during summer.

Ice cream does not cause drowning.

---

## Only Linear Relationships

Correlation may miss:

```text
Curved Relationships

Nonlinear Patterns
```

---

## Outlier Sensitivity

A single extreme value can significantly affect results.

---

# Interview Questions

### What is bivariate analysis?

Analysis of two variables simultaneously.

---

### Why is bivariate analysis important?

It helps discover relationships between variables.

---

### Common techniques?

* Correlation
* Covariance
* Contingency Tables

---

### Best visualization for numerical variables?

Scatter Plot.

---

### Best visualization for categorical relationships?

Heatmap of contingency table.

---

### Difference between univariate and bivariate analysis?

| Univariate   | Bivariate     |
| ------------ | ------------- |
| One Variable | Two Variables |
| Distribution | Relationship  |
| Histogram    | Scatter Plot  |

---

# Key Takeaways

* Bivariate analysis studies relationships between two variables.
* It helps discover patterns, trends, and associations.
* Correlation and covariance are used for numerical variables.
* Contingency tables are used for categorical variables.
* Scatter plots visualize numerical relationships.
* Box plots compare numerical distributions across categories.
* Heatmaps visualize correlation matrices and contingency tables.
* Bivariate analysis is a foundation for predictive modeling, feature selection, and business analytics.
* Understanding relationships between variables is one of the core goals of Exploratory Data Analysis (EDA).

# Scatter Plots

## Introduction

A **Scatter Plot** is a two-dimensional graph used to visualize the relationship between two continuous variables.

Each point on the graph represents a single observation:

* X-coordinate → value of first variable
* Y-coordinate → value of second variable

Scatter plots are one of the most important tools in Exploratory Data Analysis (EDA) because they help identify:

* Relationships
* Trends
* Correlations
* Clusters
* Outliers

---

## Why Scatter Plots Are Important

Scatter plots help answer questions such as:

* Does income increase with age?
* Do study hours affect exam scores?
* Is there a relationship between advertising spend and sales?
* Are there unusual data points?

Instead of looking at numbers in a table, scatter plots provide an immediate visual understanding of relationships.

---

## Importing Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

---

## Creating Sample Data

```python
np.random.seed(42)

x = np.random.rand(50) * 100
y = 2 * x + np.random.randn(50) * 20
```

### Explanation

```python
np.random.seed(42)
```

Ensures reproducible results.

```python
x = np.random.rand(50) * 100
```

Creates 50 random values between 0 and 100.

```python
y = 2*x + noise
```

Creates a dependent variable with some randomness.

---

## Basic Scatter Plot

```python
plt.figure(figsize=(10,6))

plt.scatter(
    x,
    y,
    marker='o',
    s=50,
    color='blue',
    alpha=0.7
)

plt.title("Basic Scatter Plot")
plt.xlabel("X Variable")
plt.ylabel("Y Variable")

plt.show()
```

---

## Understanding Parameters

### marker

Controls point shape.

Examples:

```python
'o'
'*'
'^'
's'
'+'
```

---

### s

Size of markers.

```python
s=50
```

Larger value = larger points.

---

### color

Point color.

```python
color='red'
color='green'
color='black'
```

---

### alpha

Transparency.

```python
alpha=1.0
```

Fully visible.

```python
alpha=0.5
```

Semi-transparent.

Useful when points overlap.

---

## Output Interpretation

Each point represents one observation.

Look for:

* Upward trend
* Downward trend
* Random distribution
* Clusters
* Outliers

---

## Multiple Scatter Plots

Often we need to compare two datasets.

### Example

```python
x2 = np.random.rand(50) * 100
y2 = 1.5 * x2 + np.random.randn(50) * 25

plt.figure(figsize=(10,6))

plt.scatter(x, y, label="Dataset 1")
plt.scatter(x2, y2, label="Dataset 2")

plt.title("Multiple Scatter Plots")
plt.xlabel("X")
plt.ylabel("Y")

plt.legend()

plt.show()
```

---

## Why Use Multiple Scatter Plots?

Useful for:

* Comparing groups
* Comparing departments
* Comparing products
* Comparing experiments

---

## Adding a Trend Line

A trend line summarizes the overall relationship.

### Step 1: Fit Line

```python
z = np.polyfit(x, y, 1)
```

Degree 1 means straight line.

---

### Step 2: Create Polynomial Function

```python
p = np.poly1d(z)
```

---

### Step 3: Plot

```python
plt.scatter(x, y)

plt.plot(
    x,
    p(x),
    'r--',
    linewidth=2
)

plt.show()
```

---

## Why Trend Lines Matter

Trend lines help determine:

* Positive relationship
* Negative relationship
* Strength of relationship

Without manually inspecting every point.

---

## Interpreting Scatter Plots

### Positive Correlation

As X increases:

Y increases.

Example:

* Study hours vs marks
* Experience vs salary

Visual:

```
.
  .
    .
      .
        .
```

---

### Negative Correlation

As X increases:

Y decreases.

Example:

* Product price vs demand

Visual:

```
        .
      .
    .
  .
.
```

---

### No Correlation

No visible pattern.

Visual:

```
.   .      .
     .
  .      .
       .
```

Variables are unrelated.

---

## Strength of Correlation

### Strong Correlation

Points closely follow a line.

```
.
 .
  .
   .
    .
```

Easy to predict values.

---

### Weak Correlation

Points generally move in same direction but are spread out.

```
. .
   .
 .
     .
```

Prediction becomes less reliable.

---

### No Correlation

Random cloud of points.

```
.    .
     .
  .
       .
```

No predictive relationship.

---

## Identifying Outliers

Outliers are observations far away from most points.

Example:

```
. . . . .
. . . . .
. . . . .

             X
```

The point marked **X** is an outlier.

---

## Why Outliers Matter

Outliers may indicate:

* Data entry errors
* Rare events
* Fraud
* Equipment malfunction

Always investigate them.

---

## Identifying Clusters

Clusters occur when points naturally form groups.

Example:

```
***


                ***
```

Possible interpretations:

* Different customer groups
* Different market segments
* Different species
* Different departments

---

## Linear vs Nonlinear Relationships

### Linear Relationship

Points follow a straight line.

```
.
 .
  .
   .
    .
```

Can often use:

```python
Linear Regression
```

---

### Nonlinear Relationship

Points follow a curve.

```
.
  .
    .
      .
        .
      .
    .
```

May require:

* Polynomial Regression
* Machine Learning models

---

## Correlation Does Not Mean Causation

One of the most important concepts in data analysis.

### Example

Ice Cream Sales ↑

Drowning Incidents ↑

These variables are correlated.

But:

Ice cream sales do NOT cause drowning.

The real cause is:

```text
Hot Weather
```

which increases both.

---

## Examples

### Correlation Without Causation

* Ice cream sales vs drowning
* Shoe size vs reading ability in children

---

### Correlation With Causation

* Study time vs exam scores
* Advertising spend vs sales

Even here, further analysis is required.

---

## Common Use Cases

Scatter plots are used when:

### Relationship Analysis

```python
Age vs Income
```

---

### Customer Analysis

```python
Visits vs Purchases
```

---

### Sales Analysis

```python
Ad Spend vs Revenue
```

---

### Education

```python
Study Hours vs Marks
```

---

### Finance

```python
Risk vs Return
```

---

## Advantages

* Easy to understand
* Shows relationships clearly
* Detects outliers
* Detects clusters
* Detects trends
* Useful before modeling

---

## Limitations

* Only works well with two variables
* Large datasets can become cluttered
* Correlation may be misleading
* Cannot prove causation

---

## Key Interview Questions

### What is a scatter plot?

A graph that visualizes the relationship between two continuous variables using points.

---

### What does each point represent?

A single observation containing values for two variables.

---

### How do you identify positive correlation?

Points move upward from left to right.

---

### How do you identify negative correlation?

Points move downward from left to right.

---

### What is a trend line?

A line representing the overall direction of the data.

---

### What are outliers?

Data points significantly different from the rest of the dataset.

---

### Can scatter plots prove causation?

No.

They only show relationships and correlations.

---

## Summary

A scatter plot:

* Visualizes relationships between two variables
* Detects trends
* Detects clusters
* Detects outliers
* Helps understand correlation
* Serves as a foundation for regression and predictive modeling

---

# Line Plots

## Introduction

A **Line Plot** (or Line Chart) is a graph that displays data points connected by straight lines.

It is primarily used to show:

* Trends over time
* Changes across an ordered sequence
* Continuous data behavior
* Growth or decline patterns

Line plots are among the most commonly used visualizations in business analytics, finance, economics, weather forecasting, and time-series analysis.

---

## What Is a Line Plot?

A line plot consists of:

* Data points plotted on a graph
* Consecutive points connected by straight lines

The:

* X-axis usually represents time or sequence
* Y-axis represents measured values

Example:

```text
Value
 ^
 |
 |       *
 |     *
 |   *
 | *
 +-----------------> Time
```

The upward slope indicates increasing values over time.

---

## Why Use Line Plots?

Line plots help answer questions such as:

* Is sales revenue increasing?
* Is website traffic declining?
* How does temperature change throughout the day?
* How do stock prices move over time?

Instead of looking at tables of numbers, line plots immediately reveal trends and patterns.

---

# Importing Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

---

# Creating Sample Data

```python
x = np.linspace(0, 10, 100)

y1 = np.sin(x)
y2 = np.cos(x)
```

---

## Understanding the Data

### x values

```python
np.linspace(0,10,100)
```

Creates:

```text
0.0
0.1
0.2
...
10.0
```

100 equally spaced values.

---

### y values

```python
y1 = sin(x)
```

Creates a sine wave.

```python
y2 = cos(x)
```

Creates a cosine wave.

---

## Basic Line Plot

```python
plt.figure(figsize=(10,6))

plt.plot(x, y1)

plt.title("Basic Line Plot")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")

plt.show()
```

---

## How It Works

```python
plt.plot(x,y)
```

Connects all points using straight lines.

Instead of showing individual dots, the graph displays a continuous curve.

---

## Understanding plot()

### Syntax

```python
plt.plot(x, y)
```

Where:

* x → independent variable
* y → dependent variable

---

## Output Interpretation

The graph shows:

* Peaks
* Troughs
* Increasing trends
* Decreasing trends
* Cycles

All become immediately visible.

---

# Multiple Line Plots

Often we need to compare multiple variables.

Example:

```python
plt.figure(figsize=(10,6))

plt.plot(x, y1)
plt.plot(x, y2)

plt.show()
```

---

## Why Multiple Lines?

Useful for:

* Comparing products
* Comparing stocks
* Comparing departments
* Comparing yearly performance

Example:

```text
Sales Product A
Sales Product B
```

on the same graph.

---

# Customizing Lines

---

## Changing Color

```python
plt.plot(x, y1, color='red')
```

Possible colors:

```python
red
blue
green
black
yellow
```

---

## Changing Line Style

### Solid Line

```python
'-'
```

Example:

```python
plt.plot(x,y,'-')
```

---

### Dashed Line

```python
'--'
```

Example:

```python
plt.plot(x,y,'--')
```

---

### Dotted Line

```python
':'
```

Example:

```python
plt.plot(x,y,':')
```

---

### Dash-Dot

```python
'-.'
```

Example:

```python
plt.plot(x,y,'-.')
```

---

## Changing Line Width

```python
plt.plot(
    x,
    y,
    linewidth=3
)
```

Larger value → thicker line.

---

## Adding Labels

```python
plt.plot(
    x,
    y1,
    label="Sine"
)

plt.plot(
    x,
    y2,
    label="Cosine"
)

plt.legend()
```

---

## Why Legends Matter

Without legends:

```text
Which line is which?
```

Impossible to know.

Legends identify each series clearly.

---

# Complete Example

```python
plt.figure(figsize=(10,6))

plt.plot(
    x,
    y1,
    color='red',
    linestyle='--',
    linewidth=2,
    label='Sine'
)

plt.plot(
    x,
    y2,
    color='blue',
    linestyle=':',
    linewidth=2,
    label='Cosine'
)

plt.title("Multiple Line Plot")

plt.xlabel("X")
plt.ylabel("Y")

plt.legend()

plt.show()
```

---

# Customizing Axes

Sometimes we want to zoom into a specific area.

---

## X-axis Limits

```python
plt.xlim(2,8)
```

Shows only:

```text
2 ≤ x ≤ 8
```

---

## Y-axis Limits

```python
plt.ylim(-1,1)
```

Shows only:

```text
-1 ≤ y ≤ 1
```

---

## Example

```python
plt.plot(x,y)

plt.xlim(2,8)
plt.ylim(-1,1)

plt.show()
```

---

# Adding Grid Lines

```python
plt.grid(True)
```

---

## Why Use Grids?

Makes it easier to:

* Compare values
* Read coordinates
* Analyze trends

---

## Example

```python
plt.plot(x,y)

plt.grid(True)

plt.show()
```

---

# Annotating Important Points

Annotations highlight key observations.

---

## Example: Maximum Point

```python
max_x = x[np.argmax(y1)]
max_y = np.max(y1)
```

---

### Add Annotation

```python
plt.annotate(
    "Maximum",
    xy=(max_x,max_y),
    xytext=(5,1.2),
    arrowprops=dict(
        facecolor='black'
    )
)
```

---

## Result

An arrow points directly to the maximum value.

Useful for:

* Peaks
* Troughs
* Important events
* Milestones

---

# Common Features to Analyze

---

## Peaks

Highest points.

Example:

```text
Sales Peak
Highest Temperature
Highest Revenue
```

---

## Troughs

Lowest points.

Example:

```text
Lowest Revenue
Lowest Stock Price
```

---

## Turning Points

Places where trend changes.

Example:

```text
Increasing → Decreasing
```

or

```text
Decreasing → Increasing
```

---

## Rate of Change

Measured using slope.

---

### Steep Slope

```text
Rapid Change
```

Example:

```text
Stock price jump
```

---

### Gentle Slope

```text
Slow Change
```

---

### Flat Line

```text
No Change
```

---

# Trend Analysis

---

## Increasing Trend

```text
    *
   *
  *
 *
*
```

Indicates growth.

Examples:

* Sales
* Revenue
* Population

---

## Decreasing Trend

```text
*
 *
  *
   *
    *
```

Indicates decline.

Examples:

* Demand
* Profit
* Traffic

---

## Stable Trend

```text
*******
```

Values remain constant.

---

## Fluctuating Trend

```text
 /\  /\
/  \/  \
```

Values move up and down frequently.

---

# Cyclic Patterns

Regular repetition.

Examples:

* Day-night temperatures
* Seasonal sales
* Monthly electricity demand

---

## Example

```text
 /\    /\
/  \__/  \
```

Repeating cycles.

---

# Seasonal Patterns

Patterns occurring at fixed intervals.

Examples:

* Summer sales
* Winter electricity usage
* Holiday spending

---

# Detecting Outliers

Outliers appear as unusual spikes.

Example:

```text
*
*
*
*
***********
*
*
```

The large spike may indicate:

* Error
* Promotion campaign
* Market event

---

# Multiple Subplots

Sometimes comparing graphs side-by-side is better.

---

## Example

```python
fig, (ax1, ax2) = plt.subplots(1,2)

ax1.plot(x,y1)
ax2.plot(x,y2)

plt.show()
```

---

## Benefits

* Easier comparison
* Cleaner presentation
* Better dashboards

---

# Real World Applications

---

## Stock Market

```text
Date vs Price
```

---

## Weather

```text
Day vs Temperature
```

---

## Website Analytics

```text
Date vs Visitors
```

---

## Sales

```text
Month vs Revenue
```

---

## Fitness

```text
Day vs Weight
```

---

# Advantages

✅ Easy to understand

✅ Excellent for trends

✅ Great for time-series data

✅ Works with multiple datasets

✅ Highly customizable

---

# Limitations

❌ Not suitable for categorical comparisons

❌ Too many lines can clutter the graph

❌ Missing values may break continuity

❌ Doesn't show distribution as well as histograms

---

# Interview Questions

### What is a line plot?

A graph that connects data points using straight lines to show trends over an ordered sequence.

---

### When should line plots be used?

When data is continuous and order matters, especially time-series data.

---

### What is the difference between a line plot and scatter plot?

| Line Plot        | Scatter Plot         |
| ---------------- | -------------------- |
| Shows trends     | Shows relationships  |
| Connected points | Separate points      |
| Time-series data | Correlation analysis |

---

### What are peaks and troughs?

* Peak = highest point
* Trough = lowest point

---

### Why use legends?

To identify multiple data series.

---

## Summary

Line plots are one of the most powerful visualizations for understanding continuous data and trends over time.

They help us:

* Track growth and decline
* Detect cycles
* Identify peaks and troughs
* Compare multiple datasets
* Analyze time-series data

Mastering line plots is essential for EDA, business analytics, finance, forecasting, and machine learning.

---

# Bar Plots

## Introduction

A **Bar Plot (Bar Chart)** is one of the most widely used data visualization techniques for displaying and comparing categorical data.

It represents data using rectangular bars where:

* Length or height of the bar represents the value.
* Each bar corresponds to a category.
* Taller bars indicate larger values.
* Shorter bars indicate smaller values.

Bar plots make it easy to compare quantities across different categories.

---

## What is a Bar Plot?

A bar plot displays:

```text
Sales
 ^
 |
 |        █
 |        █
 |   █    █
 |   █    █
 | █ █    █
 +---------------->
    A B    C
```

Where:

* A, B, C = Categories
* Bar Height = Numerical Value

---

## Why Use Bar Plots?

Bar plots help answer questions like:

* Which product sold the most?
* Which department has the highest revenue?
* Which city has the largest population?
* Which category has the highest frequency?

Instead of reading tables, bar plots allow instant comparison.

---

# Import Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

---

# Creating Sample Dataset

```python
categories = ['A','B','C','D','E']

values = np.random.randint(
    10,
    100,
    size=5
)
```

Example:

```text
A → 45
B → 78
C → 22
D → 91
E → 56
```

---

# Basic Vertical Bar Plot

```python
plt.figure(figsize=(8,5))

plt.bar(
    categories,
    values
)

plt.title("Basic Bar Plot")

plt.xlabel("Category")
plt.ylabel("Value")

plt.show()
```

---

## Understanding plt.bar()

### Syntax

```python
plt.bar(
    x_values,
    y_values
)
```

Where:

* x-values = categories
* y-values = corresponding numerical values

---

## Output Interpretation

```text
A → ████
B → ███████
C → ██
D → █████████
E → █████
```

Higher bar = larger value.

---

# Components of a Bar Plot

---

## X-Axis

Contains categories.

Example:

```text
Product A
Product B
Product C
```

---

## Y-Axis

Contains numerical measurements.

Example:

```text
Sales
Revenue
Profit
Frequency
Population
```

---

## Bars

Each rectangle represents:

```text
Category + Value
```

---

# Horizontal Bar Plot

Sometimes category names are long.

Instead of vertical bars:

```python
plt.barh(
    categories,
    values
)
```

---

## Example

```python
plt.figure(figsize=(8,5))

plt.barh(
    categories,
    values
)

plt.title("Horizontal Bar Plot")

plt.show()
```

---

## Why Use Horizontal Bars?

Useful when category names are long.

Example:

```text
Electronics Accessories
Home Appliances
Fashion Accessories
```

Horizontal bars improve readability.

---

# Vertical vs Horizontal

| Vertical             | Horizontal             |
| -------------------- | ---------------------- |
| Common               | Better for long labels |
| Easy comparison      | Easier reading         |
| Categories on X-axis | Categories on Y-axis   |

---

# Customizing Colors

```python
plt.bar(
    categories,
    values,
    color='green'
)
```

---

### Different Colors

```python
plt.bar(
    categories,
    values,
    color=[
        'red',
        'blue',
        'green',
        'orange',
        'purple'
    ]
)
```

---

## Why Use Colors?

Colors help:

* Highlight important categories
* Improve readability
* Differentiate groups

---

# Adding Bar Borders

```python
plt.bar(
    categories,
    values,
    edgecolor='black'
)
```

Creates clear separation between bars.

---

# Adjusting Width

```python
plt.bar(
    categories,
    values,
    width=0.5
)
```

---

## Width Meaning

Smaller width:

```text
| |
| |
| |
```

Larger width:

```text
|||||
|||||
|||||
```

---

# Adding Data Labels

Often we want values displayed above bars.

```python
bars = plt.bar(
    categories,
    values
)

for bar in bars:
    plt.text(
        bar.get_x(),
        bar.get_height(),
        str(bar.get_height())
    )
```

---

## Result

```text
     90
     █
     █
     █

     60
     █
     █
```

Values become immediately visible.

---

# Grouped Bar Plot

Used to compare multiple datasets.

Example:

```text
Product A Sales
Product B Sales
```

for the same categories.

---

## Sample Data

```python
product_a = [40,60,80,70,50]
product_b = [50,55,75,65,45]
```

---

## Creating Grouped Bar Plot

```python
x = np.arange(len(categories))

width = 0.35

plt.bar(
    x-width/2,
    product_a,
    width,
    label='Product A'
)

plt.bar(
    x+width/2,
    product_b,
    width,
    label='Product B'
)

plt.legend()
```

---

## Why Grouped Bars?

Useful for:

* Year comparisons
* Product comparisons
* Department comparisons

---

## Example

```text
Category A

█ █

Category B

█ █
```

Bars appear side-by-side.

---

# Stacked Bar Plot

Stacked bars show:

```text
Total Value
+
Composition
```

---

## Example

```python
plt.bar(
    categories,
    product_a
)

plt.bar(
    categories,
    product_b,
    bottom=product_a
)
```

---

## Understanding bottom=

```python
bottom=product_a
```

Places Product B on top of Product A.

---

## Visual Representation

```text
████ B
████ A
```

Total height:

```text
A + B
```

---

# Why Use Stacked Bars?

Shows:

* Total value
* Component contribution

at the same time.

Example:

```text
Company Revenue

North Region
South Region
East Region
```

inside one bar.

---

# Percentage Stacked Bar Plot

Sometimes totals differ greatly.

We want percentages instead.

---

## Calculate Percentages

```python
total = product_a + product_b

percent_a = (
    product_a/total
)*100

percent_b = (
    product_b/total
)*100
```

---

## Plot

```python
plt.bar(
    categories,
    percent_a
)

plt.bar(
    categories,
    percent_b,
    bottom=percent_a
)
```

---

## Result

Every bar becomes:

```text
100%
```

allowing direct comparison.

---

# Interpreting Bar Plots

---

## Compare Heights

Taller bar:

```text
Higher value
```

Shorter bar:

```text
Lower value
```

---

## Look for Patterns

Possible observations:

### Increasing

```text
█
██
███
████
```

---

### Decreasing

```text
████
███
██
█
```

---

### Fluctuating

```text
██
████
█
███
```

---

# Detecting Outliers

Example:

```text
█
██
█
████████████
█
```

One unusually large bar may indicate:

* Exceptional performance
* Error
* Special event

---

# Importance of Scale

Always check:

```text
Y-axis starts at 0
```

Otherwise differences may appear exaggerated.

---

## Misleading Example

Actual Values:

```text
95
100
```

If Y-axis starts at:

```text
90
```

difference appears huge.

---

# Reading Grouped Bar Plots

Focus on:

### Within Category

Compare bars inside category.

Example:

```text
Category A

Product A
vs
Product B
```

---

### Across Categories

Compare:

```text
Product A
across all categories
```

---

# Reading Stacked Bar Plots

Focus on:

### Total Height

Represents total value.

### Segment Size

Represents contribution.

Example:

```text
60% Sales
40% Service
```

---

# Common Real-World Applications

---

## Sales Analysis

```text
Product vs Revenue
```

---

## Survey Results

```text
Category vs Responses
```

---

## Population Studies

```text
City vs Population
```

---

## Education

```text
Department vs Students
```

---

## Finance

```text
Year vs Profit
```

---

# When to Use Vertical Bars

Use when:

* Categories are short
* Simple comparison needed
* Most standard presentation

Example:

```text
A
B
C
D
```

---

# When to Use Horizontal Bars

Use when:

* Category names are long
* Many categories exist
* Rankings are shown

Example:

```text
Top Universities
Top Companies
Top Countries
```

---

# Advantages

✅ Easy to understand

✅ Excellent for comparisons

✅ Works with categorical data

✅ Multiple styles available

✅ Very business-friendly

---

# Limitations

❌ Not suitable for continuous distributions

❌ Too many categories create clutter

❌ Can be misleading with bad scaling

❌ Doesn't show relationships like scatter plots

---

# Interview Questions

### What is a bar plot?

A chart that represents categorical data using rectangular bars whose height or length corresponds to values.

---

### Difference between bar plot and histogram?

| Bar Plot          | Histogram       |
| ----------------- | --------------- |
| Categorical Data  | Continuous Data |
| Gaps between bars | No gaps         |
| Comparison        | Distribution    |

---

### When should grouped bar plots be used?

When comparing multiple datasets across the same categories.

---

### When should stacked bar plots be used?

When showing both total value and composition simultaneously.

---

### Why are horizontal bar plots useful?

They improve readability when category labels are long.

---

# Summary

Bar plots are one of the most important visualization techniques in Exploratory Data Analysis.

They help:

* Compare categories
* Detect patterns
* Identify outliers
* Analyze compositions
* Present business insights clearly

Types of bar plots include:

1. Vertical Bar Plot
2. Horizontal Bar Plot
3. Grouped Bar Plot
4. Stacked Bar Plot
5. Percentage Stacked Bar Plot

Mastering bar plots is essential for dashboards, reporting, business analytics, and data storytelling.

---

# Histograms

## Introduction

A **Histogram** is a graphical representation of the distribution of numerical data.

Unlike a bar plot, which compares categories, a histogram shows:

* How data is distributed
* How often values occur
* Shape of the data
* Spread of the data
* Presence of outliers

Histograms are one of the most important visualization tools in **Exploratory Data Analysis (EDA)** because they help us understand the underlying structure of numerical variables.

---

# What is a Histogram?

A histogram groups numerical values into intervals called **bins** and counts how many observations fall inside each bin.

Example dataset:

```text
72
75
78
80
81
82
85
88
90
92
```

Histogram:

```text
Frequency
 ^
 |
 |      ████
 |    ███████
 |  ██████████
 |████████████
 +-------------------->
   70 80 90 100
```

---

## Histogram vs Bar Plot

| Histogram             | Bar Plot               |
| --------------------- | ---------------------- |
| Numerical Data        | Categorical Data       |
| Shows Distribution    | Shows Comparison       |
| Bins on X-axis        | Categories on X-axis   |
| Bars Touch Each Other | Bars Usually Have Gaps |
| Continuous Data       | Discrete Categories    |

---

# Why Histograms Are Important

Histograms help answer questions like:

* Is the data normally distributed?
* Is the data skewed?
* Are there multiple peaks?
* Are there outliers?
* How spread out is the data?

These insights are crucial before building machine learning models.

---

# Import Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

---

# Creating Sample Data

```python
np.random.seed(42)

data = np.random.normal(
    loc=100,
    scale=20,
    size=1000
)
```

---

## Understanding the Parameters

### loc

```python
loc = 100
```

Mean of distribution.

---

### scale

```python
scale = 20
```

Standard deviation.

---

### size

```python
size = 1000
```

Number of observations.

---

## Result

Generates:

```text
98
105
120
87
95
...
```

1000 values centered around 100.

---

# Basic Histogram

```python
plt.figure(figsize=(10,6))

plt.hist(data)

plt.title("Basic Histogram")

plt.xlabel("Values")
plt.ylabel("Frequency")

plt.show()
```

---

## Understanding plt.hist()

### Syntax

```python
plt.hist(data)
```

Automatically:

1. Creates bins
2. Counts observations
3. Draws histogram

---

# Understanding Histogram Components

---

## X-Axis

Represents value ranges.

Example:

```text
80-90
90-100
100-110
110-120
```

---

## Y-Axis

Represents frequency.

Example:

```text
40 observations
60 observations
90 observations
```

---

## Bars

Each bar represents:

```text
Frequency inside a bin
```

---

# What Are Bins?

Bins are intervals that group values.

Example:

Dataset:

```text
71
73
75
78
82
84
88
```

Bins:

```text
70-80
80-90
```

---

## Why Bins Matter

Too few bins:

```text
Oversimplified
```

Too many bins:

```text
Too noisy
```

Choosing appropriate bins is important.

---

# Custom Number of Bins

```python
plt.hist(
    data,
    bins=30
)
```

---

## What Happens?

Instead of automatic bins:

```text
30 intervals created
```

Provides more detailed visualization.

---

# Adding Bar Borders

```python
plt.hist(
    data,
    bins=30,
    edgecolor='black'
)
```

---

## Why Use Borders?

Makes bin boundaries easier to see.

Without borders:

```text
████████████
```

With borders:

```text
|██|██|██|██|
```

---

# Normalized Histogram

Instead of frequency, we can show probability density.

```python
plt.hist(
    data,
    density=True
)
```

---

## What Changes?

Y-axis becomes:

```text
Probability Density
```

instead of:

```text
Frequency
```

---

## Why Use Density?

Useful when comparing datasets of different sizes.

Example:

```text
Dataset A = 100 rows
Dataset B = 10,000 rows
```

Density allows fair comparison.

---

# Adding Mean Line

The mean helps identify the center.

```python
mean = np.mean(data)

plt.axvline(
    mean,
    color='red',
    linestyle='--'
)
```

---

## What Does axvline Do?

Creates a vertical line.

```text
        |
        |
--------|---------
      Mean
```

---

# Adding Median Line

```python
median = np.median(data)

plt.axvline(
    median,
    color='green',
    linestyle='--'
)
```

---

## Why Compare Mean and Median?

Helps detect skewness.

### Symmetric Data

```text
Mean ≈ Median
```

---

### Right Skewed Data

```text
Mean > Median
```

---

### Left Skewed Data

```text
Mean < Median
```

---

# Multiple Histograms

Comparing distributions.

---

## Create Second Dataset

```python
data2 = np.random.normal(
    120,
    20,
    1000
)
```

---

## Plot Together

```python
plt.hist(
    data,
    alpha=0.5,
    label='Data 1'
)

plt.hist(
    data2,
    alpha=0.5,
    label='Data 2'
)

plt.legend()
```

---

## Why Use alpha?

```python
alpha=0.5
```

Adds transparency.

Without transparency:

```text
Bars overlap completely.
```

With transparency:

```text
Both distributions visible.
```

---

# Understanding Distribution Shapes

Histograms reveal distribution shape.

---

# Normal Distribution

Also called:

```text
Bell Curve
```

Shape:

```text
      █
    ████
  ████████
████████████
  ████████
    ████
      █
```

Characteristics:

* Symmetric
* Mean ≈ Median
* Most common distribution

---

# Right Skewed Distribution

Shape:

```text
█████████
██████
████
██
█
█
```

Long tail to the right.

Characteristics:

```text
Mean > Median
```

Examples:

* Income
* Wealth
* House prices

---

# Left Skewed Distribution

Shape:

```text
      █
      █
     ██
   ████
██████████
```

Long tail to the left.

Characteristics:

```text
Mean < Median
```

---

# Uniform Distribution

All bins have similar frequency.

```text
████
████
████
████
████
```

Every value equally likely.

---

# Bimodal Distribution

Contains two peaks.

```text
███
██████
███

      ███
     █████
      ███
```

Indicates:

```text
Two separate groups
```

Example:

* Heights of males and females combined.

---

# Detecting Outliers

Outliers appear as isolated bars.

Example:

```text
████████████

          █
```

Possible causes:

* Errors
* Rare events
* Exceptional cases

---

# Measuring Spread

Histograms reveal variability.

---

## Narrow Histogram

```text
    ███
  ███████
███████████
```

Low variation.

---

## Wide Histogram

```text
██
████
██████
████
██
```

High variation.

---

# Interpreting Histograms

Always analyze:

### Center

Where is the peak?

---

### Spread

How wide is the distribution?

---

### Shape

Normal?
Skewed?
Uniform?

---

### Outliers

Any isolated observations?

---

### Number of Peaks

One peak?

```text
Unimodal
```

Two peaks?

```text
Bimodal
```

Multiple peaks?

```text
Multimodal
```

---

# 2D Histogram (Heatmap Histogram)

Used for two variables.

Example:

```python
plt.hist2d(
    x,
    y,
    bins=30
)
```

---

## Purpose

Shows frequency of:

```text
X and Y combinations
```

---

## Color Meaning

Darker color:

```text
Higher frequency
```

Lighter color:

```text
Lower frequency
```

---

# Real-World Applications

---

## Exam Scores

```text
Score Distribution
```

---

## Salaries

```text
Income Distribution
```

---

## Website Traffic

```text
Visitors Per Day
```

---

## Product Prices

```text
Price Distribution
```

---

## Stock Returns

```text
Daily Return Distribution
```

---

# Advantages

✅ Easy to understand

✅ Shows distribution clearly

✅ Detects skewness

✅ Detects outliers

✅ Reveals spread

✅ Essential for EDA

---

# Limitations

❌ Depends heavily on bin size

❌ Exact values not visible

❌ Can be misleading with poor bin selection

❌ Less effective for small datasets

---

# Interview Questions

### What is a histogram?

A graph showing the frequency distribution of numerical data using bins.

---

### Difference between histogram and bar chart?

| Histogram          | Bar Chart        |
| ------------------ | ---------------- |
| Numerical Data     | Categorical Data |
| Continuous         | Discrete         |
| Bars Touch         | Bars Have Gaps   |
| Shows Distribution | Shows Comparison |

---

### What are bins?

Intervals used to group numerical data.

---

### Why are histograms useful in EDA?

They help identify:

* Distribution shape
* Outliers
* Skewness
* Spread
* Data quality issues

---

### What is a bimodal histogram?

A histogram containing two peaks, indicating two separate groups in the data.

---

# Summary

Histograms are one of the most powerful tools in Exploratory Data Analysis.

They help us understand:

* Data distribution
* Central tendency
* Spread
* Skewness
* Outliers
* Number of modes

Key concepts:

1. Bins
2. Frequency
3. Density
4. Distribution Shape
5. Outlier Detection
6. Normal vs Skewed Data
7. 2D Histograms

A histogram is often the **first visualization a data analyst creates when exploring a numerical variable**.

---

# Pandas Library Demo (Jupyter Notebook Practical)

## Introduction

This practical session demonstrates all the Pandas concepts covered previously using a Jupyter Notebook.

Topics demonstrated:

* Pandas Series
* Pandas DataFrames
* Indexing
* Selection
* Filtering
* Operations on DataFrames

The objective is to move from theory to actual implementation and understand the outputs generated by Pandas.

---

# Importing Pandas

Before using Pandas, we must import the library.

```python
import pandas as pd
```

### Why use `pd`?

`pd` is simply an alias for Pandas.

Instead of writing:

```python
pandas.DataFrame()
```

we can write:

```python
pd.DataFrame()
```

which is shorter and more readable.

---

# Pandas Series Demonstration

---

## Creating a Series from a List

```python
s = pd.Series([10,20,30,40,50])

print(s)
```

### Output

```text
0    10
1    20
2    30
3    40
4    50
dtype: int64
```

---

## What Happened?

Pandas automatically created an index.

```text
Index → 0 1 2 3 4
Values → 10 20 30 40 50
```

Every Series contains:

* Index
* Values

---

# Series with Custom Index

Instead of numerical indices:

```python
s = pd.Series(
    [10,20,30,40,50],
    index=['A','B','C','D','E']
)
```

Output:

```text
A    10
B    20
C    30
D    40
E    50
```

---

## Why Custom Indexes?

More meaningful labels.

Example:

```text
Student Names
Product IDs
Employee IDs
Dates
```

instead of:

```text
0
1
2
3
```

---

# Series from Dictionary

```python
data = {
    'A':10,
    'B':20,
    'C':30
}

s = pd.Series(data)
```

Output:

```text
A    10
B    20
C    30
```

---

## Observation

Dictionary:

```text
Key → Index
Value → Data
```

Pandas automatically converts:

```python
{
 'A':10
}
```

into

```text
A    10
```

---

# Accessing Series Elements

---

## By Label

```python
s['B']
```

Output:

```python
20
```

---

## By Position

```python
s[1]
```

Output:

```python
20
```

---

## Slicing

```python
s[1:3]
```

Output:

```text
B    20
C    30
```

---

## Why Use Slicing?

Useful for:

* Selecting ranges
* Extracting subsets
* Data preprocessing

---

# Series Attributes

Every Series contains useful metadata.

---

## Index

```python
s.index
```

Output:

```text
Index(['A','B','C'])
```

---

## Values

```python
s.values
```

Output:

```python
array([10,20,30])
```

---

## Data Type

```python
s.dtype
```

Output:

```text
int64
```

---

## Importance

Helps understand:

* Structure
* Data storage
* Compatibility

---

# Series Operations

---

## Addition

```python
s1 + s2
```

Example:

```python
s1 = [10,20,30]
s2 = [1,2,3]
```

Result:

```text
11
22
33
```

---

## Scalar Multiplication

```python
s1 * 2
```

Output:

```text
20
40
60
```

---

## Why Important?

Used heavily in:

* Feature engineering
* Scaling
* Mathematical transformations

---

# Filtering Series

Example:

```python
s[s > 30]
```

Output:

```text
40
50
```

---

## What Happens?

Condition:

```python
s > 30
```

creates:

```text
False
False
False
True
True
```

Pandas returns only rows with:

```text
True
```

---

# Applying Functions

```python
s.apply(lambda x: x**2)
```

Output:

```text
100
400
900
1600
2500
```

---

## Why Use apply()?

Transforms every value.

Examples:

* Squaring
* Currency conversion
* Text processing
* Feature creation

---

# Handling Missing Values

---

## Check Missing Values

```python
s.isnull()
```

Output:

```text
False
False
True
False
```

---

## Remove Missing Values

```python
s.dropna()
```

---

### Before

```text
10
20
NaN
40
```

### After

```text
10
20
40
```

---

# Mixed Data Types

```python
s = pd.Series([
    10,
    "Hello",
    3.14,
    True
])
```

---

## Observation

A Series can contain:

* Integers
* Strings
* Floats
* Booleans

simultaneously.

Useful when dealing with real-world messy datasets.

---

# DataFrame Demonstration

---

## Creating DataFrame

```python
data = {
    "Name":["John","Mary","Alex"],
    "Age":[28,35,42],
    "City":["NY","LA","Chicago"]
}

df = pd.DataFrame(data)
```

---

## Output

| Name | Age | City    |
| ---- | --- | ------- |
| John | 28  | NY      |
| Mary | 35  | LA      |
| Alex | 42  | Chicago |

---

# DataFrame with Custom Index

```python
df = pd.DataFrame(
    data,
    index=['P1','P2','P3']
)
```

Output:

| Index | Name |
| ----- | ---- |
| P1    | John |
| P2    | Mary |
| P3    | Alex |

---

# Adding New Column

```python
df['Country'] = [
    'USA',
    'USA',
    'USA'
]
```

---

## Result

| Name | Age | City | Country |
| ---- | --- | ---- | ------- |
| John | 28  | NY   | USA     |

---

# DataFrame Information

---

## describe()

```python
df.describe()
```

Provides:

* Count
* Mean
* Std
* Min
* Max
* Quartiles

---

## Example Output

| Statistic | Age |
| --------- | --- |
| Count     | 3   |
| Mean      | 35  |
| Std       | 7   |
| Min       | 28  |

---

# info()

```python
df.info()
```

Shows:

* Number of rows
* Number of columns
* Data types
* Non-null counts

---

## Why Important?

Quick dataset overview.

Helps identify:

* Missing values
* Data types
* Dataset size

---

# Applying Functions to Columns

Example:

```python
df['Age'] = df['Age'].apply(
    lambda x: x + 1
)
```

---

## Result

Before:

```text
28
35
42
```

After:

```text
29
36
43
```

---

# Indexing DataFrames

---

## Single Column

```python
df['Name']
```

Returns:

```python
Series
```

---

## Multiple Columns

```python
df[
    ['Name','Age']
]
```

Returns:

```python
DataFrame
```

---

# Row Selection using loc

---

## Select Row

```python
df.loc['P1']
```

Returns:

```text
John
28
NY
```

---

## Multiple Rows

```python
df.loc[
    'P1':'P3',
    ['Name','Age']
]
```

---

# Row Selection using iloc

---

## Select Row by Position

```python
df.iloc[1]
```

Returns second row.

---

## Multiple Rows

```python
df.iloc[0:2]
```

Returns first two rows.

---

# Boolean Indexing

Example:

```python
df[
    df['Age'] > 30
]
```

---

## Output

Only rows where:

```text
Age > 30
```

---

# Selection Techniques

---

## Select Multiple Columns

```python
df[
 ['Name','Salary']
]
```

---

## Using loc

```python
df.loc[
    :,
    ['Name','Salary']
]
```

---

## Using iloc

```python
df.iloc[
    0:3,
    0:2
]
```

---

# Filtering DataFrames

---

## Single Condition

```python
df[
    df['Age'] > 35
]
```

---

## Multiple Conditions

```python
df[
 (df['Age'] > 35)
 &
 (df['Salary'] > 60000)
]
```

---

## OR Condition

```python
df[
 (df['Age'] > 35)
 |
 (df['Salary'] > 60000)
]
```

---

# isin()

```python
df[
    df['City'].isin(
        ['London','Tokyo']
    )
]
```

---

## Purpose

Checks membership.

Equivalent to:

```text
City == London
OR
City == Tokyo
```

---

# String Filtering

```python
df[
    df['Name']
    .str.startswith('A')
]
```

Returns:

```text
Alex
Alice
Andrew
```

---

# Query Method

```python
df.query(
    "Age > 35 and City != 'Tokyo'"
)
```

Provides cleaner filtering syntax.

---

# DataFrame Operations

---

## Arithmetic Operations

```python
df1 + df2
```

Performs:

```text
Element-wise Addition
```

---

## Scalar Operations

```python
df1 * 2
```

Multiplies every value.

---

# Creating New Columns

```python
df['C'] = df['A'].apply(
    lambda x: x**2
)
```

---

## Result

| A | C  |
| - | -- |
| 2 | 4  |
| 3 | 9  |
| 4 | 16 |

---

# applymap()

Apply function to every cell.

```python
df.applymap(
    lambda x: x*10
)
```

---

## Result

Every value multiplied by:

```text
10
```

---

# Grouping Data

```python
df.groupby(
    'Category'
).mean()
```

---

## Purpose

Creates groups and computes statistics.

Example:

```text
Category A → Mean
Category B → Mean
```

---

# Aggregation

```python
grouped.agg([
    'mean',
    'sum',
    'count'
])
```

Produces multiple summaries simultaneously.

---

# Merging DataFrames

```python
pd.merge(
    df1,
    df2,
    on='Key'
)
```

---

## Purpose

Combine datasets using common columns.

Similar to SQL JOIN operations.

---

# Joining DataFrames

```python
df1.join(df2)
```

Combines using indexes.

---

## Missing Values During Join

Missing matches become:

```text
NaN
```

which means:

```text
Not a Number
```

or missing value.

---

# Summary

This Pandas practical demonstrated:

### Series

* Creation
* Indexing
* Filtering
* Operations
* Missing values

### DataFrames

* Creation
* Selection
* Indexing
* Filtering
* Transformations

### Advanced Operations

* GroupBy
* Aggregation
* Merge
* Join

These operations form the foundation of real-world data cleaning, preprocessing, and exploratory data analysis.

---

# EDA Demo (Jupyter Notebook Practical)

## Introduction

This practical session demonstrates how Exploratory Data Analysis (EDA) is performed using Python.

The demo combines concepts from:

* Descriptive Statistics
* Correlation & Covariance
* Univariate Analysis
* Bivariate Analysis
* Categorical Data Analysis
* Outlier Detection
* Data Visualization

The goal is to understand how analysts explore a dataset before building machine learning models or generating business insights.

---

# Required Libraries

The demo uses multiple Python libraries.

```python
import numpy as np
import pandas as pd

from scipy import stats

import matplotlib.pyplot as plt
import seaborn as sns
```

---

## Why These Libraries?

### NumPy

Used for:

* Numerical computations
* Arrays
* Statistics

---

### Pandas

Used for:

* DataFrames
* Data manipulation
* Data analysis

---

### SciPy

Used for:

* Statistical functions
* Hypothesis testing
* Skewness
* Kurtosis
* Z-score

---

### Matplotlib

Used for:

* Plotting graphs
* Charts
* Visualizations

---

### Seaborn

Built on top of Matplotlib.

Provides:

* Better aesthetics
* Statistical visualizations
* Heatmaps
* Distribution plots

---

# Sample Numerical Dataset

```python
data = [2,4,4,4,5,5,7,9]
```

This dataset is used for computing summary statistics.

---

# Measures of Central Tendency

---

## Mean

```python
np.mean(data)
```

Formula:

\bar{x}=\frac{\sum x}{n}

Example:

```python
5.0
```

---

## Median

```python
np.median(data)
```

Middle value after sorting.

Result:

```python
4.5
```

---

## Mode

```python
stats.mode(data)
```

Result:

```python
4
```

because 4 appears most frequently.

---

# Measures of Dispersion

Dispersion measures how spread out the data is.

---

## Range

```python
np.max(data) - np.min(data)
```

Formula:

Range=Maximum-Minimum

Result:

```python
7
```

---

## Variance

```python
np.var(data)
```

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"s^2=\frac{\sum (x-\bar{x})^2}{n-1}"}}

Measures average squared distance from the mean.

---

## Standard Deviation

```python
np.std(data)
```

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"s=\sqrt{s^2}"}}

Provides spread in original units.

---

# Interquartile Range (IQR)

---

## Step 1: Compute Quartiles

```python
Q1 = np.percentile(data,25)

Q3 = np.percentile(data,75)
```

---

## Step 2: Compute IQR

```python
IQR = Q3 - Q1
```

Formula:

IQR=Q_3-Q_1

---

## Why IQR?

Used for:

* Outlier detection
* Robust spread measurement

Less sensitive to extreme values.

---

# Shape Measures

---

## Skewness

Measures asymmetry.

```python
stats.skew(data)
```

---

### Interpretation

| Value    | Meaning      |
| -------- | ------------ |
| 0        | Symmetric    |
| Positive | Right Skewed |
| Negative | Left Skewed  |

---

## Kurtosis

Measures tail heaviness.

```python
stats.kurtosis(data)
```

---

### Interpretation

| Value | Meaning     |
| ----- | ----------- |
| > 0   | Heavy Tails |
| < 0   | Light Tails |
| ≈ 0   | Normal-like |

---

# Correlation and Covariance Demo

Now we create two variables.

```python
x = np.random.rand(100)

y = x * 5 + np.random.normal(0,1,100)
```

---

## Why Create y Like This?

Because:

```python
y = 5x + noise
```

creates a strong positive relationship.

---

# Covariance

```python
np.cov(x,y)
```

Measures how variables move together.

---

## Interpretation

### Positive Covariance

```text
x ↑
y ↑
```

---

### Negative Covariance

```text
x ↑
y ↓
```

---

### Near Zero

No linear relationship.

---

# Correlation

```python
np.corrcoef(x,y)
```

Formula:

r=\frac{Cov(X,Y)}{\sigma_X\sigma_Y}

---

## Interpretation

| Correlation | Strength |
| ----------- | -------- |
| 0.0         | None     |
| 0.1–0.3     | Weak     |
| 0.3–0.7     | Moderate |
| 0.7–1.0     | Strong   |

---

# Using Pandas for Correlation

Convert data into DataFrame.

```python
df = pd.DataFrame({
    'X':x,
    'Y':y
})
```

---

## Correlation Matrix

```python
df.corr()
```

Output:

|   | X    | Y    |
| - | ---- | ---- |
| X | 1    | 0.89 |
| Y | 0.89 | 1    |

---

## Covariance Matrix

```python
df.cov()
```

Provides covariance values.

---

# Categorical Data Analysis

Create sample dataset.

```python
df = pd.DataFrame({
 'Category':['Electronics','Books','Clothing'],
 'Satisfaction':['Good','Poor','Excellent']
})
```

---

# Frequency Distribution

```python
df['Satisfaction'].value_counts()
```

Example Output:

```text
Good         40
Average      30
Excellent    20
Poor         10
```

---

# Relative Frequency

Convert counts into percentages.

```python
df['Satisfaction'].value_counts(
    normalize=True
)*100
```

Output:

```text
40%
30%
20%
10%
```

---

# Contingency Table

Used to analyze two categorical variables.

```python
pd.crosstab(
    df['Category'],
    df['Satisfaction']
)
```

---

## Example Output

|             | Good | Poor |
| ----------- | ---- | ---- |
| Electronics | 20   | 5    |
| Books       | 10   | 8    |

---

# Heatmap Visualization

Convert contingency table into heatmap.

```python
sns.heatmap(
    contingency_table,
    annot=True,
    cmap='YlOrRd'
)
```

---

## Interpretation

Darker colors:

```text
Higher Frequency
```

Lighter colors:

```text
Lower Frequency
```

---

# Univariate Analysis Demo

Univariate Analysis studies one variable at a time.

---

# Sample Dataset

```python
df = pd.DataFrame({
 'Age':...,
 'Income':...,
 'EducationYears':...
})
```

---

# Central Tendency for Every Column

```python
df.mean()
```

Provides average values.

---

# Dispersion Measures

```python
df.std()
```

Provides spread.

---

# Percentiles

```python
df.quantile(
    [0.25,0.5,0.75]
)
```

Returns:

* Q1
* Median
* Q3

---

# Frequency Table for Categorical Data

```python
df['Satisfaction'].value_counts()
```

Provides category counts.

---

# Skewness

```python
df.skew()
```

Used to determine asymmetry.

---

# Kurtosis

```python
df.kurtosis()
```

Used to determine tail heaviness.

---

# Outlier Detection Using Z-Score

---

## Formula

genui{"math_block_widget_always_prefetch_v2":{"content":"z=\frac{x-\mu}{\sigma}"}}

---

## Implementation

```python
z_scores = stats.zscore(df['Age'])
```

---

## Detect Outliers

```python
outliers = df[
    abs(z_scores) > 3
]
```

---

### Rule

```text
|Z| > 3
```

Potential Outlier

---

# Histogram Visualization

```python
df['Income'].hist()
```

---

## What We Learn

* Shape
* Center
* Spread
* Outliers

---

# Density Plot

```python
sns.kdeplot(df['Income'])
```

Provides smooth probability distribution.

---

# Box Plot

```python
sns.boxplot(
    x=df['Income']
)
```

---

## Why Boxplots?

Shows:

* Median
* Quartiles
* Outliers

in a single visualization.

---

# Bivariate Analysis Demo

Bivariate Analysis studies relationships between two variables.

---

# Correlation Matrix

```python
df.corr()
```

Example:

|        | Age   | Income |
| ------ | ----- | ------ |
| Age    | 1     | -0.03  |
| Income | -0.03 | 1      |

---

## Interpretation

Negative value:

```text
Weak Negative Relationship
```

---

# Scatter Plot

```python
plt.scatter(
    df['Age'],
    df['Income']
)
```

---

## Purpose

Visualize:

```text
Age vs Income
```

relationship.

---

# Contingency Table for Categorical Variables

```python
pd.crosstab(
    df['Department'],
    df['Satisfaction']
)
```

---

# Heatmap for Bivariate Categorical Analysis

```python
sns.heatmap(
    contingency_table,
    annot=True
)
```

Provides visual representation of category relationships.

---

# Key EDA Workflow Demonstrated

The notebook followed a standard EDA workflow:

### Step 1

Load Libraries

```python
numpy
pandas
scipy
matplotlib
seaborn
```

---

### Step 2

Understand Dataset

```python
head()
info()
describe()
```

---

### Step 3

Compute Summary Statistics

* Mean
* Median
* Mode
* Variance
* Standard Deviation

---

### Step 4

Study Relationships

* Correlation
* Covariance

---

### Step 5

Analyze Categories

* Frequency Tables
* Crosstabs

---

### Step 6

Detect Outliers

* Z-score
* Boxplot

---

### Step 7

Visualize Data

* Histograms
* Heatmaps
* Scatter Plots

---

# Summary

This practical demonstrated how EDA is performed in real-world projects.

Major concepts covered:

### Numerical Analysis

* Mean
* Median
* Mode
* Variance
* Standard Deviation
* IQR
* Skewness
* Kurtosis

### Relationship Analysis

* Covariance
* Correlation

### Categorical Analysis

* Frequency Tables
* Contingency Tables

### Outlier Detection

* Z-score Method

### Visualization

* Histograms
* Boxplots
* Heatmaps
* Scatter Plots

These techniques form the foundation of every data science, machine learning, and business analytics project.

---

# Matplotlib Demo (Practical)

## Introduction

This practical session demonstrates how to create visualizations using **Matplotlib**, one of the most important plotting libraries in Python.

The demo covers:

* Scatter Plots
* Line Plots
* Bar Plots
* Histograms
* Trend Lines
* Multiple Plots
* Annotations
* Heatmaps

The goal is to learn how to visualize data effectively during Exploratory Data Analysis (EDA).

---

# Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

For some advanced visualizations:

```python
import seaborn as sns
```

---

# Scatter Plot Demo

Scatter plots show relationships between two numerical variables.

---

## Generate Sample Data

```python
np.random.seed(42)

x = np.random.uniform(0,100,50)

y = 2*x + np.random.normal(0,20,50)
```

---

## Basic Scatter Plot

```python
plt.figure(figsize=(10,6))

plt.scatter(
    x,
    y,
    marker='o',
    s=50,
    color='blue',
    alpha=0.7
)

plt.title("Scatter Plot")
plt.xlabel("X")
plt.ylabel("Y")

plt.show()
```

---

## Parameters Explained

### marker

Controls point shape.

Examples:

```python
'o'   # circle
'*'   # star
'^'   # triangle
's'   # square
```

---

### s

Controls marker size.

```python
s = 50
```

---

### color

Controls point color.

```python
color='red'
```

---

### alpha

Controls transparency.

```python
alpha=0.7
```

Range:

```text
0 = invisible

1 = fully visible
```

---

# Multiple Scatter Plots

---

## Create Additional Dataset

```python
x2 = np.random.uniform(0,100,50)

y2 = 3*x2 + np.random.normal(0,15,50)
```

---

## Plot Both Datasets

```python
plt.figure(figsize=(10,6))

plt.scatter(x,y,label='Dataset 1')

plt.scatter(x2,y2,label='Dataset 2')

plt.legend()

plt.show()
```

---

## Why Use Multiple Scatter Plots?

Useful for:

* Comparing groups
* Comparing experiments
* Customer segmentation
* Cluster visualization

---

# Adding Trend Lines

Trend lines reveal overall direction.

---

## Fit Linear Model

```python
z = np.polyfit(x,y,1)

p = np.poly1d(z)
```

---

## Plot Trend Line

```python
plt.scatter(x,y)

plt.plot(
    x,
    p(x),
    'r--'
)

plt.show()
```

---

## Interpretation

### Positive Slope

```text
X ↑

Y ↑
```

Positive Relationship

---

### Negative Slope

```text
X ↑

Y ↓
```

Negative Relationship

---

# Line Plot Demo

Line plots visualize trends across ordered data.

---

## Generate Data

```python
x = np.linspace(0,10,100)

y1 = np.sin(x)

y2 = np.cos(x)
```

---

## Basic Line Plot

```python
plt.figure(figsize=(10,6))

plt.plot(x,y1)

plt.title("Sine Wave")

plt.xlabel("X")

plt.ylabel("Y")

plt.show()
```

---

# Multiple Line Plot

```python
plt.figure(figsize=(10,6))

plt.plot(
    x,
    y1,
    color='red',
    linestyle='--',
    linewidth=2,
    label='Sine'
)

plt.plot(
    x,
    y2,
    color='blue',
    linestyle=':',
    linewidth=2,
    label='Cosine'
)

plt.legend()

plt.show()
```

---

## Common Line Styles

```python
'-'   Solid

'--'  Dashed

':'   Dotted

'-.'  Dash-dot
```

---

# Custom Axis Limits

Used for zooming into a specific region.

---

## Example

```python
plt.xlim(2,8)

plt.ylim(-1,1)
```

---

## Add Grid

```python
plt.grid(True)
```

Produces easier-to-read charts.

---

# Annotations

Annotations highlight important points.

---

## Find Maximum Point

```python
max_y = np.max(y1)

max_x = x[np.argmax(y1)]
```

---

## Annotate

```python
plt.annotate(
    "Maximum",
    xy=(max_x,max_y),
    xytext=(4,1.2),
    arrowprops=dict(
        facecolor='black'
    )
)
```

---

## Uses

* Highlight peaks
* Highlight anomalies
* Explain business events
* Mark milestones

---

# Subplots

Subplots allow multiple charts inside one figure.

---

## Example

```python
fig, (ax1,ax2) = plt.subplots(
    1,
    2,
    figsize=(10,5)
)
```

---

## Plot Separately

```python
ax1.plot(x,y1)

ax1.set_title("Sine")

ax2.plot(x,y2)

ax2.set_title("Cosine")
```

---

## Result

```text
+----------+----------+

|  Sine    | Cosine   |

+----------+----------+
```

Useful for side-by-side comparison.

---

# Bar Plot Demo

Bar plots compare categories.

---

## Sample Data

```python
categories = [
    'A',
    'B',
    'C',
    'D',
    'E'
]

values = np.random.randint(
    10,
    100,
    5
)
```

---

## Basic Bar Plot

```python
plt.bar(
    categories,
    values
)

plt.show()
```

---

## Interpretation

Taller bar:

```text
Higher Value
```

Shorter bar:

```text
Lower Value
```

---

# Horizontal Bar Plot

```python
plt.barh(
    categories,
    values
)
```

Useful for:

* Long labels
* Rankings
* Large category names

---

# Grouped Bar Plot

Compare multiple products.

---

## Create Data

```python
product_A = [30,40,50,60]

product_B = [25,45,55,70]
```

---

## Plot

```python
x = np.arange(4)

width = 0.35

plt.bar(
    x-width/2,
    product_A,
    width
)

plt.bar(
    x+width/2,
    product_B,
    width
)
```

---

## Use Cases

* Sales comparison
* Department performance
* Before vs After analysis

---

# Stacked Bar Plot

Shows composition.

---

## Example

```python
plt.bar(
    categories,
    product_A
)

plt.bar(
    categories,
    product_B,
    bottom=product_A
)
```

---

## Interpretation

Each bar contains:

```text
Part A

+

Part B
```

Total height = Combined value

---

# Percentage Stacked Bar Plot

Shows proportions.

---

## Example

```python
percentage_A =
product_A/(product_A+product_B)

percentage_B =
product_B/(product_A+product_B)
```

---

Each bar totals:

```text
100%
```

Useful for composition analysis.

---

# Histogram Demo

Histograms visualize distributions.

---

## Generate Data

```python
np.random.seed(42)

data = np.random.normal(
    100,
    20,
    1000
)
```

---

## Basic Histogram

```python
plt.hist(data)

plt.show()
```

---

## Interpretation

### X-Axis

Value ranges

---

### Y-Axis

Frequency

---

### Bars

Number of observations inside each bin

---

# Custom Histogram

```python
plt.hist(
    data,
    bins=30,
    edgecolor='black'
)
```

---

## Why Adjust Bins?

More bins:

```text
More Detail
```

Fewer bins:

```text
Simpler View
```

---

# Mean and Median Lines

---

## Calculate

```python
mean = np.mean(data)

median = np.median(data)
```

---

## Plot

```python
plt.axvline(
    mean,
    color='red',
    linestyle='--'
)

plt.axvline(
    median,
    color='green',
    linestyle='--'
)
```

---

## Why?

Shows:

* Center of distribution
* Skewness
* Symmetry

---

# Density Histogram

```python
plt.hist(
    data,
    density=True
)
```

---

## Difference

Normal Histogram:

```text
Y = Frequency
```

Density Histogram:

```text
Y = Probability Density
```

---

# Multiple Histograms

Compare distributions.

---

## Example

```python
data2 =
np.random.normal(
    120,
    15,
    1000
)
```

---

```python
plt.hist(
    data,
    alpha=0.5,
    label='Dataset 1'
)

plt.hist(
    data2,
    alpha=0.5,
    label='Dataset 2'
)

plt.legend()
```

---

## Use Cases

* Customer comparison
* Experimental groups
* Before/After comparisons

---

# 2D Histogram (Heatmap Style)

Used for two variables.

---

## Generate Data

```python
x = np.random.normal(
    0,
    1,
    1000
)

y = np.random.normal(
    0,
    1,
    1000
)
```

---

## Plot

```python
plt.hist2d(
    x,
    y,
    bins=30,
    cmap='YlOrRd'
)

plt.colorbar()
```

---

## Interpretation

### Darker Color

```text
More Data Points
```

### Lighter Color

```text
Fewer Data Points
```

---

# Visualization Best Practices

## Scatter Plots

Use for:

* Correlation
* Relationships
* Clustering

---

## Line Plots

Use for:

* Time series
* Trends
* Sequential data

---

## Bar Plots

Use for:

* Categorical comparison
* Rankings
* Group comparison

---

## Histograms

Use for:

* Distribution analysis
* Outlier detection
* Understanding spread

---

# Complete Visualization Workflow

A data analyst typically follows:

### Step 1

Generate / Load Data

```python
pd.read_csv()
```

---

### Step 2

Understand Data

```python
head()

info()

describe()
```

---

### Step 3

Create Visualizations

* Scatter Plot
* Line Plot
* Bar Plot
* Histogram

---

### Step 4

Identify

* Trends
* Correlations
* Outliers
* Patterns

---

### Step 5
Generate Insights

Business decisions are made based on these visual findings.

---
# Module 4 Completed ✅

You now have notes for:

1. Pandas Series
2. Pandas DataFrame
3. DataFrame Indexing
4. DataFrame Selection
5. DataFrame Filtering
6. DataFrame Operations
7. Pandas Practical Demo
8. Numerical Descriptive Statistics
9. Categorical Descriptive Statistics
10. Correlation & Covariance
11. Univariate Analysis
12. Bivariate Analysis
13. EDA Practical Demo
14. Scatter Plots
15. Line Plots
16. Bar Plots
17. Histograms
18. Matplotlib Practical Demo

**Module 4 (Exploratory Data Analysis) is now 100% complete.** ✅