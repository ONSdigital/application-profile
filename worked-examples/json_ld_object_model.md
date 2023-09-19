# Object Model

```mermaid


classDiagram
Distribution <|-- DatasetVersion : dcat.Distribution 
DatasetVersion <|-- Edition : dcat.hasVersion
Edition --|> DatasetSeries : dcat.inSeries 
CatalogRecord --|> DatasetSeries : foaf.primaryTopic
Catalog --|> CatalogRecord : dcat.record
MethodDataset --|> Edition : prov.influenced
AnalysisDataset --|> Edition : prov.wasDerivedFrom
VcardKind --|> Edition : dcat.contactPoint
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
    -dcat:hasVersion ∋ dcat:Dataset
    -dcterms:modified ∋ rdfs:Literal as xsd:dateTime
    -dcterms:issued ∋ rdfs:Literal as xsd:dateTime
    -dcterms:spatial ∋ dcterms:Location
    -onsns:spatialResolution ∋ [skos:Concept]
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
    +onsns:nextRelease ∋ rdfs:Literal as xsd:dateTime
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
    +onsns:spatialResolution ∋ [skos:Concept]
    +dcterms:temporal ∋ dcterms:PeriodOfTime
    +dcat:temporalResolution ∋ [rdfs:Literal as xsd:duration]
    -dcat:first ∋ dcat:Dataset
    -dcat:last ∋ dcat:Dataset

}

class MethodDataset["MethodDataset a dcat:Dataset"]{
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcterms:title, rdfs:label ∋ rdfs:Literal as xsd:string
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
    +dcterms:abstract ∋ rdfs:Literal as xsd:string
    +dcterms:description ∋ rdfs:Literal as xsd:string/markdown
    -dcat:prev ∋ dcat:Dataset
    -dcat:next ∋ dcat:Dataset
}

class AnalysisDataset["AnalysisDataset a dcat:Dataset"] {
    +dcterms:identifier ∋ rdfs:Literal as xsd:string
    +dcterms:title, rdfs:label ∋ rdfs:Literal as xsd:string
    +dcterms:created ∋ rdfs:Literal as xsd:dateTime
    +dcterms:abstract ∋ rdfs:Literal as xsd:string
    +dcterms:description ∋ rdfs:Literal as xsd:string/markdown
    +prov:wasDerivedFrom ∋ [prov:Entity]
    -dcat:prev ∋ dcat:Dataset
    -dcat:next ∋ dcat:Dataset
}
```

## Some definitions
### Dataset metadata surrounding the publication, issuance, modification, etc.

We make the following assumptions, that a dataset will be created prior to its publications.

For datasetVersion:
* `dcterms:created` - the date the dataset earliest version was created in system
* `dcterms:issued` - the date the dataset was published for public consumption

For dataset:
* `dcterms:created` - the date the earliest dataset version created in system
* `dcterms:issued` - the date the earliest dataset version was first published for public consumption
* `dcterms:modified` - the date the newest dataset version created in system

For datasetSeries:
* `dcterms:created` - the date the earliest dataset created in system
* `dcterms:issued` - the date the earliest dataset was first published for public consumption
* `dcterms:modified` - the date the newest dataset created in system
