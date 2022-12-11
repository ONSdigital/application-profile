# Application Profile

_Working draft._

The key words must, must not, required, shall, shall not, should, should not, recommended, may, and optional are to be interpreted as described in RFC 2119.

## Preamble

The UK government often [publishes its statistics](https://www.gov.uk/search/research-and-statistics?content_store_document_type=statistics_published&order=updated-newest) in presentational spreadsheets. While this succeeds in getting important information into the public domain, we recognise there are still barriers and challenges in accessing and using the data we produce:
- Analysts need to wrangle data because data are in unstandardised and presentational formats.
- A user must locate and navigate through many large spreadsheets to understand what data are available.
- Metadata are provided in an unstructured or unstandardised ways.
- Data are in silos, making it difficult to link or relate statistics from different sources.
- The accessibility and usability of statistics varies from dataset to dataset.

The [Data on the Web Best Practices (DWBP)](https://www.w3.org/TR/dwbp/) describes recommendations for publishing data to the web. If followed, we can enable these benefits:

> - **Comprehension**: humans will have a better understanding about the data structure, the data meaning, the metadata and the nature of the dataset.
> - **Processability**: machines will be able to automatically process and manipulate the data within a dataset.
> - **Discoverability** machines will be able to automatically discover a dataset or data within a dataset.
> - **Reuse**: the chances of dataset reuse by different groups of data consumers will increase.
> - **Trust**: the confidence that consumers have in the dataset will improve.
> - **Linkability**: it will be possible to create links between data resources (datasets and data items).
> - **Access**: humans and machines will be able to access up to date data in a variety of forms.
> - **Interoperability**: it will be easier to reach consensus among data publishers and consumers.

Amalgamating the 5* and the FAIR data principles provides a means understanding and lowering the above mentioned challenges relating to the access and use of data.

5* Open Data is based on the following principles,

★     data needs to be able to be published on the web,

★★    data needs to be machine-readable,

★★★   data needs to be non-proprietary,

★★★★  identifiers need to be used to denote things, so that people can talk about resources unambiguously,

★★★★★ data needs to able to be linkied to other data to provide context.

To aid humans who increasingly rely on computational support to deal with increased volumes of data, complexity, and creation speed of data, The FAIR Principles were conceived.

The FAIR Principle consist of the following,

Findability, 
Accessibility, 
Interoperability, 
and Reuse of digital assets.

Merging these two similar concepts requires data publishers and users to shift their perspective from a tabular view of the world with its rows, columns and cells to one of graphs, nodes and edges. CSV as a starting point is useful, however learning a new set of technologies like RDF ontologies and SPARQL queries is important to get things into context.
In spite al the above, the following shortcomings restrict the CSV data format attaining 5* Open Data Status

These shortcomings include
1. Different dialects of CSV, which require different approaches to quoting fields and escaping special characters.
2. Multiple differences are possible in encoding, thus creating confusion within any text format.
3. Ther inability to say in advance how the fields in CSV file ought to be interpreted 

This brings into focus the FAIR Guiding Principles for scientific data management and stewardship. The  CSV format is an incredibly simple way to reach the third star of the 5 star deployment scheme for open data:

★ you can publish CSV on the web (with an open license) This means you can make CSV data available on the web, in whatever format, but with an open license, so as to be Open Data. Consumers can look, search, store, change data and share the data with anyone they like. As a data publisher, an organization knows that CSV is simple to publish and does not need to constantly explain to others that they can use the data.

★★ CSV is a machine-readable format. CSV can be made available as machine-readable structured data, for example, an excel spreadsheet instead of an image scan of a table. The users of 2-star open data can do anything they do with a 1-star data plus directly processing it with proprietary software and exporting it into another structured format. However, that type of data is still locked up because users depend on proprietary software to be able to get the data out of a document.

★★★ CSV is non-proprietary. Users don’t require proprietary software package in order to analyze CSV, (CSV) format that stores tabular data in plain text.

★★★★  CSV does not conform to a 4th star Web data format. Identifiers cannot be used to denote things, and people cannot talk about resources unambiguously. Overlapping with the FAIR Guiding Principles, CSV data is not Findable. The first step in (re)using data is to find them. Metadata and data should be easy to find for both humans and computers, CSV does not have Metadata capabilities. Machine-readable metadata are essential for automatic discovery of datasets and services,

★★★★★ CSV data needs to able to be linkied to other data to provide context, which is not the case. CSV data need to be Interoperable in order to be integrated with other data. In addition, the data need to interoperate with applications or workflows for analysis, storage, and processing. Interoperability is the third principle, the "I" part of the FAIR Guiding Principles. With the help of the W3C standards and Linked Data principles, data publishers link their data to other people’s data to provide context. This is the prerequisite for getting the fifth star for Linked Open Data, according to Sir Berners-Lee. In order for data to provide context it needs to be linked.

The shortcomings of CSV mentioned above prompted a W3C working group set out to provide recommendations for working with CSV on the Web. This “CSVW” standard provides a way to resolve the problems with CSV. CSVW is a standard for describing and clarifying the content of CSV tables. 

The CSV format has been proved to be highly effective for machine-readability, and needs to be mapped to to RDF resources, and CSVW (CSV for the Web) provides a means for the rows, cells, column headers of a CSV to be mapped. This standard provides a way to resolve shortcomings that arise with CSV. This includes standardising dialects and expressing types. Furthermore it extends CSV with identifiers to make 5 star linked-data in CSV format. In essence, a CSV file is linked with a JSON document to provide some addition metadata to describe and clarify the content of the CSV file.

CSVW metadata can be used to drive a user interface for users to discover metadata. Linked data is not a specification, it is a set of practices for providing a data infrastructure of shared data across the web. Linked data provides us with the opportunity to exploit open data on the web, in applications.

Linked data is powered by technologies such as RDF, OWL, SKOS, and SPARQL. CSVW standard is used to make a machine-readable definition of how to interpret a CSV file, this is done by a JSON file.

We have explored how to follow the best practices when publishing statistics, in particular through the use of the CSV on the Web (CSVW), Data Catalog (DCAT) and RDF Data Cube (QB) standards and vocabularies. This document is an application profile of these standards, describing a recommendation on how to use these standards together in order to achieve the data on the web best practices.
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
| `xkos`    | `http://rdf-vocabulary.ddialliance.org/xkos#` | XKOS: an SKOS extension for representing statistical classifications                 |
| `xsd`     | `http://www.w3.org/2001/XMLSchema#`           | XML Schema Part 2: Datatypes Second Edition                                          |
| `vcard`   | `http://www.w3.org/2006/vcard/ns#`            | File format standard for electronic business cards                                   |

## Data structure

### Publish machine-readable data

> Machine-readable data is data in a standard format that can be read and processed automatically by a computing system. Traditional word processing documents and portable document format (PDF) files are easily read by humans but typically are difficult for machines to interpret and manipulate. Formats such as XML, JSON, HDF5, RDF and CSV are machine-readable data formats [^machine]

Many of the excel workbooks produced by statisticians are designed to be easily read by humans but typically are difficult for machines to interpret and manipulate.

As mentioned above, CSV on the Web (CSVW) standard adds metadata to describe the contents and structure of comma-separated values (CSV) data files thus bringing the power of linked-data to the versatile CSV format.

In order to achieve JSON, RDF, and SPARQL formats data has to undergo a transformation. The Semantic Web Project's value proposition is to enable the ability to say anything, about anything, whenever, and from wherever, in a manner that's both machine and human comprehensible.

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

In this example, adopting ISO 8601 time intervals allows machines to provide additional functionality for computing with this type of data. Adopting geography codes allows for linking between data sets.

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

When [using a CSVW to create an RDF data cube](#using-csvw-to-create-an-rdf-data-cube), any redundant columns must be suppressed by setting `"suppressOutput": "true"`.

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

> TODO: Is there a need to support a multiple-measure structure instead of a measure-type dimension, e.g.
>
> | area      | period                  | sex    | life_expectancy | life_expectancy_marker | disability_free_life_expectancy | disability_free_life_expectancy_marker |
> | ----------- | ------------------------- | -------- | ----------------- | ------------------------ | --------------------------------- | ---------------------------------------- |
> | W06000022 | 2004-01-01T00:00:00/P3Y | Male   | 76.7            |                        | 70.1                            |                                        |
> | W06000022 | 2004-01-01T00:00:00/P3Y | Female | 80.7            |                        | 80.2                            | [p]                                    |
> | W06000015 | 2004-01-01T00:00:00/P3Y | Male   | 78.7            |                        | 70.3                            |                                        |
> | W06000015 | 2004-01-01T00:00:00/P3Y | Female |                 | [x]                    | 80.4                            |                                        |
> | ...       | ...                     | ...    | ...             |                        |                                 |                                        |

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

### Different granularity of time periods

Statisticians may wish to report statistics at different time granularities. For example, a single dataset may report statistics by month, quarter, year and financial year.

| period    | industry | trade_value |
| --------- | -------- | ----------- |
| 2004      | 0        | ...         |
| 2004-2005 | 0        | ...         |
| 2004-01   | 0        | ...         |
| 2004-02   | 0        | ...         |
| ...       | ...      | ...         |
| 2005      | 00       | ...         |
| 2005-01   | 001      | ...         |
| 2005-02   | 01       | ...         |
| ...       | ...      | ...         |

We adopt IRIs from the [reference.data.gov.uk service](https://github.com/epimorphics/IntervalServer/blob/master/interval-uris.md).

`http://reference.data.gov.uk/id/{period_type}/{period}`

| period_type     | period    | industry | trade_value |
| --------------- | --------- | -------- | ----------- |
| year            | 2004      | 0        | ...         |
| government-year | 2004-2005 | 0        | ...         |
| month           | 2004-01   | 0        | ...         |
| month           | 2004-02   | 0        | ...         |
| ...             | ...       | ...      | ...         |
| year            | 2005      | 00       | ...         |
| government-year | 2005-2006 | 00       | ...         |
| month           | 2005-01   | 001      | ...         |
| month           | 2005-02   | 01       | ...         |
| ...             | ...       | ...      | ...         |

## Cataloguing

> TODO: Should we support dcat:DatasetSeries?

> TODO: Do we support cataloguing catalogues?

A catalogue is a collection of metadata about datasets which has been gathered and curated.

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

### Catalogue

We recommend catalogues have IRIs of the form:

- ```http://{domain}/catalogue```
- ```http://{domain}/catalogue/{catalogue_slug}```

For example:

- ```http://data.gov.uk/catalogue```
- ```http://data.gov.uk/catalogue/climate-change```

We recommend the use of the following properties:

| Property                | Requirement level | Notes                                                                     |
| ----------------------- | ----------------- | ------------------------------------------------------------------------- |
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

### Catalog Record

We recommend creaing a IRI for catalogue records by appending `/record` or `#record` to the IRI of the resource being described by the catalogue record:

- `{dataset_iri}/record`
- `{dataset_iri}#record`

For example:

- `http://data.gov.uk/dataset/my-dataset/record`
- `http://data.gov.uk/dataset/my-dataset#record`

We recommend the use of the following properties:

| Property               | Requirement level | Notes                                                                          |
| ---------------------- | ----------------- | ------------------------------------------------------------------------------ |
| `dcterms:issued`       | mandatory         | See [dates and times](#dates-and-times)                                        |
| `foaf:primaryTopic`    | mandatory         | This points to the IRI of the `dcat:Dataset` described by the catalogue record |
| `prov:wasAttributedTo` | recommended       |                                                                                |
| `dcterms:modified`     | recommended       | See [dates and times](#dates-and-times)                                        |

We may use `prov:wasAttributedTo` to attribute the creation of the catalogue record to a specific entity, such as the person who added the dataset to the catalogue.

For example:

```ttl
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix prov: <http://www.w3.org/ns/prov#> .

<http://data.gov.uk/dataset/my-dataset/record> a dcat:CatalogRecord ;
    dcterms:issued "2015-01-01"^^xsd:date ;
    foaf:primaryTopic <http://data.gov.uk/dataset/my-dataset> ;
    prov:wasAttributedTo <mailto:joe.bloggs@ons.gov.uk> ;
    .
```

### Dataset

We recommend standalone datasets have IRIs of the form:

- `http://{domain}/dataset/{dataset_slug}`

For datasets belonging to a dataset series, we recommend extending the series IRI to form the dataset IRI:

- `http://{domain}/series/{series_slug}/dataset/{edition_year}`

For example:

- `http://data.gov.uk/dataset/my-dataset`
- `http://data.gov.uk/series/some-dataset-series/dataset/2018`

We recommend the use of the following properties:

| Property                     | Requirement level | Notes                                                                     |
| ---------------------------- | ----------------- | ------------------------------------------------------------------------- |
| `dcterms:title`              | mandatory         | See [titles](#titles)                                                      |
| `dcterms:description`        | mandatory         | See [descriptions](#descriptions)                                          |
| `dcterms:publisher`          | mandatory         | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:license`            | mandatory         | See [licenses](#licenses)                                                  |
| `dcat:distribution`          | mandatory         | See [distributions](#distributions)                                        |
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
| `dcat:landingPage`           | optional          |                                                                           |
| `dcterms:identifier`         | optional          |                                                                           |
| `dcterms:isReferencedBy`     | optional          |                                                                           |

For example:

```ttl
<http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018> a dcat:Dataset ;
    dcterms:title "Final UK greenhouse gas emissions national statistics: 1990 to 2018"@en ;
    dcterms:description "Final estimates of UK territorial greenhouse gas emissions..."@en ;
    dcterms:license <https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/> ;
    dcterms:publisher <http://www.gov.uk/government/organisations/department-for-business-energy-and-industrial-strategy> ;
    dcterms:issued "2020-02-04T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2020-07-30T08:30:06"^^xsd:dateTime ;
    dcat:keyword "greenhouse gases"@en, "carbon emissions"@en, "greenhouse gas emissions"@en ;
    dcat:theme <http://osr.statisticsauthority.gov.uk/themes/transport-environment-climate-change/> ;
    dcat:contactPoint <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018/contact> ;
    dcat:distribution <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018/datacube>, 
        <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018.csv>, 
        <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018.json> ;
    dcterms:isReferencedBy <https://www.gov.uk/government/statistics/final-uk-greenhouse-gas-emissions-national-statistics-1990-to-2018> ;
    dcat:landingPage "http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018"^^xsd:anyURI ;
    dcterms:accrualPeriodicity <http://purl.org/cld/freq/annual> ;
    dcterms:spatial <http://statistics.data.gov.uk/id/statistical-geography/K02000001> ;
    dcterms:temporal <http://reference.data.gov.uk/id/gregorian-interval/1990-01-01T00:00:00/P28Y> ;
    dcat:inSeries <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics> ;
    dcat:hasCurrentVersion <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018/version/2> ;
    dcat:hasVersion <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018/version/1>, 
        <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018/version/2> ;
    dcat:version 2 ;
    adms:versionNotes "Dataset was corrected following an error being recognised."@en ;
    dcat:prev <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2017> ;
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

| Property                     | Requirement level | Notes                                                                     |
| ---------------------------- | ----------------- | ------------------------------------------------------------------------- |
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
<http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics> a dcat:DatasetSeries ;
    dcterms:title "UK territorial greenhouse gas emissions national statistics"@en ;
    dcterms:description "Final and provisional estimates of UK territorial greenhouse gas emissions from 1990."@en ;
    dcterms:issued "2015-02-11T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2022-03-31T08:30:14"^^xsd:dateTime ;
    .
```

Many of the properties which apply to dataset series are also applicable to datasets within that series. We recommend specifying properties for both resources.

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

We also recommend placing catalogue records into a named graph that is the same as the IRI of the catalog.

```ttl
<http://data.gov.uk/catalogue/my-datasets> {

    <http://data.gov.uk/catalogue/my-datasets> a dcat:Catalog ;
        dcterms:title "My datasets"@en ;
        dcterms:description "A description of my catalogue."@en ;
        dcterms:publisher <http://www.gov.uk/government/organisations/office-for-national-statistics> ;
        dcterms:issued "2015-01-01"^^xsd:date ;
        dcterms:modified "2018-01-01"^^xsd:date ;
        dcat:record <http://data.gov.uk/dataset/my-dataset/record> ;
        .

    <http://data.gov.uk/dataset/my-dataset/record> a dcat:CatalogRecord ;
        dcterms:title "My Dataset" ;
        dcterms:description "A description of my dataset."@en ;
        dcterms:publisher <http://www.gov.uk/government/organisations/office-for-national-statistics> ;
        dcterms:issued "2018-01-01"^^xsd:date ;
        .

}
```

## Distributions

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

The exception is when representing an RDF data cube as a distribution, for which there is no physical file and therefore no extension. In that instance, we recommend appending `/datacube` or `#datacube` to the dataset IRI.

- `http://{dataset_iri}/datacube`
- `http://{dataset_iri}#datacube`

For example:

- `http://data.gov.uk/dataset/my-dataset.csv`
- `http://data.gov.uk/dataset/my-dataset.ttl`
- `http://data.gov.uk/dataset/my-dataset.json`
- `http://data.gov.uk/dataset/my-dataset/datacube`

| Property                | Requirement level | Notes                                                                          |
| ----------------------- | ----------------- | ------------------------------------------------------------------------------ |
| `dcterms:title`         | mandatory         | See [titles](#titles)                                                           |
| `dcterms:description`   | mandatory         | See [descriptions](#descriptions)                                               |
| `dcterms:license`       | mandatory         | See [licenses](#licenses)                                                       |
| `dcterms:creator`       | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts)      |
| `dcterms:issued`        | recommended       | See [dates and times](#dates-and-times)                                         |
| `dcterms:modified`      | recommended       | See [dates and times](#dates-and-times)                                         |
| `dcat:isDistributionOf` | recommended       | See [CSVs as self contained datasets](#csvs-as-self-contained-datasets)         |
| `dcat:mediaType`        | recommended       | See [media types](#media-types)                                                 |
| `dcat:downloadURL`      | recommended       |                                                                                |
| `dcat:byteSize`         | recommended       |                                                                                |
| `spdx:checksum`         | recommended       |                                                                                |
| `wdrs:describedby`      | optional          | For CSV distributions, we can relate the CSVW metadata using`wdrs:describedby` |

For example:

```ttl
<http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018.csv> a dcat:Distribution ;
    dcterms:title "Final UK greenhouse gas emissions national statistics: 1990 to 2018 (CSV)"@en ;
    dcterms:description "Final estimates of UK territorial greenhouse gas emissions..."@en ;
    dcterms:license <https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/> ;
    dcterms:issued "2020-02-04T09:30:00"^^xsd:dateTime ;
    dcterms:modified "2020-07-30T08:30:06"^^xsd:dateTime ;
    dcterms:title "2018.csv" ;
    wdrs:describedby <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018.csv-metadata.json> ;
    dcat:mediaType <https://www.w3.org/ns/iana/media-types/text/csv#Resource> ;
    dcat:downloadURL <http://data.gov.uk/series/uk-territorial-greenhouse-gas-emissions-national-statistics/dataset/2018.csv> ;
    dcat:byteSize "12345"^^xsd:nonNegativeInteger ;
    spdx:checksum "CE114E4501D2F4E2DCEA3E17B546F339"^^spdx:Checksum ;
    .
```

### Content negotiation of distributions

We recommend that data providers implement content negotiation as a method for clients to access the data in the format they require.

The IRI of the `dcat:Dataset` should be used as the generic IRI which a user can request different formats of the data from.

For example, a `dcat:Dataset` with an IRI of `http://data.gov.uk/dataset/my-dataset` may have a CSV distribution with its own IRI of `http://data.gov.uk/dataset/my-dataset.csv`. A user agent wishing to access the data in CSV format could navigate to `http://data.gov.uk/dataset/my-dataset.csv` directly, or content negotiate against the IRI of the `dcat:Dataset` to find the CSV distribution.

```sh
curl http://data.gov.uk/dataset/my-dataset -H "Accept: text/csv"
```

> What is the flow, do we 303 redirect to the CSV distribution of the dataset?

```mermaid
sequenceDiagram
    User Agent ->> Server: GET http://data.gov.uk/dataset/my-dataset -H "accept: text/csv"
    Server ->> User Agent: 303 See Other
    User Agent ->> Server: GET http://data.gov.uk/dataset/my-dataset.csv
    Server ->> User Agent: 200 OK
```

## Editions

> `dcat:DatasetSeries` is recommended as part of [DCAT v3](https://w3c.github.io/dxwg/dcat/), which is still in draft.

Many statistics producers publish sets of statistics at a regular frequency as monthly, quarterly, or annual releases.

Previous years of data may be repeated without any changes, though in some instances some previous year's data may be revised or updated to include new data or better estimates.

We refer to these as _editions_, as opposed to _versions_ which are used to specifically describe changes in a dataset resulting from a revision. Each edition is given its own IRI which typically contains the latest time period for which data is available.

For example, `http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018` is the IRI of the 2018 edition of the series `name-of-my-statistical-series`.

Editions should be related to a `dcat:DatasetSeries`. The dataset series should have an IRI which does not reference particular time period and can represent the collection of editions.

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

### Scheduled revisions (provisional and final releases)

Statisticians may wish to release early or provisional estimates of statistics which are later revised as "final" statistics when additional data is available. The Government Statistical Service [refers to these as scheduled revisions](https://analysisfunction.civilservice.gov.uk/policy-store/communicating-quality-uncertainty-and-change/).

The IRIs of provisional and final datasets should contain `provisional` or `final`. Provisional and final statistics can both be attached to the same dataset series and related to one another by the `dcat:prev` property.

```mermaid
flowchart LR

    2017/provisional --> 2017/final
    2017/final --> 2018/provisional
    2018/provisional --> 2018/final

    2017/final -->|dcat:prev| 2017/provisional
    2018/provisional -->|dcat:prev| 2017/final
    2018/final -->|dcat:prev| 2018/provisional
   
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

## Versions

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

Given the above CSV, a fairly basic CSVW metadata file would look as follows:

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
                "datatype": "dayTimeDuration"
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

> **Note**
> This method of relating CSVW and DCAT together suggests the use of a DCAT inverse property `dcat:isDistributionOf`. This would need to introduce a new inverse property to the DCAT v3 vocabulary. We have contributed to an open issue [here](https://github.com/w3c/dxwg/issues/1322) which is being considered.

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

A example of a CSVW metadata file containing the relevant relationship with a `dcat:Dataset` could look as follows:

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
                "datatype": "dayTimeDuration"
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

### Components

The components of a data cube (dimensions/measures/attributes).

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

| Property             | Requirement level | Notes                       |
| -------------------- | ----------------- | --------------------------- |
| `rdfs:label`         | mandatory         |                             |
| `rdfs:comment`       | mandatory         |                             |
| `rdfs:range`         | mandatory         |                             |
| `qb:concept`         | recommended       |                             |
| `rdfs:subPropertyOf` | recommended       |                             |

#### Dimension

```ttl
ex:dimension1 a qb:DimensionProperty ;
    rdfs:label "Dimension 1"@en ;
    rdfs:comment "A dimension property"@en ;
    rdfs:range xsd:string ;
    .
```

| Property             | Requirement level | Notes                       |
| -------------------- | ----------------- | --------------------------- |
| `rdfs:label`         | mandatory         |                             |
| `rdfs:comment`       | mandatory         |                             |
| `rdfs:range`         | recommended       |                             |
| `qb:codelist`        | recommended       | See [codelists](#codelists) |
| `qb:concept`         | recommended       |                             |
| `rdfs:subPropertyOf` | recommended       |                             |

Dimensions must have an associated codelist (see [codelists](#codelists)).

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
| `rdfs:range`         | recommended       |                             |
| `qb:codelist`        | recommended       | See [codelists](#codelists) |
| `qb:concept`         | recommended       |                             |
| `rdfs:subPropertyOf` | recommended       |                             |


We allow attributes to be attached to a list of of values via `qb:codeList`.

### Observation

The dimensions form a composite key for each observation in the cube - meaning the combination of dimensions can be used to uniquely identify each observation in the cube.

We recommend IRIs for observations be of the form:

- `http://{domain}/obs/{dimension_1}-{...}-{dimension_n}`
- `http://{domain}#obs/{dimension_1}-{...}-{dimension_n}`

For example:

- `http://data.gov.uk/dataset/life-expectancy-by-region-sex-and-time/datacube/obs/W06000022-2004-01-01T00:00:00/P3Y-Male`

### Using CSVW to create an RDF data cube

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

Within a single CSVW metadata file we are able to describe a dataset and define two distributions, a CSV distribution and an RDF data cube.

For example, we can represent the relationships between the following resources within a single CSVW metadata file:

- a dataset: `<http://data.gov.uk/dataset/my-dataset>`
- a CSV distribution of that dataset: `<http://data.gov.uk/dataset/my-dataset.csv>`
- an RDF data cube distribution of a dataset: `<http://data.gov.uk/dataset/my-dataset/datacube>`

Our recommended format for a CSVW is as follows. Note the use of virtual columns within the CSVW `columns` definition to assert additional RDF relationships when converting CSV to RDF.

```jsonc
{
    "@context": "http://www.w3.org/ns/csvw",
    "@id": "http://data.gov.uk/dataset/my-dataset.csv",
    "@type": "Table",
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
        "@id": "https://www.w3.org/ns/iana/media-types/text/csv#Resource"
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

We adopt the [measure dimension](https://www.w3.org/TR/vocab-data-cube/#dfn-measure-dimension) approach as, unlike the [multi-measure observations](https://www.w3.org/TR/vocab-data-cube/#dsd-mm-obs) approach, this allows us to specify measure- and observation-specific attributes.

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

## Codelists

> What is the relationship between a `skos:ConceptScheme` and a `dcat:Dataset`? In the way that we propose `qb:DataSet` is a distribution of a `dcat:Dataset`, maybe a `skos:ConceptScheme` is a distribution of a `dcat:Dataset`. Does the advice on editions/versioning also apply to `skos:ConceptScheme`s?

> TODO: Some stuff [here](https://groups.niso.org/higherlogic/ws/public/download/12591/z39-19-2005r2010.pdf) around the styling of labels used in a taxonomy.

> TODO: Some UN best practices for creating classifications [here](https://unstats.un.org/unsd/classifications/bestpractices/Best_practice_Nov_2013.pdf).

Every `qb:DimensionConcept` must have a `skos:ConceptScheme` associated with it which is related using the `qb:codeList` property. The `skos:ConceptScheme` is used to define the list of codes used by the dimension.

All codes which are part of a codelist must have type `skos:Concept` and be related to the codelist using the `skos:inScheme` property.

### Classes

```mermaid
classDiagram
    class Dimension {
        a qb:DimensionProperty
    }
    class Codelist {
        a skos:ConceptScheme
    }
    class Code {
        a skos:Concept
    }

    Dimension --> "1" Codelist : qb.codeList
    Codelist --> "1..*" Code : skos.hasTopConcept
    Code --> "1" Codelist : skos.inScheme
    Code --> "1..*" Code : skos.narrower
    Code "1" <--  Code : skos.broader
```

We recommend the use of `skos:ConceptScheme`, `skos:Concept`.

### Concept Scheme

We recommend dataset series have IRIs of the form:

- `http://{domain}/codelist/{codelist_slug}`
- `http://{domain}/codelist/{codelist_slug}/{edition_year}`

For example:

- `http://data.gov.uk/codelist/some-codelist`
- `http://data.gov.uk/codelist/sitc/2022`

| Property              | Requirement level | Notes                                                                     |
| --------------------- | ----------------- | ------------------------------------------------------------------------- |
| `dcterms:title`       | mandatory         | See [titles](#titles)                                                      |
| `dcterms:description` | mandatory         | See [descriptions](#descriptions)                                          |
| `dcterms:publisher`   | mandatory         | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:license`     | mandatory         | See [licenses](#licenses)                                                  |
| `dcat:distribution`   | mandatory         | See [distributions](#distributions)                                        |
| `dcterms:creator`     | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcat:contactPoint`   | recommended       | See [publishers, creators and contacts](#publishers-creators-and-contacts) |
| `dcterms:issued`      | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcterms:modified`    | recommended       | See [dates and times](#dates-and-times)                                    |
| `dcat:keyword`        | recommended       | See [keywords](#keywords)                                                  |
| `dcat:theme`          | recommended       | See [themes](#themes)                                                      |


### Concept

- `http://{domain}/codelist/{codelist_slug}/code/{code_slug}`

For example:

- `http://data.gov.uk/codelist/some-codelist`
- `http://data.gov.uk/codelist/sitc/rev4`


| Property           | Requirement level | Notes                                                                     |
| ------------------ | ----------------- | ------------------------------------------------------------------------- |
| `skos:inScheme`    | mandatory         | See [codelists](#codelists)                                               |
| `rdfs:label`       | mandatory         | See [titles](#titles)                                                     |
| `skos:prefLabel`   | mandatory         | See [titles](#titles)                                                     |
| `skos:notation`    | mandatory         |                                                                           |
| `skos:broader`     | recommended       | See [hierarchical codelists](#hierarchical-codelists)                     |
| `skos:narrower`    | recommended       | See [hierarchical codelists](#hierarchical-codelists)                     |
| `skos:related`     | recommended       | See [correspondence between codelists](#correspondence-between-codelists) |
| `skos:exactMatch`  | recommended       | See [correspondence between codelists](#correspondence-between-codelists) |
| `skos:closeMatch`  | recommended       | See [correspondence between codelists](#correspondence-between-codelists) |
| `skos:broadMatch`  | recommended       | See [correspondence between codelists](#correspondence-between-codelists) |
| `skos:altLabel`    | optional          |                                                                           |
| `skos:hiddenLabel` | optional          |                                                                           |

### Hierarchical codelists

Hierarchies in codelists must be indicated by using the `skos:broader` and `skos:narrower` predicates.

For example, in a dataset describing types of animals, we can express the relationship:

- _some_ animals are mammals,
- but _all_ mammals are animals

by asserting:

```ttl
<#animals> skos:narrower <#mammals> .
<#mammals> skos:broader <#animals> .
```

This looks diagrammatically as follows:

```mermaid
flowchart TD
    id1[animals] -->|some| id2[mammals]
    id2[mammals] -->|all| id1[animals]
    id3[animals] -->|skos:narrower| id4[mammals]
    id4[mammals] -->|skos:broader| id3[animals]
```

The codes at the top of the hierarchy (and so have no `skos:broader` relationships) must be related to the codelist using the `skos:hasTopConcept` property.

```mermaid
flowchart TD
    Animals[Animals Codelist] -->|skos:hasTopConcept| animals
    animals -->|skos:narrower| mammals
    mammals -->|skos:broader| animals
```

### Extending codelists

Wherever possible, statisticians should aim to reuse codes from common codelists, however, they may wish to combine or alter codes within a codelist for reasons of statistical suppression or quality. In doing so, they create a variant of some official codelist which is customised to suit their needs.

Codelists should be related to their variants using the `xkos:variant` property.

For example, some statistics which make use of the Standard Industrial Classification (SIC) have changed some categories and included the following notations for these codes within their statistical output:

- `11.01-06`
- `20.11 + 20.13`
- `20.14+20.16+20.17+20.6`
- `20.15 /1`
- `20.15 /2`
- `24.4-5 (not 24.42 nor 24.46)`
- `33 (not 33.15-16)`

> TODO: How to express these sorts of semantics using OWL?

Notations like these, while intending to be descriptive, may be consfusing or not be appropriate to be included in an IRI. When extending a codelist with custom codes, we recommend generating new notations which are:

- Similar in style and convention to the codelist which is being extended.
- Do not clash with any current (or future) notations which feature in the codelist.

We may achieve this in several ways:

- Assigning new codes to large unused digits (such as `99`) or unused letters (e.g. `X` or `Z`),
- Combining new or related digits with an unused character (e.g. `33x` or `33.15x`, `X.1`, `X.2` etc.),
- Appending `/1` through `/9` when creating new subdivisions of an already existing code.

When extending an already established codelist, the creator of the new codelist must familiarise themselves with the existing codelist, how it is structured and ensure their extension does not introduce any clashes with existing codes.

| Example                        | Possible notation         | Notes                                                                                                                      |
| ------------------------------ | ------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `11.01-06`                     | `11.0X`, `11.0Z`, `11.9x` | Expresses the sum of`11.01` through to `11.06`, which are subdivisions of `11.0`. `11.07` is occupied by another category. |
| `20.15 /1`                     | `20.15/1`                 | Expresses a custom subdivision of an already existing category,`25.15`.                                                    |
| `20.14+20.16+20.17+20.6`       | `20.X`, `20.Z`, `20.9x`   | Expresses the sum of`20.14`, `20.16` and `20.17`, which are subdivisions of `20.1`, along with `20.6`.                     |
| `24.4-5 (not 24.42 nor 24.46)` | `24.X`, `24.Z`, `24.9x`   | Expresses the sum of`24.4` and `24.5` but excluding the subdivisions `24.42` and `24.46`.                                  |
| `33 (not 33.15-16)`            | `33X`, `33Z`, `33.9x`     | Expresses the sum of`33.1` and `33.2`, which are subdivisons of `33`, excluding `33.15` and `33.16`.                       |
|                                |                           |                                                                                                                            |

### Using CSVW to create a codelist

We can use CSVW as a convenient way to create a codelist, represented in RDF using SKOS.

For example, take the Standard Industrial Trade Classification (SITC):

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

We can create a CSV representation of the different classifications along with the hierarchy as follows:

| notation | label                                                    | comment | parent |
| -------- | -------------------------------------------------------- | ------- | ------ |
| 0        | Food and live animals                                    | ...     |        |
| 00       | Live animals other than animals of division 03           | ...     | 0      |
| 001      | Live animals other than animals of division 03           | ...     | 00     |
| 01       | Meat and meat preparations                               | ...     | 0      |
| 011      | Meat of bovine animals, fresh, chilled or frozen         | ...     | 01     |
| 012      | Other meat and edible meat offal                         | ...     | 01     |
| 016      | Meat, edible meat offal, salted, dried; flours, meals    | ...     | 01     |
| 017      | Meat, edible meat offal, prepared, preserved, n.e.s      | ...     | 01     |
| ...      | ...                                                      | ...     |        |
| 02       | Dairy products and birds' eggs                           | ...     | 0      |
| 022      | Milk, cream and milk products (excluding butter, cheese) | ...     | 02     |
| ...      | ...                                                      | ...     |        |

We are able to create a CSVW file which can be used to create a codelist. Note the use of virtual columns to assert the type and the relationship between the concepts and the concept scheme.

```json
{
    "@context": "http://www.w3.org/ns/csvw",
    "@id": "http://data.gov.uk/codelist/standard-international-trade-classification/revision-4.csv",
    "@type": "Table",
    "url": "http://data.gov.uk/codelist/standard-international-trade-classification/revision-4.csv",
    "tableSchema": {
        "columns": [
            {
                "titles": "notation",
                "name": "notation",
                "required": true,
                "propertyUrl": "skos:notation"
            },
            {
                "titles": "label",
                "name": "label",
                "required": true,
                "propertyUrl": "rdfs:label"
            },
            {
                "titles": "comment",
                "name": "comment",
                "required": false,
                "propertyUrl": "rdfs:comment"
            },
            {
                "titles": "parent_notation",
                "name": "parent_notation",
                "required": false,
                "propertyUrl": "skos:broader",
                "valueUrl": "http://data.gov.uk/codelist/standard-international-trade-classification/revision-4/{+parent_notation}"
            },
            {
                "virtual": true,
                "propertyUrl": "skos:inScheme",
                "valueUrl": "http://data.gov.uk/codelist/standard-international-trade-classification/revision-4"
            },
            {
                "virtual": true,
                "propertyUrl": "rdf:type",
                "valueUrl": "skos:Concept"
            }
        ],
        "aboutUrl": "http://data.gov.uk/codelist/standard-international-trade-classification/revision-4/{+notation}"
    }
}
```

Performing `csv2rdf` on this CSVW produces RDF like:

```ttl
<http://data.gov.uk/codelist/standard-international-trade-classification/revision-4/0> a skos:Concept ;
    skos:notation "0" ;
    rdfs:label "Food and live animals" ;
    rdfs:comment "..." ;
    skos:inScheme <http://data.gov.uk/codelist/standard-international-trade-classification/revision-4> ;
    .

<http://data.gov.uk/codelist/standard-international-trade-classification/revision-4/00> a skos:Concept ;
    skos:notation "00" ;
    rdfs:label "Live animals other than animals of division 03" ;
    rdfs:comment "..." ;
    skos:broader <http://data.gov.uk/codelist/standard-international-trade-classification/revision-4/0> ;
    skos:inScheme <http://data.gov.uk/codelist/standard-international-trade-classification/revision-4> ;
    .

# etc...
```

A limitation of using CSVW to produce a `skos:ConceptScheme` is the inability to set both `skos:narrower` and `skos:broader` relationships concurrently, and to set the `skos:hasTopConcept` relationship. When loading a `skos:ConceptScheme` generated from CSVW in this way, we serialise these additional relationships using `CONSTRUCT` queries in SPARQL.

The following SPARQL query produces `skos:narrower` relationships:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

CONSTRUCT {
    ?broaderConcept skos:narrower ?concept.
}
WHERE {
    ?conceptScheme a skos:ConceptScheme .
    ?concept 
        skos:inScheme ?conceptScheme;
        skos:broader ?broaderConcept.
        FILTER NOT EXISTS {
            ?broaderConcept skos:narrower ?concept.
        }
}
```

The following SPARQL query produces `skos:hasTopConcept` relationships:

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

CONSTRUCT {
    ?conceptScheme skos:hasTopConcept ?concept.
}
WHERE {
    ?conceptScheme a skos:ConceptScheme .
    ?concept skos:inScheme ?conceptScheme.
        FILTER NOT EXISTS {
            # Find concepts which don't have anything broader, they are by definition topConcepts.
            ?concept skos:broader ?broaderConcept.
        }
        FILTER NOT EXISTS {
            # Ensure we don't add topConcept where it is already set.
            ?conceptScheme skos:hasTopConcept ?concept.
        }
}
```

#### Mixing codes from different namespaces

Statisticians may wish to report statistics against multiple classifications. Doing so may be difficult, as different classifications typically use different namespaces for their IRIs.

For example, consider a dataset which mixes codes from the NUTS geography codelist with codes from the ONS geography codelist.

| geography | geography_label     | value |
| --------- | ------------------- | ----- |
| UKC       | North East, England | ...   |
| UKD       | North West, England | ...   |
| E92000001 | England             | ...   |

The NUTS codes have IRIs which are maintained by Eurostat, such as `http://data.europa.eu/nuts/code/UKC`, whereas the ONS geography codes are maintained by the ONS at the `http://statistics.data.gov.uk/id/statistical-geography/E92000001` namespace.

We map the cells of the dataset to RDF by using the `valueUrl` CSVW property. Only a single `valueUrl` can be applied to all the cells in a column. This is problematic, as the IRIs we wish to map to have different bases. Setting `valueUrl` to `http://data.europa.eu/nuts/code/{geography}` would result in a non-existant identifier `http://data.europa.eu/nuts/code/E92000001` appearing in the RDF output.

We address this by creating new identifiers for each of the codes under a shared namespace, and using `owl:sameAs` relations to relate these new identifiers to the more commonly used identifiers. For example, 

```ttl
<http://data.gov.uk/dataset/some-dataset/codelist/geography/code/E92000001>
    owl:sameAs <http://statistics.data.gov.uk/id/statistical-geography/E92000001> ;
    .
```

> TODO: Should this be `owl:sameAs` or `skos:exactMatch`?

If [using a CSVW to create a codelist](#using-csvw-to-create-a-codelist), then the `owl:sameAs` relationships can be expressed by adding an additional column to the CSV:

| notation  | label               | same_as                                                            |     |
| --------- | ------------------- | ------------------------------------------------------------------ | --- |
| UKC       | North East, England | `http://data.europa.eu/nuts/code/UKC`                              | ... |
| UKD       | North West, England | `http://data.europa.eu/nuts/code/UKD`                              | ... |
| E92000001 | England             | `http://statistics.data.gov.uk/id/statistical-geography/E92000001` | ... |

The additional column would have the following specification inside the CSVW:

```json
{
    "titles": "same_as",
    "name": "same_as",
    "required": true,
    "propertyUrl": "owl:sameAs",
    "valueUrl": "{+same_as}"
}
```

This would result in the following RDF:

```ttl
<http://data.gov.uk/dataset/some-dataset/codelist/geography/code/UKC> a skos:Concept ;
    skos:notation "UKC" ;
    rdfs:label "North East, England" ;
    skos:prefLabel "North East, England" ;
    skos:inScheme <http://data.gov.uk/dataset/some-dataset/codelist/geography> ;
    owl:sameAs <http://data.europa.eu/nuts/code/UKC> ;
    .

# ...

<http://data.gov.uk/dataset/some-dataset/codelist/geography/code/E92000001> a skos:Concept ;
    skos:notation "E92000001" ;
    rdfs:label "England" ;
    skos:prefLabel "England" ;
    skos:inScheme <http://data.gov.uk/dataset/some-dataset/codelist/geography> ;
    owl:sameAs <http://statistics.data.gov.uk/id/statistical-geography/E92000001> ;
    .
```

### Correspondence between codelists

> TODO: https://rdf-vocabulary.ddialliance.org/xkos.html

For example, the Combined Nonclementure (CN8) is a classification of commodities of trade. These get updated in legislation each year.

HMRC publishes each annual edition of CN8 and [provides correspondence tables](https://www.trade-tariff.service.gov.uk/help/cn2021_cn2022) between the different year's editions.

| 2021 code  | 2022 code  |
| ---------- | ---------- |
| 0208 90 98 | 0208 90 98 |
| 0208 90 98 | 0410 10 10 |
| 0210 99 39 | 0210 99 39 |
| 0210 99 39 | 0410 10 99 |
| 0210 99 90 | 0210 99 90 |
| 0210 99 90 | 0410 10 91 |

```
<> a xkos:Correspondence ;
    xkos:compares 
        <http://data.gov.uk/codelist/combined-nonclementure/2022>,
        <http://data.gov.uk/codelist/combined-nonclementure/2021> ;
    xkos:madeOf <> ;
    .

<> a xkos:ConceptAssociation ;
    xkos:sourceConcept <http://data.gov.uk/codelist/combined-nonclementure/02089098> ;
    xkos:targetConcept 
        <http://data.gov.uk/codelist/combined-nonclementure/02089098> ,
        <http://data.gov.uk/codelist/combined-nonclementure/04101010> ;
    .
```

https://www.uktradeinfo.com/find-commodity-data/help-with-classifying-goods/

## Provenance

> TODO: http://www.w3.org/TR/prov-o/

### Datasets derived from other datasets

## Data quality

> TODO: http://www.w3.org/TR/vocab-dqv/

## Data usage

> TODO: http://www.w3.org/TR/vocab-duv/

## Data privacy

> TODO: http://dpvcg.github.io/dpv/

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

> TODO

Prefer using `xsd:date` and `xsd:dateTime` to describe `dcterms:issued` and `dcterms:modified`, for example:

```
<http://data.gov.uk/dataset/my-dataset> dcterms:issued "2018-01-01"^^xsd:date .
```

Prefer using IRIs from the `http://reference.data.gov.uk` vocabulary to describe dates and times within datasets (for example a time dimension). The IRI scheme is described [here](https://github.com/epimorphics/IntervalServer/blob/master/interval-IRIs.md).

#### Frequency

Prefer using IRIs from the [Dublin core collection description frequency vocabulary](https://www.dublincore.org/specifications/dublin-core/collection-description/frequency/), `http://purl.org/cld/freq/`.

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

For example: `http://www.gov.uk/government/organisations/office-for-national-statistics`.

#### Statistics designations

> TODO: IRIs for official/national/experimental stats classifications.

| Label                   | IRI                                          |
| ----------------------- | -------------------------------------------- |
| National Statistics     | `http://data.gov.uk/national-statistics`     |
| Official Statistics     | `http://data.gov.uk/official-statistics`     |
| Experimental Statistics | `http://data.gov.uk/experimental-statistics` |

#### Symbols and shorthand in tables

> TODO: [Recently updated guidance exists](https://analysisfunction.civilservice.gov.uk/policy-store/symbols-in-tables-definitions-and-help/). We may need to update our markers codelist.

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

> TODO: OSR have [domains](https://osr.statisticsauthority.gov.uk/what-we-do/our-domains/). Might be similar to the statistics authority themes.

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
| CSV    | `https://www.w3.org/ns/iana/media-types/text/csv#Resource`         |
| JSON   | `https://www.w3.org/ns/iana/media-types/application/json#Resource` |
| Turtle | `https://www.w3.org/ns/iana/media-types/text/turtle#Resource`      |

### Style

#### Titles

> TODO: Do we want to recommend a house style for titles?
>
> ONS style guide suggests:
>
> Titles appear in search results and should:
>
> - accurately describe the statistics, using plain English
> - include the geographical area and period covered by the content
> - be unique
> - use sentence case as this is easier to read, for example: “The quick brown fox"
>
> GOV.UK: https://www.gov.uk/guidance/content-design/writing-for-gov-uk#titles

#### Descriptions

> TODO: Do we want to recommend a house style for descriptions?
>
> ONS style guide suggests:
>
> The metadata description is the summary of the release content. It is mainly used for search purposes and should be searchable. This can make up the text that appears in search results. Users should be able to immediately understand what the link contains.
>
> The description should:
>
> - be an accurate, concise and clear description of the content
> - be “frontloaded”, with a summary of the content at the start of the description
> - not start with phrases such as “This page provides…”
> - have a unique description that is specific to the content, which does not repeat the title
> - be no more than 160 characters including spaces (search engines ignore any text over this)
>
> GOV.UK: https://www.gov.uk/guidance/content-design/writing-for-gov-uk#summaries

#### Keywords

> TODO: Advice for keywords

#### Welsh language

> TODO: Language string example for Welsh

### Hash or slash IRIs

### `rdfs` vs `dcterms`

> TODO: When do we use `rdfs:label`, `rdfs:comment` vs. `dcterms:title`, `dcterms:description`?
>
> - Do we always specify both?
> - Should `rdfs:label == dcterms:title`?
>
> Some discussion [here](https://jazz.net/wiki/bin/view/LinkedData/UseOfRdfsLabelVersusDctermsTitle).
>
> `rdfs` offers `rdfs:label` and `rdfs:comment`.
>
> `DCTERMS` offers `dcterms:title` and `dcterms:description`.
>
> Above link suggests vocabularies to use `rdfs`, so `skos:Concept`, `qb:ComponentProperty` resources should use `rdfs`.
>
> Document-like resources to use `dcterms`. So `dcat:Dataset`, `dcat:Catalog`, `dcat:Distribution` etc. should use `dcterms`.

### Publishers, creators and contacts

> TODO: Should publisher/creator be an organisation or a person? Maybe the object of `dcat:publisher` and `dcat:creator` is an organisation, but `dcat:contactPoint` is a person.
>
> TODO: Should we use `vcard`?
>
> ```ttl
> <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018> dcat:contactPoint <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/contact> .
>
> <http://data.gov.uk/series/name-of-my-statistical-series/dataset/2018/contact> a vcard:Individual ;
>     vcard:hasEmail <mailto:joe.bloggs@ons.gov.uk> ;
>     vcard:hasTelephone <tel:+441234123456> ;
>     vcard:fn "Joe Bloggs" ;
>     .
> ```

[^machine]: https://w3c.github.io/dwbp/bp.html#machine_readable
    
[^named-graphs]: https://www.w3.org/TR/vocab-dcat-3/#Class:Catalog_Record

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
        a skos:ConceptScheme
    }
    class Code {
        a skos:Concept
    }

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
```
