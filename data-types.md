# Data types

There are four main data types that you can use to describe the data in your columns. These four are strings, decimal, float and boolean.

By describing your columns data type, this will help you explicitly state what the types are.

If you do not specify the data type it will use a default. The default data type is a string (5.11.2 Derived dataypes - W3.org tabular data). This would mean the data is not being represented correctly.

## String

The string data type represents characters. The value space of string is the set of finite-length sequences of characters. 

Examples include: 
- `Dimension` columns would contain values such as Year, Quarter, County and Region. 
- `Measure` column would contain values such as Index. 
- `Unit` column would contain values such as Unitless and Number.

```JSON
"columns": [
    {
        "title": "Period Type",
        "name": "period_type",
        "datatype": "stirng"
    }
]
```

**NOTE** : If you have a column called period code this will need to be described as a string.
This is because if you have quarterly data (For example: 2020-Q2) this is now not purely numerical data.

## Decimal

Decimal represents a subset of the real numbers, which can be represented by decimal numerals.

Decimals help with delivering full precision for numerical data. This helps with publications like Gross Domestic Product (GDP).

Examples include – 0.5, 1.7, 100.1.

```JSON
"columns": [
    {
        "title": "Observation",
        "name": "observation",
        "datatype": "decimal"
    }
]
```
## Float

[Float](https://en.wikipedia.org/wiki/Floating-point_arithmetic) is patterned after the IEEE single-precision 32-bit floating point type.

Float helps with high levels of precision.

Examples include – 0.1243, 12.5489 and 1000.63287.


```JSON
"columns": [
    {
        "title": "",
        "name": "",
        "datatype": "float"
    }
]
```

**Note** Using float is space efficient in some databases, where perfect accuracy is required when working with real numbers we suggest you use the decimal datatype. Float calculations can differ between operating systems and computer architectures.



## Boolean

Boolean has the value space required to support the mathematical concept of binary-valued logic.

Examples include - True and False.

```JSON
"columns": [
    {
        "title": "",
        "name": "",
        "datatype": "boolean"
    }
]
```

**NOTE** : You need to be aware of whitespace. In both your csv and JSON file.



