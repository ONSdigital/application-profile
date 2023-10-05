# Style

- [Style](#style)
  - [Titles](#titles)
  - [Descriptions](#descriptions)
  - [Keywords](#keywords)
  - [Checksums](#checksums)
  - [Using the appropriate literals](#using-the-appropriate-literals)
    - [Dates and times](#dates-and-times)
  - [Using IRIs](#using-iris)
    - [Hash or slash?](#hash-or-slash)
  - [`rdfs` vs `dcterms`](#rdfs-vs-dcterms)

## Titles

- [GOVUK title guidance](https://www.gov.uk/guidance/content-design/writing-for-gov-uk#titles)
- [ONS title guidance for datasets](https://style.ons.gov.uk/data-visualisation/dataset-titles-and-summaries/)
- [ONS title guidance for articles](https://style.ons.gov.uk/category/articles/article-titles-and-summaries/)
- [ONS title guidance for bulletins](https://style.ons.gov.uk/category/statistical-bulletin/bulletin-titles-and-summaries/)

We recommend that titles not exceed 65 characters, including spaces.

## Descriptions

> TODO: Separate out the guidance for abstracts/sumamries from descriptions.

- [GOVUK description guidance](https://www.gov.uk/guidance/content-design/writing-for-gov-uk#summaries)
- [ONS description guidance for datasets](https://style.ons.gov.uk/data-visualisation/dataset-titles-and-summaries/)
- [ONS description guidance for articles](https://style.ons.gov.uk/category/articles/article-titles-and-summaries/)
- [ONS description guidance for bulletins](https://style.ons.gov.uk/category/statistical-bulletin/bulletin-titles-and-summaries/)

We recommend that descriptions not exceed 160 characters, including spaces.

## Keywords

- [ONS keyword guidance](https://style.ons.gov.uk/house-style/keywords-2/)

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

Using IRIs instead of strings allows for better interoperability between datasets and avoids duplication of definitions. For example, use `K02000001` instead of "United Kingdom" to represent the United Kingdom in a dataset. See [code lists](code_lists.md#Recommended code lists) for examples of code lists which can be reused across your publications.
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
