# Application Profile

_Working draft._

The key words must, must not, required, shall, shall not, should, should not, recommended, may, and optional are to be interpreted as described in RFC 2119.

- [Application Profile](#application-profile)
  - [Preamble](#preamble)
    - [Data on the Web Best Practises](#data-on-the-web-best-practises)
    - [Five star data](#five-star-data)
    - [FAIR principles](#fair-principles)
    - [CSV on the Web](#csv-on-the-web)
  - [Specifications used](#specifications-used)
  - [Data structure](#data-structure)
    - [Publish machine-readable data](#publish-machine-readable-data)
    - [Adopt common identifiers](#adopt-common-identifiers)
    - [Using symbols and shorthand in tables](#using-symbols-and-shorthand-in-tables)
    - [Expressing concept hierarchies](#expressing-concept-hierarchies)
    - [Units of measurement](#units-of-measurement)
    - [Representing model components and uncertainty](#representing-model-components-and-uncertainty)
    - [Seasonal adjustments and unadjusted values](#seasonal-adjustments-and-unadjusted-values)
    - [Mixing time periods](#mixing-time-periods)
  - [Cataloguing](#cataloguing)
    - [Classes](#classes)
    - [Catalog](#catalog)
    - [Catalogue record](#catalogue-record)
    - [Dataset](#dataset)
    - [Dataset series](#dataset-series)
    - [Distributions](#distributions)
    - [Named graphs for catalogue metadata](#named-graphs-for-catalogue-metadata)
    - [Content negotiation of distributions](#content-negotiation-of-distributions)
    - [Editions](#editions)
      - [Scheduled revisions (provisional and final releases)](#scheduled-revisions-provisional-and-final-releases)
    - [Versions](#versions)
  - [Publish CSV on the web (CSVW)](#publish-csv-on-the-web-csvw)
    - [Structural CSV metadata](#structural-csv-metadata)
    - [CSVs as self-contained datasets](#csvs-as-self-contained-datasets)
    - [Discoverability of CSVW](#discoverability-of-csvw)
    - [Foreign-key constraints](#foreign-key-constraints)
  - [RDF data cubes](#rdf-data-cubes)
    - [Classes](#classes-1)
    - [Datacube](#datacube)
    - [Data structure definition](#data-structure-definition)
      - [Component specification](#component-specification)
    - [Components](#components)
      - [Measure](#measure)
      - [Dimension](#dimension)
      - [Attribute](#attribute)
    - [Observation](#observation)
    - [Using CSVW to create a RDF data cube](#using-csvw-to-create-a-rdf-data-cube)
    - [Multiple measures](#multiple-measures)
  - [Appendicies](#appendicies)
    - [Recommended codelists](#recommended-codelists)
      - [Geography](#geography)
      - [Dates and times](#dates-and-times)
      - [Frequency](#frequency)
      - [Licenses](#licenses)
      - [Organisations](#organisations)
      - [Statistics designations](#statistics-designations)
      - [Symbols and shorthand in tables](#symbols-and-shorthand-in-tables)
      - [Themes](#themes)
      - [Media types](#media-types)
    - [Hash or slash IRIs](#hash-or-slash-iris)
    - [`rdfs` vs `dcterms`](#rdfs-vs-dcterms)
    - [Publishers, creators and contacts](#publishers-creators-and-contacts)
    - [Class diagram](#class-diagram)
    - [Future work](#future-work)
      - [Provenance](#provenance)


## Preamble

The UK government often [publishes its statistics](https://www.gov.uk/search/research-and-statistics?content_store_document_type=statistics_published&order=updated-newest) in presentational spreadsheets. While this succeeds in getting important information into the public domain, we recognise there are still barriers and challenges in accessing and using the data we produce:

- Analysts need to wrangle data because data are in unstandardised and presentational formats.
- A user must locate and navigate through many large spreadsheets to understand what data are available.
- Metadata are provided in an unstructured or unstandardised ways.
- Data are in silos, making it difficult to link or relate statistics from different sources.
- The accessibility and usability of statistics varies from dataset to dataset.

We have explored how to follow best practices when publishing statistics, in particular through the use of the CSV on the Web (CSVW), Data Catalog (DCAT) and RDF Data Cube (QB) standards and vocabularies. This document is an application profile of these standards, describing a recommendation on how to use these standards together in order to achieve the data on the web best practices, 5-star data, and the FAIR data principles.

### Data on the Web Best Practises 

The [Data on the Web Best Practices (DWBP)](https://www.w3.org/TR/dwbp/) describes recommendations for publishing data to the web. If followed, we can enable these benefits:

> - **Comprehension**: humans will have a better understanding about the data structure, the data meaning, the metadata and the nature of the dataset.
> - **Processability**: machines will be able to automatically process and manipulate the data within a dataset.
> - **Discoverability** machines will be able to automatically discover a dataset or data within a dataset.
> - **Reuse**: the chances of dataset reuse by different groups of data consumers will increase.
> - **Trust**: the confidence that consumers have in the dataset will improve.
> - **Linkability**: it will be possible to create links between data resources (datasets and data items).
> - **Access**: humans and machines will be able to access up to date data in a variety of forms.
> - **Interoperability**: it will be easier to reach consensus among data publishers and consumers.

### Five star data

5★ Open Data has a five point scale which describes data on the web which increases the utility of said data for each increase from one to five stars.

|   Stars    | Requirements                                                                                         |
| :--------: | :--------------------------------------------------------------------------------------------------- |
| ★☆☆☆☆      | data needs to be able to be published on the web,                                                    |
| ★★☆☆☆      | data needs to be machine-readable,                                                                   |
| ★★★☆☆      | data needs to be non-proprietary,                                                                    |
| ★★★★☆      | identifiers need to be used to denote things, so that people can talk about resources unambiguously, |
| ★★★★★      | data needs to able to be linkied to other data to provide context.                                   |

### FAIR principles

To aid humans who increasingly rely on computational support to deal with increased volumes of data, complexity, and creation speed of data, the [FAIR principles](https://www.go-fair.org/fair-principles/) were conceived.

The FAIR principles describe data which is:

> - **Findable**: data and metadata encoded for machines and humans
> - **Accessible**: using standard protocols for access and authentication of data
> - **Interoperable**: data and metadata is represented in an appropriate knowledge representation standard
> - **Reusable**: using common vocabularies for knowledge representation allows for reuse and remixing of data

### CSV on the Web

> CSVW extends standard CSV with the ingredients for a reliable, flexible and extensible data exchange format. Most importantly, CSVW accommodates metadata. [^csvw-intro]

The [CSV on the Web (CSVW) standard](https://w3c.github.io/csvw/syntax/) provides a method for describing and clarifying the content of CSV tabular data.

The CSV format is at its best when machine readable. CSVW improves machine-readability by pairing CSV with a JSON document to provide additional metadata to describe the content of the CSV file.

One such improvement to CSVs is providing data type information for cells contents so they can be mapped as decimals, integers, dates, etc. without ambiguity. Furthermore, CSVW is extensible to fully 5-star linked-data, providing a mapping to the contents of a CSV file to RDF.

## Specifications used

The Application Profile uses terms from various existing specifications. Classes and properties specified in the following sections come from the following namespaces.

| Namespace | Namespace IRI                                 | Specification name                                                                   |
| --------- | --------------------------------------------- | ------------------------------------------------------------------------------------ |
| `adms`    | `http://www.w3.org/ns/adms#`                  | Asset Description Metadata Schema                                                    |
| `dcat`    | `http://www.w3.org/ns/dcat#`                  | Data Catalog Vocabulary                                                              |
| `dcterms` | `http://purl.org/dc/terms/`                   | DCMI (Dublin Core Metadata Initiative) Metadata Terms                                |
| `dpv`     | `http://www.w3.org/ns/dpv#`                   | Data Privacy Vocabulary (DPV)                                                        |
| `foaf`    | `http://xmlns.com/foaf/0.1/`                  | FOAF (Friend of a friend) Vocabulary                                                 |
| `owl`     | `http://www.w3.org/2002/07/owl#`              | OWL Web Ontology Language                                                            |
| `prov`    | `http://www.w3.org/ns/prov#`                  | Provenance Vocabulary                                                                |
| `qb`      | `http://purl.org/linked-data/cube#`           | RDF Data Cube Vocabulary                                                             |
| `rdfs`    | `http://www.w3.org/2000/01/rdf-schema#`       | RDF (Resource Description Framework) Vocabulary Description Language 1.0: RDF Schema |
| `skos`    | `http://www.w3.org/2004/02/skos/core#`        | SKOS Simple Knowledge Organization System - Reference                                |
| `spdx`    | `http://spdx.org/rdf/terms#`                  | Software Package Data Exchange                                                       |
| `vcard`   | `http://www.w3.org/2006/vcard/ns#`            | File format standard for electronic business cards                                   |
| `wdrs`    | `http://www.w3.org/2007/05/powder-s#`         | Protocol for Web Description Resources (POWDER-S)                                    |
| `xkos`    | `http://rdf-vocabulary.ddialliance.org/xkos#` | XKOS: an SKOS extension for representing statistical classifications                 |
| `xsd`     | `http://www.w3.org/2001/XMLSchema#`           | XML Schema Part 2: Datatypes Second Edition                                          |

## Data structure

### Publish machine-readable data

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

| area    | period    | sex    | life_expectancy |
| ------- | --------- | ------ | --------------- |
| Newport | 2004-2006 | Male   | 76.7            |
| Newport | 2004-2006 | Female | 80.7            |
| Cardiff | 2004-2006 | Male   | 78.7            |
| Cardiff | 2004-2006 | Female | 83.3            |
| ...     | ...       | ...    | ...             |

### Adopt common identifiers

We should adopt common and unambiguous identifiers for data items such as ONS geography codes or ISO-8601 time intervals.

| area      | period                  | sex    | life_expectancy |
| --------- | ----------------------- | ------ | --------------- |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | 83.3            |
| ...       | ...                     | ...    | ...             |

In this example, adopting ISO 8601 time intervals allows machines to provide additional functionality for computing with this type of data. Adopting geography codes allows for linking between datasets.

```r
# A tibble: 4 x 4
  area      period                         sex    life_expectancy
  <chr>     <Interval>                     <chr>            <dbl>
1 W06000022 2004-01-01 UTC--2007-01-01 UTC Male              76.7
2 W06000022 2004-01-01 UTC--2007-01-01 UTC Female            80.7
3 W06000015 2004-01-01 UTC--2007-01-01 UTC Male              78.7
4 W06000015 2004-01-01 UTC--2007-01-01 UTC Female            83.3
```

Producing data which _only_ uses identifiers could reduce usability by humans. It may be reasonable to include some of the redundant, human-friendly data such as labels alongside identifiers (known formally as denormalisation).

When [using a CSVW to create an RDF data cube](#using-csvw-to-create-an-rdf-data-cube), any redundant columns must be suppressed by setting `"suppressOutput": "true"`. CSVW provides a way for values rows, and column headings of a CSV file to be mapped to RDF resources. Some schema fields refer to codelists, to limit and standardize the possible values of the fields, in order to promote data interoperability.

| area      | area_label | period                  | period_label | sex    | life_expectancy |
| --------- | ---------- | ----------------------- | ------------ | ------ | --------------- |
| W06000022 | Newport    | 2004-01-01T00:00:00/P3Y | 2004-2006    | Male   | 76.7            |
| W06000022 | Newport    | 2004-01-01T00:00:00/P3Y | 2004-2006    | Female | 80.7            |
| W06000015 | Cardiff    | 2004-01-01T00:00:00/P3Y | 2004-2006    | Male   | 78.7            |
| W06000015 | Cardiff    | 2004-01-01T00:00:00/P3Y | 2004-2006    | Female | 83.3            |
| ...       | ...        | ...                     | ...          | ...    | ...             |

To adopt common identifiers, there needs to exist a list of identifiers which can be shared and reused. We cover the creation of classifications in [codelists](#codelists). 

### Using symbols and shorthand in tables

Statisticians often need to add metadata and additional context to their tables, such as describing that data are not available, an estimate is provisional or an estimate is statistically significant. The Government Statistical Service (GSS) [has a guide](https://analysisfunction.civilservice.gov.uk/policy-store/symbols-in-tables-definitions-and-help/) which provides a number of symbols and shorthand for common annotations (see [here](#symbols-and-shorthand-in-tables)).

For example, this table indicates that the life expectancy is not available (`[x]`) or provisional (`[p]`) for some entries.

| area      | period                  | sex    | life_expectancy |
| --------- | ----------------------- | ------ | --------------- |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7 [p]        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | [x]             |
| ...       | ...                     | ...    | ...             |

These annotations are usually included inside the table alongside numeric data. When this happens the columns no longer contain a single type. By placing symbols such as `[x]` in the same column as numeric values, statistical software will interpret the column as containing strings and not numbers.

To avoid the mixing of types, we recommend that these annotations be placed in their own column. We refer to these annotations as _statistical markers_.

| area      | period                  | sex    | life_expectancy | marker |
| --------- | ----------------------- | ------ | --------------- | ------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            |        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female |                 | [x]    |
| ...       | ...                     | ...    | ...             |        |

This adds some complexity when a table has multiple statistical measures as it is unclear which of the columns the marker applies to. In the following example, it is unclear whether the entry for `life_expectancy` or `disability_free_life_expectancy` (or both) is provisional.

| area      | period                  | sex    | life_expectancy | disability_free_life_expectancy | marker |
| --------- | ----------------------- | ------ | --------------- | ------------------------------- | ------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | 70.1                            |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            | 80.2                            |        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | 70.3                            | [p]    |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female |                 | 80.4                            | [x]    |
| ...       | ...                     | ...    | ...             |                                 |        |

We solve this by pivoting the measures into a `measure_type` column, so each row represents a single statistical measure, with a single marker relating specifically to that measure.

| area      | period                  | sex    | measure_type                    | value | marker |
| --------- | ----------------------- | ------ | ------------------------------- | ----- | ------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 76.7  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 | 80.7  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | disability-free-life-expectancy | 70.1  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | disability-free-life-expectancy | 80.2  | [p]    |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 78.7  |        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 |       | [x]    |
| ...       | ...                     | ...    | ...                             | ...   |        |

Data in this format allows users to filter and sort based upon annotations. For example, users can filter out results which are provisional or not applicable.

If necessary, the data can be pivoted back into a format which would feel more familiar by discarding the marker column.

```python
# R ----------------------------------------------

df |>
  dplyr::select(-marker) |>
  tidyr::pivot_wider(names_from = measure_type) |>
  janitor::clean_names()

# python -----------------------------------------

import pandas as pd

df = (
    df
    .set_index(["area", "period" ,"sex", "measure_type"])["value"]
    .unstack()
    .reset_index()
)
```

After pivoting with the above code, each of the measures has its own column.

| area      | period                  | sex    | life_expectancy | disability_free_life_expectancy |
| --------- | ----------------------- | ------ | --------------- | ------------------------------- |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | 70.1                            |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            | 80.2                            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | 70.3                            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female |                 | 80.4                            |
| ...       | ...                     | ...    | ...             |                                 |

### Expressing concept hierarchies

Statistics publishers may wish to indicate that their data includes a hierarchy. A typical approach may be to include multiple columns, one for each level of the hierarchy, though this can sometimes be ambiguous and difficult to interpret.

Consider a mock dataset which uses the Standard Industrial Trade Classification (SITC). SITC is a classification system for the trade of goods and services. It has several top level categories then broken down into subcategories.

```
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

We suggest collapsing the hierarchy into a single column, and using a defined classification which indicates the hierarchy of classes. We cover the creation of classifications in [codelists](#codelists).

| period | industry | industry_label                                   | trade_value |
| ------ | -------- | ------------------------------------------------ | ----------- |
| 2004   | 0        | Food and live animals                            | ...         |
| 2004   | 00       | Live animals other than animals of division 03   | ...         |
| 2004   | 001      | Live animals other than animals of division 03   | ...         |
| 2004   | 01       | Meat and meat preparations                       | ...         |
| 2004   | 011      | Meat of bovine animals, fresh, chilled or frozen | ...         |
| ...    | ...      | ...                                              | ...         |

It can be helpful to humans to include some information about the hierarchy inside the dataset, for example to make some aggregations simpler to perform. We recommend including a single `parent_x` column where there is a need to do so (a form of denormalisation). A blank entry in the parent column indicates no parent exists. 

When [using a CSVW to create an RDF data cube](#using-csvw-to-create-an-rdf-data-cube), the `parent_x` column must be suppressed by setting `"suppressOutput": "true"`.

| period | parent_industry | industry | industry_label                                   | trade_value |
| ------ | --------------- | -------- | ------------------------------------------------ | ----------- |
| 2004   |                 | 0        | Food and live animals                            | ...         |
| 2004   | 0               | 00       | Live animals other than animals of division 03   | ...         |
| 2004   | 00              | 001      | Live animals other than animals of division 03   | ...         |
| 2004   | 0               | 01       | Meat and meat preparations                       | ...         |
| 2004   | 01              | 011      | Meat of bovine animals, fresh, chilled or frozen | ...         |
| ...    |                 | ...      | ...                                              | ...         |

### Units of measurement

Units of an observation may be specified by including a units column.

| area      | period                  | sex    | life_expectancy | units |
| --------- | ----------------------- | ------ | --------------- | ----- |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            | years |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            | years |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            | years |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | 83.3            | years |
| ...       | ...                     | ...    | ...             |       |

In the case of a single-measure dataset (or multiple-measures where those measures share the same units of measurement), the units of an observation may be specified via a CSVW virtual column.

### Representing model components and uncertainty

Similarly to [secondary observations with different units](#secondary-observations-with-different-units), model components and uncertainty should be expressed using literal attributes. An extension of the average human height by country dataset containing additional information about the observations provide information including the age range and count of study participants, and the standard deviation of the observation.

| country     | sex    | study_period | height_in_cm | height_in_inches | age_range | participants | std |
| ----------- | ------ | ------------ | ------------ | ---------------- | --------- | ------------ | --- |
| Nepal       | Male   | 2012-2013    | 161.7        | 63.5             | 15-69     | 1326         |     |
| Nepal       | Female | 2012-2013    | 150.4        | 59               | 15-69     | 2798         |     |
| Netherlands | Male   | 2009         | 183.8        | 72.5             | 21        | 74           | 7.1 |
| Netherlands | Female | 2009         | 170.7        | 67               | 21        | 50           | 6.3 |

> Source: https://en.wikipedia.org/wiki/Average_human_height_by_country

For datasets with confidence internals, we recommend attaching the upper and lower bounds to the primary observation as individiual literal attributes and not as a range.

> TODO: This is the confidence/credible interval level section/plug

### Seasonal adjustments and unadjusted values

Seasonally adjusted and non-seasonally adjusted figures are frequently contained within the same dataset. In this case, although Seasonally Adjusted figures are a model component/output, we recommend that the measure used be extended so that SA and NSA both are captured as primary observations. In the example below the units are a number in thousands, and the column `all_aged_16_and_over` are a model component treated as a literal attribute.

| period  | measure                                 | value | all_aged_16_and_over |
| ------- | --------------------------------------- | ----- | -------------------- |
| 2022-Q2 | economically-active-unadjusted          | 33945 | 53900                |
| 2022-Q3 | economically-active-unadjusted          | 33999 | 53935                |
| 2022-Q2 | economically-active-seasonally-adjusted | 33970 | 53900                |
| 2022-Q3 | economically-active-seasonally-adjusted | 33942 | 53935                |

> Combined datasets from ONS [A02 SA: Employment, ... (seasonally adjusted)](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/datasets/employmentunemploymentandeconomicinactivityforpeopleaged16andoverandagedfrom16to64seasonallyadjusteda02sa) and [A02 NSA: Employment, ... (not seasonally adjusted)](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/datasets/nsaemploymentunemploymentandeconomicinactivityforpeopleaged16andoverandagedfrom16to64a02).

### Mixing time periods

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

## Cataloguing

A catalogue is a collection of metadata about datasets which has been gathered and curated. Catalogues are often used to provide a single point of access to a collection of datasets, and to provide a means of discovering datasets. We adopt the [DCAT](https://www.w3.org/TR/vocab-dcat-3/) vocabulary for describing catalogues and their contents.

### Classes

```mermaid
classDiagram
    class Catalog {
        a dcat:Catalog
    }
    class CatalogRecord {
        a dcat:CatalogRecord
    }
    class DatasetSeries{
        a dcat:DatasetSeries
    }
    class Dataset {
        a dcat:Dataset
    }

    Catalog --> "1..*" CatalogRecord : dcat.record
    CatalogRecord --> "1" DatasetSeries : foaf.primaryTopic
    CatalogRecord --> "1" Dataset : foaf.primaryTopic

    DatasetSeries "1" <-- Dataset : dcat.inSeries
```

We recommend the use of `dcat:Catalog`, `dcat:CatalogRecord`, `dcat:DatasetSeries` and `dcat:Dataset` classes.

### Catalog

We recommend catalogues have IRIs of the form:

- ```http://{domain}/catalogue```
- ```http://{domain}/catalogue/{catalogue_slug}```

For example:

- ```http://data.gov.uk/catalogue```
- ```http://data.gov.uk/catalogue/climate-change```

We recommend the use of the following properties:

| Property                | Requirement level | Notes                                                                      |
| ----------------------- | ----------------- | -------------------------------------------------------------------------- |
| `dcterms:title`         | mandatory         | See [titles](#titles)                                                      |
| `dcterms:description`   | mandatory         | See [descriptions](#descriptions)                                          |
| `dcterms:publisher`     | mandatory         | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:creator`       | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcat:contactPoint`     | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:issued`        | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcterms:modified`      | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcterms:themeTaxonomy` | optional          | See [themes](#themes)                                                      |

For example:

```ttl
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dcterms: <http://purl.org/dc/terms/> .

<http://data.gov.uk/catalogue/climate-change> a dcat:Catalog ;
    dcterms:title "Climate change datasets"@en ;
    dcterms:description "A catalogue of datasets about climate change"@en ;
    dcterms:publisher <http://www.gov.uk/government/organisations/department-for-business-energy-and-industrial-strategy> ;
    dcterms:creator <http://www.gov.uk/government/organisations/department-for-business-energy-and-industrial-strategy> ;
    dcat:contactPoint <http://data.gov.uk/catalogue/climate-change/contact> ;
    dcterms:issued "2015-01-01"^^xsd:date ;
    dcterms:modified "2015-01-01"^^xsd:date ;
    dcterms:themeTaxonomy <http://data.gov.uk/themes> ;
    .
```

### Catalogue record

We recommend creaing a IRI for catalogue records by appending `/record` or `#record` to the IRI of the resource being described by the catalogue record:

- `http://{dataset_iri}/record`
- `http://{dataset_iri}#record`

For example:

- `http://data.gov.uk/dataset/my-dataset/record`
- `http://data.gov.uk/dataset/my-dataset#record`

| Property               | Requirement level | Notes                                                                          |
| ---------------------- | ----------------- | ------------------------------------------------------------------------------ |
| `dcterms:issued`       | mandatory         | See [dates and times](#dates-and-times)                                        |
| `foaf:primaryTopic`    | mandatory         | This points to the IRI of the `dcat:Dataset` described by the catalogue record |
| `prov:wasAttributedTo` | recommended       |                                                                                |
| `dcterms:modified`     | recommended       | See [dates and times](#dates-and-times)                                        |

### Dataset

We recommend standalone datasets have IRIs in the form of

- `http://{domain}/dataset/{dataset_slug}`

For example:

- `http://data.gov.uk/dataset/my-dataset`

For datasets belonging to a dataset series, we recommend extending the series IRI to form the dataset IRI. We recommend the `edition_slug` adopt identifiers from the [`reference.data.gov.uk` service](https://github.com/epimorphics/IntervalServer/blob/master/interval-uris.md).

- `http://{domain}/series/{series_slug}/dataset/{edition_slug}`

For example:

- `http://data.gov.uk/series/some-dataset-series/dataset/2018-Q3`

We recommend the use of the following properties:

| Property                     | Requirement level | Notes                                                                      |
| ---------------------------- | ----------------- | -------------------------------------------------------------------------- |
| `dcterms:title`              | mandatory         | See [titles](#titles)                                                      |
| `dcterms:description`        | mandatory         | See [descriptions](#descriptions)                                          |
| `dcterms:publisher`          | mandatory         | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:license`            | mandatory         | See [licenses](#licenses)                                                  |
| `dcat:distribution`          | recommended       | See [distributions](#distributions)                                        |
| `dcterms:creator`            | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcat:contactPoint`          | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:issued`             | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcterms:modified`           | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcat:keyword`               | recommended       | See [keywords](#keywords)                                                  |
| `dcat:theme`                 | recommended       | See [themes](#themes)                                                      |
| `dcterms:accrualPeriodicity` | recommended       | See [frequency](#frequency)                                                |
| `dcterms:spatial`            | recommended       | See [geography](#geography)                                                |
| `dcterms:temporal`           | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcat:inSeries`              | recommended       | See [editions](#editions)                                                  |
| `dcat:hasCurrentVersion`     | recommended       | See [versions](#versions)                                                  |
| `dcat:hasVersion`            | recommended       | See [versions](#versions)                                                  |
| `dcat:version`               | recommended       | See [versions](#versions)                                                  |
| `adms:versionNotes`          | recommended       | See [versions](#versions)                                                  |
| `dcat:prev`                  | recommended       | See [versions](#versions)                                                  |
| `dcat:landingPage`           | optional          |                                                                            |
| `dcterms:identifier`         | optional          |                                                                            |
| `dcterms:isReferencedBy`     | optional          |                                                                            |

For example:

```ttl
<http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018> a dcat:Dataset ;
    dcterms:title "Final UK greenhouse gas emissions national statistics: 1990 to 2018"@en ;
    dcterms:description "Final estimates of UK territorial greenhouse gas emissions..."@en ;
    dcterms:license <http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/> ;
    dcterms:publisher <http://www.gov.uk/government/organisations/department-for-business-energy-and-industrial-strategy> ;
    dcterms:issued "2020-02-04T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2020-07-30T08:30:06"^^xsd:dateTime ;
    dcat:keyword "greenhouse gases"@en, "carbon emissions"@en, "greenhouse gas emissions"@en ;
    dcat:theme <http://osr.statisticsauthority.gov.uk/themes/transport-environment-climate-change/> ;
    dcat:contactPoint <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018/contact> ;
    dcat:distribution <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018/datacube>, 
        <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.csv>, 
        <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.json> ;
    dcterms:isReferencedBy <http://www.gov.uk/government/statistics/final-uk-greenhouse-gas-emissions-national-statistics-1990-to-2018> ;
    dcat:landingPage "http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018"^^xsd:anyURI ;
    dcterms:accrualPeriodicity <http://purl.org/cld/freq/annual> ;
    dcterms:spatial <http://statistics.data.gov.uk/id/statistical-geography/K02000001> ;
    dcterms:temporal <http://reference.data.gov.uk/id/gregorian-interval/1990-01-01T00:00:00/P28Y> ;
    dcat:inSeries <http://data.gov.uk/series/greenhouse-gas-emissions> ;
    dcat:hasCurrentVersion <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018/version/2> ;
    dcat:hasVersion <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018/version/1>, 
        <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018/version/2> ;
    dcat:version 2 ;
    adms:versionNotes "Dataset was corrected following an error being recognised."@en ;
    dcat:prev <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2017> ;
    dcterms:identifier "ghg-2018" ;
    .
```

### Dataset series

Our use of dataset series is described in [editions](#editions).

We recommend dataset series have IRIs of the form:

- `http://{domain}/series/{series_slug}`

For example:

- `http://data.gov.uk/series/some-dataset-series`

We recommend the use of the following properties:

| Property                     | Requirement level | Notes                                                                      |
| ---------------------------- | ----------------- | -------------------------------------------------------------------------- |
| `dcterms:title`              | mandatory         | See [titles](#titles)                                                      |
| `dcterms:description`        | mandatory         | See [descriptions](#descriptions)                                          |
| `dcterms:publisher`          | mandatory         | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:license`            | mandatory         | See [licenses](#licenses)                                                  |
| `dcterms:creator`            | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcat:contactPoint`          | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:issued`             | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcterms:modified`           | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcat:keyword`               | recommended       | See [keywords](#keywords)                                                  |
| `dcat:theme`                 | recommended       | See [themes](#themes)                                                      |
| `dcterms:accrualPeriodicity` | recommended       | See [frequency](#frequency)                                                |
| `dcterms:spatial`            | recommended       | See [geography](#geography)                                                |
| `dcterms:temporal`           | recommended       | See [dates and times](#dates-and-times)                                    |

For example:

```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .
<http://data.gov.uk/series/greenhouse-gas-emissions> a dcat:DatasetSeries ;
    dcterms:title "UK territorial greenhouse gas emissions national statistics"@en ;
    dcterms:description "Final and provisional estimates of UK territorial greenhouse gas emissions from 1990."@en ;
    dcterms:publisher <http://www.gov.uk/government/organisations/department-for-business-energy-and-industrial-strategy> ;
    dcterms:license <http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/> ;
    dcterms:issued "2015-02-11T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2022-03-31T08:30:14"^^xsd:dateTime ;
    .
```

Many of the properties which apply to dataset series are also applicable to datasets within that series. We recommend specifying properties for both resources.

### Distributions

```mermaid
classDiagram
    class Dataset {
        a dcat:Dataset
    }
    class Distribution{
        a dcat:Distribution
    }

    Dataset --> "1..*" Distribution : dcat.distribution
```

> a `dcat:Distribution` represents an accessible form of a dataset such as a downloadable file.

We recommend distributions have IRIs which are identical to the dataset IRI, with file extension appended.

- `http://{dataset_iri}.{extension}`

The exception is when representing an RDF data cube as a distribution, for which there is no physical file and therefore no extension. In that instance, we recommend appending `/datacube` or `#datacube` to the dataset IRI (see [Data cube](#data-cube)).

For example:

- `http://data.gov.uk/dataset/my-dataset.csv`
- `http://data.gov.uk/dataset/my-dataset.ttl`
- `http://data.gov.uk/dataset/my-dataset.json`
- `http://data.gov.uk/dataset/my-dataset/datacube`

| Property                | Requirement level | Notes                                                                          |
| ----------------------- | ----------------- | ------------------------------------------------------------------------------ |
| `dcterms:title`         | mandatory         | See [titles](#titles)                                                          |
| `dcterms:description`   | mandatory         | See [descriptions](#descriptions)                                              |
| `dcterms:license`       | mandatory         | See [licenses](#licenses)                                                      |
| `dcterms:creator`       | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts)     |
| `dcterms:issued`        | recommended       | See [dates and times](#dates-and-times)                                        |
| `dcterms:modified`      | recommended       | See [dates and times](#dates-and-times)                                        |
| `dcat:isDistributionOf` | recommended       | See [CSVs as self contained datasets](#csvs-as-self-contained-datasets)        |
| `dcat:mediaType`        | recommended       | See [media types](#media-types)                                                |
| `dcat:downloadURL`      | recommended       |                                                                                |
| `dcat:byteSize`         | recommended       |                                                                                |
| `spdx:checksum`         | recommended       | See [checksums](#checksums)                                                    |
| `wdrs:describedby`      | optional          | For CSV distributions, we can relate the CSVW metadata using`wdrs:describedby` |

For example:

```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .

<http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.csv> a dcat:Distribution ;
    dcterms:title "Final UK greenhouse gas emissions national statistics: 1990 to 2018 (CSV)"@en ;
    dcterms:description "Final estimates of UK territorial greenhouse gas emissions..."@en ;
    dcterms:license <http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/> ;
    dcterms:issued "2020-02-04T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2020-07-30T08:30:06"^^xsd:dateTime ;
    dcterms:title "2018.csv" ;
    wdrs:describedby <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.csv-metadata.json> ;
    dcat:mediaType <http://www.w3.org/ns/iana/media-types/text/csv#Resource> ;
    dcat:downloadURL <http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.csv> ;
    dcat:byteSize "12345"^^xsd:nonNegativeInteger ;
    spdx:checksum [
        spdx:checksumValue "CE114E4501D2F4E2DCEA3E17B546F339"^^xsd:hexBinary ;
        spdx:checksumAlgorithm spdx:checksumAlgorithm_sha256 ;
    ] ;
    .
```

### Named graphs for catalogue metadata

Where metadata is stored as RDF, such as being made available via a SPARQL endpoint, DCAT makes a recommendation about the names of graphs to use for catalogue records.

> If a catalog is represented as an RDF Dataset with named graphs (as defined in [[SPARQL11-QUERY]](https://www.w3.org/TR/sparql11-query/)), then it is appropriate to place the description of each dataset (consisting of all RDF triples that mention the dcat:Dataset, dcat:CatalogRecord, and any of its dcat:Distributions) into a separate named graph. The name of that graph SHOULD be the IRI of the catalog record.[^named-graphs]

```ttl
<http://data.gov.uk/dataset/my-dataset/record> {
    ...
}
```

Doing this results in a neat ability to query for dataset metadata by limiting a SPARQL query to the IRI of the catalogue record.

```sparql
SELECT * 
FROM <http://data.gov.uk/dataset/my-dataset/record> 
WHERE {
    ?s ?p ?o .
}
```

### Content negotiation of distributions

We recommend that data providers implement content negotiation as a method for clients to access the data in the format they require.

The IRI of the `dcat:Dataset` should be used as the generic IRI which a user can request different formats of the data from.

For example, a `dcat:Dataset` with an IRI of `http://data.gov.uk/dataset/my-dataset` may have a CSV distribution with its own IRI of `http://data.gov.uk/dataset/my-dataset.csv`. A user agent wishing to access the data in CSV format could navigate to `http://data.gov.uk/dataset/my-dataset.csv` directly, or content negotiate against the IRI of the `dcat:Dataset` to find the CSV distribution.

```sh
curl http://data.gov.uk/dataset/my-dataset -H "Accept: text/csv"
```

### Editions

> **Note**
> `dcat:DatasetSeries` is recommended as part of [DCAT v3](https://w3c.github.io/dxwg/dcat/), which is still in draft.

Many statistics producers publish sets of statistics at a regular frequency as monthly, quarterly, or annual releases.

We refer to these as _editions_, as opposed to [_versions_](#versions) which are used to specifically describe changes in a dataset resulting from a revision. 

Each edition is a `dcat:Dataset`, with a unique IRI which typically contains the latest time period for which data is available.

For example, `http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018` is the IRI of the 2018 edition of the series `name-of-my-statistical-series`.

Editions must be related to their associated `dcat:DatasetSeries`. The dataset series must have an IRI which does not reference particular time period and can represent the collection of editions.

For example, the following dataset series has two editions from 2017 and 2018.

```ttl
<http://data.gov.uk/series/name-of-my-statistical-series> a dcat:DatasetSeries .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017> ;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2016> ;
    .
```

#### Scheduled revisions (provisional and final releases)

Statisticians may wish to release early or provisional estimates of statistics which are later revised as "final" statistics when additional data is available. The Government Statistical Service [refers to these as scheduled revisions](https://analysisfunction.civilservice.gov.uk/policy-store/communicating-quality-uncertainty-and-change/).

The IRIs of provisional and final datasets should contain `provisional` or `final`. Provisional and final statistics can both be attached to the same dataset series and related to one another by the `dcat:prev` property.

```mermaid
flowchart LR

    2017p((2017/provisional)) --> 2017f((2017/final))
    2017f --> 2018p((2018/provisional))
    2018p --> 2018f((2018/final))

    2017f -->|dcat:prev| 2017p
    2018p -->|dcat:prev| 2017f
    2018f -->|dcat:prev| 2018p
   
```

For example, the following dataset series has two editions from both 2017 and 2018, one provisional and one final.

```ttl
<http://data.gov.uk/series/name-of-my-statistical-series> a dcat:DatasetSeries .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/final> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/provisional> ;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/provisional> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017/final> ;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017/final> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017/provisional> ;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017/provisional> a dcat:Dataset ;
    dcat:inSeries <http://data.gov.uk/series/name-of-my-statistical-series> ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2016/final> ;
    .
```

### Versions

> **Note**
> `dcat:version` is recommended as part of [DCAT v3](https://w3c.github.io/dxwg/dcat/), which is still in draft.

Different versions of a dataset are the result of an unscheduled revision or correction.

We recommend the IRI of a `dcat:Dataset` is chosen to be generic and not specific to a particular version. A user should expect that the generic IRI of a dataset refers to the latest version of the dataset.

IRIs should be created to represent each specific version of a dataset. We should assert an equivalence between IRI of the generic dataset and the latest version of the dataset with an `owl:sameAs` relationship, for example:

```ttl
<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018>
    owl:sameAs
        <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/2> ;
    .
```

| Property                 | Requirement level |
| ------------------------ | ----------------- |
| `dcat:hasCurrentVersion` | recommended       |
| `dcat:hasVersion`        | recommended       |
| `dcat:version`           | recommended       |
| `adms:versionNotes`      | recommended       |
| `dcat:prev`              | recommended       |

For specific versions, we recommend using the following properties:

| Property                | Requirement level |
| ----------------------- | ----------------- |
| `dcterms:issued`        | recommended       |
| `dcat:isVersionOf`      | recommended       |
| `dcat:previousVersion`  | recommended       |
| `prov:wasRevisionOf`    | recommended       |
| `prov:specializationOf` | recommended       |

```ttl
<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> a dcat:Dataset ;
    dcat:hasCurrentVersion <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/2> ;
    dcat:hasVersion <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/1>, 
        <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/2> ;
    dcat:version 2 ;
    adms:versionNotes "Dataset was corrected following an error being recognised."@en ;
    dcat:prev <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2017> ;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/2> a dcat:Dataset ;
    dcterms:issued "2018-03-01T00:00:00Z"^^xsd:dateTime ;
    dcat:isVersionOf <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> ;
    dcat:previousVersion <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/1>;
    prov:wasRevisionOf <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/1>;
    prov:specializationOf <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018>;
    .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/version/1> a dcat:Dataset ;
    dcterms:issued "2018-01-01T00:00:00Z"^^xsd:dateTime ;
    dcat:isVersionOf <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> ;
    prov:specializationOf <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018>;
    prov:invalidatedAtTime "2018-03-01T00:00:00Z"^^xsd:dateTime ;
    .
```


## Publish CSV on the web (CSVW)

Our aim is to publish metadata in a machine readable and structured format alongside the statistical data.

Structured data formats, such as JSON-LD can be understood by search engines and are used for [search engine optimisation](https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data), with some search engines offering specific [dataset search functionality](https://developers.google.com/search/docs/advanced/structured-data/dataset) where structured metadata are provided using common vocabularies such as DCAT or [schema.org](https://schema.org/).

### Structural CSV metadata

The most basic of CSVW metadata will include the `tableSchema` properties with details of the columns in the CSV. Since the CSVW metadata specification includes several defaults for properties, a basic CSVW provides some implicit information, such as the file being comma delimited.

We can consider the following CSV file:

| area      | period                  | sex    | life_expectancy |
| --------- | ----------------------- | ------ | --------------- |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | 83.3            |
| ...       | ...                     | ...    | ...             |

Given the above CSV, a minimal CSVW metadata file would look as follows:

```json
{
    "@context": "http://www.w3.org/ns/csvw",
    "url": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time.csv",
    "tableSchema": {
        "columns": [
            {
                "name": "area",
                "titles": "area",
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

### CSVs as self-contained datasets

A CSVW should provide all the necessary metadata that would be needed for a user of the data to feature it in a `dcat:Catalog`. 

The subject resource of a CSVW metadata file is typically a `csvw:Table` which corresponds to a CSV file. This CSV file can be considered as a distribution of some `dcat:Dataset`.

When using a CSVW metadata file to describe some CSV, we recommend asserting the distribution relationship between the `csvw:Table` and the `dcat:Dataset`. The CSVW specification prohibits the use of the `@reverse` JSON-LD property, meaning we are unable to use the `dcat:distribution` property to achieve this, and instead rely upon its inverse `dcat:isDistributionOf`.

```mermaid
classDiagram
    class `Table` {
        a csvw:Table, dcat:Distribution
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
        "dcterms:title": "Life expectancy by local authority and sex",
        "dcterms:description": "The figures in this table are constructed from the estimated population and total deaths by single year / quinary age each year, based on a three year average. The expected years of life is the lifetime of a newborn person if they were subject throughout their lives to the average recorded death rate of the three year period. Such a calculation excludes future improvements to mortality rates."
    },
    "tableSchema": {
        "columns": [
            {
                "name": "area",
                "titles": "area",
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

### Discoverability of CSVW

We recommend naming CSVW metadata files by appending `-metadata.json` to end the CSV's filename, so a CSV file named `countries.csv` would have a metadata file named `countries.csv-metadata.json`.

Where possible, we recommend serving CSV files with a `Link` header within the response with the `rel="describedby"` attribute pointing to the CSVW metadata file.

We recommend CSVW metadata is served with the media type `application/csvm+json`.

### Foreign-key constraints

Publishers may wish to use the `csvw:foreignKey` property to assert relationships between different CSVs.

## RDF data cubes

The [RDF data cube vocabulary](https://www.w3.org/TR/vocab-data-cube/) provides a way to provide an explicit linked-data representation of a tabular dataset. 

### Classes

```mermaid
classDiagram
    class `RDF Data Cube` {
        a qb:DataSet, dcat:Distribution
    }
    class `Data Structure Definition` {
        a qb:DataStructureDefinition
    }
    class Component {
        a qb:ComponentSpecification
    }
    class Dimension {
        a qb:DimensionProperty
    }
    class Measure {
        a qb:MeasureProperty
    }
    class Attribute {
        a qb:AttributeProperty
    }

    `RDF Data Cube` --> "1" `Data Structure Definition` : qb.structure
    `Data Structure Definition` --> "1..*" Component: qb.component
    Component --> "1" Dimension: qb.dimension
    Component --> "1" Measure: qb.measure
    Component --> "1" Attribute: qb.attribute
  
```

### Datacube

We recommend datacubes have IRIs of the form:

- `http://{dataset_iri}/datacube`
- `http://{dataset_iri}#datacube`

| Property       | Requirement level | Notes |
| -------------- | ----------------- | ----- |
| `qb:structure` | mandatory         |       |

For additional properties see [Distributions](#distributions).

### Data structure definition

We recommend data structure definitions have IRIs of the form:

- `http://{dataset_iri}/datacube/structure`
- `http://{dataset_iri}#datacube/structure`

| Property       | Requirement level | Notes |
| -------------- | ----------------- | ----- |
| `qb:component` | mandatory         |       |

#### Component specification

We recommend component specifications have IRIs of the form:

- `http://{dataset_iri}/datacube/component/{component_name}`
- `http://{dataset_iri}#datacube/component/{component_name}`


| Property       | Requirement level | Notes |
| -------------- | ----------------- | ----- |
| `qb:dimension` | mandatory         |       |
| `qb:measure`   | mandatory         |       |
| `qb:order`     | recommended       |       |
| `qb:attribute` | optional          |       |

### Components

The components of a data cube are its dimensions, measures and attributes.

- If components are used across many different data cubes (common dimensions such as time or geography) then we should assign an IRI which is sufficiently general and not tied to a particular dataset.
- If components are unlikely to be used across many different data cubes (for example if they are domain specific) but will be reused by cubes in the same series, then we can assign an IRI which is "local" to the dataset series.
- If components are likely to only be used within one dataset, then we can assign an IRI which is "local" to that dataset.

IRI schemes which follow this idea are:

- `http://{domain}/dimension/{dimension_name}` (example of a general IRI)
- `http://{domain}/series/name-of-my-statistical-series/dimension/{dimension_name}` (example of an IRI which is local to a dataset series)
- `http://{domain}/dataset/name-of-my-dataset/dimension/{dimension_name}` (example of an IRI which is local to a dataset)

#### Measure

```ttl
ex:measure1 a qb:MeasureProperty ;
    rdfs:label "Measure 1"@en ;
    rdfs:comment "A measure property"@en ;
    rdfs:range xsd:decimal ;
    .
```

| Property             | Requirement level | Notes |
| -------------------- | ----------------- | ----- |
| `rdfs:label`         | mandatory         |       |
| `rdfs:comment`       | mandatory         |       |
| `rdfs:range`         | mandatory         |       |
| `qb:concept`         | recommended       |       |
| `rdfs:subPropertyOf` | optional          |       |

#### Dimension

```ttl
ex:dimension1 a qb:DimensionProperty ;
    rdfs:label "Dimension 1"@en ;
    rdfs:comment "A dimension property"@en ;
    rdfs:range skos:Concept ;
    qb:codeList <http://data.gov.uk/codelist/some-codelist> ;
    .
```

| Property             | Requirement level | Notes                       |
| -------------------- | ----------------- | --------------------------- |
| `rdfs:label`         | mandatory         |                             |
| `rdfs:comment`       | mandatory         |                             |
| `qb:codelist`        | recommended       | See [codelists](#codelists) |
| `rdfs:range`         | recommended       | Typically `skos:Concept`    |
| `qb:concept`         | recommended       |                             |
| `rdfs:subPropertyOf` | optional          |                             |

Dimensions should have an associated codelist (see [codelists](#codelists)).

#### Attribute

```ttl
ex:attribute1 a qb:AttributeProperty ;
    rdfs:label "Attribute 1"@en ;
    rdfs:comment "An attribute property"@en ;
    rdfs:range skos:Concept ;
    qb:codeList <http://data.gov.uk/codelist/statistical-markers> ;
    .
```

| Property             | Requirement level | Notes                       |
| -------------------- | ----------------- | --------------------------- |
| `rdfs:label`         | mandatory         |                             |
| `rdfs:comment`       | mandatory         |                             |
| `qb:codelist`        | recommended       | See [codelists](#codelists) |
| `rdfs:range`         | recommended       | Typically `skos:Concept`    |
| `qb:concept`         | recommended       |                             |
| `rdfs:subPropertyOf` | optional          |                             |

We allow attributes to be attached to a list of of values via `qb:codeList`.

### Observation

The dimensions form a composite key for each observation in the cube - meaning the combination of dimensions can be used to uniquely identify each observation in the cube. Note that a measure is a dimension.

We recommend IRIs for observations be of the form:

- `http://{domain}/datacube/obs/{dimension_1}-{...}-{dimension_n}`
- `http://{domain}#datacube/obs/{dimension_1}-{...}-{dimension_n}`

For example:

- `http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/datacube/obs/W06000022-2004-01-01T00:00:00/P3Y-Male`

### Using CSVW to create a RDF data cube

A CSVW provides a way for the rows, cells and column headers of a CSV files to be mapped to RDF resources.

The CSVW specification also describes a method for [transforming CSV files into RDF](https://www.w3.org/TR/csv2rdf/). By doing so, we can generate an RDF data cube. The idea is to use the CSVW `aboutUrl`, `propertyUrl` and `valueUrl` to construct triples from the CSV data.

Given a CSVW with a column specification as follows:

```jsonc
    // ...
    "tableSchema": {
        "columns": [
            {
                "name": "area",
                "titles": "area",
                "datatype": "string",
                "propertyUrl": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/dimension/area",
                "valueUrl": "http://statistics.data.gov.uk/id/statistical-geography/{area}"
            },
            // ...
        ],
        "aboutUrl": "http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/datacube/obs/{+area}-{+period}-{+sex}"
```

The `aboutUrl`, `propertyUrl` and `valueUrl` and the CSV data produce triples as follows:

```ttl
<http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/datacube/obs/W06000022-2004-01-01T00:00:00/P3Y-Male>
  <http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/dimension/area>
    <http://statistics.data.gov.uk/id/statistical-geography/W06000022> ;
    # ...
    .
```

For example, we can represent the relationships between the following resources within a single CSVW metadata file:

- a dataset: `<http://data.gov.uk/dataset/my-dataset>`
- a CSV distribution of that dataset: `<http://data.gov.uk/dataset/my-dataset.csv>`
- an RDF data cube distribution of that dataset: `<http://data.gov.uk/dataset/my-dataset/datacube>`

Our recommended format for a CSVW is as follows. Note the use of virtual columns within the CSVW `columns` definition to assert additional RDF relationships when converting CSV to RDF.

```jsonc
{
    "@context": "http://www.w3.org/ns/csvw",
    "@id": "http://data.gov.uk/dataset/my-dataset.csv",
    "url": "http://data.gov.uk/dataset/my-dataset.csv",
    "tableSchema": {
        "columns": [
            // CSVW column definitions,
            // ...
            {
                "virtual": true,
                "propertyUrl": "rdf:type",
                "valueUrl": "qb:Observation"
            },
            {
                "virtual": true,
                "propertyUrl": "qb:dataSet",
                "valueUrl": "http://data.gov.uk/dataset/my-dataset/datacube"
            }
        ]
    },
    "dcat:mediaType": {
        "@id": "http://www.w3.org/ns/iana/media-types/text/csv#Resource"
    },
    "dcat:isDistributionOf": {
        "@id": "http://data.gov.uk/dataset/my-dataset",
        "@type": "dcat:Dataset",
        "dcat:distribution": [
            {
                "@id": "http://data.gov.uk/dataset/my-dataset.csv",
                "@type": "dcat:Distribution"
            },
            {
                "@id": "http://data.gov.uk/dataset/my-dataset/datacube",
                "@type": [
                    "qb:DataSet",
                    "dcat:Distribution"
                ],
                "qb:structure": {
                    "@id": "http://data.gov.uk/dataset/my-dataset/datacube/structure",
                    "@type": "qb:DataStructureDefinition",
                    "qb:component": [
                        // dimension, measures, attributes...
                    ]
                }
            }
        ]
    }
}
```

Diagramatically, the CSV distribution, the dataset and the RDF data cube distribution (and its components) are related in the following way:

```mermaid
classDiagram
    class `Table` {
        a csvw:Table, dcat:Distribution
    }
    class `Dataset` {
        a dcat:Dataset
    }
    class `RDF Data Cube` {
        a qb:DataSet, dcat:Distribution
    }
    class `Data Structure Definition` {
        a qb:DataStructureDefinition
    }
    class Component {
        a qb:ComponentSpecification
    }
    class Dimension {
        a qb:DimensionProperty
    }
    class Measure {
        a qb:MeasureProperty
    }
    class Attribute {
        a qb:AttributeProperty
    }

    Table --> "1" Dataset: dcat.isDistributionOf
    Table "1" <-- Dataset: dcat.distribution
    Dataset --> "1" `RDF Data Cube` : dcat.distribution
    `RDF Data Cube` --> "1" `Data Structure Definition` : qb.structure
    `Data Structure Definition` --> "1..*" Component: qb.component
    Component --> "1" Dimension: qb.dimension
    Component --> "1" Measure: qb.measure
    Component --> "1" Attribute: qb.attribute
  
```

We may then generate an RDF representation of the data which describes an RDF data cube, using a CSVW and following the approach as set out in [Generating RDF from Tabular Data on the Web](https://www.w3.org/TR/csv2rdf/).

### Multiple measures

We adopt the [measure dimension](https://www.w3.org/TR/vocab-data-cube/#dfn-measure-dimension) approach as, unlike the [multi-measure observations](https://www.w3.org/TR/vocab-data-cube/#dsd-mm-obs) approach, this allows us to specify measure-specific and observation-specific attributes.

We include a column in the CSV which specifies the measure for each observation.


| area      | period                  | sex    | measure_type                    | value | marker |
| --------- | ----------------------- | ------ | ------------------------------- | ----- | ------ |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 76.7  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 | 80.7  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Male   | disability-free-life-expectancy | 70.1  |        |
| W06000022 | 2004-01-01T00:00:00/P3Y | Female | disability-free-life-expectancy | 80.2  | [p]    |
| W06000015 | 2004-01-01T00:00:00/P3Y | Male   | life-expectancy                 | 78.7  |        |
| W06000015 | 2004-01-01T00:00:00/P3Y | Female | life-expectancy                 |       | [x]    |
| ...       | ...                     | ...    | ...                             | ...   |        |

Within the CSVW metadata, we add a column definition for the measure dimension and values columns look as follows:

```json
{
    "titles": "measure_type",
    "name": "measure_type",
    "propertyUrl": "qb:measureType",
    "valueUrl": "http://{domain}/dataset/name-of-my-dataset/measure/{measure_type}"
},
{
    "titles": "value",
    "name": "value",
    "propertyUrl": "http://{domain}/dataset/name-of-my-dataset/measure/{measure_type}"
}
```

```ttl
<http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/datacube/obs/W06000022-2004-01-01T00:00:00/P3Y-Male> a qb:Observation ;
    # area, period, sex, ...
    qb:measureType
        <http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/measure/life-expectancy> ;
    <http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/measure/life-expectancy>
        76.7 ;
    .
```


## Appendicies

### Recommended codelists

#### Geography

Prefer using IRIs from the `http://statistics.data.gov.uk` vocabulary, based on ONS geography codes.

| Label             | IRI                                                                |
| ----------------- | ------------------------------------------------------------------ |
| United Kingdom    | `http://statistics.data.gov.uk/id/statistical-geography/K02000001` |
| Great Britain     | `http://statistics.data.gov.uk/id/statistical-geography/K03000001` |
| England and Wales | `http://statistics.data.gov.uk/id/statistical-geography/K04000001` |
| England           | `http://statistics.data.gov.uk/id/statistical-geography/E92000001` |
| Northern Ireland  | `http://statistics.data.gov.uk/id/statistical-geography/N92000002` |
| Scotland          | `http://statistics.data.gov.uk/id/statistical-geography/S92000002` |
| Wales             | `http://statistics.data.gov.uk/id/statistical-geography/W92000002` |

#### Dates and times

Data providers should prefer using `xsd:date` and `xsd:dateTime` literals to describe `dcterms:issued` and `dcterms:modified`, for example:

```
<http://data.gov.uk/dataset/my-dataset> dcterms:issued "2018-01-01"^^xsd:date .
<http://data.gov.uk/dataset/my-dataset-2> dcterms:issued "2018-01-01T09:30:00"^^xsd:dateTime .
```

Data providers should prefer using IRIs from the `http://reference.data.gov.uk` vocabulary to describe dates and times within datasets (for example a time dimension). The IRI scheme is described [here](https://github.com/epimorphics/IntervalServer/blob/master/interval-IRIs.md).

#### Frequency

Data providers should prefer using IRIs from the [Dublin core collection description frequency vocabulary](https://www.dublincore.org/specifications/dublin-core/collection-description/frequency/), `http://purl.org/cld/freq/`.

Common options include:

| Label     | IRI                                  |
| --------- | ------------------------------------ |
| Annual    | `http://purl.org/cld/freq/annual`    |
| Quarterly | `http://purl.org/cld/freq/quarterly` |
| Monthly   | `http://purl.org/cld/freq/monthly`   |
| Weekly    | `http://purl.org/cld/freq/weekly`    |
| Daily     | `http://purl.org/cld/freq/daily`     |

#### Licenses

| Label                        | IRI                                                                         |
| ---------------------------- | --------------------------------------------------------------------------- |
| Open Government Licence v3.0 | `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/` |
| Open Government Licence v2.0 | `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/` |
| Open Government Licence v1.0 | `http://www.nationalarchives.gov.uk/doc/open-government-licence/version/1/` |

#### Organisations

GOV.UK provides a [list of government organisations](https://www.gov.uk/government/organisations), which can be used to populate the `dcterms:publisher` and `dcterms:creator` properties.

For example: `https://www.gov.uk/government/organisations/office-for-national-statistics`.

#### Statistics designations

> TODO: IRIs for official / national / experimental stats classifications.

| Label                   | IRI                                           |
| ----------------------- | --------------------------------------------- |
| National Statistics     | `https://data.gov.uk/national-statistics`     |
| Official Statistics     | `https://data.gov.uk/official-statistics`     |
| Experimental Statistics | `https://data.gov.uk/experimental-statistics` |

#### Symbols and shorthand in tables

Data providers should adopt the [analytical function guidance](https://analysisfunction.civilservice.gov.uk/policy-store/symbols-in-tables-definitions-and-help/) for statistical markers. See [using symbols and shorthand in tables](#using-symbols-and-shorthand-in-tables) for usage.

See [Using symbols and shorthand in tables](#using-symbols-and-shorthand-in-tables) for usage.

| Label                       | Notation | IRI                                                          |
| --------------------------- | -------- | ------------------------------------------------------------ |
| Break in time series        | `[b]`    | `http://data.gov.uk/codelist/statistical-markers/code/[b]`   |
| Confidential                | `[c]`    | `http://data.gov.uk/codelist/statistical-markers/code/[c]`   |
| Estimated                   | `[e]`    | `http://data.gov.uk/codelist/statistical-markers/code/[e]`   |
| Earliest revision           | `[er]`   | `http://data.gov.uk/codelist/statistical-markers/code/[er]`  |
| Forecast                    | `[f]`    | `http://data.gov.uk/codelist/statistical-markers/code/[f]`   |
| Low                         | `[low]`  | `http://data.gov.uk/codelist/statistical-markers/code/[low]` |
| Not significant             | `[ns]`   | `http://data.gov.uk/codelist/statistical-markers/code/[ns]`  |
| Provisional                 | `[p]`    | `http://data.gov.uk/codelist/statistical-markers/code/[p]`   |
| Revised                     | `[r]`    | `http://data.gov.uk/codelist/statistical-markers/code/[r]`   |
| Significance level of 0.05  | `[s]`    | `http://data.gov.uk/codelist/statistical-markers/code/[s]`   |
| Significance level of 0.01  | `[ss]`   | `http://data.gov.uk/codelist/statistical-markers/code/[ss]`  |
| Significance level of 0.001 | `[sss]`  | `http://data.gov.uk/codelist/statistical-markers/code/[sss]` |
| Low reliability             | `[u]`    | `http://data.gov.uk/codelist/statistical-markers/code/[u]`   |
| None recorded in survey     | `[w]`    | `http://data.gov.uk/codelist/statistical-markers/code/[w]`   |
| Not available               | `[x]`    | `http://data.gov.uk/codelist/statistical-markers/code/[x]`   |
| Not applicable              | `[z]`    | `http://data.gov.uk/codelist/statistical-markers/code/[z]`   |

#### Themes

| Label                                         | IRI                                                                                     |
| --------------------------------------------- | --------------------------------------------------------------------------------------- |
| Business, Trade and International Development | `http://osr.statisticsauthority.gov.uk/themes/business-trade-international-development` |
| Children, Education and Skills                | `http://osr.statisticsauthority.gov.uk/themes/children-education-skills`                |
| Crime and Security                            | `http://osr.statisticsauthority.gov.uk/themes/crime-security`                           |
| Economy                                       | `http://osr.statisticsauthority.gov.uk/themes/economy`                                  |
| Health and Social Care                        | `http://osr.statisticsauthority.gov.uk/themes/health-social-care`                       |
| Housing, Planning and Local Services          | `http://osr.statisticsauthority.gov.uk/themes/housing-planning-local-services`          |
| Labour Market and Welfare                     | `http://osr.statisticsauthority.gov.uk/themes/labour-market-welfare`                    |
| Population and Society                        | `http://osr.statisticsauthority.gov.uk/themes/population-society`                       |
| Transport, Environment and Climate Change     | `http://osr.statisticsauthority.gov.uk/themes/transport-environment-climate-change`     |

#### Media types

https://www.w3.org/ns/iana/media-types/

| Label  | IRI                                                                |
| ------ | ------------------------------------------------------------------ |
| CSV    | `http://www.w3.org/ns/iana/media-types/text/csv#Resource`         |
| JSON   | `http://www.w3.org/ns/iana/media-types/application/json#Resource` |
| Turtle | `http://www.w3.org/ns/iana/media-types/text/turtle#Resource`      |

### Hash or slash IRIs

- [HashVsSlash](https://www.w3.org/wiki/HashVsSlash)
- [Best Practice Recipes for Publishing RDF Vocabularies](https://www.w3.org/TR/swbp-vocab-pub)

Data producers must ensure that resource IRIs resolve sensibly and avoid `40X` or `50X` HTTP status codes. Throughout this profile we present IRI choices using both hash `#` and slash `/` IRIs. Data producers should pick the most appropriate choice, considering whether the resulting IRIs will resolve sensibly.

Newly created IRIs should avoid including a trailing slash.

### `rdfs` vs `dcterms`

> Some helpful discussion [here](https://jazz.net/wiki/bin/view/LinkedData/UseOfRdfsLabelVersusDctermsTitle).

The `rdfs` and `dcterms` vocabularies offer similar properties: `rdfs:label` and `rdfs:comment` vs. `dcterms:title` and `dcterms:description`.

For document-like resources, we use `dcterms`. So resources of class `dcat:Dataset`, `dcat:Catalog`, `dcat:Distribution` etc. should use `dcterms`.

For vocabulary definitions we adopt `rdfs`, so `skos:Concept` and `qb:ComponentProperty` resources should use `rdfs`.

### Publishers, creators and contacts

We intend the object of `dcat:publisher` and `dcat:creator` predicates to be an IRI, representing the publishing or creating organisation.

For contact points, we adopt the `vcard` vocabulary.

```ttl
<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> 
    dcat:contactPoint <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/contact> .

<http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/contact> a vcard:Individual ;
    vcard:hasEmail <mailto:joe.bloggs@ons.gov.uk> ;
    vcard:hasTelephone <tel:+441234123456> ;
    vcard:fn "Joe Bloggs" ;
    .
```

### Class diagram

```mermaid
classDiagram
    class `Table` {
        a csvw:Table, dcat:Distribution
    }
    class `Table Schema` {
        a csvw:TableSchema
    }
    class `Column` {
        a csvw:Column
    }
    class `Dataset` {
        a dcat:Dataset
    }
    class `RDF Data Cube` {
        a qb:DataSet, dcat:Distribution
    }
    class `Data Structure Definition` {
        a qb:DataStructureDefinition
    }
    class Component {
        a qb:ComponentSpecification
    }
    class Dimension {
        a qb:DimensionProperty
    }
    class Measure {
        a qb:MeasureProperty
    }
    class Attribute {
        a qb:AttributeProperty
    }
    class Codelist {
        a skos:ConceptScheme, dcat:Dataset
    }
    class Code {
        a skos:Concept
    }
    class Catalog {
        a dcat:Catalog
    }
    class CatalogRecord {
        a dcat:CatalogRecord
    }
    class DatasetSeries{
        a dcat:DatasetSeries
    }

    Catalog --> "1..*" CatalogRecord : dcat.record
    CatalogRecord --> "1" DatasetSeries : foaf.primaryTopic
    CatalogRecord --> "1" Dataset : foaf.primaryTopic

    DatasetSeries "1" <-- Dataset : dcat.inSeries

    Table --> "1" `Table Schema`: csvw.tableSchema
    `Table Schema` --> "1..*" Column: csvw.column
    Table --> "1" Dataset: dcat.isDistributionOf
    Table "1" <-- Dataset: dcat.distribution
    Dataset --> "1" `RDF Data Cube` : dcat.distribution
    `RDF Data Cube` --> "1" `Data Structure Definition` : qb.structure
    `Data Structure Definition` --> "1..*" Component: qb.component
    Component --> "1" Dimension: qb.dimension
    Component --> "1" Measure: qb.measure
    Component --> "1" Attribute: qb.attribute
    Dimension --> "1" Codelist : qb.codeList
    Codelist --> "1..*" Code : skos.hasTopConcept
    Code --> "1" Codelist : skos.inScheme
    Code --> "1..*" Code : skos.narrower
    Code "1" <--  Code : skos.broader
    Dataset --> Codelist : dcat.qualifiedRelation
```

### Future work

This section includes links to other vocabularies or ideas we may develop further for full inclusion in the profile.

- [Data quality vocab](http://www.w3.org/TR/vocab-dqv/)
- [Data usage vocab](http://www.w3.org/TR/vocab-duv/)
- [Data privacy vocab](http://dpvcg.github.io/dpv/)

#### Provenance

> **Warning**
> This section needs further work.

> TODO: https://www.w3.org/TR/prov-o/

> TODO: https://ceur-ws.org/Vol-2549/article-08.pdf

```ttl
# We have a dcat:Dataset with a CSVW distribution and a qb:DataSet distribution
</dataset/sweden-at-eurovision> a dcat:Dataset ;
    dcat:distribution </dataset/sweden-at-eurovision.csv>, </dataset/sweden-at-eurovision/datacube> ;
    .

# The CSVW distribution is prov:derivedFrom some upstream datasource
</dataset/sweden-at-eurovision.csv> a csvw:Table ;
    prov:wasDerivedFrom <https://en.wikipedia.org/wiki/Sweden_in_the_Eurovision_Song_Contest> ;
    # We can qualify (provide more detail) about the derivation if we want:
    prov:qualifiedDerivation [
        a prov:Derivation;
        # The CSV was derived from the wikipedia page
        prov:entity <https://en.wikipedia.org/wiki/Sweden_in_the_Eurovision_Song_Contest> ;
        # It was derived in the Jenkins pipeline
        prov:hadActivity <http://ci.data.gov.uk/12718530-bff7-4a6f-907d-f0ee564e8cac> ;
    ] ;
    prov:wasGeneratedBy <http://ci.data.gov.uk/12718530-bff7-4a6f-907d-f0ee564e8cac> ;
    .

# The qb:DataSet was derived from the CSV + CSVW metadata
</dataset/sweden-at-eurovision/datacube> a qb:DataSet ; 
    prov:wasDerivedFrom </dataset/sweden-at-eurovision.csv>, </dataset/sweden-at-eurovision.csv-metadata.json> ;
    prov:wasGeneratedBy <http://ci.data.gov.uk/12718530-bff7-4a6f-907d-f0ee564e8cac> ;
    .

<http://ci.data.gov.uk/12718530-bff7-4a6f-907d-f0ee564e8cac> a prov:Activity ;
    prov:wasAssociatedWith <https://github.com/Swirrl/csv2rdf>, <https://github.com/GSS-Cogs/csvcubed> ;
    prov:startedAtTime "2015-02-13T15:12:44"^^xsd:dateTime ;
    prov:endedAtTime   "2015-02-13T15:12:46"^^xsd:dateTime ;
    prov:used <https://en.wikipedia.org/wiki/Sweden_in_the_Eurovision_Song_Contest>,
        </dataset/sweden-at-eurovision.csv>,
        </dataset/sweden-at-eurovision.csv-metadata.json> ;
    prov:qualifiedUsage [ a prov:Usage ;
        prov:entity </dataset/sweden-at-eurovision.csv> ;
        prov:hadRole csvw:csvEncodedTabularData
    ];
    prov:qualifiedUsage [ a prov:Usage ;
        prov:entity </dataset/sweden-at-eurovision.csv-metadata.json> ;
        prov:hadRole csvw:tabularMetadata
    ];
    .
```

[^machine]: https://w3c.github.io/dwbp/bp.html#machine_readable
    
[^named-graphs]: https://www.w3.org/TR/vocab-dcat-3/#Class:Catalog_Record