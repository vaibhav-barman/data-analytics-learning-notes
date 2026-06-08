### Module 5 – Data Cleaning and Preparation

## Chapter 1: Reading and Writing Text Data

---

# Introduction

In any data analytics project, data rarely arrives in a clean and analysis-ready format. Most real-world datasets are stored in text-based files such as CSV, TSV, JSON, log files, and fixed-width files. Before any analysis, visualization, machine learning, or business intelligence activity can begin, analysts must first import data correctly and later export cleaned data for reporting, storage, or integration with other systems.

Python's **Pandas** library provides powerful tools for reading and writing data in multiple text formats. Understanding these tools is the first step toward building a professional data-cleaning workflow.

By the end of this chapter, you will be able to:

* Read data from various text formats.
* Handle delimiters and separators.
* Work with file encodings.
* Skip unnecessary rows and comments.
* Import only required columns.
* Process large files efficiently.
* Export datasets to multiple formats.
* Append data to existing files.
* Preserve special characters during export.

---

# Why Text Formats Matter

Text formats are among the most common methods for storing and exchanging data.

Common examples include:

| Format            | Description                    | Typical Use Case                |
| ----------------- | ------------------------------ | ------------------------------- |
| CSV               | Comma Separated Values         | Business reports, Excel exports |
| TSV               | Tab Separated Values           | Data interchange                |
| JSON              | JavaScript Object Notation     | APIs, Web Applications          |
| Fixed Width Files | Columns occupy fixed positions | Banking Systems                 |
| TXT               | Plain Text Files               | Logs and reports                |

Each format has unique characteristics and requires specific techniques for importing and exporting data correctly.

---

# Reading Data from CSV Files

## What is a CSV File?

CSV (Comma-Separated Values) is the most widely used format for storing tabular data.

Example:

```csv
Name,Age,Salary
John,25,50000
Alice,30,60000
Bob,28,55000
```

Each row represents a record.

Each comma separates fields.

---

## Reading a CSV File Using Pandas

```python
import pandas as pd

df = pd.read_csv("data.csv")

print(df.head())
```

### Explanation

* `read_csv()` imports the file.
* Pandas automatically detects commas.
* Returns a DataFrame.
* `head()` displays the first five rows.

---

## Verifying Imported Data

Always verify imported data immediately:

```python
print(df.head())
print(df.info())
print(df.shape)
```

This helps identify:

* Missing values
* Incorrect datatypes
* Unexpected columns
* Import errors

---

# Customizing CSV Imports

Real-world CSV files are often messy.

Consider this file:

```text
Name;Age;Salary
John;25;50000
Alice;30;60000
```

The separator is semicolon instead of comma.

---

## Custom Separator

```python
df = pd.read_csv(
    "data.csv",
    sep=";"
)
```

---

## Defining Header Row

```python
df = pd.read_csv(
    "data.csv",
    header=0
)
```

`header=0`

Means:

```text
First row contains column names.
```

---

## Custom Column Names

```python
df = pd.read_csv(
    "data.csv",
    names=["Employee","Age","Salary"]
)
```

Output:

```text
Employee Age Salary
John      25 50000
Alice     30 60000
```

---

# Reading TSV Files

## What is TSV?

TSV stands for:

```text
Tab Separated Values
```

Example:

```text
Name    Age    Salary
John    25     50000
Alice   30     60000
```

Instead of commas, tabs separate fields.

---

## Reading TSV Files

```python
df = pd.read_csv(
    "data.tsv",
    sep="\t"
)
```

### Explanation

`\t`

represents a tab character.

Pandas treats tabs as separators and creates a DataFrame.

---

# Reading Fixed Width Files

## What are Fixed Width Files?

In some systems, columns occupy fixed character positions.

Example:

```text
John     25  50000
Alice    30  60000
```

Instead of delimiters, positions define columns.

---

## Reading Fixed Width Files

```python
df = pd.read_fwf(
    "data.txt"
)
```

---

## Defining Column Positions

```python
df = pd.read_fwf(
    "data.txt",
    colspecs=[
        (0,10),
        (10,15),
        (15,25)
    ]
)
```

### Meaning

```text
Column 1 → Characters 0–10
Column 2 → Characters 10–15
Column 3 → Characters 15–25
```

Useful in:

* Banking
* Insurance
* Legacy systems

---

# Reading JSON Files

## What is JSON?

JSON stands for:

```text
JavaScript Object Notation
```

Example:

```json
[
  {
    "Name":"John",
    "Age":25
  },
  {
    "Name":"Alice",
    "Age":30
  }
]
```

Widely used by:

* APIs
* Web applications
* Cloud services

---

## Reading JSON

```python
df = pd.read_json(
    "data.json"
)
```

Pandas automatically converts JSON structures into tabular format.

---

## Why JSON Matters

Modern data analysts frequently collect data from:

* REST APIs
* Web services
* Cloud platforms

Most of these systems return JSON responses.

---

# File Encodings

## Why Encodings Matter

Computers store text as numbers.

An encoding determines how characters are represented.

Different systems may use different encodings.

---

## Common Encodings

| Encoding   | Usage              |
| ---------- | ------------------ |
| UTF-8      | Most common        |
| UTF-16     | Unicode systems    |
| ISO-8859-1 | Legacy systems     |
| Latin-1    | European languages |

---

## Example Problem

Without correct encoding:

```text
Café
```

May become:

```text
CafÃ©
```

---

## Reading With Encoding

```python
df = pd.read_csv(
    "data.csv",
    encoding="utf-8"
)
```

Alternative:

```python
df = pd.read_csv(
    "data.csv",
    encoding="latin1"
)
```

---

# Skipping Rows and Comments

Many files contain metadata.

Example:

```text
# Employee Salary Data
# Generated June 2026

Name,Age,Salary
John,25,50000
```

The first rows are not data.

---

## Skip Rows

```python
df = pd.read_csv(
    "data.csv",
    skiprows=2
)
```

Skips first two rows.

---

## Skip Specific Rows

```python
df = pd.read_csv(
    "data.csv",
    skiprows=[0,2]
)
```

Skips rows:

```text
0
2
```

---

## Ignore Comments

```python
df = pd.read_csv(
    "data.csv",
    comment="#"
)
```

Lines beginning with `#` are ignored.

---

# Selecting Specific Columns

Large files often contain hundreds of columns.

Reading unnecessary columns wastes:

* Memory
* CPU
* Processing time

---

## Read Selected Columns

```python
df = pd.read_csv(
    "employees.csv",
    usecols=[
        "Name",
        "Age",
        "Salary"
    ]
)
```

Only three columns are imported.

---

## Benefits

### Faster Processing

```text
Less memory consumption
```

### Better Performance

```text
Faster analysis
```

### Cleaner Workflow

```text
Only relevant information
```

---

# Reading Large Files Using Chunks

Sometimes datasets exceed available RAM.

Example:

```text
5 GB CSV File
```

Cannot load completely into memory.

---

## Chunk Processing

```python
chunks = pd.read_csv(
    "large.csv",
    chunksize=10000
)
```

---

## Processing Chunks

```python
for chunk in chunks:
    print(chunk.head())
```

Each chunk contains:

```text
10,000 rows
```

Only one chunk exists in memory at a time.

---

# Benefits of Chunking

### Reduced Memory Usage

```text
Handles very large files.
```

### Scalable Processing

```text
Works with Big Data.
```

### Better Performance

```text
Avoids RAM exhaustion.
```

---

# Chapter 1 Summary

In this chapter we learned:

### Reading Data

* CSV
* TSV
* JSON
* Fixed Width Files

### Import Options

* Custom separators
* Column selection
* Header handling
* File encoding
* Skipping rows
* Ignoring comments

### Large Data Handling

* Chunk processing
* Memory-efficient imports

### Key Principle

> Always inspect imported data before analysis.

A single incorrectly imported column can invalidate an entire analysis project.

---

**End of Chapter 1 – Reading Data from Text Formats**

Next, we'll continue with **Chapter 1 Part 2: Writing Data to Text Formats (CSV, TSV, JSON, TXT, Appending Data, Chunked Writing, Export Best Practices)**.

# Chapter 1: Writing Data to Text Formats

---

# Introduction

Reading data is only half of the data engineering and analytics workflow. After cleaning, transforming, validating, and analyzing data, analysts frequently need to export the results for:

* Reporting
* Data sharing
* Dashboard integration
* Machine learning pipelines
* Database loading
* Archival storage

Pandas provides powerful methods for writing DataFrames into various text formats including:

* CSV
* TSV
* JSON
* Plain Text
* Large chunked files

Understanding how to properly export data ensures data integrity and compatibility with other systems.

---

# Creating a Sample Dataset

Before exporting data, let's create a sample DataFrame.

```python
import pandas as pd

df = pd.DataFrame({
    "Name":["John","Alice","Bob"],
    "Age":[25,30,28],
    "Salary":[50000,60000,55000]
})

print(df)
```

Output:

```text
    Name   Age  Salary
0   John   25   50000
1  Alice   30   60000
2    Bob   28   55000
```

This DataFrame will be used throughout this chapter.

---

# Writing Data to CSV Files

## Why CSV?

CSV is the most commonly used format because:

* Human-readable
* Lightweight
* Supported by Excel
* Supported by databases
* Easy to exchange between systems

---

## Basic CSV Export

```python
df.to_csv("output.csv")
```

This creates:

```csv
,Name,Age,Salary
0,John,25,50000
1,Alice,30,60000
2,Bob,28,55000
```

Notice the extra index column.

---

# Removing the Index Column

Most business users do not want Pandas indexes.

```python
df.to_csv(
    "output.csv",
    index=False
)
```

Output:

```csv
Name,Age,Salary
John,25,50000
Alice,30,60000
Bob,28,55000
```

This is the preferred export format.

---

# Exporting Selected Columns

Sometimes only certain columns need to be shared.

Example:

```python
df.to_csv(
    "employees.csv",
    columns=["Name","Salary"],
    index=False
)
```

Output:

```csv
Name,Salary
John,50000
Alice,60000
Bob,55000
```

---

# Custom Delimiters

Not all systems use commas.

Some systems require:

```text
;
|
:
```

as separators.

---

## Semicolon-Separated Export

```python
df.to_csv(
    "employees.csv",
    sep=";",
    index=False
)
```

Output:

```text
Name;Age;Salary
John;25;50000
Alice;30;60000
```

Useful for European software systems.

---

# Writing Without Headers

Sometimes data must be appended to existing files.

Headers should not be repeated.

---

## Export Without Column Names

```python
df.to_csv(
    "output.csv",
    header=False,
    index=False
)
```

Output:

```text
John,25,50000
Alice,30,60000
Bob,28,55000
```

---

# Writing TSV Files

## What is TSV?

TSV stands for:

```text
Tab Separated Values
```

Instead of commas, tabs separate values.

---

## Export TSV

```python
df.to_csv(
    "output.tsv",
    sep="\t",
    index=False
)
```

Output:

```text
Name    Age    Salary
John    25     50000
Alice   30     60000
Bob     28     55000
```

---

# When TSV is Preferred

TSV is useful when data contains commas.

Example:

```text
"New York, USA"
```

In CSV this may require escaping.

TSV avoids many delimiter conflicts.

---

# Writing JSON Files

## Why JSON?

JSON is widely used in:

* APIs
* Web Applications
* Cloud Systems
* Data Exchange Platforms

---

## Basic JSON Export

```python
df.to_json(
    "output.json"
)
```

Produces machine-readable JSON.

---

# Records Orientation

Most commonly used format:

```python
df.to_json(
    "output.json",
    orient="records"
)
```

Output:

```json
[
  {
    "Name":"John",
    "Age":25,
    "Salary":50000
  },
  {
    "Name":"Alice",
    "Age":30,
    "Salary":60000
  }
]
```

This resembles API responses.

---

# Pretty Printed JSON

Raw JSON is difficult to read.

Use indentation for readability.

```python
df.to_json(
    "output.json",
    orient="records",
    indent=4
)
```

Output:

```json
[
    {
        "Name":"John",
        "Age":25,
        "Salary":50000
    }
]
```

Useful for:

* Debugging
* Documentation
* Configuration files

---

# Writing Plain Text Files

Sometimes simple text output is required.

Example:

* Logs
* Reports
* Quick exports

---

## Converting DataFrame to String

```python
text_data = df.to_string(
    index=False
)

print(text_data)
```

Output:

```text
Name   Age  Salary
John   25   50000
Alice  30   60000
Bob    28   55000
```

---

## Writing to TXT File

```python
with open(
    "output.txt",
    "w"
) as file:

    file.write(
        df.to_string(index=False)
    )
```

Generated file:

```text
Name   Age  Salary
John   25   50000
Alice  30   60000
Bob    28   55000
```

---

# Writing Large Datasets

Real-world datasets can contain millions of rows.

Example:

```text
10 Million Records
```

Writing everything at once may:

* Consume large memory
* Slow down processing
* Cause crashes

---

## Chunk-Based Writing

```python
large_df.to_csv(
    "large.csv",
    chunksize=10000,
    index=False
)
```

---

# What Happens?

Instead of writing:

```text
10 million rows at once
```

Pandas writes:

```text
10,000 rows
↓
10,000 rows
↓
10,000 rows
↓
...
```

This reduces memory consumption significantly.

---

# Appending Data to Existing Files

Normally:

```python
df.to_csv("sales.csv")
```

overwrites the file.

Sometimes we want to add new records instead.

---

## Append Mode

```python
df.to_csv(
    "sales.csv",
    mode="a",
    header=False,
    index=False
)
```

### Parameters

| Parameter    | Purpose                 |
| ------------ | ----------------------- |
| mode='a'     | Append                  |
| header=False | Avoid duplicate headers |
| index=False  | Exclude index           |

---

# Example

Existing file:

```csv
Name,Age,Salary
John,25,50000
```

After append:

```csv
Name,Age,Salary
John,25,50000
Alice,30,60000
Bob,28,55000
```

No data is overwritten.

---

# Character Encoding During Export

Encoding problems can destroy data.

Consider:

```text
Café
München
São Paulo
```

Without proper encoding:

```text
CafÃ©
MÃ¼nchen
SÃ£o Paulo
```

may appear.

---

## Export with UTF-8

```python
df.to_csv(
    "international.csv",
    encoding="utf-8",
    index=False
)
```

UTF-8 is recommended for almost all modern systems.

---

# Data Integrity Verification

Never assume exported files are correct.

Always verify.

---

## Re-Read Exported File

```python
exported = pd.read_csv(
    "output.csv"
)

print(exported.head())
```

---

## Verify Shape

```python
print(df.shape)
print(exported.shape)
```

Both should match.

---

## Verify Missing Values

```python
print(exported.isnull().sum())
```

---

## Verify Datatypes

```python
print(exported.dtypes)
```

A successful export preserves:

* Rows
* Columns
* Values
* Data types

---

# Common Export Mistakes

## Forgetting index=False

Creates unwanted index columns.

---

## Wrong Encoding

Causes corrupted characters.

---

## Repeated Headers During Append

Produces:

```csv
Name,Age
John,25
Name,Age
Alice,30
```

Always use:

```python
header=False
```

when appending.

---

## Wrong Separator

May cause import failures in other systems.

---

## Not Verifying Exports

Can lead to silent data corruption.

---

# Real-World Data Export Workflow

A professional analyst typically follows:

```text
Raw Data
     ↓
Import
     ↓
Clean
     ↓
Transform
     ↓
Validate
     ↓
Export
     ↓
Re-import Verification
     ↓
Final Delivery
```

Skipping verification is one of the most common causes of production data issues.

---

# Chapter 1 Complete Summary

In this chapter, we learned how to export data into various text formats using Pandas.

### Reading Concepts Covered

✅ CSV Files
✅ TSV Files
✅ JSON Files
✅ Fixed Width Files
✅ Encodings
✅ Skipping Rows
✅ Selecting Columns
✅ Chunk Processing

### Writing Concepts Covered

✅ CSV Export
✅ TSV Export
✅ JSON Export
✅ TXT Export
✅ Appending Files
✅ Chunked Writing
✅ Encoding Management
✅ Export Verification

### Most Important Functions

```python
pd.read_csv()
pd.read_json()
pd.read_fwf()

df.to_csv()
df.to_json()
df.to_string()
```

### Key Principle

> Data import and export are not just file operations. They are critical stages where data corruption, loss, and inconsistency can be introduced. Always validate what you read and what you write.

---

# End of Chapter 1 – Reading and Writing Text Data

**Next: Chapter 2 – Data Quality (Missing Data, Duplicates, Inconsistencies, Invalid Data, Outliers, Data Validation, and Data Quality Assessment Frameworks)**.

# Chapter 2: Data Quality

---

# Introduction

Data quality is one of the most critical aspects of data analytics. No matter how sophisticated the analysis, machine learning model, or visualization, poor-quality data will inevitably lead to poor-quality results.

There is a famous principle in data science:

> **Garbage In, Garbage Out (GIGO)**

This means that if inaccurate, incomplete, inconsistent, or invalid data is fed into an analytical process, the output will also be inaccurate and unreliable.

Before performing any analysis, a data analyst must assess and improve the quality of the data.

---

# Learning Objectives

After completing this chapter, you will be able to:

* Understand the concept of data quality.
* Identify common data quality issues.
* Assess dataset quality using Pandas.
* Detect missing values.
* Identify duplicate records.
* Find inconsistent formatting.
* Detect invalid data.
* Identify datatype problems.
* Detect outliers.
* Build a systematic data quality assessment workflow.

---

# What is Data Quality?

Data quality refers to the degree to which data is:

* Accurate
* Complete
* Consistent
* Reliable
* Relevant
* Timely

High-quality data accurately represents the real-world entities and events it describes.

Poor-quality data contains errors that can distort analysis and lead to incorrect business decisions.

---

# Why Data Quality Matters

Imagine a hospital database where:

```text
Patient Age = 250
Blood Group = XYZ
Email = abc.com
```

Clearly these values are invalid.

If such data is used:

* Doctors may make wrong decisions.
* Reports become inaccurate.
* Machine learning models fail.
* Regulatory compliance issues arise.

The same principle applies to:

* Marketing Analytics
* Finance
* Healthcare
* Manufacturing
* Government Systems
* E-Commerce

---

# Dimensions of Data Quality

Data quality is typically evaluated using several dimensions.

| Dimension    | Meaning                           |
| ------------ | --------------------------------- |
| Accuracy     | Data correctly represents reality |
| Completeness | Required data exists              |
| Consistency  | Data follows the same format      |
| Validity     | Data follows rules                |
| Uniqueness   | No unnecessary duplicates         |
| Timeliness   | Data is up-to-date                |

---

# Common Data Quality Problems

In real-world datasets, analysts frequently encounter:

1. Missing Data
2. Duplicate Records
3. Inconsistent Formatting
4. Invalid Values
5. Outliers
6. Datatype Mismatches
7. Inconsistent Naming Conventions

These seven problems account for the majority of data quality issues encountered during analysis.

---

# Data Quality Issue #1: Missing Data

## What is Missing Data?

Missing data refers to information that should exist but does not.

Examples:

```text
Name      Age
John      25
Alice
Bob       30
```

Alice's age is missing.

---

## Causes of Missing Data

### Data Entry Errors

```text
User forgot to fill a field.
```

### System Failures

```text
Sensor stopped recording.
```

### Survey Non-Response

```text
Participant skipped question.
```

### Data Corruption

```text
Value lost during transfer.
```

---

## Why Missing Data is Dangerous

Missing values can:

* Distort statistics
* Bias machine learning models
* Reduce sample size
* Create misleading conclusions

---

# Data Quality Issue #2: Duplicate Records

## What are Duplicates?

Duplicate records occur when the same information appears multiple times.

Example:

| ID | Name | Age |
| -- | ---- | --- |
| 1  | John | 25  |
| 1  | John | 25  |

Same record appears twice.

---

## Causes of Duplicates

### System Synchronization Problems

Multiple systems insert the same record.

### Data Imports

Files loaded multiple times.

### Human Errors

Users accidentally enter records twice.

### Database Issues

Improper constraints allow duplicates.

---

## Impact of Duplicates

Duplicates can:

* Inflate counts
* Distort averages
* Increase storage costs
* Produce misleading reports

---

# Data Quality Issue #3: Inconsistent Formats

Consider these entries:

```text
john
John
JOHN
```

All represent the same person.

Yet computers treat them as different values.

---

## Examples

### Date Formats

```text
01/05/2025
2025-05-01
May 1, 2025
```

---

### Phone Numbers

```text
9876543210
+91-9876543210
91 9876543210
```

---

### Country Names

```text
USA
U.S.A.
United States
```

---

## Impact

Inconsistent formats create problems during:

* Aggregation
* Grouping
* Merging
* Filtering
* Reporting

---

# Data Quality Issue #4: Invalid Data

Invalid data violates business rules.

Examples:

```text
Age = -10
```

```text
Age = 500
```

```text
Email = abc.com
```

```text
Gender = UnknownUnknown
```

---

## Sources

### Typing Mistakes

### Data Conversion Errors

### Poor Validation Rules

### Software Bugs

---

## Impact

Invalid data produces:

* Incorrect statistics
* Wrong business decisions
* Failed machine learning models

---

# Data Quality Issue #5: Outliers

Outliers are observations that differ significantly from the majority of data.

Example:

```text
Salary Dataset

30000
35000
40000
45000
50000
9000000
```

The last value is an outlier.

---

## Outliers Are Not Always Errors

Outliers may represent:

### Data Entry Errors

```text
Age = 999
```

or

### Genuine Extreme Cases

```text
CEO salary
```

Therefore:

> Never automatically remove outliers.

Investigate first.

---

# Data Quality Issue #6: Datatype Mismatches

Each column should have an appropriate datatype.

Examples:

| Column | Correct Type |
| ------ | ------------ |
| Age    | Integer      |
| Salary | Float        |
| Name   | String       |
| Date   | Datetime     |

---

## Common Problems

Age stored as text:

```text
"25"
"30"
"40"
```

instead of:

```python
25
30
40
```

---

## Consequences

Datatype mismatches can:

* Cause calculation errors
* Prevent aggregation
* Slow performance
* Break machine learning pipelines

---

# Data Quality Issue #7: Inconsistent Naming

Consider:

```text
John
john
JOHN
```

or

```text
New York
NewYork
new york
```

These represent the same entity but appear differently.

---

## Why It Matters

Grouping data becomes inaccurate.

Example:

```python
df["name"].value_counts()
```

May return:

```text
John     20
john      8
JOHN      3
```

Instead of:

```text
John     31
```

---

# Creating a Sample Dataset with Quality Issues

Let's intentionally create a dataset containing multiple quality problems.

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({

    "ID":[1,2,2,3,4],

    "Name":[
        "John",
        "Alice",
        "Alice",
        None,
        "JOHN"
    ],

    "Age":[
        25,
        30,
        30,
        np.nan,
        999
    ],

    "Email":[
        "john@gmail.com",
        "alice@gmail.com",
        "alice@gmail.com",
        "invalid_email",
        "JOHN@gmail.com"
    ]
})

df
```

This dataset contains:

* Missing values
* Duplicates
* Invalid email
* Outlier age
* Naming inconsistencies

---

# Assessing Missing Values

## Finding Missing Data

```python
df.isnull()
```

Returns a Boolean mask:

```text
True  → Missing
False → Not Missing
```

---

## Count Missing Values

```python
df.isnull().sum()
```

Example output:

```text
ID       0
Name     1
Age      1
Email    0
```

---

## Missing Value Percentage

```python
(df.isnull().sum() / len(df)) * 100
```

Output:

```text
Name    20%
Age     20%
```

This helps prioritize cleaning efforts.

---

# Assessing Duplicate Records

## Detecting Duplicates

```python
df.duplicated()
```

Returns:

```text
False
False
True
False
False
```

---

## Count Duplicates

```python
df.duplicated().sum()
```

Example:

```text
1
```

One duplicate exists.

---

## View Duplicate Rows

```python
df[df.duplicated(keep=False)]
```

Displays all duplicate records.

Useful before deciding whether to remove them.

---

# Assessing Datatypes

## View Column Types

```python
df.dtypes
```

Example:

```text
ID          int64
Name       object
Age       float64
Email      object
```

---

## Why This Matters

A column expected to be numeric may appear as:

```text
object
```

due to:

```text
25
30
abc
40
```

Mixed values force Pandas to treat the column as text.

---

# Selecting String Columns

```python
df.select_dtypes(include="object")
```

Useful for:

* Text cleaning
* Standardization
* Format validation

---

# Validating Email Format

A simple email validation rule:

```python
df["Email"].str.contains("@")
```

Returns:

```text
True
True
True
False
True
```

---

## Extract Invalid Emails

```python
df[
    ~df["Email"]
      .str.contains("@")
]
```

Output:

```text
invalid_email
```

---

# Assessing Naming Consistency

## Raw Frequencies

```python
df["Name"].value_counts(
    dropna=False
)
```

Output:

```text
Alice    2
John     1
JOHN     1
None     1
```

---

## Standardized Frequencies

```python
df["Name"] = (
    df["Name"]
    .str.lower()
)
```

Then:

```python
df["Name"].value_counts(
    dropna=False
)
```

Output:

```text
john     2
alice    2
None     1
```

Now frequencies reflect reality.

---

# Data Quality Assessment Workflow

Professional analysts usually follow this sequence:

```text
Import Dataset
        ↓
Check Shape
        ↓
Check Datatypes
        ↓
Check Missing Values
        ↓
Check Duplicates
        ↓
Validate Formats
        ↓
Detect Outliers
        ↓
Standardize Values
        ↓
Create Data Quality Report
```

---

# Data Quality Checklist

Before starting analysis, verify:

### Completeness

```text
Are values missing?
```

### Accuracy

```text
Do values make sense?
```

### Consistency

```text
Do formats match?
```

### Uniqueness

```text
Are duplicates present?
```

### Validity

```text
Do values follow rules?
```

### Datatypes

```text
Are columns stored correctly?
```

### Outliers

```text
Are unusual values investigated?
```

---

# Best Practices

### Never Trust Raw Data

Assume errors exist until proven otherwise.

### Profile Every Dataset

Always inspect:

```python
df.info()
df.describe()
df.head()
```

### Document Issues

Maintain a data-quality log.

### Fix Root Causes

Don't only clean symptoms.

### Validate After Cleaning

Always recheck quality metrics.

---

# Chapter 2 Summary

Data quality is the foundation of reliable analytics.

The most common quality issues are:

1. Missing Values
2. Duplicate Records
3. Inconsistent Formats
4. Invalid Data
5. Outliers
6. Datatype Problems
7. Naming Inconsistencies

Key functions introduced:

```python
df.isnull()

df.isnull().sum()

df.duplicated()

df.dtypes

df.select_dtypes()

df.value_counts()

df.str.contains()
```

Most importantly:

> Data cleaning begins with data quality assessment. Never start modeling or analysis before understanding the quality of your data.

---

# End of Chapter 2 – Data Quality

**Next: Chapter 3 – Handling Missing Data (Filtering Missing Values, Imputation, Mean/Median Replacement, Interpolation, SimpleImputer, and Best Practices)**.

# Chapter 3: Handling Missing Data

---

# Introduction

Missing data is one of the most common and challenging problems encountered in real-world datasets. Whether data comes from surveys, databases, sensors, APIs, financial systems, or web scraping, missing values are almost inevitable.

If not handled properly, missing data can:

* Distort statistical calculations
* Reduce dataset quality
* Introduce bias
* Lower machine learning performance
* Lead to incorrect business decisions

The goal of missing data handling is not simply to remove missing values but to make informed decisions about how they should be treated while preserving the integrity of the dataset.

---

# Learning Objectives

After completing this chapter, you will be able to:

* Understand different types of missing data.
* Detect missing values using Pandas.
* Filter missing data.
* Remove missing values strategically.
* Fill missing values using various imputation techniques.
* Apply interpolation methods.
* Use Scikit-Learn's SimpleImputer.
* Evaluate the impact of missing data handling.

---

# Understanding Missing Data

Missing data refers to values that should exist but are unavailable.

Example:

| Name  | Age | Salary |
| ----- | --- | ------ |
| John  | 25  | 50000  |
| Alice | NaN | 60000  |
| Bob   | 28  | NaN    |

Here:

```text
Age for Alice is missing
Salary for Bob is missing
```

---

# How Pandas Represents Missing Values

Pandas typically represents missing values as:

```python
NaN
```

which stands for:

```text
Not a Number
```

---

## Example

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({

    "Name":[
        "John",
        "Alice",
        "Bob"
    ],

    "Age":[
        25,
        np.nan,
        28
    ]
})

print(df)
```

Output:

```text
    Name   Age
0   John  25.0
1  Alice   NaN
2    Bob  28.0
```

---

# Why Missing Data Occurs

Missing values can arise from many situations.

## Human Error

```text
User forgot to enter information.
```

---

## Survey Non-Response

```text
Respondent skipped a question.
```

---

## Sensor Failure

```text
Device temporarily stopped collecting data.
```

---

## Data Corruption

```text
Value lost during transfer.
```

---

## System Integration Problems

```text
Field missing after merging datasets.
```

---

# Types of Missing Data

Understanding why data is missing is important before deciding how to handle it.

---

## MCAR – Missing Completely At Random

Missingness has no relationship with any variable.

Example:

```text
Random database failure removed some records.
```

Safe for many statistical methods.

---

## MAR – Missing At Random

Missingness depends on another variable.

Example:

```text
Income missing more frequently for younger users.
```

Requires careful treatment.

---

## MNAR – Missing Not At Random

Missingness depends on the missing value itself.

Example:

```text
High-income individuals refuse to disclose income.
```

Most difficult scenario.

---

# Creating a Sample Dataset

Throughout this chapter we will use:

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({

    "A":[
        1,
        2,
        np.nan,
        4,
        5
    ],

    "B":[
        np.nan,
        2,
        np.nan,
        4,
        5
    ],

    "C":[
        1,
        2,
        3,
        4,
        5
    ],

    "D":[
        np.nan,
        np.nan,
        np.nan,
        4,
        np.nan
    ]
})

print(df)
```

Output:

```text
     A    B   C    D
0  1.0  NaN  1  NaN
1  2.0  2.0  2  NaN
2  NaN  NaN  3  NaN
3  4.0  4.0  4  4.0
4  5.0  5.0  5  NaN
```

---

# Detecting Missing Values

Before handling missing data, we must identify where it exists.

---

## Using isnull()

```python
df.isnull()
```

Output:

```text
True  → Missing
False → Present
```

Example:

```text
       A      B      C      D
0  False   True  False   True
1  False  False  False   True
```

---

# Counting Missing Values

## Column-wise Count

```python
df.isnull().sum()
```

Output:

```text
A    1
B    2
C    0
D    4
```

---

# Percentage of Missing Data

A count alone isn't enough.

We often calculate percentages.

```python
(df.isnull().sum() / len(df)) * 100
```

Output:

```text
A    20%
B    40%
C     0%
D    80%
```

---

# Visualizing Missing Data

A quick visualization:

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(
    df.isnull(),
    cbar=False
)

plt.show()
```

This highlights missing values visually.

Useful for large datasets.

---

# Strategy 1: Removing Missing Data

The simplest solution:

```text
Remove incomplete observations.
```

---

# dropna()

Pandas provides:

```python
df.dropna()
```

Output:

```text
     A    B    C    D
3  4.0  4.0   4  4.0
```

Only complete rows remain.

---

# Advantages

✔ Easy

✔ Fast

✔ No assumptions

---

# Disadvantages

✘ Significant data loss

✘ Reduced sample size

✘ Potential bias

---

# Removing Rows with Any Missing Value

Default behavior:

```python
df.dropna()
```

Equivalent to:

```python
df.dropna(
    how="any"
)
```

Meaning:

```text
Remove row if ANY value is missing.
```

---

# Removing Rows Only if All Values are Missing

Sometimes less aggressive.

```python
df.dropna(
    how="all"
)
```

Meaning:

```text
Remove only completely empty rows.
```

---

# Removing Missing Values from Specific Columns

Suppose only columns A and B are critical.

```python
df.dropna(
    subset=["A","B"]
)
```

Only rows missing A or B are removed.

---

# Removing Columns Instead of Rows

Sometimes a column is mostly missing.

Example:

```text
Column D = 80% missing
```

May be better to remove the column.

---

## Drop Columns

```python
df.dropna(
    axis=1
)
```

Output:

```text
     C
0    1
1    2
2    3
3    4
4    5
```

Only complete columns remain.

---

# Measuring Data Loss

Always measure impact.

---

## Original Size

```python
original_rows = len(df)
```

---

## Clean Size

```python
clean_rows = len(
    df.dropna()
)
```

---

## Percentage Loss

```python
loss = (
    (original_rows - clean_rows)
    / original_rows
) * 100

print(loss)
```

Output:

```text
80%
```

This means:

```text
80% of data removed.
```

Usually unacceptable.

---

# Strategy 2: Filling Missing Values (Imputation)

Instead of removing data:

```text
Estimate missing values.
```

This process is called:

# Imputation

---

# Constant Value Imputation

Replace every missing value with the same value.

---

## Replace with Zero

```python
df.fillna(0)
```

Output:

```text
A  B  C  D
1  0  1  0
2  2  2  0
...
```

---

# Advantages

✔ Simple

✔ Fast

✔ Useful in some cases

---

# Disadvantages

✘ May distort distributions

✘ May introduce bias

---

# Mean Imputation

A common technique for numerical variables.

---

## Formula

\bar{x}=\frac{\sum x_i}{n}

---

## Example

```python
df.fillna(
    df.mean()
)
```

Suppose:

```text
Age:
20
25
30
NaN
35
```

Mean:

```text
27.5
```

Missing value becomes:

```text
27.5
```

---

# Advantages

✔ Preserves sample size

✔ Easy implementation

---

# Disadvantages

✘ Sensitive to outliers

✘ Reduces variance

---

# Median Imputation

Better when outliers exist.

---

## Example

```python
df.fillna(
    df.median()
)
```

Given:

```text
20
25
30
35
1000
```

Median:

```text
30
```

More robust than mean.

---

# Why Median is Often Preferred

Consider:

```text
20
25
30
35
1000
```

Mean:

```text
222
```

Median:

```text
30
```

Median better represents typical observations.

---

# Column-Specific Imputation

Different columns may require different methods.

Example:

```python
df["A"] = df["A"].fillna(
    df["A"].mean()
)
```

Only column A is modified.

---

# Mixed Imputation Strategies

Real datasets often contain:

* Numerical columns
* Categorical columns

Different methods may be needed.

---

## Example

```python
df["Age"] = (
    df["Age"]
    .fillna(
        df["Age"].mean()
    )
)

df["City"] = (
    df["City"]
    .fillna(
        "Unknown"
    )
)
```

---

# Dictionary-Based Imputation

Pandas allows multiple rules simultaneously.

```python
df.fillna({

    "Age":0,

    "Salary":50000,

    "City":"Unknown"

})
```

Each column receives its own fill value.

---

# Interpolation

Interpolation estimates missing values using neighboring observations.

Useful when data has an order:

* Time Series
* Sensor Data
* Financial Data

---

## Example

Original:

```text
10
20
NaN
40
50
```

---

## Interpolate

```python
df.interpolate()
```

Output:

```text
10
20
30
40
50
```

Pandas estimates:

```text
30
```

between:

```text
20 and 40
```

---

# Advantages of Interpolation

✔ Maintains trends

✔ Preserves continuity

✔ Useful for time series

---

# Limitations

✘ Not suitable for categorical data

✘ Requires logical ordering

---

# Using Scikit-Learn SimpleImputer

For machine learning pipelines, Scikit-Learn provides:

```python
SimpleImputer
```

---

## Import

```python
from sklearn.impute import SimpleImputer
```

---

## Mean Imputation

```python
imputer = SimpleImputer(
    strategy="mean"
)
```

---

## Fit and Transform

```python
df["A"] = imputer.fit_transform(
    df[["A"]]
)
```

---

# Available Strategies

| Strategy      | Purpose     |
| ------------- | ----------- |
| mean          | Average     |
| median        | Median      |
| most_frequent | Mode        |
| constant      | Fixed value |

---

# Example: Most Frequent Value

```python
SimpleImputer(
    strategy="most_frequent"
)
```

Useful for:

```text
Gender
City
Department
Category
```

---

# Comparing Imputation Methods

| Method        | Suitable For                 |
| ------------- | ---------------------------- |
| Constant      | Simple replacement           |
| Mean          | Symmetric numerical data     |
| Median        | Numerical data with outliers |
| Mode          | Categorical data             |
| Interpolation | Ordered data                 |
| SimpleImputer | Machine Learning Pipelines   |

---

# Best Practices for Missing Data

---

## Understand Why Data is Missing

Never blindly fill values.

Investigate causes first.

---

## Measure Missingness

Always calculate:

```python
df.isnull().sum()
```

and

```python
(df.isnull().sum()/len(df))*100
```

---

## Avoid Excessive Row Removal

Large losses may introduce bias.

---

## Use Median for Outlier-Prone Data

Median is often more robust.

---

## Use Interpolation for Time Series

Maintains temporal patterns.

---

## Document Every Decision

Always record:

```text
Column
Missing %
Method Used
Reason
```

---

# Real-World Missing Data Workflow

```text
Import Dataset
       ↓
Detect Missing Values
       ↓
Calculate Missing %
       ↓
Understand Cause
       ↓
Choose Strategy
       ↓
Apply Imputation
       ↓
Validate Results
       ↓
Proceed to Analysis
```

---

# Chapter 3 Summary

Missing data is one of the most common quality problems in analytics.

Key functions learned:

```python
df.isnull()

df.isnull().sum()

df.dropna()

df.fillna()

df.interpolate()

SimpleImputer()
```

Key strategies:

✅ Remove rows

✅ Remove columns

✅ Constant Imputation

✅ Mean Imputation

✅ Median Imputation

✅ Mode Imputation

✅ Interpolation

✅ Machine Learning Imputation

Most importantly:

> Missing data should never be handled automatically. The best treatment depends on why the data is missing and how much information would be lost by removing it.

---

# End of Chapter 3 – Handling Missing Data

**Next: Chapter 4 – Data Transformation (Removing Duplicates, Mapping, Replacing Values, Discretization, Encoding Categorical Data, Detecting Outliers, and Filtering Outliers).**

# Chapter 4: Data Transformation

---

# Introduction

After assessing data quality and handling missing values, the next major stage in data preparation is **data transformation**.

Data transformation involves converting raw, inconsistent, or poorly structured data into a format suitable for analysis, visualization, reporting, or machine learning.

In real-world datasets, transformation activities often consume **60–80% of a data analyst's time**.

Common transformation tasks include:

* Removing duplicate records
* Mapping values
* Replacing incorrect values
* Discretization and binning
* Encoding categorical variables
* Detecting outliers
* Filtering outliers

These operations improve data quality and make datasets suitable for advanced analytics.

---

# Learning Objectives

After completing this chapter, you will be able to:

* Detect and remove duplicate records.
* Apply mapping transformations.
* Replace values efficiently.
* Convert continuous variables into categories.
* Encode categorical variables.
* Detect outliers using statistical methods.
* Filter or treat outliers appropriately.
* Build a complete data transformation workflow.

---

# Section 1: Removing Duplicates

---

# What Are Duplicate Records?

Duplicates are records that appear multiple times within a dataset.

Example:

| ID | Name | Age |
| -- | ---- | --- |
| 1  | John | 25  |
| 1  | John | 25  |

The second row is an exact duplicate.

---

# Why Duplicates Are Dangerous

Duplicates can:

* Inflate counts
* Distort averages
* Bias machine learning models
* Increase storage requirements
* Produce incorrect reports

---

## Example

Without duplicates:

```text
Customers = 100
```

With duplicates:

```text
Customers = 120
```

Business decisions become inaccurate.

---

# Creating Sample Data

```python
import pandas as pd

df = pd.DataFrame({

    "ID":[1,2,2,3,4,4],

    "Name":[
        "John",
        "Alice",
        "Alice",
        "Bob",
        "David",
        "DAVID"
    ],

    "Age":[
        25,
        30,
        30,
        28,
        40,
        40
    ]
})

print(df)
```

---

# Detecting Duplicates

Pandas provides:

```python
df.duplicated()
```

Output:

```text
False
False
True
False
False
False
```

The third row is identified as a duplicate.

---

# Counting Duplicates

```python
df.duplicated().sum()
```

Output:

```text
1
```

---

# Viewing Duplicate Records

Before removing duplicates, inspect them.

```python
df[df.duplicated(keep=False)]
```

Output:

```text
   ID   Name   Age
1  2  Alice   30
2  2  Alice   30
```

---

# Removing Exact Duplicates

```python
df.drop_duplicates()
```

Output:

```text
Duplicate rows removed.
```

By default:

```text
First occurrence retained.
Subsequent duplicates removed.
```

---

# Resetting Index

After removing rows:

```python
df = (
    df
    .drop_duplicates()
    .reset_index(drop=True)
)
```

Produces clean sequential indexing.

---

# Partial Duplicates

Sometimes only certain columns define duplication.

Example:

```text
Same Name
Same Age
Different IDs
```

May still represent the same person.

---

## Using Subset

```python
df.drop_duplicates(
    subset=[
        "Name",
        "Age"
    ]
)
```

Now duplication is evaluated only on selected columns.

---

# Near Duplicates

Consider:

```text
David
DAVID
david
```

These represent the same person.

Computers treat them differently.

---

## Standardization

```python
df["Name"] = (
    df["Name"]
    .str.lower()
)
```

Result:

```text
david
david
david
```

Now duplicates become visible.

---

# Measuring Data Loss

```python
loss = (
    (len(df_original)
    -
    len(df_clean))
    /
    len(df_original)
) * 100
```

Example:

```text
15% records removed.
```

Always document this.

---

# Duplicate Removal Best Practices

✔ Inspect duplicates first

✔ Understand source of duplication

✔ Standardize text before checking

✔ Document removed records

✔ Measure data loss

---

# Section 2: Transforming Data Using Mapping

---

# What Is Mapping?

Mapping means transforming values according to predefined rules.

Example:

```text
A → Laptop
B → T-Shirt
C → Novel
```

Mapping is widely used for:

* Data standardization
* Feature engineering
* Category transformation
* Label creation

---

# Dictionary Mapping

---

## Sample Dataset

```python
df = pd.DataFrame({

    "Product":[
        "A",
        "B",
        "C"
    ]
})
```

---

## Mapping

```python
mapping = {

    "A":"Laptop",

    "B":"T-Shirt",

    "C":"Novel"
}
```

---

## Apply Mapping

```python
df["Product_Name"] = (
    df["Product"]
    .map(mapping)
)
```

Output:

```text
A → Laptop
B → T-Shirt
C → Novel
```

---

# Why Mapping Is Useful

Raw data:

```text
A
B
C
```

Business-friendly version:

```text
Laptop
T-Shirt
Novel
```

Much easier to interpret.

---

# Mapping Using Functions

More complex rules may require functions.

---

## Example

```python
def price_category(price):

    if price < 50:
        return "Low"

    elif price < 100:
        return "Medium"

    return "High"
```

---

## Apply Function

```python
df["Category"] = (
    df["Price"]
    .map(price_category)
)
```

Output:

```text
25 → Low
75 → Medium
150 → High
```

---

# Lambda Mapping

Small transformations often use lambda functions.

---

## Example

```python
df["Double_Price"] = (
    df["Price"]
    .map(lambda x: x * 2)
)
```

---

# Apply Method

Unlike map(), apply() works on rows.

---

## Example

```python
df["Discounted"] = (

    df.apply(

        lambda row:

        row["Price"] * 0.9

        if row["Category"]
           == "Electronics"

        else row["Price"],

        axis=1

    )

)
```

This allows multi-column logic.

---

# Transform Method

Transform performs operations across multiple columns.

---

## Example

```python
df.transform({

    "Product":str.lower,

    "Category":str.upper,

    "Price":lambda x:
        x.round(2)

})
```

Useful for bulk transformations.

---

# Section 3: Replacing Values

---

# Why Replace Values?

Data often contains:

* Errors
* Misspellings
* Placeholder values
* Legacy codes

Example:

```text
NY
New York
N.Y.
```

Should be standardized.

---

# Basic Replacement

```python
df.replace(

    "NY",

    "New York"

)
```

---

# Replacing Sentinel Values

Many systems use:

```text
-999
9999
99999
```

to indicate missing data.

---

## Convert to NaN

```python
import numpy as np

df.replace(

    -999,

    np.nan

)
```

---

# Multiple Replacements

```python
df.replace({

    "a":"A",

    "b":"B",

    "c":"C"

})
```

---

# Dictionary Mapping Replacement

```python
df["Level"] = (

    df["Level"]

    .replace({

        "X":"High",

        "Y":"Medium",

        "Z":"Low"

    })

)
```

---

# Conditional Replacement

Replace values based on conditions.

---

## Example

```python
df.loc[
    df["Age"] > 100,

    "Age"

] = np.nan
```

Invalid ages become missing values.

---

# Regular Expression Replacement

Useful for pattern matching.

---

## Example

```python
df.replace(

    r"[a-z]",

    "LOWER",

    regex=True

)
```

Regex enables advanced string transformations.

---

# In-Place Replacement

```python
df.replace(

    "d",

    "D",

    inplace=True

)
```

Modifies original DataFrame directly.

---

# Best Practices

✔ Preserve original data

✔ Validate replacements

✔ Use dictionaries for large mappings

✔ Document changes

---

# Section 4: Discretization and Binning

---

# What Is Discretization?

Discretization converts continuous numerical values into categories.

Example:

```text
Age = 24 → Young

Age = 42 → Adult

Age = 70 → Senior
```

---

# Why Discretize?

Benefits:

✔ Simpler interpretation

✔ Noise reduction

✔ Better visualization

✔ Improved model performance

✔ Easier business reporting

---

# Types of Binning

1. Equal Width Binning
2. Equal Frequency Binning
3. Custom Binning

---

# Equal Width Binning

Range divided into equal intervals.

---

## Formula

\text{Bin Width}=\frac{\text{Max}-\text{Min}}{\text{Number of Bins}}

---

## Example

```python
pd.cut(

    df["Age"],

    bins=5

)
```

Creates 5 equal-width intervals.

---

# Equal Frequency Binning

Each bin contains approximately the same number of observations.

---

## Example

```python
pd.qcut(

    df["Age"],

    q=5

)
```

Creates 5 quantile-based groups.

---

# Difference

Equal Width:

```text
Same interval size
Different frequencies
```

Equal Frequency:

```text
Different interval size
Same frequencies
```

---

# Custom Binning

Business rules often define categories.

---

## Example

```python
bins = [

    0,

    25,

    35,

    50,

    65,

    100

]
```

Labels:

```python
labels = [

    "Young",

    "Adult",

    "Middle-Aged",

    "Senior",

    "Elderly"

]
```

---

## Apply

```python
df["Age_Group"] = pd.cut(

    df["Age"],

    bins=bins,

    labels=labels

)
```

---

# Grade Binning Example

```python
score_bins = [

    0,

    60,

    70,

    80,

    90,

    100

]
```

```python
grades = [

    "F",

    "D",

    "C",

    "B",

    "A"

]
```

Produces:

```text
92 → A
75 → C
65 → D
```

---

# Chapter 4 Progress

We have completed:

✅ Removing Duplicates

✅ Mapping Transformations

✅ Replacing Values

✅ Discretization & Binning

**Next Part of Chapter 4 will cover:**

* Encoding Categorical Data
* Detecting Outliers
* Filtering Outliers
* End-to-End Data Transformation Workflow
* Chapter Summary

(Chapter 4 is large, so it is being split into two major parts.)

# Section 5: Encoding Categorical Data

---

# Introduction

Real-world datasets contain large amounts of categorical information.

Examples:

| Customer | Gender |
| -------- | ------ |
| John     | Male   |
| Sarah    | Female |

| Product | Category    |
| ------- | ----------- |
| Laptop  | Electronics |
| Shirt   | Clothing    |

Humans understand categories naturally.

Machines do not.

Most machine learning algorithms require numerical inputs.

Therefore, categorical variables must be converted into numbers.

This process is known as:

**Categorical Encoding**

---

# Why Encoding Is Important

Machine learning models cannot understand:

```text
Red
Blue
Green
```

or

```text
Small
Medium
Large
```

They require:

```text
0
1
2
```

or

```text
0 1 0
1 0 0
0 0 1
```

Encoding transforms categorical information into numerical representations.

---

# Types of Categorical Variables

There are two major categories.

---

## 1. Nominal Variables

Categories without order.

Examples:

```text
Red
Blue
Green
```

```text
India
USA
Japan
```

```text
Electronics
Books
Clothing
```

No category is larger or smaller.

---

## 2. Ordinal Variables

Categories with meaningful order.

Examples:

```text
Small
Medium
Large
```

```text
Poor
Average
Good
Excellent
```

```text
Low
Medium
High
```

Order matters.

---

# Sample Dataset

```python
import pandas as pd

df = pd.DataFrame({

    "Color":[
        "Red",
        "Blue",
        "Green",
        "Red",
        "Blue"
    ],

    "Size":[
        "Small",
        "Medium",
        "Large",
        "Small",
        "Large"
    ],

    "Category":[
        "A",
        "B",
        "C",
        "A",
        "B"
    ]

})

print(df)
```

Output:

```text
   Color   Size  Category

0   Red   Small      A

1  Blue  Medium      B

2 Green   Large      C

3   Red   Small      A

4  Blue   Large      B
```

---

# One-Hot Encoding

---

# What Is One-Hot Encoding?

Creates a separate binary column for every category.

Example:

```text
Color
------
Red
Blue
Green
```

Becomes:

```text
Color_Red
Color_Blue
Color_Green
```

---

# Mathematical Representation

```text
Red    → [1,0,0]

Blue   → [0,1,0]

Green  → [0,0,1]
```

Each category gets its own dimension.

---

# Using Pandas get_dummies()

```python
pd.get_dummies(
    df["Color"]
)
```

Output:

```text
   Blue  Green  Red

0     0      0    1

1     1      0    0

2     0      1    0

3     0      0    1

4     1      0    0
```

---

# Adding Prefix

```python
pd.get_dummies(
    df["Color"],
    prefix="Color"
)
```

Output:

```text
Color_Blue
Color_Green
Color_Red
```

Much easier to interpret.

---

# Encoding Multiple Columns

```python
pd.get_dummies(

    df,

    columns=[
        "Color",
        "Size"
    ]

)
```

Output columns:

```text
Color_Blue
Color_Green
Color_Red

Size_Small
Size_Medium
Size_Large
```

---

# Advantages

✔ No artificial ordering

✔ Works well for nominal data

✔ Highly interpretable

✔ Widely used

---

# Disadvantages

High cardinality problems.

Example:

```text
Country
```

with

```text
195 unique countries
```

becomes:

```text
195 new columns
```

Known as:

**Curse of Dimensionality**

---

# Label Encoding

---

# What Is Label Encoding?

Assigns an integer to every category.

Example:

```text
A → 0

B → 1

C → 2
```

---

# Using Scikit-Learn

```python
from sklearn.preprocessing import LabelEncoder

encoder = LabelEncoder()

df["Category_Encoded"] = (

    encoder.fit_transform(
        df["Category"]
    )

)
```

Output:

```text
A → 0

B → 1

C → 2
```

---

# Why It Can Be Dangerous

Machine learning models may interpret:

```text
2 > 1 > 0
```

which implies:

```text
C > B > A
```

even when no such relationship exists.

---

# When To Use

Good for:

✔ Tree-based algorithms

✔ Decision Trees

✔ Random Forest

✔ XGBoost

Use carefully elsewhere.

---

# Ordinal Encoding

---

# What Is Ordinal Encoding?

Used when categories have natural ordering.

Example:

```text
Small
Medium
Large
```

---

# Mapping Order

```python
size_map = {

    "Small":1,

    "Medium":2,

    "Large":3

}
```

---

# Apply Encoding

```python
df["Size_Code"] = (

    df["Size"]

    .map(size_map)

)
```

Output:

```text
Small  → 1

Medium → 2

Large  → 3
```

---

# Why Ordinal Encoding Works

Because:

```text
Small < Medium < Large
```

actually represents real-world ordering.

Unlike label encoding on nominal variables.

---

# Frequency Encoding

---

# Concept

Replace category with frequency of occurrence.

Example:

```text
Red
Red
Blue
Green
Red
```

Counts:

```text
Red   = 3

Blue  = 1

Green = 1
```

---

# Frequency Calculation

```python
frequency = (

    df["Color"]

    .value_counts()

)
```

Output:

```text
Red      3

Blue     1

Green    1
```

---

# Mapping Frequencies

```python
df["Color_Freq"] = (

    df["Color"]

    .map(frequency)

)
```

Result:

```text
Red   → 3

Blue  → 1

Green → 1
```

---

# Advantages

✔ Handles many categories

✔ Reduces dimensionality

✔ Useful for large datasets

---

# Disadvantages

Different categories may receive same frequency.

Example:

```text
Blue  = 5

Green = 5
```

Now machine cannot distinguish them.

---

# Comparing Encoding Methods

| Method    | Best For           | Creates Extra Columns |
| --------- | ------------------ | --------------------- |
| One-Hot   | Nominal Data       | Yes                   |
| Label     | Tree Models        | No                    |
| Ordinal   | Ordered Categories | No                    |
| Frequency | High Cardinality   | No                    |

---

# Choosing The Right Encoding

Use One-Hot when:

```text
Categories are nominal
Number of categories is small
```

Use Ordinal when:

```text
Natural ordering exists
```

Use Frequency when:

```text
Too many categories
```

Use Label when:

```text
Using tree-based models
```

---

# Common Interview Question

### Why not use Label Encoding for Colors?

Example:

```text
Red   → 0

Blue  → 1

Green → 2
```

Model interprets:

```text
Green > Blue > Red
```

which is false.

Colors have no natural order.

Therefore:

**One-Hot Encoding is preferred.**

---

# Real World Example

Customer Dataset:

```text
Gender
Country
Education
Income Level
```

Recommended:

```text
Gender     → One-Hot

Country    → Frequency

Education  → Ordinal

Income     → Ordinal
```

---

# Best Practices

✔ Understand category type first

✔ Use One-Hot for nominal variables

✔ Use Ordinal only when order exists

✔ Avoid unnecessary dimensions

✔ Validate encoding impact on model performance

---

# Section 6: Detecting Outliers

---

# What Are Outliers?

Outliers are observations significantly different from the rest of the dataset.

Example:

```text
10
12
11
13
15
14
1000
```

Clearly:

```text
1000
```

does not belong to the normal pattern.

It is an outlier.

---

# Why Outliers Matter

Outliers can:

✔ Distort averages

✔ Affect variance

✔ Mislead machine learning models

✔ Create misleading visualizations

✔ Indicate fraud or anomalies

---

# Sources of Outliers

---

## Data Entry Errors

```text
Age = 350
```

instead of

```text
Age = 35
```

---

## Sensor Errors

Equipment malfunction.

---

## Natural Extreme Values

Example:

```text
Millionaire income
```

inside average salary dataset.

---

## Fraudulent Activity

Credit card fraud detection often relies on outliers.

---

# Sample Dataset

```python
import numpy as np
import pandas as pd

np.random.seed(42)

data = np.random.normal(
    0,
    1,
    1000
)

outliers = np.array([
    8,
    9,
    -7,
    -8,
    10
])

data = np.concatenate([
    data,
    outliers
])

df = pd.DataFrame(
    {"Value":data}
)
```

---

# Visual Detection Using Boxplot

```python
import seaborn as sns

sns.boxplot(
    x=df["Value"]
)
```

Boxplots reveal extreme observations immediately.

---

# Understanding Boxplot

```text
|-----|====|-----|
```

Components:

* Minimum
* Q1
* Median
* Q3
* Maximum

Points outside whiskers:

```text
•
•
•
```

Potential outliers.

---

# Visual Detection Using Histogram

```python
sns.histplot(
    df["Value"],
    kde=True
)
```

Outliers appear far away from the main distribution.

---

# Z-Score Method

Measures how many standard deviations a value is from the mean.

Formula:

genui{"math_block_widget_always_prefetch_v2":{"content":"z=\frac{x-\mu}{\sigma}"}}

---

# Z-Score Interpretation

```text
z = 0
```

Exactly at mean.

```text
z = 1
```

1 standard deviation away.

```text
z = 3
```

3 standard deviations away.

---

# Common Rule

```text
|z| > 3
```

Potential outlier.

---

# Detecting Outliers

```python
from scipy import stats

z_scores = stats.zscore(
    df["Value"]
)

outliers = df[
    abs(z_scores) > 3
]
```

Returns extreme observations.

---

# Why Z-Score Works

For normal distributions:

```text
99.7%
```

of values lie within:

```text
±3 Standard Deviations
```

Anything beyond that is unusual.

---

**Next Part:** Filtering Outliers + Complete Data Transformation Workflow + Chapter 4 Summary.

# Section 7: Filtering Outliers

---

# Introduction

Detecting outliers is only the first step.

After identifying them, we must decide:

```text
Should we remove them?
Should we modify them?
Should we keep them?
```

This process is called:

**Outlier Treatment** or **Outlier Filtering**

---

# Why Filter Outliers?

Outliers can:

✔ Distort averages

✔ Affect standard deviation

✔ Reduce model accuracy

✔ Mislead visualizations

✔ Produce unreliable statistical conclusions

Example:

Dataset:

```text
10, 12, 11, 13, 14, 15
```

Mean:

```text
12.5
```

Add an outlier:

```text
10, 12, 11, 13, 14, 15, 1000
```

Mean becomes:

```text
153.57
```

Completely misleading.

---

# Important Warning

Not every outlier should be removed.

Example:

```text
Income Dataset
```

A billionaire is technically an outlier.

But:

```text
It is a valid observation.
```

Removing it would destroy useful information.

Always investigate before filtering.

---

# Sample Dataset

```python
import numpy as np
import pandas as pd

np.random.seed(42)

data = np.random.normal(
    0,
    1,
    1000
)

outliers = np.array([
    8,
    9,
    -7,
    -8,
    10,
    12,
    -10
])

data = np.concatenate([
    data,
    outliers
])

df = pd.DataFrame({
    "Value":data
})
```

---

# Visualize Before Filtering

```python
import seaborn as sns

sns.boxplot(
    x=df["Value"]
)
```

Observe:

```text
Main Data Cluster
+
Several Extreme Points
```

---

# Method 1: Filtering Using Z-Score

---

## Step 1: Calculate Z-Scores

```python
from scipy import stats

z_scores = stats.zscore(
    df["Value"]
)
```

---

## Step 2: Keep Normal Data

```python
filtered_df = df[
    abs(z_scores) < 3
]
```

Logic:

```text
Keep everything within
±3 standard deviations
```

---

## Step 3: Count Removed Records

```python
original_rows = len(df)

filtered_rows = len(filtered_df)

removed = original_rows - filtered_rows

print(removed)
```

---

# Visualize After Z-Score Filtering

```python
sns.boxplot(
    x=filtered_df["Value"]
)
```

Result:

```text
Most extreme points disappear
```

Distribution becomes cleaner.

---

# Method 2: Filtering Using IQR

---

# Why IQR?

Z-score assumes normal distribution.

Real-world datasets often aren't normally distributed.

IQR works better for:

✔ Skewed data

✔ Non-normal distributions

✔ Robust outlier detection

---

# Step 1: Calculate Quartiles

```python
Q1 = df["Value"].quantile(0.25)

Q3 = df["Value"].quantile(0.75)
```

---

# Step 2: Calculate IQR

```python
IQR = Q3 - Q1
```

---

# Step 3: Calculate Bounds

Formula:

Lower\ Bound = Q_1 - 1.5(IQR)

and

Upper\ Bound = Q_3 + 1.5(IQR)

---

# Step 4: Filter Data

```python
filtered_df = df[
    (df["Value"] >= lower_bound)
    &
    (df["Value"] <= upper_bound)
]
```

---

# Why IQR Is Often Preferred

Suppose:

```text
Dataset:
10
11
12
13
14
15
1000
```

Mean becomes heavily distorted.

Quartiles barely change.

Therefore:

```text
IQR is robust.
```

---

# Comparing Z-Score and IQR

| Feature                     | Z-Score | IQR         |
| --------------------------- | ------- | ----------- |
| Assumes Normal Distribution | Yes     | No          |
| Sensitive To Extreme Values | Yes     | No          |
| Easy To Compute             | Yes     | Yes         |
| Works For Skewed Data       | Poor    | Better      |
| Industry Usage              | Common  | Very Common |

---

# Alternative: Winsorization

Instead of deleting outliers:

Replace them.

Example:

```text
Original:

5
10
15
20
500
```

Winsorized:

```text
5
10
15
20
50
```

Extreme values are capped.

---

# Using NumPy

```python
import numpy as np

df["Value"] = np.clip(
    df["Value"],
    lower_bound,
    upper_bound
)
```

Benefits:

✔ No data loss

✔ Maintains sample size

✔ Reduces extreme influence

---

# Alternative: Log Transformation

Useful when data is heavily skewed.

Example:

```text
Income Data

1000
2000
5000
10000
1000000
```

Transform:

```python
import numpy as np

df["LogIncome"] = np.log(
    df["Income"]
)
```

Large values shrink dramatically.

---

# When NOT To Remove Outliers

Never automatically remove:

### Fraud Detection

Fraudulent transactions ARE outliers.

---

### Cybersecurity

Attack traffic is often outlier traffic.

---

### Medical Diagnosis

Rare diseases create unusual observations.

---

### Financial Markets

Market crashes are outliers.

Yet extremely important.

---

# Real-World Outlier Handling Workflow

```text
Collect Data
       ↓
Visualize
       ↓
Detect Outliers
       ↓
Investigate Cause
       ↓
Decide:
   Remove
   Cap
   Transform
   Keep
       ↓
Document Decision
```

---

# Best Practices

✔ Always visualize first

✔ Use multiple methods

✔ Understand business context

✔ Document every decision

✔ Avoid blind deletion

✔ Compare results before and after filtering

---

# Data Transformation Pipeline

At this point in the course, we have learned:

```text
Missing Values
Duplicates
Mapping
Replacement
Encoding
Binning
Outliers
```

These together form:

# Data Cleaning & Transformation Pipeline

```text
Raw Data
    ↓
Missing Value Treatment
    ↓
Duplicate Removal
    ↓
Data Standardization
    ↓
Encoding
    ↓
Binning
    ↓
Outlier Treatment
    ↓
Clean Dataset
```

---

# End-to-End Example

Raw Dataset:

| Name  | Age  | Salary | City   |
| ----- | ---- | ------ | ------ |
| John  | 25   | 50000  | Jaipur |
| John  | 25   | 50000  | Jaipur |
| Sarah | NULL | 60000  | Delhi  |
| Mike  | 300  | 70000  | Mumbai |

Issues:

```text
Duplicate
Missing Value
Outlier
```

Cleaning Process:

```python
# Remove duplicates

df = df.drop_duplicates()

# Fill missing age

df["Age"] = df["Age"].fillna(
    df["Age"].median()
)

# Remove outlier

Q1 = df["Age"].quantile(0.25)
Q3 = df["Age"].quantile(0.75)

IQR = Q3 - Q1

df = df[
    (df["Age"] >= Q1 - 1.5*IQR)
    &
    (df["Age"] <= Q3 + 1.5*IQR)
]
```

Result:

```text
Clean
Consistent
Reliable
Analysis-Ready Data
```

---

# Module 5 Summary

You have now covered:

### Data Quality

* Missing Data
* Duplicates
* Inconsistencies
* Invalid Formats
* Data Validation

### Reading & Writing Files

* CSV
* TSV
* JSON
* Text Files
* Encodings
* Chunk Processing

### Missing Data Handling

* Detection
* Removal
* Imputation
* Mean
* Median
* Interpolation
* SimpleImputer

### Data Transformations

* Duplicate Removal
* Mapping
* Replacement
* Encoding
* Binning
* Outlier Detection
* Outlier Treatment

### Data Aggregation

* Split
* Apply
* Combine
* GroupBy
* Aggregation Functions
* Transform
* Merge
* Join

---

# Module 5 Complete ✅

This finishes the entire **Data Cleaning & Preparation** module in a single consolidated set of notes.

Next module in the course is:

# Module 6 – Exploratory Data Analysis (EDA)

where you'll learn:

* Descriptive Statistics
* Distribution Analysis
* Correlation
* Covariance
* Univariate Analysis
* Bivariate Analysis
* Multivariate Analysis
* Data Visualization for EDA
* Statistical Insights Generation
* Business Interpretation of Data

This is the module where analysts start finding patterns and insights instead of just cleaning data.
