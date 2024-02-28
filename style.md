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

Contrary to guidance from ONS on titles geographic information isn't necessary as this information is better captured elsewhere in the metadata; however it is important to align the titles of datasets in this service to the titles of datasets in other services to prevent unnecessary divergance.

- [GOVUK title guidance](https://www.gov.uk/guidance/content-design/writing-for-gov-uk#titles)
- [ONS title guidance for datasets](https://service-manual.ons.gov.uk/content/content-types/datasets#dataset-titles-and-summaries)

We recommend that titles not exceed 60 characters, including spaces.

## Summaries

Summaries are designed to support users to further refine their selection of the best dataset for their intended use. They should be written in 160 characters or less, including spaces. They should be written in plain English, avoiding jargon and acronyms. Including intended temporal and spatial coverage and resolution is recommended at the end of the summary. Summaries should not contain update or publication dates which are otherwise captured in the metadata.

A well contstructed summary should cover the topic of measurement, its population, the time period, and its geographic scope in that order. For example, "Egg packing station throughput and prices for the UK, quarterly from 1996."

- [ONS summary guidance for datasets](https://service-manual.ons.gov.uk/content/content-types/datasets#dataset-titles-and-summaries)

## Descriptions

Descriptions are designed to provide users with a more detailed understanding of the dataset. They should be written in plain English, avoiding jargon and acronyms. Descriptions should be concise and informative, providing enough information for a user to understand the purpose and content of the dataset. Descriptions should not contain update or publication dates which are otherwise captured in the metadata.

Our description fields support markdown, which can be used to format text. This can be used to create lists, headings, and links.

We suggest using the description field to provide details of the methodology, data sources, and any limitations of the dataset for now; however we intend on providing a separate field for these components in the future.

When providing a description, follow these guidelines:

- Be concise: Keep your descriptions short and to the point.
- Be clear: Avoid jargon, abbreviations, and technical terms when possible. If you must use them, provide definitions.
- Be informative: The description should provide enough information for a user to understand the purpose and content of the dataset.
- Be consistent: Use a consistent style and tone across all descriptions.
- Use active voice: Active voice makes your writing stronger and more direct.
- Include keywords: If there are specific keywords related to the dataset, include them in the description.

## Keywords

When using `dcat:keyword` to describe resources in metadata, it's important to choose keywords that are relevant, descriptive, and concise. Here are some guidelines:

- Be relevant: Keywords should be closely related to the content of the resource. They should reflect the search words people would use to find it via a search engine.
- Be descriptive: Keywords should be descriptive enough to give a clear idea of the resource's content. Avoid vague or generic terms.
- Be concisene: Try to keep keywords short and to the point. Long phrases or sentences are not suitable as keywords.
- Don't repeat yourself: Place names, or time periods are not appropriate as keywords. This information is better conveyed in the spatial/temporal bounds/resolution of the resource. These fields are also searchable.
- Use spaces and lowercases: Keywords should be written in lowercase and separated by spaces, unless the keyword is a proper name. For example, "Scotch whiskey" and "imports" are appropriate, but "Alcohol Duties" is not.
- Proper Names: If a keyword is a proper name, it should be written as it is normally used, including any capitalization. For example, "Scotch whiskey" or "Champagne".

Remember, the goal of using keywords is to help users find and understand your resource. Choose keywords that will make your resource easily discoverable and understandable.

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
