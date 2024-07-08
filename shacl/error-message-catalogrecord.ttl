The error message below appeared after running this command:

pyshacl -s catalogrecord.ttl -m -i rdfs -a -j -f human 4g-coverage.ttl

# Error

SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (2):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

Validator encountered a Runtime Error:
SHACL File does not validate against the SHACL Shapes SHACL (MetaSHACL) file.
Validation Report
Conforms: False
Results (2):
Constraint Violation in MaxCountConstraintComponent (http://www.w3.org/ns/shacl#MaxCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:maxCount Literal("1", datatype=xsd:integer) ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:or ( shsh:PathShape [ sh:nodeKind sh:IRI ] ) ; sh:path sh:path ]
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Result Path: sh:path
        Message: More than 1 values on [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]->sh:path
Constraint Violation in XoneConstraintComponent (http://www.w3.org/ns/shacl#XoneConstraintComponent):
        Severity: sh:Violation
        Source Shape: shsh:ShapeShape
        Focus Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Value Node: [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ]
        Message: Node [ rdf:type rdfs:Resource ; sh:message Literal("A dcat:CatalogRecord must have at least one foaf:primaryTopic .") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:DatasetSeries, foaf:primaryTopic ] does not conform to exactly one shape in shsh:NodeShapeShape , shsh:PropertyShapeShape

If you believe this is a bug in pyshacl, open an Issue on the pyshacl github page.