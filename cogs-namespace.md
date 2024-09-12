# Office for National Statistics RDF Namespace

The Connected Open Graph Statistics (COGS) RDF namespace is used for statistics, data representation, and dataset cataloguing. The namespace provides a standard way to identify and reference data for recurring statistical publications within the Semantic Web. An additional goal was to meet the Statistical Code of Practice by the Government Statistical Service.

## Extending dcat object types for cataloguing recurring statistical publications

In order to improve the adoption of dcat by government departments, offices, and agencies, we have extended the dcat object types to use more familiar terms for existing publishing workflows.

```mermaid
classDiagram

Dataset --|> Edition : cogs&Colon;serriesMember
Dataset <|-- Edition : cogs&Colon;inSeries
Edition --|> Version : cogs&Colon;hasVersion
Edition <|-- Version : cogs&Colon;isVersionOf
Version --|> Distribution : cogs&Colon;distribution
Version <|-- Distribution : cogs&Colon;isDistributionOf


class Dataset {
    rdfs:subClassOf cogs&#58;DatasetSeries
}

class Edition {
    rdfs:subClassOf cogs&#58;Dataset
}

class Version {
    rdfs:subClassOf cogs&#58;Dataset
}

class Distribution {
    rdfs:subClassOf cogs&#58;Distribution
}

```

Note: The use of `∷` (i.e. `&Colon;`) in the above diagram is due to a [bug in mermaid](https://github.com/mermaid-js/mermaid/issues/1266), please read these characters as `:` (i.e. `&colon;`).

## Adding new attributes to support Code of Practice requirements

We have added new attributes to several cogs objects to support the Code of Practice requirements. These attributes are:

cogs:nextRelease
Type: owl:DatatypeProperty
Domain: cogs:Dataset
Range: xsd:dateTime
Label: "Next release date"
Indicates the date and time when the next edition of a dataset will be released. If the date is specified without a time component, the release occurs on that day. If a specific time is provided, the release is expected at that precise time.

cogs:spatialResolution
Type: owl:DatatypeProperty
Domain: cogs:Dataset, cogs:Edition
Range: skos:Concept
Label: "Spatial resolution"
Indicates the spatial resolution of the dataset or edition. This should use one or more concepts from a controlled vocabulary such as the SKOS concept scheme. Similar to the dcat:temporalResolution property.

cogs:caveat
Type: owl:DatatypeProperty
Domain: cogs:Dataset, cogs:Edition, cogs:Version
Range: xsd:string
Label: "Caveat"
Indicates any caveats or limitations associated with the dataset, edition, or version. This could include information on data quality, coverage, or other important considerations for users.

