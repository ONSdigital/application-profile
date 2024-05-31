# Publish CSV on the web (CSVW)

Our aim is to publish metadata in a machine readable and structured format alongside the statistical data.

Structured data formats, such as JSON-LD can be understood by search engines and are used for [search engine optimisation](https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data), with some search engines offering specific [dataset search functionality](https://developers.google.com/search/docs/advanced/structured-data/dataset) where structured metadata are provided using common vocabularies such as DCAT or [schema.org](https://schema.org/).

CSVWs are a way to provide structured metadata and tabular data, and are comprised of two parts:

- The CSV file itself, containing the tabular data
- A JSON file containing the metadata describing the CSV file

For guidance on how to create a high quality tidy data CSV file, see the [csv](./csv.md) guidance.

The JSON file is known as the CSVW metadata file, and is used to describe the structure of the CSV file, including the columns and their data types. It can also be used to provide additional information about the dataset, such as the title, description, and licensing information.

## Structural CSV metadata

The most basic of CSVW metadata will include the `tableSchema` properties with details of the columns in the CSV. Since the CSVW metadata specification includes several defaults for properties, a basic CSVW provides some implicit information, such as the file being comma delimited.

We can consider the following CSV file:

| geography      | period                  | sex    | life_expectancy |
| -------------- | ----------------------- | ------ | --------------- |
| W06000022      | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022      | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015      | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |
| W06000015      | 2004-01-01T00:00:00/P3Y | Female | 83.3            |
| ...            | ...                     | ...    | ...             |

Given the above CSV, a minimal CSVW metadata file would look as follows:

```json
{
    "@context": ["http://www.w3.org/ns/csvw", {"@language": "en"}],
    "url": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time.csv",
    "tableSchema": {
        "columns": [
            {
                "name": "geography",
                "titles": "geography",
                "datatype": "string"
            },
            {
                "name": "period",
                "titles": "period",
                "datatype": "string"
            },
            {
                "name": "sex",
                "titles": "sex",
                "datatype": "string"
            },
            {
                "name": "life_expectancy",
                "titles": "life_expectancy",
                "datatype": "decimal"
            }
        ]
    }
}
```

### Required properties

- `@context` It is a URL that points to the context in which the JSON-LD context for CSVW is written. This is a required property.
- `@language` is an object property which describes the default language for all literal strings within the metadata and tabular data.
- `url` This is the URL of the CSV file that the metadata is describing. This is a required property, it can be a relative URL if the CSV and metadata are in the same location.
- `tableSchema` This is the schema of the table, and contains the column definitions. This is a required property.
- `columns` This is an array of column definitions. Each column definition should contain a `name`, `titles`, and `datatype` property. The `name` property is the name of the column in the CSV file, the `titles` property is the human-readable title of the column, and the `datatype` property is the data type of the column.

### Data types

We use four main data types to describe data within our tabular data's columns. These four are strings, decimal, float and boolean.

By describing your columns data type, this will help you explicitly state what the types are.

If you do not specify the data type it will use a default. The default data type is a string (5.11.2 Derived dataypes - W3.org tabular data).

#### `string`

The string data type represents characters. The value space of string is the set of finite-length sequences of characters.

Examples include:

- `Dimension` columns are always strings. Examples include geography (i.e. geographies), period (i.e. time periods), or UK Standard International Classification (i.e. SIC). Dimensions need to be represented by at least two columns to be human and machine readable. A coded column and a corresponding human readable label.
- `Measure` column can contain values such as Index, Rate, or Count.
- `Unit` column must always contain values, e.g. Percent, Number, or Unitless.

```JSON
"columns": [
    {
        "title": "Period Type",
        "name": "period_type",
        "datatype": "string"
    }
]
```

##### Why use strings for all dimensions?

Consider a dataset is initially published only as annual data; however due to process improvements it can now be released quarterly. By defining the period_code dimension as strings, no changes are required to the schema to accept `2019-Q3` along with `2017`.

#### Decimal

Decimal represents a subset of the real numbers, which can be represented by decimal numerals.

Decimals help with delivering full precision for numerical data.

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

#### Float

[Float](https://en.wikipedia.org/wiki/Floating-point_arithmetic) is patterned after the IEEE single-precision 32-bit floating point type.

Float helps with high, but not full, levels of precision.

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

**Note** Implementations of float differ between operating systems and computer architectures. Floats are often more space efficient but if precision is required use decimal datatype.

#### Boolean

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

### Optional Properties

#### Foreign-key constraints

Publishers may wish to use the `foreignKey` property to assert relationships between different CSVs. See the [W3C CSVW specification](https://www.w3.org/TR/tabular-metadata/#foreign-key-reference-between-tables) for more information.

#### Machine Readability

CSVs are best serialised so that they can be interpreted by both humans and machines; however not all cells are useful for machine interpretability.

### Suppressing Cell Output

Consider the pattern often used for geographies:

| geography_code | geography_label        | geography_type           | value | ... |
| -------------- | ---------------------- | ------------------------ | ----- | --- |
| E08000006      | Salford                | Metropolitan Districts   | 42    | ... |
| E14001459      | Salford                | Westminster Constituency | 68    | ... |
| E92000001      | England                | Country                  | 1337  | ... |
| K04000001      | England and Wales      | England and Wales        | 1701  | ... |

In this case, `geography_label` and `geography_type` are useful for humans, and `geography_code` is useful for machines. In fact, using linked data, the `geography_label` and `geography_type` values can be looked up from the `geography_code` value. In order to have more efficience storage and interpretation of data, data which isn't machine readable should be suppressed.

Columns can be suppressed for interpretation by including the optional value `suppressOutput`. If this is true, it suppresses any output that would be generated when converting cells in this column into other formats. The default is false. [^column-properties]

In the following example only `geography_code` is kept for machine readability, and `geography_label`, and `geography_type` are suppressed.

```json
[
    {
        "name": "geography_code"
    },
    {
        "name": "geography_label",
        "suppressOutput": true,
    },
    {
        "name": "geography_type",
        "suppressOutput": true
    }
]
```

### Cell Value Templates

Cell value templates are used to map cell contents with additional information, we use a column's property `valueUrl` to provide machine readability to concepts such as geography codes.

In the example below a value of `E08000006` in the column `geography_code` would expand to <http://statistics.data.gov.uk/id/statistical-geography/E08000006> when interpreted by a CSVW aware client.

```json
[
    {
        "name": "geography_code",
        "valueUrl": "http://statistics.data.gov.uk/id/statistical-geography/{geography_code}"
    }
]
```

### Virtual Columns

In addition to suppressing cells which aren't required for machine readability, or making them machine readable, you can use virtual columns to create cells which are a combination of values of other cells for more advanced conversions.

In the example below there are three columns to describe time periods: `period_type`, `period_code`, `period_label`. The values are `month`, `2019-10`, and `October 2010` respectively. We use the virtual column `period` to create the machine readable time period. This example configuration resolves to <http://reference.data.gov.uk/id/month/2019-10> for machine readability.

```csv
period_type,period_code,period_label
month,2019-10,October 2010
```

```json
[
    {
        "name": "period_type",
        "suppressOutput": true
    },
    {
        "name": "period_code",
        "suppressOutput": true
    },
    {
        "name": "period_label",
        "suppressOutput": true
    },
    {
        "name": "period",
        "virtual": true,
        "valueUrl": "http://reference.data.gov.uk/id/{period_type}/{period_code}"
    }
]



## CSVs as self-contained datasets

A CSVW should additionally provide all the necessary metadata that would be needed for a user of the data to feature it in a `dcat:Catalog`.

The subject resource of a CSVW metadata file is typically a `csvw:Table` which corresponds to a CSV file. This CSVW file can be considered as a distribution of some `dcat:Dataset`.

When using a CSVW metadata file to describe some CSV, we recommend asserting the distribution relationship between the `csvw:Table` and the `dcat:Dataset`. The CSVW specification prohibits the use of the `@reverse` JSON-LD property, meaning we are unable to use the `dcat:distribution` property to achieve this, and instead rely upon its inverse `dcat:isDistributionOf`.

```mermaid
classDiagram
    class `Table` {
        a csvw:Table, dcat:Distribution, qb:DataSet
    }
    class `TableSchema` {
        a csvw:TableSchema
    }
    class `Column` {
        a csvw:Column
    }
    class `Dataset` {
        a dcat:Dataset
    }

    Table --> "1" Dataset: dcat.isDistributionOf
    Table --> "1..*" TableSchema: csvw.tableSchema
    TableSchema --> "1" Column: csvw.column
  
```

An example of a CSVW metadata file containing the relevant relationship with a `dcat:Dataset` could look as follows:

```json
{
    "@context": ["http://www.w3.org/ns/csvw", {"@language": "en"}],
    "@id": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time.csv",
    "url": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time.csv",
    "dcterms:title": "Life expectancy by local authority and sex (CSV)",
    "dcterms:description": "A CSV version of the life expectancy by local authority and sex dataset.",
    "dcat:isDistributionOf": {
        "@id": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time",
        "@type": "dcat:Dataset",
        "dc:title": "Life expectancy by local authority and sex",
        "dc:description": "The figures in this table are constructed from the estimated population and total deaths by single year / quinary age each year, based on a three year average. The expected years of life is the lifetime of a newborn person if they were subject throughout their lives to the average recorded death rate of the three year period. Such a calculation excludes future improvements to mortality rates."
    },
    "tableSchema": {
        "columns": [
            {
                "name": "geography",
                "titles": "geography",
                "datatype": "string"
            },
            {
                "name": "period",
                "titles": "period",
                "datatype": "string"
            },
            {
                "name": "sex",
                "titles": "sex",
                "datatype": "string"
            },
            {
                "name": "life_expectancy",
                "titles": "life_expectancy",
                "datatype": "decimal"
            }
        ]
    }
}
```

### Catalogue Metadata

Metadata improves the discoverability of datasets, in CSVWs the following properties are recommended. See [cataloguing.md](./cataloguing.md) for more details on how to use these properties. The purpose is to describe your data and provide additional context.

- `@language` You will be able to put the language of your choice.
- `dc:title` This is the title of your dataset. You need to keep this brief.
- `dcat:creator` You put the url of the creator of the dataset.
- `dc:abstract` Another string used to describe the dataset. This needs to be more detailed than the `title`.
- `dc:description` This is used to provide all the information you want to provide for the dataset.
- `dcat:license` This is where you place which license you are using.
- `dcat:keywords` You use this provide keywords, that can be used as searcahable terms.
- `dc:publisher` This is where you put the publisher of the dataset.
- `dcat:theme` If your dataset is part of an overreaching geography. Such as Economy, Business, Industry and Trade. This is where you oput the url of where the dataset is.

## Discoverability of CSVW

We recommend naming CSVW metadata files by appending `-metadata.json` to end the CSV's filename, so a CSV file named `countries.csv` would have a metadata file named `countries.csv-metadata.json`.[^csvw-default-metadata-location]

Where possible, we recommend serving CSV files with a `Link` header within the response with the `rel="describedby"` attribute pointing to the CSVW metadata file.

We recommend CSVW metadata is served with the media type `application/csvm+json`, and the CSV served with media type `text/csv`.

**NOTE** : You need to be aware of whitespace. In both your csv and JSON file.

For humans, we recommend keeping to a pattern of dimension_code, dimension_label in the csv; but when encoding for machines, we recommend suppressing the dimension_label if the dimension_code resolves to an existing resource with the label present.

- `propertyuri`, `valueurl`, `aboutUrl`  This metadata creates a relationship model between data in each column by different combinations of aboutUrl, propertyUrl, and valueUrl on existing columns, and defining new virtual columns to supply additional information. (from w.3/org-tabular-metadata)
- `label` this can be used for additional context.

### Table Breakdown

This section will help you how to write your table section of your JSON-LD file. But also, how to describe each column from your csv file.

The first section will show you what needs to be done for each csv you are using.

The second section will go through a step by step process of writing and describing the columns in your csv.

### How to write the table section

```JSON
"tables": [
    {
        "url": "football.csv",
        "tableSchema": {
            "columns": [ ...
```

`url` This link property gives the single URL of the CSV file that the table is held in, relative to the location of the metadata document. (from w.3/org-tabular-metadata)

`tableSchema` An object property that provides a single schema description, used as the default for all the tables in the group. This may be provided as an embedded object within the JSON metadata or as a URL reference to a separate JSON object that is a schema description.(from w.3/org-tabular-metadata)

`columns` This will be the geography where you describe each column from your csv.

### How to write the column section

The way you write your JSON-LD should follow the same layout as your csv.

You write the JSON-LD runs from top to bottom and you should read your csv from left to right.

For example the first entry in the JSON-LD should be the column that appears on the left hand side of the csv.

#### Time Period

```JSON
{
    "title": "Period Type",
    "name": "period_type",
    "data_type": "string",
    "suppressOutput": true
},
```  

This section will look at the period type column. This entry should include a `title`, and `data type`. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column. The suppress output uses the information you have provided.

```JSON
{
    "title": "Period Code",
    "name": "period_notation",
    "data_type": "string",
    "suppressOutput": true
},
```

This section will look at the period code column. This entry should include a `title`, `name` and `data type` The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column. The suppress output uses the information you have provided.

```JSON
{
    "title": "Variable Name",
    "name": "variable_name",
    "data_type": "string",
    "suppressOutput": true  
},{
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
}
```

### Putting it together

In this section, we combine the metadata of the overarching dataset, and its component tables; we provide details about the title of individual tables, and the table schema we have built before.

```JSON
{
    "@language": "en",
    "@context": "./draft_ons_context.json",
    "title": "Value of different countries sports teams",
    "creator": "https://www.gov.uk/government/organisations/office-for-national-statistics",
    "summary": "Value of different sports teams from the United Kingdom and the United States.",
    "description": "This dataset contains the most valuable top 5 sports team. They are from the United Kingdom and the United States as of 2023.",
    "license": "http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/",
    "keywords": [],
    "publisher": "https://www.gov.uk/government/organisations/office-for-national-statistics",
    "themes": "https://www.ons.gov.uk/peoplepopulationandcommunity/crimeandjustice/datasets/crimeinenglandandwalesannualsupplementarytables",
    "tables": [
        {
            "url": "football.csv",
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
                        "title": "Football Team",
                        "name": "variable_name",
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
                ]
            }
        }
    ]
}
```

## Footnotes

[^csvw-default-metadata-location]: <https://www.w3.org/TR/tabular-data-model/#default-locations-and-site-wide-location-configuration>
[^column-properties]: <https://www.w3.org/TR/tabular-metadata/#columns>
