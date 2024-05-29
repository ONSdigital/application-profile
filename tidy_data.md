# Publish machine-readable data

> Machine-readable data is data in a standard format that can be read and processed automatically by a computing system. Traditional word processing documents and portable document format (PDF) files are easily read by humans but typically are difficult for machines to interpret and manipulate. Formats such as XML, JSON, HDF5, RDF and CSV are machine-readable data formats [^machine]

Many of the Excel workbooks produced by statisticians are designed to be easily read by humans but typically are difficult for machines to interpret and manipulate.

Consider this example taken from the [RDF data cube vocabulary](https://www.w3.org/TR/vocab-data-cube/), extracted from StatsWales report number 003311 which describes life expectancy broken down by region (unitary authority), sex and time:

<table id="example-data" style="text-align: left;">
  <tbody>
    <tr>
      <td style="vertical-align: top;"><br>
      </td>
      <td colspan="2" rowspan="1" style="vertical-align: top; text-align: center; font-weight: bold;">2004-2006<br>
      </td>
      <td colspan="2" rowspan="1" style="vertical-align: top; text-align: center; font-weight: bold;">2005-2007<br>
      </td>
      <td colspan="2" rowspan="1" style="vertical-align: top; text-align: center; font-weight: bold;">2006-2008<br>
      </td>
    </tr>
    <tr>
      <td style="vertical-align: top;"><br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Male<br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Female<br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Male<br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Female<br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Male<br>
      </td>
      <td style="vertical-align: top; text-align: center; font-weight: bold;">Female<br>
      </td>
    </tr>
    <tr>
      <td style="vertical-align: top; text-align: right; font-weight: bold;">Newport<br>
      </td>
      <td style="vertical-align: top;">76.7<br>
      </td>
      <td style="vertical-align: top;">80.7<br>
      </td>
      <td style="vertical-align: top;">77.1<br>
      </td>
      <td style="vertical-align: top;">80.9<br>
      </td>
      <td style="vertical-align: top;">77.0<br>
      </td>
      <td style="vertical-align: top;">81.5<br>
      </td>
    </tr>
    <tr>
      <td style="vertical-align: top; text-align: right; font-weight: bold;">Cardiff<br>
      </td>
      <td style="vertical-align: top;">78.7<br>
      </td>
      <td style="vertical-align: top;">83.3<br>
      </td>
      <td style="vertical-align: top;">78.6<br>
      </td>
      <td style="vertical-align: top;">83.7<br>
      </td>
      <td style="vertical-align: top;">78.7<br>
      </td>
      <td style="vertical-align: top;">83.4<br>
      </td>
    </tr>
    <tr>
      <td style="vertical-align: top; text-align: right; font-weight: bold;">Monmouthshire<br>
      </td>
      <td style="vertical-align: top;">76.6<br>
      </td>
      <td style="vertical-align: top;">81.3<br>
      </td>
      <td style="vertical-align: top;">76.5<br>
      </td>
      <td style="vertical-align: top;">81.5<br>
      </td>
      <td style="vertical-align: top;">76.6<br>
      </td>
      <td style="vertical-align: top;">81.7<br>
      </td>
    </tr>
    <tr>
      <td style="vertical-align: top; text-align: right; font-weight: bold;">Merthyr Tydfil<br>
      </td>
      <td style="vertical-align: top;">75.5<br>
      </td>
      <td style="vertical-align: top;">79.1<br>
      </td>
      <td style="vertical-align: top;">75.5<br>
      </td>
      <td style="vertical-align: top;">79.4<br>
      </td>
      <td style="vertical-align: top;">74.9<br>
      </td>
      <td style="vertical-align: top;">79.6<br>
      </td>
    </tr>
  </tbody>
</table>

The table is a cross tabulation of the data, with the columns representing the time period of the observation and the sex of the observed population and the rows representing different locations. Having multiple header rows which span multiple columns makes the data difficult to read with software. Downstream users of the data will have to wrangle the data into a usable format.

Importing the above table into a statistical software such as [R](https://www.r-project.org/) produces a result with some problems:

- The header rows are not treated as headers.
- The header row representing time period is not fully populated.
- The first column contains empty strings.
- Numbers in the data are treated as strings, due to columns having mixed data types.

```r
# An example of how the above table looks once imported into R:

# A tibble: 6 x 7
  V1                V2        V3        V4        V5     V6    V7  
  <chr>             <chr>     <chr>     <chr>     <chr>  <chr> <chr> 
1 ""                2004-2006 2005-2007 2006-2008 NA     NA    NA  
2 ""                Male      Female    Male      Female Male  Female
3 "Newport"         76.7      80.7      77.1      80.9   77.0  81.5  
4 "Cardiff"         78.7      83.3      78.6      83.7   78.7  83.4  
5 "Monmouthshire"   76.6      81.3      76.5      81.5   76.6  81.7  
6 "Merthyr Tydfil"  75.5      79.1      75.5      79.4   74.9  79.6  
```

Organising the table as [tidy data](https://r4ds.had.co.nz/tidy-data.html), with each variable having its own column gives an output which can be instantly read into R, without need for further cleaning.

For data to be classified as tidy data:

1. Each variable forms a column.
2. Each observation forms a row.
3. Each type of observational unit forms a table.

| geography    | period    | sex    | life_expectancy |
| ------------ | --------- | ------ | --------------- |
| Newport      | 2004-2006 | Male   | 76.7            |
| Newport      | 2004-2006 | Female | 80.7            |
| Cardiff      | 2004-2006 | Male   | 78.7            |
| Cardiff      | 2004-2006 | Female | 83.3            |
| ...          | ...       | ...    | ...             |

## Adopt common identifiers

We should adopt common and unambiguous identifiers for data items such as ONS geography codes or ISO-8601 time intervals.

| geography_code      | period                  | sex    | life_expectancy |
| ------------------- | ----------------------- | ------ | --------------- |
| W06000022           | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022           | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015           | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |
| W06000015           | 2004-01-01T00:00:00/P3Y | Female | 83.3            |
| ...                 | ...                     | ...    | ...             |

In this example, adopting ISO 8601 time intervals allows machines to provide additional functionality for computing with this type of data. Adopting geography codes allows for linking between datasets.

```r
# A tibble: 4 x 4
  geography period                         sex    life_expectancy
  <chr>     <Interval>                     <chr>            <dbl>
1 W06000022 2004-01-01 UTC--2007-01-01 UTC Male              76.7
2 W06000022 2004-01-01 UTC--2007-01-01 UTC Female            80.7
3 W06000015 2004-01-01 UTC--2007-01-01 UTC Male              78.7
4 W06000015 2004-01-01 UTC--2007-01-01 UTC Female            83.3
```

Producing data which _only_ uses identifiers could reduce usability by humans. It may be reasonable to include some of the redundant, human-friendly data such as labels alongside identifiers (known formally as denormalisation).

When [using a CSVW to create an RDF data cube](rdf_cubes.md#using-csvw-to-create-an-rdf-data-cube), any redundant columns must be suppressed by setting `"suppressOutput": "true"`. CSVW provides a way for values rows, and column headings of a CSV file to be mapped to RDF resources. Some schema fields refer to codelists, to limit and standardize the possible values of the fields, in order to promote data interoperability.

| geography_code | geography_label | period_code             | period_label | sex    | life_expectancy |
| -------------- | --------------- | ----------------------- | ------------ | ------ | --------------- |
| W06000022      | Newport         | 2004-01-01T00:00:00/P3Y | 2004-2006    | Male   | 76.7            |
| W06000022      | Newport         | 2004-01-01T00:00:00/P3Y | 2004-2006    | Female | 80.7            |
| W06000015      | Cardiff         | 2004-01-01T00:00:00/P3Y | 2004-2006    | Male   | 78.7            |
| W06000015      | Cardiff         | 2004-01-01T00:00:00/P3Y | 2004-2006    | Female | 83.3            |
| ...            | ...             | ...                     | ...          | ...    | ...             |

To adopt common identifiers, there needs to exist a list of identifiers which can be shared and reused. We cover the creation of classifications in [codelists](code-lists.md).

## Using symbols and shorthand in tables

Statisticians often need to add metadata and additional context to their tables, such as describing that data are not available, an estimate is provisional or an estimate is ommitted to prevent disclosing individual responses. The [Statistical Data and Metadata eXchange (SDMX)](https://sdmx.org/) has defined a code list which supports several data markups, currently at [version 2.2](https://sdmx.org/wp-content/uploads/CL_OBS_STATUS_v2_2.docx).

For example, this table indicates that the life expectancy is not available (`O`) or provisional (`P`) for some entries.

| geography      | period                  | sex    | life_expectancy |
| -------------- | ----------------------- | ------ | --------------- |
| W06000022      | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022      | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015      | 2004-01-01T00:00:00/P3Y | Male   | 78.7 P          |
| W06000015      | 2004-01-01T00:00:00/P3Y | Female | O               |
| ...            | ...                     | ...    | ...             |

These annotations are usually included inside the table alongside numeric data. When this happens the columns no longer contain a single type. By placing symbols such as `O` in the same column as numeric values, statistical software will interpret the column as containing strings and not numbers.

To avoid the mixing of types, we recommend that these annotations be placed in their own column. We refer to these annotations as _observation statuses_.

| geography      | period                  | sex    | life_expectancy | observation_status |
| -------------- | ----------------------- | ------ | --------------- | ------------------ |
| W06000022      | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |                    |
| W06000022      | 2004-01-01T00:00:00/P3Y | Female | 80.7            |                    |
| W06000015      | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | P                  |
| W06000015      | 2004-01-01T00:00:00/P3Y | Female |                 | O                  |
| ...            | ...                     | ...    | ...             |                    |

This adds some complexity when a table has multiple statistical measures as it is unclear which of the columns the `observation_status` applies to. In the following example, it is unclear whether the entry for `life_expectancy` or `disability_free_life_expectancy` (or both) is provisional.

| geography      | period                  | sex    | life_expectancy | disability_free_life_expectancy | observation_status |
| --------- | ----------------------- | ------ | --------------- | ------------------------------- | ------------------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | 70.1                            |                    |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            | 80.2                            |                    |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | 70.3                            | P                  |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female |                 | 80.4                            | O                  |
| ...       | ...                     | ...    | ...             |                                 |                    |

We solve this by pivoting the measures into a `measure_type` column, so each row represents a single statistical measure, with a single observation status relating specifically to that measure.

| geography      | period                  | sex    | measure_type                    | value | observation_status |
| --------- | ----------------------- | ------ | ------------------------------- | ----- | ------------------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 76.7  |                    |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 | 80.7  |                    |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | disability-free-life-expectancy | 70.1  |                    |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | disability-free-life-expectancy | 80.2  | P                  |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 78.7  |                    |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 |       | O                  |
| ...       | ...                     | ...    | ...                             | ...   |                    |

Data in this format allows users to filter and sort based upon annotations. For example, users can filter out results which are provisional or not applicable.

If necessary, the data can be pivoted back into a format which would feel more familiar by discarding the `observation_status` column.

```python
# R ----------------------------------------------

df |>
  dplyr::select(-observation_status) |>
  tidyr::pivot_wider(names_from = measure_type) |>
  janitor::clean_names()

# python -----------------------------------------

import pandas as pd

df = (
    df
    .set_index(["geography", "period" ,"sex", "measure_type"])["value"]
    .unstack()
    .reset_index()
)
```

After pivoting with the above code, each of the measures has its own column.

| geography      | period                  | sex    | life_expectancy | disability_free_life_expectancy |
| -------------- | ----------------------- | ------ | --------------- | ------------------------------- |
| W06000022      | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | 70.1                            |
| W06000022      | 2004-01-01T00:00:00/P3Y | Female | 80.7            | 80.2                            |
| W06000015      | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | 70.3                            |
| W06000015      | 2004-01-01T00:00:00/P3Y | Female |                 | 80.4                            |
| ...            | ...                     | ...    | ...             |                                 |

## Expressing concept hierarchies

Statistics publishers may wish to indicate that their data includes a hierarchy. A typical approach may be to include multiple columns, one for each level of the hierarchy, though this can sometimes be ambiguous and difficult to interpret.

Consider a mock dataset which uses the Standard Industrial Trade Classification (SITC). SITC is a classification system for the trade of goods and services. It has several top level categories then broken down into subcategories.

```txt
0 Food and live animals
├─ 00 Live animals other than animals of division 03
│  ├─ 001 Live animals other than animals of division 03
├─ 01 Meat and meat preparations
│  ├─ 011 Meat of bovine animals, fresh, chilled or frozen
│  ├─ 012 Other meat and edible meat offal
│  ├─ 016 Meat, edible meat offal, salted, dried; flours, meals
│  ├─ 017 Meat, edible meat offal, prepared, preserved, n.e.s
│  ├─ ...
├─ 02 Dairy products and birds' eggs
│  ├─   022 Milk, cream and milk products (excluding butter, cheese)
│  ├─ ...
```

This would typically be presented in a dataset with `industry`, `sub_industry` and `sub_industry_2` columns. Some entries may be blank depending on the level of the hierarchy being described.

| period | industry | sub_industry | sub_industry_2 | industry_label                                   | trade_value |
| ------ | -------- | ------------ | -------------- | ------------------------------------------------ | ----------- |
| 2004   | 0        |              |                | Food and live animals                            | ...         |
| 2004   | 0        | 00           |                | Live animals other than animals of division 03   | ...         |
| 2004   | 0        | 00           | 001            | Live animals other than animals of division 03   | ...         |
| 2004   | 0        | 01           |                | Meat and meat preparations                       | ...         |
| 2004   | 0        | 01           | 011            | Meat of bovine animals, fresh, chilled or frozen | ...         |
| ...    | ...      |              |                | ...                                              | ...         |

There may be some difficulties in working with data structured in this way:

- Different publishers may indicate hierarchy in different ways, using different combinations of multiple columns and blank entries. Understanding how each dataset's structure relates to its interpretation requires investigation.
- The number of columns is determined by the number of levels in the hierarchy, potentially making datasets very wide. Naming becomes more difficult as the number of columns increases.
- Using blank entries to indicate hierarchy means blank entries cannot then also be used where data is unknown or does not exist.
- The hierarchical relationship between columns is not explicit. It can be difficult to infer the structure, especially when a dataset has multiple hierarchies.

By creating codelists such as SITC we can make the hierarchy of categories explicit. By creating codelists and publishing these alongside the statistical data, we remove the need to include hierarchical structure inside the dataset.

We suggest collapsing the hierarchy into a single column, and using a defined classification which indicates the hierarchy of classes. We cover the creation of classifications in [codelists](code-lists.md).

| period | industry | industry_label                                   | trade_value |
| ------ | -------- | ------------------------------------------------ | ----------- |
| 2004   | 0        | Food and live animals                            | ...         |
| 2004   | 00       | Live animals other than animals of division 03   | ...         |
| 2004   | 001      | Live animals other than animals of division 03   | ...         |
| 2004   | 01       | Meat and meat preparations                       | ...         |
| 2004   | 011      | Meat of bovine animals, fresh, chilled or frozen | ...         |
| ...    | ...      | ...                                              | ...         |

It can be helpful to humans to include some information about the hierarchy inside the dataset, for example to make some aggregations simpler to perform. We recommend including a single `parent_x` column where there is a need to do so (a form of denormalisation). A blank entry in the parent column indicates no parent exists.

When [using a CSVW to create an RDF data cube](rdf_cubes#using-csvw-to-create-a-rdf-data-cube), the `parent_x` column must be suppressed by setting `"suppressOutput": "true"`.

| period | parent_industry | industry | industry_label                                   | trade_value |
| ------ | --------------- | -------- | ------------------------------------------------ | ----------- |
| 2004   |                 | 0        | Food and live animals                            | ...         |
| 2004   | 0               | 00       | Live animals other than animals of division 03   | ...         |
| 2004   | 00              | 001      | Live animals other than animals of division 03   | ...         |
| 2004   | 0               | 01       | Meat and meat preparations                       | ...         |
| 2004   | 01              | 011      | Meat of bovine animals, fresh, chilled or frozen | ...         |
| ...    |                 | ...      | ...                                              | ...         |

## Units of measurement

Units of an observation should be specified by including a units column for readability of the csv.

| geography      | period                  | sex    | life_expectancy | units |
| -------------- | ----------------------- | ------ | --------------- | ----- |
| W06000022      | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | years |
| W06000022      | 2004-01-01T00:00:00/P3Y | Female | 80.7            | years |
| W06000015      | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | years |
| W06000015      | 2004-01-01T00:00:00/P3Y | Female | 83.3            | years |
| ...            | ...                     | ...    | ...             |       |

In the case of a single-measure dataset (or multiple-measures where those measures share the same units of measurement), the units of an observation may be specified via a CSVW virtual column.

## Representing model components and uncertainty

Model components and uncertainty should be expressed using literal attributes. An extension of the average human height by country dataset containing additional information about the observations provide information including the age range and count of study participants, and the standard deviation of the observation.

| country     | sex    | study_period | height_in_cm | height_in_inches | age_range | participants | std |
| ----------- | ------ | ------------ | ------------ | ---------------- | --------- | ------------ | --- |
| Nepal       | Male   | 2012-2013    | 161.7        | 63.5             | 15-69     | 1326         |     |
| Nepal       | Female | 2012-2013    | 150.4        | 59               | 15-69     | 2798         |     |
| Netherlands | Male   | 2009         | 183.8        | 72.5             | 21        | 74           | 7.1 |
| Netherlands | Female | 2009         | 170.7        | 67               | 21        | 50           | 6.3 |

> Source: [Wikipedia](https://en.wikipedia.org/wiki/Average_human_height_by_country)

For datasets with confidence internals, we recommend attaching the upper and lower bounds to the primary observation as individiual literal attributes and not as a range.

> TODO: This is the confidence/credible interval level section/plug

## Seasonal adjustments and unadjusted values

Seasonally adjusted and non-seasonally adjusted figures are frequently contained within the same dataset. In this case, although Seasonally Adjusted figures are a model component/output, we recommend that the measure used be extended so that SA and NSA both are captured as primary observations. In the example below the units are a number in thousands, and the column `all_aged_16_and_over` are a model component treated as a literal attribute.

| period  | measure                                 | value | all_aged_16_and_over |
| ------- | --------------------------------------- | ----- | -------------------- |
| 2022-Q2 | economically-active-unadjusted          | 33945 | 53900                |
| 2022-Q3 | economically-active-unadjusted          | 33999 | 53935                |
| 2022-Q2 | economically-active-seasonally-adjusted | 33970 | 53900                |
| 2022-Q3 | economically-active-seasonally-adjusted | 33942 | 53935                |

> Combined datasets from ONS [A02 SA: Employment, ... (seasonally adjusted)](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/datasets/employmentunemploymentandeconomicinactivityforpeopleaged16andoverandagedfrom16to64seasonallyadjusteda02sa) and [A02 NSA: Employment, ... (not seasonally adjusted)](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/datasets/nsaemploymentunemploymentandeconomicinactivityforpeopleaged16andoverandagedfrom16to64a02).

## Mixing time periods

Statisticians may wish to report statistics at different time granularities. For example, a single dataset may report statistics by month, quarter, year and financial year.

| period    | industry | trade_value |
| --------- | -------- | ----------- |
| 2004      | 0        | ...         |
| 2004-2005 | 0        | ...         |
| 2004-01   | 0        | ...         |
| 2004-W34  | 0        | ...         |
| ...       | ...      | ...         |
| 2005      | 00       | ...         |
| 2005-01   | 001      | ...         |
| 2004-W34  | 01       | ...         |
| ...       | ...      | ...         |

We adopt IRIs from the [`reference.data.gov.uk` service](https://github.com/epimorphics/IntervalServer/blob/master/interval-uris.md), which take the form `http://reference.data.gov.uk/id/{period_type}/{period_notation}`.

| period_type     | period_notation | industry | trade_value |
| --------------- | --------------- | -------- | ----------- |
| year            | 2004            | 0        | ...         |
| government-year | 2004-2005       | 0        | ...         |
| month           | 2004-01         | 0        | ...         |
| week            | 2004-W34        | 0        | ...         |
| ...             | ...             | ...      | ...         |
| year            | 2005            | 00       | ...         |
| government-year | 2005-2006       | 00       | ...         |
| month           | 2005-01         | 001      | ...         |
| week            | 2004-W34        | 01       | ...         |
| ...             | ...             | ...      | ...         |

[^machine]: <https://w3c.github.io/dwbp/bp.html#machine_readable>
