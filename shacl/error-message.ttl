The error message below appeared after running this command:

pyshacl -s datasetversion.ttl -m -i rdfs -a -j -f human 4g-coverage.ttl

# Error

Validation Report
Conforms: False
Results (6):
Constraint Violation in MinCountConstraintComponent (http://www.w3.org/ns/shacl#MinCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:datatype xsd:string ; sh:message Literal("A dcat:Dataset must have a dcat:version.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:version ]
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Result Path: dcat:version
        Message: A dcat:Dataset must have a dcat:version.
Constraint Violation in MinCountConstraintComponent (http://www.w3.org/ns/shacl#MinCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:datatype xsd:string ; sh:message Literal("A dcat:Dataset must have a adms:versionNotes.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path adms:versionNotes ]
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Result Path: adms:versionNotes
        Message: A dcat:Dataset must have a adms:versionNotes.
Constraint Violation in MinCountConstraintComponent (http://www.w3.org/ns/shacl#MinCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:datatype xsd:dateTime ; sh:message Literal("A dcat:Dataset must have a dcterms:created.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcterms:created ]
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Result Path: dcterms:created
        Message: A dcat:Dataset must have a dcterms:created.
Constraint Violation in MinCountConstraintComponent (http://www.w3.org/ns/shacl#MinCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:message Literal("A dcat:Dataset must have a dcat:previousVersion.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:previousVersion ]
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Result Path: dcat:previousVersion
        Message: A dcat:Dataset must have a dcat:previousVersion.
Constraint Violation in MinCountConstraintComponent (http://www.w3.org/ns/shacl#MinCountConstraintComponent):
        Severity: sh:Violation
        Source Shape: [ sh:message Literal("A dcat:Dataset must have a dcat:version.") ; sh:minCount Literal("1", datatype=xsd:integer) ; sh:path dcat:nextVersion ]
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Result Path: dcat:nextVersion
        Message: A dcat:Dataset must have a dcat:version.
Constraint Violation in NotConstraintComponent (http://www.w3.org/ns/shacl#NotConstraintComponent):
        Severity: sh:Violation
        Source Shape: :DatasetShape
        Focus Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Value Node: <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset>
        Message: Node <https://gss-cogs.github.io/family-ess/out/4g-coverage/4g-coverage/4g-coverage.csv#dataset> conforms to shape [ sh:class qb:DataSet ; sh:message Literal("A dcat:Dataset cannot also be a qb:DataSet, a dcat:Dataset has dcat:distributions which can be a qb:DataSet.") ]