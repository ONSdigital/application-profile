# Shacl Scripts

I have created 7 shacl scripts to validate against turtle files.

These are:

- catalog.ttl
- catalogrecord.ttl
- datasets.ttl
- datasetseries.ttl
- datasetversion.ttl
- distribution.ttl
- edition.tttl

These shacl scripts are based on the object model diagram. The model is a high-level view of the relationship, between the objects in our statistical data publication lifecycle.

The purpose of these scripts is to be used as a form of validation. To make sure that what we want in the JSON file which is part of the CSV-W process is correct. That is why some of the properties in the shacl script contain Warning and Info error messages.

The command I ran:

pyshacl 4g-coverage.ttl -m -i rdfs -a -j datasetseries.ttl

You can interchange both the 4g-coverage and datasetseries turtle file, to whichever shape and data graphs you want to validate.