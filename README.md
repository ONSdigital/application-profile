# Application Profile

_Working draft._

The key words must, must not, required, shall, shall not, should, should not, recommended, may, and optional are to be interpreted as described in RFC 2119.

## Table of Contents

- [Application Profile](#application-profile)
  - [Table of Contents](#table-of-contents)
  - [Preamble](#preamble)
    - [Data on the Web Best Practises](#data-on-the-web-best-practises)
    - [Five star data](#five-star-data)
    - [FAIR principles](#fair-principles)
  - [Specifications used](#specifications-used)
  - [Data structure](#data-structure)
    - [Tidy Data dependencies](#tidy-data-dependencies)
    - [Using JSON-LD to describe statistical data](#using-json-ld-to-describe-statistical-data)
      - [Standards divergence from CSVW](#standards-divergence-from-csvw)
  - [Our statistical Object Model Diagram](#our-statistical-object-model-diagram)
    - [Our API endpoints](#our-api-endpoints)
    - [Design decisions on object model](#design-decisions-on-object-model)
    - [Draft JSON-LD Context](#draft-json-ld-context)
    - [HTTP verbs and their applicability to our objects](#http-verbs-and-their-applicability-to-our-objects)
    - [Datasets](#datasets)
      - [GET of a CPIH Dataset](#get-of-a-cpih-dataset)
      - [POST of a CPIH dataset](#post-of-a-cpih-dataset)
    - [Editions](#editions)
      - [Statistics quality designations](#statistics-quality-designations)
    - [Versions](#versions)
    - [Distributions](#distributions)
      - [CSV-W Distributions](#csv-w-distributions)
  - [Versioning](#versioning)
    - [Example of versioning in RDF for CPIH](#example-of-versioning-in-rdf-for-cpih)

## Preamble

The UK government often [publishes its statistics](https://www.gov.uk/search/research-and-statistics?content_store_document_type=statistics_published&order=updated-newest) in presentational spreadsheets. While this succeeds in getting important information into the public domain, we recognise there are still barriers and challenges in accessing and using the data we produce:

- Analysts need to wrangle data because data are in unstandardised and presentational formats.
- A user must locate and navigate through many large spreadsheets to understand what data are available.
- Metadata are provided in an unstructured or unstandardised ways.
- Data are in silos, making it difficult to link or relate statistics from different sources.
- The accessibility and usability of statistics varies from dataset to dataset.

We have explored how to follow best practices when publishing statistics, in particular through the use of the JSON-LD (JSON Linked Data), CSV on the Web (CSVW), Data Catalog (DCAT) and RDF Data Cube (QB) standards and vocabularies. This document is an application profile of these standards, describing a recommendation on how to use these standards together in order to achieve the data on the web best practices, 5-star data, and the FAIR data principles.

### Data on the Web Best Practises

The [Data on the Web Best Practices (DWBP)](https://www.w3.org/TR/dwbp/) describes recommendations for publishing data to the web. If followed, we can enable these benefits:

> - **Comprehension**: humans will have a better understanding about the data structure, the data meaning, the metadata and the nature of the dataset.
> - **Processability**: machines will be able to automatically process and manipulate the data within a dataset.
> - **Discoverability**: machines will be able to automatically discover a dataset or data within a dataset.
> - **Reuse**: the chances of dataset reuse by different groups of data consumers will increase.
> - **Trust**: the confidence that consumers have in the dataset will improve.
> - **Linkability**: it will be possible to create links between data resources (datasets and data items).
> - **Access**: humans and machines will be able to access up to date data in a variety of forms.
> - **Interoperability**: it will be easier to reach consensus among data publishers and consumers.

### Five star data

5★ Open Data has a five point scale which describes data on the web which increases the utility of said data for each increase from one to five stars.

| Stars | Requirements                                                                                         |
| :---: | :--------------------------------------------------------------------------------------------------- |
| ★☆☆☆☆ | data needs to be able to be published on the web,                                                    |
| ★★☆☆☆ | data needs to be machine-readable,                                                                   |
| ★★★☆☆ | data needs to be non-proprietary,                                                                    |
| ★★★★☆ | identifiers need to be used to denote things, so that people can talk about resources unambiguously, |
| ★★★★★ | data needs to able to be linked to other data to provide context.                                   |

### FAIR principles

To aid humans who increasingly rely on computational support to deal with increased volumes of data, complexity, and creation speed of data, the [FAIR principles](https://www.go-fair.org/fair-principles/) were conceived.

The FAIR principles describe data which is:

> - **Findable**: data and metadata encoded for machines and humans
> - **Accessible**: using standard protocols for access and authentication of data
> - **Interoperable**: data and metadata is represented in an appropriate knowledge representation standard
> - **Reusable**: using common vocabularies for knowledge representation allows for reuse and remixing of data

## Specifications used

The Application Profile uses terms from various existing specifications. Classes and properties specified in the following sections come from the following namespaces.

| Namespace | Namespace IRI                                 | Specification name                                                                   |
| --------- | --------------------------------------------- | ------------------------------------------------------------------------------------ |
| `adms`    | `http://www.w3.org/ns/adms#`                  | Asset Description Metadata Schema                                                    |
| `dcat`    | `http://www.w3.org/ns/dcat#`                  | Data Catalog Vocabulary                                                              |
| `dcterms` | `http://purl.org/dc/terms/`                   | DCMI (Dublin Core Metadata Initiative) Metadata Terms                                |
| `dqv`     | `https://www.w3.org/TR/vocab-dqv/`            | Data Quality Vocabulary                                                              |
| `foaf`    | `http://xmlns.com/foaf/0.1/`                  | FOAF (Friend of a friend) Vocabulary                                                 |
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

### Tidy Data dependencies

Our standards and vocabularies are based on the [Tidy Data](https://vita.had.co.nz/papers/tidy-data.pdf) principles. Tidy Data is a framework for structuring data to make analysis easier. The principles are:

> - Each variable (i.e. dimension) has its own column.
> - Each observation forms a row.
> - Each type of observation has a unit and a measure.
> - Each unit is based off QUDT units.
> - Each measure is based off QUDT measures.
> - Missing observations must be marked as missing using attributes.
> - Attributes provide additional metadata about the observation.
> - For every combination of dimensions and measure there is a single observation.

### Using JSON-LD to describe statistical data

We use JSON-LD to encode the metadata about statistical publications; metadata includes data which helps discovery, and provides guarantees on strucutre. JSON-LD is a standard for encoding linked data in JSON. JSON-LD is a subset of JSON, so any valid JSON-LD is also valid JSON. This makes using our JSON-LD representation of statistical data easy to use in any JSON application but better in ours.

#### Standards divergence from CSVW

In order to gain the benefits of JSON-LD being directly consumable as RDF, we add the CSVW context which is a violation of the CSVW specification. CSVW specfically states that the only acceptable context of a CSVW document is the CSVW context, whereas we use the CSVW namespace in conjunction with other namespaces within our own contexts. This allows us to link our metadata about statistical publications with tabular data and its structure using familiar terms from the CSV on the Web standard.

(Note: We know the drama between JSON-LD and CSVW was a bit of a mess when both were being developed, but we think the benefits of using JSON-LD outweigh the drawbacks of violating the CSVW specification.)

## Our statistical Object Model Diagram

```mermaid
classDiagram
Distribution <|-- DatasetVersion : dcat.distribution 
DatasetVersion <|-- Edition : dcat.hasVersion
Edition --|> DatasetSeries : dcat.inSeries 
CatalogRecord --|> DatasetSeries : foaf.primaryTopic
Catalog --|> CatalogRecord : dcat.record
Edition --|> VcardKind : dcat.contactPoint
Edition --|> PeriodOfTime : dcterms.temporal
TableSchema <|-- Distribution : csvw.tableSchema
Column <|-- TableSchema : csvw.column

class Catalog["Catalog a dcat:Catalog"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcat:record ∋ [dcat:CatalogRecord]
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
}

class CatalogRecord["Record a dcat:CatalogRecord"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +foaf:primaryTopic ∋ dcat:DatasetSeries
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
}

class TableSchema["TableSchema a csvw:TableSchema"] {
    +csvw:column ∋ csvw:Column
    +csvw:aboutUrl ∋ rdfs:Literal as xsd:anyURI
}

class Column["Column a csvw:Column"] {
    +csvw:name ∋ rdfs:Literal as xsd:string
    +csvw:title ∋ rdfs:Literal as xsd:string
    +rdfs:label ∋ rdfs:Literal as xsd:string
    +csvw:datatype ∋ xsd:Datatype
    +csvqb:columntype ∋ csvqb:ColumnType
    +dcterms:description ∋ rdfs:Literal as xsd:string
    +csvw:propertyUrl ∋ rdfs:Literal as xsd:anyURI
    +csvw:valueUrl ∋ rdfs:Literal as xsd:anyURI
    +csvw:aboutUrl ∋ rdfs:Literal as xsd:anyURI
}

class Edition["Edition a dcat:Dataset"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcterms:title, rdfs:label ∋ rdfs:Literal as xsd:string
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
    +dcterms:creator ∋ foaf:Agent
    +dcat:contactPoint ∋ vcard:Kind
    +dcterms:abstract ∋ rdfs:Literal as xsd:string
    +dcterms:description ∋ rdfs:Literal as xsd:string/markdown
    +adms:status ∋ skos:Concept
    +dcat:inSeries ∋ dcat:DatasetSeries
    +dqv:hasQualityQualityAnnotation ∋ dqv:QualityAnnotation
    -dcat:hasVersion ∋ dcat:Dataset
    -dcterms:modified ∋ rdfs:Literal as xsd:dateTime
    -dcterms:issued ∋ rdfs:Literal as xsd:dateTime
    -dcterms:spatial ∋ dcterms:Location
    -ons:spatialResolution ∋ [skos:Concept]
    -dcterms:temporal ∋ dcterms:PeriodOfTime
    -dcat:temporalResolution ∋ [rdfs:Literal as xsd:duration]
    -dcat:prev ∋ dcat:Dataset
    -dcat:next ∋ dcat:Dataset
    -calculateTemporalResolution()
    -calculateSpatialResolution()
    -calculateTemporalCoverage() 
    -calculateSpaitialCoverage()   
}

class VcardKind["VcardKind a vcard:Kind"] {
    +vcard:hasEmail ∋ vcard:Email
    +vcard:fn ∋ rdfs:Literal as xsd:string
    +vcard:hasTelephone ∋ vcard:Telephone
}

class PeriodOfTime["PeriodOfTime a dcterms:PeriodOfTime"] {
    +dcat:startDate ∋ rdfs:Literal as xsd:dateTime
    +dcat:endDate ∋ rdfs:Literal as xsd:dateTime
}

class Distribution["Distribution a dcat:Distribution"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
    +dcterms:creator ∋ foaf:Agent
    +dcterms:issued ∋ rdfs:Literal as xsd:dateTime
    +prov:wasDerivedFrom ∋ [prov:Entity]
    +prov:wasGeneratedBy ∋ prov:Activity
    +dcat:downloadURL ∋ rdf:Resource
    +dcat:byteSize ∋ rdfs:Literal as xsd:nonNegativeInteger
    +dcat:mediaType ∋ dcterms:MediaType
    +wdrs:describedBy ∋ rdfs:Resource
    +spdx:checksum ∋ spdx:Checksum
}

class DatasetVersion["DatasetVersion a dcat:Dataset"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcat:version ∋ rdfs:Literal as xsd:string
    +adms:versionNotes ∋ rdfs:Literal as xsd:string
    -dcterms:created ∋ rdfs:Literal as xsd:dateTime
    -dcterms:issued ∋ rdfs:Literal as xsd:dateTime
    -dcat:previousVersion ∋ dcat:Dataset
    -dcat:nextVersion ∋ dcat:Dataset
}

class DatasetSeries["DatasetSeries a dcat:DatasetSeries"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcterms:title, rdfs:label ∋ rdfs:Literal as xsd:string
    +ons:nextRelease ∋ rdfs:Literal as xsd:dateTime
    +dcterms:abstract ∋ rdfs:Literal as xsd:string
    +dcterms:description ∋ rdfs:Literal as xsd:string/markdown
    +dcat:landingPage ∋ foaf:Document
    +dcat:publisher ∋ foaf:Agent
    +dcterms:modified ∋ rdfs:Literal as xsd:dateTime
    +dcterms:creator ∋ foaf:Agent
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
    +dcterms:issued ∋ rdfs:Literal as xsd:dateTime
    +dcterms:accuralPeriodicity ∋ dcterms:Frequency
    +dcat:keyword ∋ [rdfs:Literal as xsd:string]
    +dcat:theme ∋ [skos:Concept]
    +dcterms:license ∋ dcterms:LicenseDocument
    +dcterms:spatial ∋ dcterms:Location
    +ons:spatialResolution ∋ [skos:Concept]
    +dcterms:temporal ∋ dcterms:PeriodOfTime
    +dcat:temporalResolution ∋ [rdfs:Literal as xsd:duration]
    -dcat:first ∋ dcat:Dataset
    -dcat:last ∋ dcat:Dataset
}

```

We are heavily reliant on dcat and dcterms to relate our statistical datasets, editions and versions together. In brief:

- We call our statistical publication series _Datasets_, although they are actually `dcat:DatasetSeries`.
- We call releases within these Datasets _Editions_, and they are dcat:inSeries of the `dcat:DatasetSeries` and are of type dcat:Dataset.
- We call all versions within these Editions _Versions_, and they are the object of the Editions' `dcat:hasVersion` property and are of type `dcat:Dataset`.
- Versions of data are provided as a _Distribution_, which is a `dcat:Distribution`, and can be of varying types, such as CSV, JSON, RDF, etc; however we are targetting JSON-LD with a CSVW context representing a qb:DataSet.

### Our API endpoints

Our primary objective is to establish a URL framework that caters to both user-friendly web browsing and efficient data retrieval, for example in Python using `pandas.read_csv(url)`. The link should provide users with a comprehensive webpage if visited in a browser, but when consumed using pandas it would provide a csv file - this approach is known as [content negotiation](https://www.w3.org/TR/dwbp/#Conneg).

### Design decisions on object model

Our API will use pluralised nouns to represent collections of objects and the individual objects as well. For example, the following URLs may be used to access the CPIH dataset:

> `https://data.ons.gov.uk/datasets/cpih`

- In a browser, this URL will return a webpage with the latest information about the CPIH dataset, a summary of its structure, a preview of the data, and links to download the data in open formats.
- When used programmatically along with an accept header, this URL will return the latest data in the requested format but defaulting to machine readable CSV.

> `https://data.ons.gov.uk/datasets/cpih/editions/2019-03`

- In a browser, this URL will redirect to the primary CPIH webpage.
- When used programmatically along with an accept header, this URL will return the data for the most recent version of the March 2019 dataset in the requested format but defaulting to machine readable CSV.

> `https://data.ons.gov.uk/datasets/cpih/editions/2019-03/versions/2`

- In a browser, this URL will redirect to the primary CPIH webpage.
- When used programmatically along with an accept header, this URL will return the data for the second version of the March 2019 dataset in the requested format but defaulting to machine readable CSV.

### Draft JSON-LD Context

We are building a series of JSON-LD contexts to support the publication of our statistical data. The draft context is currently [here](./worked-examples/cpih/draft_onsns_context.json), and we will be improving the context and ensuring conformation to the object model as described earlier.

### HTTP verbs and their applicability to our objects

We use the standard HTTP verbs to interact with our objects. Not all verbs are applicable to all objects, nor are all accessible publicly. We are still working out the business logic of mandatory and optional fields, and how to curate the namespace available to the ID of objects.

Additionally, the POST and PUT verbs are not required to define the `@type` of the object as this is predefined by the predicate's range. The GET verb is used to retrieve the objects, and here the reponses will be in JSON-LD format and will include the `@context` and `@type` of the object.

### Datasets

Datasets are the primary object, and are in fact [dcat:DatasetSeries](https://www.w3.org/TR/vocab-dcat-3/#Class:Dataset_Series). They are the parent object of Editions, and are the object of the CatalogRecord. They are typically a recurring publication, such as the Consumer Price Inflation including owner occupiers' housing costs (CPIH) dataset.

| Keyword             | Predicate                  | Range                               | POST/PUT |  GET  | GET {ID} | DELETE |
| ------------------- | -------------------------- | ----------------------------------- | :------: | :---: | :------: | :----: |
| @id                 | dcterms:identifier         | rdfs:Literal as xsd:string          |    ✓     |   ✓   |    ✓     |   ✓    |
| publisher           | dcat:publisher             | foaf:Agent                          |    ✓     |   ✓   |    ✓     |        |
| created             | dcterms:created            | rdfs:Literal as xsd:dateTime        |    ✓     |   ✓   |    ✓     |        |
| creator             | dcterms:creator            | foaf:Agent                          |    ✓     |       |    ✓     |        |
| issued              | dcterms:issued             | rdfs:Literal as xsd:dateTime        |    ✓     |   ✓   |    ✓     |        |
| modified            | dcterms:modified           | rdfs:Literal as xsd:dateTime        |    ✓     |   ✓   |    ✓     |        |
| title               | dcterms:title / rdfs:label | rdfs:Literal as xsd:string          |    ✓     |   ✓   |    ✓     |        |
| keywords            | dcat:keyword               | [rdfs:Literal as xsd:string]        |    ✓     |       |    ✓     |        |
| theme               | dcat:theme                 | [skos:Concept]                      |    ✓     |       |    ✓     |        |
| summary             | dcterms:abstract           | rdfs:Literal as xsd:string          |    ✓     |   ✓   |    ✓     |        |
| frequency           | dcterms:accuralPeriodicity | dcterms:Frequency                   |    ✓     |   ✓   |    ✓     |        |
| description         | dcterms:description        | rdfs:Literal as xsd:string/markdown |    ✓     |       |    ✓     |        |
| license             | dcterms:license            | dcterms:LicenseDocument             |    ✓     |   ✓   |    ✓     |        |
| temporal_resolution | dcat:temporalResolution    | [rdfs:Literal as xsd:duration]      |    ✓     |   ✓   |    ✓     |        |
| temporal_coverage   | dcterms:temporal           | dcterms:PeriodOfTime                |    ✓     |   ✓   |    ✓     |        |
| spatial_resolution  | ons:spatialResolution      | [skos:Concept]                      |    ✓     |   ✓   |    ✓     |        |
| spatial_coverage    | dcterms:spatial            | dcterms:Location                    |    ✓     |   ✓   |    ✓     |        |
| status              | adms:status                | skos:Concept                        |    ✓     |   ✓   |    ✓     |        |
| editions            | dcat:hasVersion            | [dcat:Dataset as ons:Edition]       |          |       |    ✓     |        |
| first_release       | dcat:first                 | dcat:Dataset as ons:Edition         |          |       |    ✓     |        |
| latest_release      | dcat:last                  | dcat:Dataset as ons:Edition         |          |       |    ✓     |        |
| next_release        | ons:nextRelease            | rdfs:Literal as xsd:dateTime        |    ✓     |   ✓   |    ✓     |        |
| landing_page        | dcat:landingPage           | foaf:Document                       |    ✓     |       |    ✓     |        |

#### GET of a CPIH Dataset

```JSON
{
  "@context": "https://data.ons.gov.uk/ns#",
  "@id": "https://data.ons.gov.uk/datasets/cpih",
  "@type": "dcat:DatasetSeries",
  "identifier": "cpih",
  "title": "Consumer Price Inflation including owner occupiers' housing costs (CPIH)",
  "summary": "The Consumer Prices Index including owner occupiers' housing costs (CPIH) is a measure of inflation which includes the costs associated with owning, maintaining and living in one's own home.",
  "description": "The Consumer Prices Index including owner occupiers' housing costs (CPIH) is a measure of inflation which includes the costs associated with owning, maintaining and living in one's own home. The CPIH is the most comprehensive measure of inflation.",
  "issued": "2023-06-21T00:07:00+00:00",
  "next_release": "2023-09-20T00:07:00+00:00",
  "publisher": "office-for-national-statistics",
  "creator": "office-for-national-statistics",
  "contact_point": {
    "name": "Consumer Price Inflation Enquiries",
    "email": "cpi@ons.gov.uk"
  },
  "theme": [
    "prices",
    "economy"
  ],
  "frequency": "monthly",
  "keywords": [
    "cpih",
    "inflation",
    "consumer price index",
    "consumer price inflation",
    "cpi",
    "consumer price index including owner occupiers' housing costs"
  ],
  "licence": "http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/",
  "spatial_coverage": "K02000001",
  "temporal_coverage": {
    "start": "1989-01-01T00:00:00+00:00",
    "end": "2023-08-01T00:00:00+00:00"
  },
  "temporal_resolution": "P1M",
  "editions": [
    {
      "@id": "https://data.ons.gov.uk/dataset/cpih/2023-09",
      "issued": "2023-09-21T00:07:00+00:00",
      "modified": "2023-09-21T00:07:00+00:00"
    },
    {
      "@id": "https://data.ons.gov.uk/dataset/cpih/2023-08",
      "issued": "2023-08-21T00:07:00+00:00",
      "modified": "2023-08-21T00:07:00+00:00"
    },
    {
      "@id": "https://data.ons.gov.uk/dataset/cpih/2023-07",
      "issued": "2023-07-21T00:07:00+00:00",
      "modified": "2023-07-21T00:07:00+00:00"
    }
  ]
}
```

#### POST of a CPIH dataset

```JSON
{
  "@context": "./draft_onsns_context.json",
  "@id": "https://data.ons.gov.uk/datasets/cpih",
  "@type": "dcat:DatasetSeries",
  "identifier": "cpih",
  "title": "Consumer Price Inflation including owner occupiers' housing costs (CPIH)",
  "summary": "The Consumer Prices Index including owner occupiers' housing costs (CPIH) is a measure of inflation which includes the costs associated with owning, maintaining and living in one's own home.",
  "description": "The Consumer Prices Index including owner occupiers' housing costs (CPIH) is a measure of inflation which includes the costs associated with owning, maintaining and living in one's own home. The CPIH is the most comprehensive measure of inflation.",
  "landing_page": "https://www.ons.gov.uk/economy/inflationandpriceindices/bulletins/consumerpriceinflation/latest",
  "created": "2023-06-19T00:09:38+00:00",
  "issued": "2023-06-21T00:07:00+00:00",
  "next_release": "2023-09-20T00:07:00+00:00",
  "publisher": "office-for-national-statistics",
  "creator": "office-for-national-statistics",
  "contact_point": {
    "name": "Consumer Price Inflation Enquiries",
    "email": "cpi@ons.gov.uk",
    "telephone": "+441633456900"
  },
  "theme": [
    "prices",
    "economy"
  ],
  "frequency": "Month",
  "keywords": [
    "cpih",
    "inflation",
    "consumer price index",
    "consumer price inflation",
    "cpi",
    "consumer price index including owner occupiers' housing costs"
  ],
  "licence": "http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/",
  "temporal_coverage": {
    "start": "1989-01-01T00:00:00+00:00",
    "end": "2023-08-01T00:00:00+00:00"
  },
  "temporal_resolution": "P1M",
  "spatial_coverage": "K02000001",
  "spatial_resolution": ["K02"]
}
```

### Editions

Editions are the child object of Datasets, using our own `ons:Edition` object class which is a child of `dcat:Dataset`. They are the parent object of `ons:Version`s.

| Keyword             | Predicate                  | Range                               | POST/PUT | GET | GET {ID} | DELETE |
|---------------------|----------------------------|-------------------------------------|:--------:|:---:|:--------:|:------:|
| @id                 | dcterms:identifier         | rdfs:Literal as xsd:string          |     ✓    |  ✓  |     ✓    |    ✓   |
| pulisher            | dcat:publisher             | foaf:Agent                          |     ✓    |  ✓  |     ✓    |        |
| created             | dcterms:created            | rdfs:Literal as xsd:dateTime        |     ✓    |  ✓  |     ✓    |        |
| creator             | dcterms:creator            | foaf:Agent                          |     ✓    |     |     ✓    |        |
| issued              | dcterms:issued             | rdfs:Literal as xsd:dateTime        |     ✓    |  ✓  |     ✓    |        |
| modified            | dcterms:modified           | rdfs:Literal as xsd:dateTime        |     ✓    |  ✓  |     ✓    |        |
| title               | dcterms:title / rdfs:label | rdfs:Literal as xsd:string          |     ✓    |  ✓  |     ✓    |        |
| quality             | dqv:hasQualityAnnotation   | dqv:QualityAnnotation as blank node |     ✓    |  ✓  |     ✓    |        |
| keywords            | dcat:keyword               | [rdfs:Literal as xsd:string]        |     ✓    |     |     ✓    |        |
| theme               | dcat:theme                 | [skos:Concept]                      |     ✓    |     |     ✓    |        |
| summary             | dcterms:abstract           | rdfs:Literal as xsd:string          |     ✓    |  ✓  |     ✓    |        |
| frequency           | dcterms:accuralPeriodicity | dcterms:Frequency                   |     ✓    |  ✓  |     ✓    |        |
| description         | dcterms:description        | rdfs:Literal as xsd:string/markdown |     ✓    |     |     ✓    |        |
| license             | dcterms:license            | dcterms:LicenseDocument             |     ✓    |  ✓  |     ✓    |        |
| temporal_resolution | dcat:temporalResolution    | [rdfs:Literal as xsd:duration]      |     ✓    |  ✓  |     ✓    |        |
| spatial_coverage    | dcterms:spatial            | dcterms:Location                    |     ✓    |  ✓  |     ✓    |        |
| temporal_coverage   | dcterms:temporal           | dcterms:PeriodOfTime                |     ✓    |  ✓  |     ✓    |        |
| spatial_resolution  | ons:spatialResolution      | [skos:Concept]                      |     ✓    |  ✓  |     ✓    |        |
| first_version       | dcat:first                 | dcat:Dataset                        |          |     |     ✓    |        |
| last_version        | dcat:last                  | dcat:Dataset                        |          |     |     ✓    |        |
| versions            | dcat:hasVersion            | [dcat:Dataset as ons:Version]       |          |     |     ✓    |        |
| next_release        | ons:nextRelease            | rdfs:Literal as xsd:dateTime        |     ✓    |  ✓  |     ✓    |        |
| landing_page        | dcat:landingPage           | foaf:Document                       |     ✓    |     |     ✓    |        |

#### Statistics quality designations

While the [Office for Statistics Regulation](https://osr.statisticsauthority.gov.uk/) provides definitions for different types of statistics, it does not provide a codelist or concepts of these designations. We recommend creating a blank node for each designation, assigning the appropriate `type`, `label` and `skos:exactMatch` to the appropriate IRI. These should be attached to individual Editions as `dqv:QualityAnnotation` using the `dqv:hasQualityAnnotation` predicate, it is not appropriate to attach at the Dataset (`dcat:DatasetSeries`) level as quality designations may change over time.

| Label                              | Previous name           | IRI                                                                                                                |
| ---------------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Accredited Official Statistics     | National Statistics     | `https://osr.statisticsauthority.gov.uk/accredited-official-statistics/`                                           |
| Official Statistics                | n/a                     | `https://osr.statisticsauthority.gov.uk/policies/official-statistics-policies/`                                    |
| Official Statistics in Development | Experimental Statistics | `https://osr.statisticsauthority.gov.uk/policies/official-statistics-policies/official-statistics-in-development/` |

For example, the following RDF expresses that a dataset is accredited official statistics:

```ttl
@prefix ex: <https://example.org/> .
@prefix dqv: <https://www.w3.org/TR/vocab-dqv/> .
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

ex:myDataset a dcat:Dataset ;
    dqv:hasQualityAnnotation [
        a dqv:QualityAnnotation ;
        rdfs:label "Accredited Official Statistic" ;
        skos:exactMatch <https://osr.statisticsauthority.gov.uk/accredited-official-statistics/> ;  ]
    .

```

```json
{
  "@context": "https://data.ons.gov.uk/ns#",
  "$id": "https://data.ons.gov.uk/datasets/cpih/2023-09",
  "@type": "dcat:Dataset",
  ...
  "quality_designation": 
    {
      "@type": "dqv:QualityAnnotation",
      "label": "Accredited Official Statistics",
      "exactMatch": "https://osr.statisticsauthority.gov.uk/accredited-official-statistics/"
    }
}
```

### Versions

Versions are the child object of Editions, using our own `ons:Version` object class which is a child of `dcat:Dataset`. They are the parent object of `dcat:Distribution`s.

| Keyword          | Predicate                  | Range                               |  GET  | GET {ID} | POST  | DELETE |
| ---------------- | -------------------------- | ----------------------------------- | :---: | :------: | :---: | :----: |
| @id              | dcterms:identifier         | rdfs:Literal as xsd:string          |   ✓   |    ✓     |   ✓   |   ✓    |
| created          | dcterms:created            | rdfs:Literal as xsd:dateTime        |   ✓   |    ✓     |   ✓   |        |
| creator          | dcterms:creator            | foaf:Agent                          |   ✓   |    ✓     |   ✓   |        |
| issued           | dcterms:issued             | rdfs:Literal as xsd:dateTime        |   ✓   |    ✓     |   ✓   |        |
| title            | dcterms:title / rdfs:label | rdfs:Literal as xsd:string          |   ✓   |    ✓     |   ✓   |        |
| description      | dcterms:description        | rdfs:Literal as xsd:string/markdown |       |    ✓     |   ✓   |        |
| version_notes    | adms:versionNotes          | rdfs:Literal as xsd:string          |   ✓   |    ✓     |   ✓   |        |
| next_version     | dcat:nextVersion           | dcat:Dataset                        |       |    ✓     |       |        |
| previous_version | dcat:previousVersion       | dcat:Dataset                        |       |    ✓     |       |        |

### Distributions

Distributions are the child object of Versions, and are `dcat:Distribution`. They are connected to the Version by the `dcat:distribution` predicate.

| Type         | Predicate                  | Range                                  | POST/PUT |  GET  | GET {ID} | DELETE |
| ------------ | -------------------------- | -------------------------------------- | :------: | :---: | :------: | :----: |
| @id          | dcterms:identifier         | rdfs:Literal as xsd:string             |    ✓     |   ✓   |    ✓     |   ✓    |
| created      | dcterms:created            | rdfs:Literal as xsd:dateTime           |    ✓     |   ✓   |    ✓     |        |
| creator      | dcterms:creator            | foaf:Agent                             |    ✓     |   ✓   |    ✓     |        |
| issued       | dcterms:issued             | rdfs:Literal as xsd:dateTime           |    ✓     |   ✓   |    ✓     |        |
| title        | dcterms:title / rdfs:label | rdfs:Literal as xsd:string             |    ✓     |   ✓   |    ✓     |        |
| description  | dcterms:description        | rdfs:Literal as xsd:string/markdown    |    ✓     |       |    ✓     |        |
| derived_from | prov:wasDerivedFrom        | prov:Entity                            |    ✓     |       |    ✓     |        |
| generated_by | prov:wasGeneratedBy        | prov:Activity                          |    ✓     |       |    ✓     |        |
| described_by | wdrs:describedBy           | rdfs:Resource                          |    ✓     |       |    ✓     |        |
| byte_size    | dcat:byteSize              | rdfs:Literal as xsd:nonNegativeInteger |          |       |    ✓     |        |
| download_url | dcat:downloadURL           | rdf:Resource                           |          |   ✓   |    ✓     |        |
| media_type   | dcat:mediaType             | dcterms:MediaType                      |    ✓     |   ✓   |    ✓     |        |
| checksum     | spdx:checksum              | spdx:Checksum                          |          |   ✓   |    ✓     |        |

#### CSV-W Distributions

Distributions of type CSV-W are a special case of distributions, and are `qb:DataSet` with a `csvw:TableSchema`. These properties are in addition to the standard distribution properties.

| Type             | Predicate        | Range                      | POST/PUT |  GET  | GET {ID} | DELETE |
| ---------------- | ---------------- | -------------------------- | :------: | :---: | :------: | :----: |
| csvqb:columnType | csvqb:columnType | csvqb:ColumnType           |    ✓     |   ✓   |    ✓     |        |
| csvw:aboutUrl    | csvw:aboutUrl    | rdfs:Literal as xsd:anyURI |    ✓     |       |    ✓     |        |
| csvw:column      | csvw:column      | csvw:Column                |    ✓     |       |    ✓     |        |
| csvw:datatype    | csvw:datatype    | xsd:Datatype               |    ✓     |       |    ✓     |        |
| csvw:name        | csvw:name        | rdfs:Literal as xsd:string |    ✓     |   ✓   |    ✓     |        |
| csvw:propertyUrl | csvw:propertyUrl | rdfs:Literal as xsd:anyURI |    ✓     |       |    ✓     |        |
| csvw:title       | csvw:title       | rdfs:Literal as xsd:string |    ✓     |   ✓   |    ✓     |        |
| csvw:valueUrl    | csvw:valueUrl    | rdfs:Literal as xsd:anyURI |    ✓     |       |    ✓     |        |
| csvw:virtual     | csvw:virtual     | xsd:boolean                |    ✓     |       |    ✓     |        |

## Versioning

We believe publishing data in a versioned manner is important. Every publication of a dataset at a version level cannot be amended, it can only be deleted or superseded by a new version. This is to ensure that the data is immutable. We provide fields in our service to allow producers to provide version notes, specifying the changes between versions of an edition. Additionally, there are convenience triples at both the `dcat:DatasetSeries` (datasets) and `dcat:Dataset` (editions) levels which points to the latest version of both entities, this is expressed as `dcat:hasCurrentVersion`.

### Example of versioning in RDF for CPIH

```turtle

@base <https://data.ons.gov.uk/datasets/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix data: <https://iana.org/assignments/media-types/> .
@prefix dataapp: <https://iana.org/assignments/media-types/application/> .
@prefix datatext: <https://iana.org/assignments/media-types/text/> .
@prefix wdrs: <http://www.w3.org/2007/05/powder-s#> .
@prefix qb: <http://purl.org/linked-data/cube#> .

<cpih> a dcat:DatasetSeries ;
  dcat:hasCurrentVersion <cpih/2019-03/version/2> .
<cpih/2019-01> a dcat:Dataset ;
 dcat:inSeries <cpih> ;
 dcat:hasCurrentVersion <cpih/2019-01/version/3> .
 dcat:hasVersion <cpih/2019-01/version/1>,
  <cpih/2019-01/version/2>,
  <cpih/2019-01/version/3> .

<cpih/2019-01/version/1> a dcat:Dataset ;
 dcat:distribution <cpih-2019-01-version-1.csv> .

<cpih-2019-01-version-1.csv> a dcat:Distribution ;
  dcat:mediaType datatext:csv ;
  wdrs:describedby <cpih-2019-01-version-1-metadata.json>.

<cpih-2019-01-version-1-metadata.json> dcat:mediaType <https://iana.org/assignments/media-types/application/csvm+json> .

<cpih/2019-01/version/2> a dcat:Dataset ;
 dcat:distribution <cpih-2019-01-version-2.json> .

<cpih-2019-01-version-2.json> a dcat:Distribution ;
  dcat:mediaType <https://iana.org/assignments/media-types/application/ld+json> .

<cpih/2019-01/version/3> a dcat:Dataset .

<cpih/2019-02> a dcat:Dataset ;
 dcat:inSeries <cpih> ;
 dcat:hasCurrentversion <cpih/2019-02/version/1> ;
 dcat:hasVersion <cpih/2019-02/version/1> .

<cpih/2019-02/version/1> a dcat:Dataset .

<cpih/2019-03> a dcat:Dataset ;
 dcat:inSeries <cpih> ;
 dcat:hasCurrentVersion <cpih/2019-01/version/2> ;
 dcat:hasVersion <cpih/2019-01/version/1>,
  <cpih/2019-01/version/2> .

<cpih/2019-03/version/1> a dcat:Dataset .

<cpih/2019-03/version/2> a dcat:Dataset .

<cpihQB> a dcat:Distribution , qb:Dataset .

```
