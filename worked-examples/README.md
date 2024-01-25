# worked-examples

This is a draft folder where we're experimenting with representation of data, for convenience we're using the [jsonld-cli](https://github.com/digitalbazaar/jsonld-cli) tool to convert to RDF and python's rdflib's [rdfpipe](https://rdflib.readthedocs.io/en/stable/apidocs/rdflib.tools.html#module-rdflib.tools.rdfpipe) to convert it to turtle.

For example, to convert post.jsonld to turtle:

```bash
jsonld toRdf post.jsonld -q | rdfpipe -i nquads -o ttl -
```

This helps us validate our inheritance and object models while writing directly in jsonld.

