# Graphs

We represent data in RDF and compartmentalise it into graphs. This is a useful way of organising data, and is a key feature of RDF. It is also a useful way of organising data in a triple store, as it allows us to query for data in a particular graph.

## Named graphs for catalogue metadata

Where metadata is stored as RDF, such as being made available via a SPARQL endpoint, DCAT makes a recommendation about the names of graphs to use for catalogue records.

> If a catalog is represented as an RDF Dataset with named graphs (as defined in [[SPARQL11-QUERY]](https://www.w3.org/TR/sparql11-query/)), then it is appropriate to place the description of each dataset (consisting of all RDF triples that mention the dcat:Dataset, dcat:CatalogRecord, and any of its dcat:Distributions) into a separate named graph. The name of that graph SHOULD be the IRI of the catalog record.[^named-graphs]

```ttl
<http://data.gov.uk/datasets/my-dataset/record> {
    ...
}
```

Doing this results in a neat ability to query for dataset metadata by limiting a SPARQL query to the IRI of the catalogue record.

```sparql
SELECT * 
FROM <http://data.gov.uk/datasets/my-dataset/record> 
WHERE {
    ?s ?p ?o .
}
```

## Named graphs for RDF Cube distributions

Where dataset distributions are stored as RDF, such as being made available via a SPARQL endpoint, we recommend storing the qb:Dataset in a named graph with the same IRI as the distribution.

Storing multiple versions and editions of the same dataset is costly for a Triplestore, we recommend only storing a single set of observations which represents the cumulative state of the dataset (i.e. the latest version and edition of the dataset which has all observations).

```ttl
<http://data.gov.uk/datasets/my-dataset/editions/latest/versions/latest> {
    ...
}
```

Doing this results in a neat ability to query for dataset by limiting a SPARQL query to the IRI of the distribution similar to the metadata query.

```sparql
SELECT * 
FROM <http://data.gov.uk/datasets/my-dataset/editions/latest/versions/latest>
WHERE {
    ?s ?p ?o .
}
```

[^named-graphs]: <https://www.w3.org/TR/vocab-dcat-3/#Class:Catalog_Record>
