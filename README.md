## Schemablocks Tools

Tools for managing the {S}[B] repositories and website

### sbSchemaParser

The `sbSchemaParser.pl` script is used to process schema files written in
*JSON Schema* (YAML version) into human-readable documentation (e.g. Markdown files for Jekyll
based HTML generation) and JSON data files from the embedded examples.

* [Documentation](./sbSchemaParser.md)

### sbOpenAPIparser

The `sbOpenAPIparser.py` script processes OpenAPI-style JSCON Schema files (as
e.g. used in the [Beacon](http://github.com/ga4gh-beacon/)) project) into their
single schema "components", for processing further with _sbSchemaParser_.

* [Documentation](./sbOpenAPIparser.md)

### {S}[B] Repositories

{S}[B] code repositories adhere a consistent structure & naming:

```
sb-code           # each of the code repositories
  |
  |- source       # original code
  |- working      # for editing, temporary...
  |- schemas      # JSON Schema files as YAML; read to produce the output files
  |- generated    # contains files generated from main schema YAML files
      |- json     # .json version of the schema
      |- examples # .json example data, from inline examples
      |- doc      # .md documentation, from inline documentation
```

Here  

* The `source` and `working` directories are optional.
* The `json`, `examples` and `doc` directories are populated by _sbSchemaParser_.

### Website Files

_sbSchemaParser_ also generates copies of the `myschema.json` files into 
the canonical website directory, and a GH-pages version of the Markdown
documentation file into the `pages` tree processed by the GH-pages "Jekyll"
processing engine. The .md file contains a `permalink` directive in its YAML 
header, which will lead to GH-pages placing the HTML page at  "https://schemablocks.org/schemas/ga4gh/myschema.html".

```
ga4gh-schemablocks.github.io
  |
  |- schemas
  |        |- ga4gh # json version of the schema, generated from YAML
  |                 # => https://schemablocks.org/schemas/ga4gh/myschema.json
  |- pages
        |- _schemas
                |- ga4gh  # the Jekyll Markdown files for the website
```
