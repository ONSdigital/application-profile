The error message below appeared after running this command:

 pyshacl -s edition.ttl -m -i rdfs -a -j -f human test.ttl

# Error


SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (14):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

Validator encountered a Runtime Error:
SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (14):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:spatial.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:next.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:next ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:hasVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:hasVersion ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcterms:temporal.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOfTime, dcterms:temporal ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:inSeries.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, dcat:inSeries ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a dcat:prev.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DataSet, dcat:prev ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Dataset must have a adms:status.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:status, skos:Concept ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape