# Tables

When writing your JSON-LD file to accompany your csv, you can write it in a way to include multiple csvs.

Below is an extract of two csv that will be described in the JSON-LD.

The first one is called football.csv.

| period_type | period_code | variable_name     | observation | measure | unit       |
| ----------- | ----------- | ----------------- | ----------- | ------- | ---------- |
| Year        | 2023        | Manchester United | 6           | billion | U.S dollar |
| Year        | 2023        | Liverpool         | 5.3         | billion | U.S dollar |
| Year        | 2023        | Manchester City   | 5           | billion | U.S dollar |
| Year        | 2023        | Chelsea           | 3.1         | billion | U.S dollar |
| Year        | 2023        | Tottenham Hotspur | 2.8         | billion | U.S dollar |

The second one is american_football.csv.

| period_type | period_code | variable_name        | observation | measure | unit       |
| ----------- | ----------- | -------------------- | ----------- | ------- | ---------- |
| Year        | 2023        | Dallas Cowboys       | 9           | billion | U.S dollar |
| Year        | 2023        | New England Patriots | 7           | billion | U.S dollar |
| Year        | 2023        | Los Angeles Rams     | 6.9         | billion | U.S dollar |
| Year        | 2023        | New York Giants      | 6.8         | billion | U.S dollar |
| Year        | 2023        | Chicago Bears        | 6.3         | billion | U.S dollar |

There are additional descriptors for human readability that you can add to your column sections. These include:

- `suppressOutput`  If true, suppresses any output that would be generated when converting cells in this column. The value of this property becomes the suppress output annotation for the described column. The default is false.(from w.3/org-tabular-metadata)
-  `propertyuri`, `valueurl`, `aboutUrl`  This metadata creates a relationship model between data in each column by different combinations of aboutUrl, propertyUrl, and valueUrl on existing columns, and defining new virtual columns to supply additional information. (from w.3/org-tabular-metadata)
- `label` this can be used for additional context.


## Table Breakdown

This section will help you how to write your table section of your JSON-LD file. But also, how to describe each column from your csv file. 

The first section will show you what needs to be done for each csv you are using.

The second section will go through a step by step process of writing and describing the columns in your csv.

## First Section

```JSON
"tables": [
    {
        "url": "football.csv",
        "tableSchema": {
            "columns": [
```                
                
In order to write a JSON-LD to include mulitple csvs. You need to include the csvs column details within a tables [ ] section. 

`url` This link property gives the single URL of the CSV file that the table is held in, relative to the location of the metadata document. (from w.3/org-tabular-metadata)

`tableSchema` An object property that provides a single schema description, used as the default for all the tables in the group. This may be provided as an embedded object within the JSON metadata or as a URL reference to a separate JSON object that is a schema description.(from w.3/org-tabular-metadata)

`columns` This will be the area where you describe each column from your csv.

## Second section

The way you write your JSON-LD should follow the same layout as your csv.

You write the JSON-LD runs from top to bottom and you should read your csv from left to right.

For example the first entry in the JSON-LD should be the column that appears on the left hand side of the csv.

### Time Period

```JSON              
                {
                    "title": "Period Type",
                    "name": "period_type",
                    "data_type": "string",
                    "suppressOutput": true
                },
```  
This section will look at the period type column. This entry should include a `title`, `name` and `data type`. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column. The suppress output uses the information you have provided.

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
                },
                
```
## Complete Output

```JSON
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
    },
    {
        "url": "american_football.csv",
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
                   "title": "American Football Team",
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
                }
            ]
        }
    }
]
```
