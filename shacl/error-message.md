The error message below appear after running this command:

pyshacl -s datasetseries.ttl -m -i rdfs -a -j -f human 4g-coverage.ttl


# Error

SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (12):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

Validator encountered a Runtime Error:
SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (12):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Result Path: sh:path
        Message: More than 1 values on [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:temporal.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:PeriodOftime, dcterms:temporal ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:license.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:LicenseDocument, dcterms:license ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:description.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:last ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcat:first.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:Dataset, dcat:first ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:accrualPeriodicity.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Frequency, dcterms:accrualPeriodicity ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Value Node: [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ]
        Message: Node [ <http://www.w3.org/ns/shacl#message:> Literal("A dcat:DatasetSeries must have a dcterms:spatial.") ; rdf:type rdfs:Resource ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:Location, dcterms:spatial ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

If you believe this is a bug in pyshacl, open an Issue on the pyshacl github page.