# Style

- [Style](#style)
  - [Titles](#titles)
  - [Summaries](#summaries)
  - [Descriptions](#descriptions)
  - [Keywords](#keywords)
  - [Publishers, creators and contacts](#publishers-creators-and-contacts)
  - [Checksums](#checksums)
  - [Using the appropriate literals](#using-the-appropriate-literals)
    - [Dates and times](#dates-and-times)
  - [Using IRIs](#using-iris)
    - [Hash or slash?](#hash-or-slash)
  - [`rdfs` vs `dcterms`](#rdfs-vs-dcterms)

## Titles

Titles should be front-loaded with the most important information first. They are the headline to help prospective users select the best dataset for their use. Titles are designed to be scannable by users, helping them to quickly include or exclude datasets from their search results with minimal effort and low error.

Contrary to guidance from ONS on titles geographic information isn't necessary as this information is better captured in the metadata; however it is important to align the titles of datasets in this service to the titles of datasets in other services to prevent unnecessary divergance.

- [GOVUK title guidance](https://www.gov.uk/guidance/content-design/writing-for-gov-uk#titles)
- [ONS title guidance for datasets](https://service-manual.ons.gov.uk/content/content-types/datasets#dataset-titles-and-summaries)

We recommend that titles not exceed 60 characters, including spaces.

## Summaries

Summaries are designed to support users to further refine their selection of the best dataset for their intended use. They should be written in 160 characters or less, including spaces. They should be written in plain English, avoiding jargon and acronyms. Including intended temporal and spatial coverage and resolution is recommended. Summaries should not contain update or publication dates which are otherwise captured in the metadata.

- [ONS summary guidance for datasets](https://service-manual.ons.gov.uk/content/content-types/datasets#dataset-titles-and-summaries)

## Descriptions

> TODO: No guidance covers descriptions right now, so we'll have to write it.

## Keywords

We use the `dcat:keyword` predicate to describe resources in metadata.

## Publishers, creators and contacts

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

## Checksums

Following the `spdx` specification, a `spdx:checksum` must comprise of a `spdx:checksumValue` and a `spdx:checksumAlgorithm`.

```ttl
<http://data.gov.uk/series/greenhouse-gas-emissions/dataset/2018.csv> a dcat:Distribution ;
    spdx:checksum [
        spdx:checksumValue "CE114E4501D2F4E2DCEA3E17B546F339"^^xsd:hexBinary ;
        spdx:checksumAlgorithm spdx:checksumAlgorithm_sha1 ;
    ] ;
    .
```

## Using the appropriate literals

### Dates and times

Data providers should prefer using `xsd:date` and `xsd:dateTime` literals to describe `dcterms:issued` and `dcterms:modified`, for example:

```ttl
<http://data.gov.uk/dataset/my-dataset> dcterms:issued "2018-01-01"^^xsd:date .
<http://data.gov.uk/dataset/my-dataset-2> dcterms:issued "2018-01-01T09:30:00"^^xsd:dateTime .
```

Data providers should prefer using IRIs from the `http://reference.data.gov.uk` vocabulary to describe dates and times within datasets (for example a time dimension). The IRI scheme is described [here](https://github.com/epimorphics/IntervalServer/blob/master/interval-IRIs.md).

## Using IRIs

Using IRIs instead of strings allows for better interoperability between datasets and avoids duplication of definitions. For example, use `K02000001` instead of "United Kingdom" to represent the United Kingdom in a dataset. See [code lists](code-lists.md#Recommended code lists) for examples of code lists which can be reused across your publications.

### Hash or slash?

- [HashVsSlash](https://www.w3.org/wiki/HashVsSlash)
- [Best Practice Recipes for Publishing RDF Vocabularies](https://www.w3.org/TR/swbp-vocab-pub)

Data producers must ensure that resource IRIs resolve sensibly and avoid `40X` or `50X` HTTP status codes. Throughout this profile we present IRI choices using both hash `#` and slash `/` IRIs. Data producers should pick the most appropriate choice, considering whether the resulting IRIs will resolve sensibly.

Newly created IRIs should avoid including a trailing slash.

## `rdfs` vs `dcterms`

> Some helpful discussion [here](https://jazz.net/wiki/bin/view/LinkedData/UseOfRdfsLabelVersusDctermsTitle).

The `rdfs` and `dcterms` vocabularies offer similar properties: `rdfs:label` and `rdfs:comment` vs. `dcterms:title` and `dcterms:description`.

For document-like resources, we use `dcterms`. So resources of class `dcat:Dataset`, `dcat:Catalog`, `dcat:Distribution` etc. should use `dcterms`.

For vocabulary definitions we adopt `rdfs`, so `skos:Concept` and `qb:ComponentProperty` resources should use `rdfs`.
