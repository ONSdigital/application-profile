The error message below appeared after running this command:

pyshacl -s distribution.ttl -m -i rdfs -a -j -f human 4g-coverage.ttl

# Error

SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (8):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

Validator encountered a Runtime Error:
SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (8):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]->sh:path
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one wdrs:describedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path rdfs:Resource, wdrs:describedBy ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasGeneratedBy.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Activity, prov:wasGeneratedBy ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one prov:wasDerivedFrom.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path prov:Entity, prov:wasDerivedFrom ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:Distribution must have at least one dcat:mediaType.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:mediaType, dcterms:MediaType ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

If you believe this is a bug in pyshacl, open an Issue on the pyshacl github page.