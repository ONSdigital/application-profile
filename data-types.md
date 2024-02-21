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

```
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

[Float](https://en.wikipedia.org/wiki/Floating-point_arithmetic) is patterned after the IEEE single-precision 32-bit floating point type.

Float helps with high levels of precision.

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

**Note** Never use float. As you cannot guarantee the accuracy.

**Note** Beaware that different machines offer different calculations.

## Boolean

Boolean has the value space required to support the mathematical concept of binary-valued logic.

Examples include - True and False.

```
"columns": [
    {
        "title": "",
        "name": "",
        "datatype": "boolean"
    }
]
```

**NOTE** : You need to be aware of whitespace. In both your csv and JSON file.

# Tables

When writing your JSON-LD file to accompany your csv, you can write it in a way to include multiple csvs.

Below is an extract of csv that will be described in the JSON-LD.

| period_type | period_code | period_label | area_code | area_label | area_type | observation | measure | unit | lcl_95 | ucl_95 |     obs_status |
| ----------- | ----------- | ------------ | --------- | ---------- | --------- | ----------- | ------- | ---- | ------ | ------ | ---------- | 
| government-year | 2011-2012 | 2011-2012 | K02000001 | United Kingdom | Country | 3.13 | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.11 | 3.15 |
| government-year | 2022-2023 | 2022-2023 | K02000001 | United Kingdom | Country | 3.23 | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.2 | 3.26 |
| government-year | 2021-2022 | 2021-2022 | K02000001 | United Kingdom | Country | 3.12 | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.1 | 3.15 |


In order to write a JSON-LD to include mulitple csvs. You need to include the csvs column details within a tables [ ] section. As described below.

You will need to use { } for each csv that you want to describe. Within these sections you should include a url which will contain the name of your csv. A table schema section  is next, where you describe the columns of your csv.

Each column of the csv will need to be described. Each entry should include a title, name and data type. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column.

There are additional descriptors that you can add to your column sections. These include:

- `suppressOutput` this will enable you to suppress the column from view.
- `valueurl` will contain a url.
- `propertyuri` will contain the `schema:url`.
- `label` this can be used for additional context.


```
{
                    "title": "",
                    "name": "",
                    "data_type": "",
                    "suppressOutput": true
                },
```

The right way to describe each column is shown below:

```
"tables": [
    {
        "url": "anxiety.csv",
        "tableSchema": {
            "columns": [
                {
                    "title": "Period Type",
                    "name": "period_type",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Period Code",
                    "name": "period_notation",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Period Label",
                    "name": "period_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "virtual": true,
                    "title": "Period",
                    "name": "period",
                    "valueurl": "http://reference.data.gov.uk/id/{period_type}/{period_notation}"
                },
                {
                    "title": "Area Code",
                    "description": "ONS code for area",
                    "name": "area_code",
                    "data_type": "string",
                    "valueurl": "http://statistical.data.gov.uk/id/statistical-geography/{area_code}",
                    "propertyuri": "schema:url"
                },
                {
                    "title": "Area label",
                    "name": "area_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Area type",
                    "name": "area_type",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Observation",
                    "name": "observation",
                    "datatype": "decimal",
                    "label": "Score"
                },
                {
                    "title": "Measure",
                    "name": "measure",
                    "data_type": "string"
                },
                {
                    "title": "Unit",
                    "name": "unit",
                    "data_type": "string"
                },
                {
                    "title": "Lower Confidence Limit (95%)",
                    "name": "lcl_95",
                    "datatype": "decimal"
                },
                {
                    "title": "Upper Confidence Limit (95%)",
                    "name": "ucl_95",
                    "datatype": "decimal"
                },
                {
                    "title": "Observation Status",
                    "name": "obs_status",
                    "data_type": "string"
                }
            ]
        }
    },
    {
        "url": "positive.csv",
        "tableSchema": {
            "columns": [
                {
                    "title": "Period Type",
                    "name": "period_type",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Period Code",
                    "name": "period_notation",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Period Label",
                    "name": "period_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "virtual": true,
                    "title": "Period",
                    "name": "period",
                    "valueurl": "http://reference.data.gov.uk/id/{period_type}/{period_notation}"
                },
                {
                    "title": "Area Code",
                    "description": "ONS code for area",
                    "name": "area_code",
                    "data_type": "string",
                    "valueurl": "http://statistical.data.gov.uk/id/statistical-geography/{area_code}",
                    "propertyuri": "schema:url"
                },
                {
                    "title": "Area label",
                    "name": "area_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Area type",
                    "name": "area_type",
                    "data_type": "string",
                    "suppressOutput": true
                },
                {
                    "title": "Observation",
                    "name": "observation",
                    "datatype": "decimal",
                    "label": "Score"
                },
                {
                    "title": "Measure",
                    "name": "measure",
                    "data_type": "string"
                },
                {
                    "title": "Unit",
                    "name": "unit",
                    "data_type": "string"
                },
                {
                    "title": "Lower Confidence Limit (95%)",
                    "name": "lcl_95",
                    "datatype": "decimal"
                },
                {
                    "title": "Upper Confidence Limit (95%)",
                    "name": "ucl_95",
                    "datatype": "decimal"
                },
                {
                    "title": "Observation Status",
                    "name": "obs_status",
                    "data_type": "string",
                }
```

