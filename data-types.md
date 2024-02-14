# Data types
There are four main data types that you can use to describe the data in your columns. These four are strings, decimal, float and boolean.

By describing your columns data type, this will help you explicitly state what the types are.

If you do not specify the datatype it will use a default. This would mean the data is not being represented correctly.

## String

The string datatype represents character strings in XML. The value space of string is the set of finite-length sequences of characters. 

Examples include – Year, Index, Unitless and Number.

```
"columns": [
    {
        "title": "Period Type",
        "name": "period_type",
        "datatype": "stirng"
    }
]
```
## Decimal
Decimal represents a subset of the real numbers, which can be represented by decimal numerals.

Examples include – 0.5, 1.7, 100.1.

```
"columns": [
    {
        "title": "Observation",
        "name": "observation",
        "datatype": "decimal"
    }
]
```
## Float
Float is patterned after the IEEE single-precision 32-bit floating point type.

Examples include – 0.1243, 12.5489 and 1000.63287.

```
"columns": [
    {
        "title": "",
        "name": "",
        "datatype": "float"
    }
]
```
## Boolean
Boolean has the value space required to support the mathematical concept of binary-valued logic.

Examples include - True, False, 0 and 1.

```
"columns": [
    {
        "title": "",
        "name": "",
        "datatype": "boolean"
    }
]
```
**NOTE** : If you have a column called period code this will need to be described as a string.
This is because if you have quarterly data (For example: 2020-Q2) this is now not purely numerical data.

**NOTE** : You need to be aware of whitespace. In both your csv and JSON file.


