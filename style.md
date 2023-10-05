# Style

- [Style](#style)
  - [Titles](#titles)
  - [Descriptions](#descriptions)
  - [Keywords](#keywords)
  - [Checksums](#checksums)

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
