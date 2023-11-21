# CSV Best Practises

This document outlines best practices for creating CSV files for use with JSON-LD and CSV-W.

CSV files are a common way to share data. They are easy to create and edit, and can be opened in any spreadsheet program. However, they are not a standardised format, and can be difficult to work with programmatically. CSV files are also not self-describing, and require additional documentation to be understood.

By using the following guidelines, you can create CSV files that are easier to work with programmatically, and easier to understand for humans.

## CSV Basics

CSV files used in our service should be saved as UTF-8 encoded text files with a .csv extension. The first row should contain the column headers in lowecase and snake case (e.g. `column_header`). The following rows should contain the data for each column. Each row should be separated by a new line, and each column should be separated by a comma. When a column contains a comma, the entire column's values should be wrapped in double quotes (i.e. `"`).

## In brief

- Column headers should be in lowercase and snake case (e.g. `column_header`).
- Column headers should be unique, and should not contain any special characters (e.g. `!@#$%^&*()`).
- Related columns should have the same prefix (e.g. `geo_code`, `geo_name`, `geo_type` or `GBP_millions` and `GBP_millions_obs_status`, or even `observation` and `observation_status`).
- Dimension columns should be ordered first by time period, then by geography, then in descending order by volume of options in each column
- The Observation column should come after dimension columns, followed by an observation status column (if necesary) then measure, unit, and finally any attribute columns; this structure is called "tidy data"
- Measure columns are only required when there are multiple measures within the dataset (i.e. count and per capita)
- Unit columns are only required when there are multipl emeasures within the dataset (i.e. miles and GBP)
- Multiple obesrvation columns can exist where the measure type becomes the column title (e.g. a dataset of local authorities with three observation columns `population`, `per_capita_transport_spend`, and `per_capita_health_spend`)
- Ensure that the concepts used in the CSV files are clear and easily understandable to enhance human readability.
- Each observation should be uniquely addressable by filtering all columns (except the observation column itself) to one value per column.
- Columns should be ordered as follows: time period, geographic region, and then by descending count of options in each column.
- All columns should have values for every observation, except for the observation, observation status, or attribute type columns.

## Column

### Headers

Column headers should be in lowercase and snake case (e.g. `column_header`). This is to ensure consistency and readability. Column headers should also be unique, and should not contain any special characters (e.g. `!@#$%^&*()`). This even includes the pound sign (i.e. `£`), which should be replaced with `gbp` when appropriate.

Related columns should have the same prefix (e.g. `geo_code`, `geo_name`, `geo_type` or `millions_gbp` and `millions_gbp_status`, or even `observation` and `observation_status`). This is to ensure that related columns are grouped together when sorted alphabetically, and to make it easier to find concepts whose values are spread across multiple columns.

### Types

There are five types of columns, and each CSV file should contain at least two of them.

#### Observation

Observation columns should only contain numbers. Suppressed or missing values should be left blank. If a value is suppressed, there should be a related column explaining the suppressed value. This is referred to as an observation status column (i.e. a special kind of attribute column called "observation status"). When dealing with whole numbers (i.e. counts of people) and where there isn't scaling (i.e. thousands, millions, etc.), the number should be expressed as an integer. When dealing with decimal numbers (i.e. percentages, indexes, scaled currency counts), the number should be expressed as a decimal number.

**Note:** Try and keep the same number of decimal places for all values in a given column. This will make it easier to read, and not imply false precision.

#### Dimension

Dimension columns (otherwise known as factors) are used to identify the observation through a combination of concepts. Where each dimension in a CSV is filtered to a specific value there should only be one observation. In relational databases terminology all dimensions form to be a unique composite key. Some examples of dimensions are:

- `government_year` with one value being `2019-2020` (i.e. the period of `April 2019 to March 2020`)
- `geography_code` with one value being `E09000001` (i.e. the nation of `England`)
- `sic_2007` with one value being `01.11` (i.e. the concept `Growing of cereals (except rice), leguminous crops and oil seeds`)

To improve human readability and to ensure machine readability, ensure that codes in separate columns from the related human readable labels or descriptions. While the labels and additional information can be useful for humans, mixing them in the same column with codes makes users have to clean the data. It is also important to ensure that related columns are grouped together when sorted alphabetically, and to make it easier to find the human readable values.

A quick way to check if a column only contains related data and not unique identifiable is if you filter on a column and for every value you select another column will only ever have the same value for that row it is likely to help human readability.

For example the three columns prefixed with `geo_` are related in the table below, filtering on any of the three would only ever result in one value for the other two columns. The geo_code column is a unique identifier for the geography.

| geo_code  | geo_name          | geo_type               | value | ... |
|-----------|-------------------|------------------------|-------|-----|
| E08000006 | Salford           | Metropolitan Districts | 42    | ... |
| E92000001 | England           | Country                | 1337  | ... |
| K04000001 | England and Wales | England and Wales      |       | ... |

**Note:** Dimension columns must contain values for every row in the CSV file and not be blank (i.e. they must be dense)

#### Attributes

Attribute columns are used to describe the observation. They can be used to describe the observation as a whole. Most commonly the attribute columns are used to describe the absence or quality of an observation, these are commonly called "observation status" columns.

##### Observation status columns

When creating observation status columns a naming convetion helps users understand how they relate to the observation to the qualification. In this case for a given column name containing observations, the observation status column column should have the same name as the observation column plus `_obs_status` as a suffix. For example an observation column called `gva` should have a corresponding observation status called `gva_obs_status` which should be located to the right of the observation column.

#### Measure columns

Measure columns are used to describe the measurement method for the observation when a dataset has multiple meausres. For example, a dataset may have a measure of `£` and another measure of `£ per person`. In this case, the measure column would contain the measurement method for each observation. In many datasets the measure column is not required as there is only one measure.

Example measures include counts (e.g. of people, currency, companies), indexes, and frequency.

#### Unit columns

Unit columns are used to describe the unit of measurement for the observation when a dataset employes multiple units. The majority of the time there will be a single unit for each measure, but that is not always the case. Units are critical to comparability, allowing for conversions.

Example units include kilograms, miles, numbers, and percentages.

**Note:** Count is not a unit. It is a measure. The unit you want is "number".

**Note:** Indicies are only comparable to itself, therefore they are "unitless". You can compare miles and kilometres, but you cannot compare the FTSE 100 and the FTSE 250 values directly you can only compare their trends.

The units used should *always* be QUDT units unless no appropriate unit exists, which is exceptionally rare. Again, more often in statistics you're looking at numbers, rates, percentages, fractions, and frequencies.

##### Scaling units

Often in summary statistics publications units need to be scaled in order to control disclosure, or to maintain an appropriate level of granularity. Scaled units are especially common in publications like National Accounts, which contains the caucluated and reported spend of the Government of the United Kingdom and Northern Ireland, which totals over a trillion GBP (i.e. 1000000000000) and those figures are hard to sight read.

When scaling units take the base unit and suffix the multiplication factor preceeded by an underscore. Written and decimal representations are both acceptable For several examples,

- `GBP_millions` for millions of GBP (used in National acounts)
- `NUM_1000` for thousands (used in SOME PUBLICATION)
- `PER_tenths` (i.e. `PER`cent * 0.1 a.k.a tenths) for per thousands (used in SOME PUBLICATION)
- `ratio_0.001` for per thousands (used in SOME PUBLICATION)
- `L_100` for hectolitres (used in HMRC Alcohol Bulletin)

### Ordering

Ensuring that users can understand your CSV files is important. This is especially true when the

###

Concept Clarity: Ensure that the concepts used in the CSV files are clear and easily understandable to enhance human readability.

Unique Addressability: Each observation should be uniquely addressable by filtering all columns (except the observation column) to a value.

Column Order: Columns should be ordered as follows: time period, geographic region, and then by descending count of options in each column.

Value Completeness: All columns should have values for every observation, except for the observation, observation status, or attribute type columns.

Next steps could include:

Implementing these guidelines in your CSV file creation process.
Creating a script to validate CSV files against these guidelines.
Sharing these guidelines with your team and getting their feedback.
