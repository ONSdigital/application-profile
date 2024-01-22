# CSV Best Practises

This document outlines best practices for creating CSV files for use with JSON-LD and the CSV-W vocabualarly.

CSV files are a common way to share data. They are easy to create and edit, and can be opened in any spreadsheet program. However, they are not a standardised format, and can be difficult to work with programmatically. CSV files are also not self-describing, and require additional documentation to be understood.

By using the following guidelines, you can create CSV files that are easier to work with programmatically, and easier to understand for humans with or without the JSON-LD document.

## CSV Basics

CSV files used in our service should be saved as UTF-8 encoded text files with a .csv extension. The first row should contain the column headers in lowecase and snake case (e.g. `column_header`). The following rows should contain the data for each column. Each row should be separated by a new line, and each column should be separated by a comma. When a column contains a comma, the entire column's values should be wrapped in double quotes (i.e. `"`).

## In brief

- Column headers should be in lowercase and snake case (e.g. `column_header`).
- Column headers should be unique, and should not contain any special characters (e.g. `!@#$%^&*()`).
- Related columns should have the same prefix (e.g. `geo_code`, `geo_name`, `geo_type` or `GBP_millions` and `GBP_millions_obs_status`, or even `observation` and `observation_status`).
- Columns should be ordered as follows:
    1. Dimension columns, order first by time period, then by geography, then in descending order by volume of options in each column (i.e. a column with 17 values would come before a column with 3 values).
    2. Obsevation column.
    3. Measure column(s). (e.g. count and spending per capita)
    4. Unit column. (e.g. number, GBP, miles per hour, portion, percent)
    5. Literal attribute columns providing model output (e.g. upper confidence level, sample_size, standard deviation).
    6. Observation status column (if necessary).
    7. All other attribute columns.
- TODO: DO I ACTUALLY WANT THIS? Multiple obesrvation columns can exist where the measure type becomes the column title (e.g. a dataset of local authorities with three observation columns `population`, `per_capita_transport_spend`, and `per_capita_health_spend`). This is not recommended as it as it an advanced representation and makes expressing the data as machine readble more complicated, but it is allowed.
- Ensure that the concepts used in the CSV files are clear and easily understandable to enhance human readability.
- Each observation should be uniquely addressable by filtering all dimensions to a given value. If more than one observation is returned, then there needs to be additional dimensions to make the observation addressable.
- All dimensions, measures, and unit columns should have values for every observation. These columns must be "dense".

## Column

### Headers

Column headers should be in lowercase and snake case (e.g. `column_header`). This is to ensure consistency and readability. Column headers should also be unique, and should not contain any special characters (e.g. `!@#$%^&*()`). This even includes the pound sign (i.e. `£`), which should be replaced with `gbp` when appropriate.

Related columns should have the same prefix (e.g. `area_code`, `area_label`, `area_type` or `time_period_type`, `time_period_code`, `time_period_label`, or even `observation` and `observation_status`), and should be adjancent. This is to ensure that related columns are grouped together when sorted alphabetically, and to make it easier to find concepts whose values are spread across multiple columns.

**Note** When expressing a dimension which has a label and a code, the code should come first, followed by the label; in the case of area geography, you can add an additional value which helps disambiguates geography labels by providing the geography type which would only be disambiguated by the geography code.

TODO: Provide an example of a geography code, geography label, and geography type where the geography type/code is required to disambiguate the geography label.

### Types

There are five types of columns, and each CSV file should contain at least two of them.

#### Observation

Observation columns must only contain numbers. Suppressed or missing values must be left blank. If a value is suppressed, there should be a related column explaining the suppressed value. This is referred to as an observation status column (i.e. a special kind of attribute column called "observation status"). When dealing with whole numbers (i.e. counts of people) and where there isn't scaling (i.e. thousands, millions, etc.), the number should be expressed as an integer. When dealing with decimal numbers (i.e. percentages, indexes, scaled currency counts), the number should be expressed as a decimal number.

**Note:** Try and keep the same number of decimal places for all values in a given column. This will make it easier to read, and not imply false precision.

#### Dimension

Dimension columns (otherwise known as factors or concepts) are used to identify the observation through a combination of concepts. Where each dimension in a CSV is filtered to a specific value there should only be one observation. In relational databases terminology all dimensions combine to a composite key. Some examples of dimensions are:

- `government_year` with one value being `2019-2020` (i.e. the period of `April 2019 to March 2020`)
- `geography_code` with one value being `E09000001` (i.e. the nation of `England`)
- `sic_2007` with one value being `01.11` (i.e. the concept `Growing of cereals (except rice), leguminous crops and oil seeds`)

To improve human readability and to ensure machine readability, ensure that codes are separate columns from the related human readable labels or descriptions. While the labels and additional information can be useful for humans, mixing them in the same column with codes requires users to clean the data. It is also important to ensure that related columns are grouped together when sorted alphabetically, and to make it easier to find the human readable values.

A quick way to check if a column only contains related data and not unique identifiable is if you filter on a column and for every value you select another column will only ever have the same value for that row it is likely to help human readability.

For example the three columns prefixed with `area_` are related in the table below, filtering on any of the three would only ever result in one value for the other two columns. The area_code column is a unique identifier for the geography.

| area_code | area_label        | Area_type              | value | ... |
| --------- | ----------------- | ---------------------- | ----- | --- |
| E08000006 | Salford           | Metropolitan Districts | 42    | ... |
| E92000001 | England           | Country                | 1337  | ... |
| K04000001 | England and Wales | England and Wales      |       | ... |

**Note:** Dimension columns must contain values for every row in the CSV file and not be blank (i.e. they must be dense)

#### Attributes

Attribute columns are used to qualify the observation. Most commonly the attribute columns are used to describe the absence or quality of an observation, these are commonly called "observation status" columns. There are two types of attribute columns, literal and resource columns.

##### Literal attributes

Literal attributes are used to describe the observation. When providing point estimates, often there are additional values which help provide context. For example, when providing a point estimate for the number of people in a given area, there may be a confidence interval (of which there are two values, the upper and lower bounds), a sample size, and a standard deviation. These values are all literal attributes.

##### Observation status columns

When creating observation status columns a naming convetion helps users understand how they relate to the observation to the qualification. In this case for a given column name containing observations, the observation status column column should have the same name as the observation column plus `_status` as a suffix. For example an observation column called `observation` should have a corresponding observation status called `observation_status`.

#### Measure columns

Measure columns are used to describe the measurement method for the observation when a dataset has multiple meausres. For example, a dataset may have a measure of `spend` and another measure of `spend per person`. In this case, the measure column would contain the measurement method for each observation. In many datasets the measure column is not required as there is only one measure.

Example measures include counts (e.g. of people, money, companies), indexes, and frequency.

##### Seasonal and non-seasonal measures

When a dataset contains both seasonal and non-seasonal measures, the two components should be differentiated by their measure type. For example, a dataset capturing shark attacks and ice cream sales may have a measure of `shark-attacks-SA` and another measure of `ice-cream-sales-NSA`. In this case, the measure column would contain the measurement method for each observation.

**Note** Don't forget to include the seasonal adjustment methodology in the dataset metadata!

#### Unit columns

Unit columns are used to describe the observation's unit when a dataset employes multiple units. The majority of the time there will be a single unit for each measure, but that is not always the case (i.e. average height might be captured in inches, metres, or centimetres). Units are critical to comparability, allowing for conversions (i.e. between currencies or weights).

Example units include kilograms, miles, numbers, and percentages.

**Note:** Count is not a unit. It is a measure. The unit you want is "number".

**Note:** Indicies are only comparable to itself, therefore they are "unitless". You can compare miles and kilometres, but you cannot compare the FTSE 100 and the FTSE 250 indices directly you can only compare their trends in relation to eachother, you cannot convert the former index into the latter.

The units used should *always* be [QUDT units](https://www.qudt.org/doc/DOC_VOCAB-UNITS.html) unless no appropriate unit exists, which is exceptionally rare. Again, more often in statistics you're looking at numbers, rates, percentages, fractions, frequencies, and unitless.

##### Scaling units

Often in summary statistics publications units need to be scaled in order to control disclosure, or to maintain an appropriate level of granularity. Scaled units are especially common in publications like National Accounts, which contains the caucluated and reported spend of the Government of the United Kingdom and Northern Ireland, which totals over a trillion GBP (i.e. 1000000000000) and those figures are hard to sight read.

When scaling units take the base unit and suffix the multiplication factor preceeded by an underscore. Written and decimal representations are both acceptable For several examples,

- `GBP_millions` for millions of GBP (used in National acounts)
- `NUM_1000` for thousands (used in SOME PUBLICATION)
- `PER_tenths` (i.e. `PER`cent * 0.1 a.k.a tenths) for per thousands (used in SOME PUBLICATION)
- `ratio_0.001` for per thousands (used in SOME PUBLICATION)
- `L_100` for hectolitres (used in HMRC Alcohol Bulletin)

### Ordering

Ensuring that users can understand your CSV files is important. To help with this, the columns should be ordered as follows:

1. Dimension columns, order first by time period, then by geography, then in descending order by volume of options in each column (i.e. a column with 17 values would come before a column with 3 values).
  a. Time period columns should be ordered by type, then by code, then by label.
  b. Geography columns should be ordered by code, the label, then by type.
2. Obsevation column.
3. Measure column(s). (e.g. count and spending per capita)
4. Unit column. (e.g. number, GBP, miles per hour, portion, percent)
5. Literal attribute columns providing model output (e.g. upper confidence level, sample_size, standard deviation).
6. Observation status column (if necessary).
7. All other attribute columns.

## Overall principles

Concept Clarity: Ensure that the concepts used in the CSV files are clear and easily understandable to enhance human readability.

Unique Addressability: Each observation should be uniquely addressable by filtering all dimension columns to a value.

Value Completeness: All columns should have values for every observation, except for the observation, observation status, or attribute type columns.
