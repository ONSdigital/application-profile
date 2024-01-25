# Office for National Statistics RDF Namespace

The Office for National Statistics (ONS) RDF namespace is used for statistics, data representation, and dataset cataloguing. The namespace provides a standard way to identify and reference ONS resources in the Semantic Web.

## Official, national, and experimental statistics

The ONS RDF namespace has objects for official, national, and experimental statistics, as well as management information. Use these objects to classify dataset publications from accross UK government.

| Object                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ons:OfficialStatistic](https://gss-cogs.github.io/ref_ons_ontology/ons.html#OfficialStatistic)                       | Official statistics are statistics produced by Crown bodies and other organisations listed within an Official Statistics Order, on behalf of the UK government or devolved administrations. They provide a factual basis for assessment and decisions on economic, social and environmental issues at all levels of society. This broad definition of official statistics means that the scope of official statistics can be adapted over time to suit changing circumstances.   |
| [ons:AccreditedOfficialStatistics](https://gss-cogs.github.io/ref_ons_ontology/ons.html#AccreditedOfficialStatistics) | Accredited official statistics (previously called National Statistics in the Statistics and Registration Service Act 2007) are official statistics that the Office for Statistics Regulation (OSR) has independently reviewed and confirmed comply with the standards of trustworthiness, quality and value in the Code of Practice for Statistics. For a complete list of all accredited official statistics, see the List of Accredited Official Statistics maintained by OSR. |
| [ons:ExperimentalStatistic](https://gss-cogs.github.io/ref_ons_ontology/ons.html#ExperimentalStatistic)               | Experimental statistics are official statistics that are in the testing phase and not yet fully developed. Users should be aware that experimental statistics will potentially have a wider degree of uncertainty. The limitations of the statistics will be clearly explained within the release.                                                                                                                                                                               |
| [ons:ManagementInformation](https://gss-cogs.github.io/ref_ons_ontology/ons.html#ManagementInformation)               | Management information describes information that has been combined and collated. It is used in the normal course of business to inform operational delivery, policy development, and the management of organisational performance. Management information is usually based on administrative data, but it can also be a product of survey data. The terms ‘administrative data’ and ‘management information’ are sometimes used interchangeably.                                |
| [ons:AdministrativeData](https://gss-cogs.github.io/ref_ons_ontology/ons.html#AdministrativeData)                     | Administrative data refers to information that is not collected specifically for statistics or research. These data are collected by government departments and other organisations for uses such as registration, transactions, and record-keeping. The data are usually collected as a by-product of providing a service. Administrative data are often used for operational purposes and their statistical use is usually secondary.                                          |

```ttl
@prefix ons: <https://gss-cogs.github.io/ref_ons_ontology/ons.html#> .

ons:OfficialStatistic a rdfs:Class ;
    rdfs:label "Official statistic"@en ;
    rdfs:comment "Official statistics are statistics produced by Crown bodies and other organisations listed within an Official Statistics Order, on behalf of the UK government or devolved administrations. They provide a factual basis for assessment and decisions on economic, social and environmental issues at all levels of society. This broad definition of official statistics means that the scope of official statistics can be adapted over time to suit changing circumstances"@en ;
    rdfs:isDefinedBy <https://osr.statisticsauthority.gov.uk/policies/official-statistics-policies/> .
    .

ons:AccreditedOfficialStatistics a rdfs:Class ;
    rdfs:label "Accredeited national statistic"@en ;
    rdfs:comment "Accredited official statistics (previously called National Statistics in the Statistics and Registration Service Act 2007) are official statistics that the Office for Statistics Regulation (OSR) has independently reviewed and confirmed comply with the standards of trustworthiness, quality and value in the Code of Practice for Statistics. For a complete list of all accredited official statistics, see the List of Accredited Official Statistics maintained by OSR."@en ;
    rdfs:subClassOf ons:OfficialStatistic ;
    rdfs:isDefinedBy <https://osr.statisticsauthority.gov.uk/accredited-official-statistics/> 
    .

ons:ExperimentalStatistic a rdfs:Class ;
    rdfs:label "Experimental statistic"@en ;
    rdfs:comment "Experimental statistics are official statistics that are in the testing phase and not yet fully developed. Users should be aware that experimental statistics will potentially have a wider degree of uncertainty. The limitations of the statistics will be clearly explained within the release."@en ;
    rdfs:isDefinedBy <https://www.ons.gov.uk/methodology/methodologytopicsandstatisticalconcepts/guidetoexperimentalstatistics> 
    .

ons:ManagementInformation a rdfs:Class ;
    rdfs:label "Management information"@en ;
    rdfs:comment "Management information is information that is used to inform decision-making within an organisation. It is not official statistics."@en ;
    rdfs:isDefinedBy <https://analysisfunction.civilservice.gov.uk/policy-store/national-statisticians-guidance-management-information-and-official-statistics/> 
    .

ons:AdministrativeData a rdfs:Class ;
    rdfs:label "Administrative data"@en ;
    rdfs:comment "Administrative data refers to information that is not collected specifically for statistics or research. These data are collected by government departments and other organisations for uses such as registration, transactions, and record-keeping. The data are usually collected as a by-product of providing a service. Administrative data are often used for operational purposes and their statistical use is usually secondary."@en ;
    rdfs:isDefinedBy <https://analysisfunction.civilservice.gov.uk/policy-store/national-statisticians-guidance-management-information-and-official-statistics/>
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
