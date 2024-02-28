# Tables

When writing your JSON-LD file to accompany your csv, you can write it in a way to include multiple csvs.

Below is an extract of csv that will be described in the JSON-LD.

| period_type     | period_code | period_label | area_code | area_label     | area_type | observation | measure                                               | unit     | lcl_95 | ucl_95 | obs_status |
| --------------- | ----------- | ------------ | --------- | -------------- | --------- | ----------- | ----------------------------------------------------- | -------- | ------ | ------ | ---------- |
| government-year | 2011-2012   | 2011-2012    | K02000001 | United Kingdom | Country   | 3.13        | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.11   | 3.15   |
| government-year | 2022-2023   | 2022-2023    | K02000001 | United Kingdom | Country   | 3.23        | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.2    | 3.26   |
| government-year | 2021-2022   | 2021-2022    | K02000001 | United Kingdom | Country   | 3.12        | Anxiety mean score (where 10 is 'completely anxious') | Unitless | 3.1    | 3.15   |


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
        "url": "anxiety.csv",
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
                    "title": "Period Label",
                    "name": "period_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
```
This section will look at the period label column. This entry should include a `title`, `name` and `data type`. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column. The suppress output uses the information you have provided.

### Virtual

A virtual entry is used when there is not a column in the original source.

```JSON
                {
                    "virtual": true,
                    "title": "Period",
                    "name": "period",
                    "valueurl": "http://reference.data.gov.uk/id/{period_type}/{period_notation}"
                },
```
Different from the other entries we have seen. You firstly start with `virtual` and set it to true. Next you have a `title` and `name`. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. Lastly you have `valueurl`. This  allows you to create a url indentifier with the information from a column or multiple columns. In this example we are creating a url with the information that is appearing in the period_type and period_notation column.


### Geography

```JSON
                {
                    "title": "Area Code",
                    "description": "ONS code for area",
                    "name": "area_code",
                    "data_type": "string",
                    "valueurl": "http://statistical.data.gov.uk/id/statistical-geography/{area_code}",
                    "propertyuri": "schema:url"
                },
```
This section will look at the area code column. This should include a `title`,`desciption`, `name` and `data type`. The title provies the human readable name of the column. The description provides extra information. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column.

There is also additional entries called `valueurl` and `properyuri`. The `valueurl` allows you to create a url indentifier with the information from a column or multiple columns. In this example we are creating a url with the information that is appearing in the area_code column.

```JSON

                {
                    "title": "Area label",
                    "name": "area_label",
                    "data_type": "string",
                    "suppressOutput": true
                },
```
This section will look at the area label column. This entry should include a `title`, `name` and `data type`. The title provies the human readable name of the column. The name provides the machine readable name of the column. This should be in `snake_case`. The data type provides the detail of what data type is being represented in the column. The suppress output uses the information you have provided.

Below are further examples of what needs to be included in the JSON-LD file that matches our previous csv.

```JSON
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
```
## Complete Output

```JSON
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