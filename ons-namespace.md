# Office for National Statistics RDF Namespace

The Office for National Statistics (ONS) RDF namespace is used for statistics, data representation, and dataset cataloguing. The namespace provides a standard way to identify and reference ONS resources in the Semantic Web.

## Official, national, and experimental statistics

The ONS RDF namespace has objects for official, national, and experimental statistics, as well as management information. Use these objects to classify dataset publications from accross UK government.

| Object                                                                                                  | Description                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ons:OfficialStatistic](https://gss-cogs.github.io/ref_ons_ontology/ons.html#OfficialStatistic)         | Official statistics are statistics that are produced by government departments, agencies, and other public bodies. They provide quantitative information on a wide range of social and economic matters and are used to inform debate, decision-making and research both within government and by the wider community. |
| [ons:NationalStatistic](https://gss-cogs.github.io/ref_ons_ontology/ons.html#NationalStatistic)         | National statistics are a subset of official statistics. They are produced to high professional standards set out in the Code of Practice for Statistics. They are designated as National Statistics by the UK Statistics Authority.                                                                                   |
| [ons:ExperimentalStatistic](https://gss-cogs.github.io/ref_ons_ontology/ons.html#ExperimentalStatistic) | Experimental statistics are new official statistics undergoing evaluation. They are published in order to involve users and stakeholders in their development and as a means to build in quality at an early stage.                                                                                                    |
| [ons:ManagementInformation](https://gss-cogs.github.io/ref_ons_ontology/ons.html#ManagementInformation) | Management information is information that is used to inform decision-making within an organisation. It is not official statistics.                                                                                                                                                                                    |

```ttl
@prefix ons: <https://gss-cogs.github.io/ref_ons_ontology/ons.html#> .

ons:OfficialStatistic a rdfs:Class ;
    rdfs:label "Official statistic"@en ;
    rdfs:comment "Official statistics are statistics that are produced by government departments, agencies, and other public bodies. They provide quantitative information on a wide range of social and economic matters and are used to inform debate, decision-making and research both within government and by the wider community."@en ;
    .

ons:NationalStatistic a rdfs:Class ;
    rdfs:label "National statistic"@en ;
    rdfs:comment "National statistics are a subset of official statistics. They are produced to high professional standards set out in the Code of Practice for Statistics. They are designated as National Statistics by the UK Statistics Authority."@en ;
    rdfs:subClassOf ons:OfficialStatistic ;
    .

ons:ExperimentalStatistic a rdfs:Class ;
    rdfs:label "Experimental statistic"@en ;
    rdfs:comment "Experimental statistics are new official statistics undergoing evaluation. They are published in order to involve users and stakeholders in their development and as a means to build in quality at an early stage."@en ;
    .

ons:ManagementInformation a rdfs:Class ;
    rdfs:label "Management information"@en ;
    rdfs:comment "Management information is information that is used to inform decision-making within an organisation. It is not official statistics."@en ;
    .
```

## Extending dcat object types for cataloguing UK Government data

In order to improve the adoption of dcat by government departments, offices, and agencies, we have extended the dcat object types to use more familiar terms for existing publishing workflows.

```mermaid
classDiagram

Dataset --|> Edition : dcat&Colon;serriesMember
Dataset <|-- Edition : dcat&Colon;inSeries
Edition --|> Version : dcat&Colon;hasVersion
Edition <|-- Version : dcat&Colon;isVersionOf
Version --|> Distribution : dcat&Colon;distribution
Version <|-- Distribution : dcat&Colon;isDistributionOf


class Dataset {
    rdfs:subClassOf dcat&#58;DatasetSeries
}

class Edition {
    rdfs:subClassOf dcat&#58;Dataset
}

class Version {
    rdfs:subClassOf dcat&#58;Dataset
}

class Distribution {
    rdfs:subClassOf dcat&#58;Distribution
}

```

Note: The use of `∷` (i.e. `&Colon;`) in the above diagram is due to a [bug in mermaid](https://github.com/mermaid-js/mermaid/issues/1266), please read these characters as `:` (i.e. `&colon;`).

This leads to the following RDF:

```ttl
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ons: <https://gss-cogs.github.io/ref_ons_ontology/ons.html#> .

ons:Dataset rdfs:subClassOf dcat:DatasetSeries ;
    rdfs:label "Dataset"@en ;
    rdfs:comment "A series of data, published or curated by a single agent, and available for access or download in one or more formats."@en ;
    .

ons:Edition rdfs:subClassOf dcat:Dataset ;
    rdfs:label "Edition"@en ;
    rdfs:comment "A specific edition of a dataset, typically marked by an announced release date or scheduled release period."@en ;
    .

ons:Version rdfs:subClassOf dcat:Dataset ;
    rdfs:label "Version"@en ;
    rdfs:comment "A specific version of an edition of a dataset, all editions have at least one version, but will have more if the dataset has been revised."@en ;
    .

ons:Distribution rdfs:subClassOf dcat:Distribution ;
    rdfs:label "Distribution"@en ;
    rdfs:comment "A specific representation of a version of an edition of a dataset, which may be one of many formats, media types, or have multiple access methods."@en ;
    .
```
