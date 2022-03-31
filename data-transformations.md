---
layout: page
title: Data Transformations
permalink: /data-transformations/
---

## Characteristics
We derived a set of characteristics and divided them in 2 categories:

1. Description
2. Alignment

### Description
The way in which a data transformation is described such as function's body 
or its parameters.

- **F1: Declarativeness**
If the data transformations are declaratively described,
considering the function body, parameter values, and return values.
- **F2: Shareability**
If data transformations can be shared and re-used 
through a common repository or library.
- **F3: Custom data transformations**
If custom data transformations can be described declaratively
and be used with existing data transformations.

### Alignment
How the data transformations are aligned with mapping languages
and if they can be used standalone or not.

- **F4: Independence**
The data transformation description depends 
on certain mapping languages or implementations.
- **F5: Integration with mapping languages**
How mapping languages integrate the data transformations,
interact with them and describe them in the mapping rules.

### Overview

| Data Transformation | F1                                                           | F2                       | F3        | F4               | F5                                          |
|---------------------|--------------------------------------------------------------|--------------------------|-----------|------------------|---------------------------------------------|
| SPARQL Functions    | declarative described, referenced function & parameters      | Federated Queries        | Yes       | Depend on SPARQL | Any                                         |
| GeoTriples          | declarative described, referenced function & parameters      | No                       | No        | Standalone       | R2RML or RML                                |
| KR2RML              | function body and parameters as hardcoded strings            | Python Package Index     | Yes       | Depend on KR2RML | KR2RML-only                                 |
| Function Ontology   | declarative described, referenced function & parameters      | Function Hub             | Yes       | Standalone       | Any                                         |
| FunUL               | function body as string, referenced function & parameters    | Implementation dependent | Yes       | Depend on RML    | RML-only                                    |
| D2RML               | declarative described, referenced function & parameters      | No                       | Partially | Depend on D2RML  | D2RML-only, only pre-processing input data  |
| D-REPR              | function body and parameters as string, hardcoded parameters | Python Package Index     | Yes       | Depend on D-REPR | D-REPR-only, only pre-processing input data |

## Data transformations
In this section, we analyzed 7 data transformation approaches
on 5 different characteristics to provide an overview of these approaches.

### SPARQL Functions (2013)
The W3C recommended SPARQL supports
[functions](https://www.w3.org/TR/sparql11-query/#func-rdfTerms)
which are executed during query evaluation by the SPARQL engine.
SPARQL specifies a set of built-in functions, conditions,
and how custom functions can be used (F3).
However, supported functions heavily depend on
the underlying SPARQL engine executing the query (F4).
SPARQL functions can be re-used among engines
through SPARQL Federated Queries (F2).
Function parameters and return values are not hard coded
but binded using SPARQL BIND expressions (F1).
SPARQL also provides conditions through `FILTER` and `IF` expressions
to evaluate parts of the SPARQL query only when a certain condition is met.
However, SPARQL functions cannot be used standalone because of
their tight integration with the SPARQL query and engine (F4).
SPARQL functions are integrated in SPARQL queries as a SPARQL operator
and can be applied on any part of the schema transformation (F5).
SPARQL functions are leveraged by
[SPARQL-Generate](https://github.com/sparql-generate/sparql-generate),
[XSPARQL](https://github.com/semantalytics/xsparql),
and [Facade-X](https://github.com/SPARQL-Anything/sparql.anything)
to provide data transformations.

### GeoTriples (2014)
GeoTriples extends RML with support for geographical data sources
and transformations.
GeoTriples uses [GeoSPARQL](https://www.opengis.net/doc/IS/geosparql/1.0)
and stSPARQL functions which are aligned with RML mapping rules
through two extensions: `rrx:Function` and `rrx:ArgumentMap`.
The parameters order in `rrx:ArgumentMap` matches the order of arguments
of the function (`rdf:List`).
Each function parameter is an `rr:TermMap` which allows GeoTriples
to reference values as function parameters.
The return value is used directly in the mapping rules
and are not declarative described (F1, F5).
GeoTriples supports a fixed set of GeoSPARQL and stSPARQL functions (F3)
as data transformations, but these functions are not depending on GeoTriples.
Therefore, GeoSPARQL and stSPARQL functions can be used
with other GeoSPARQL and stSPARQL engines (F4).
Currently, GeoSPARQL and stSPARQL functions are built-in into
the GeoSPARQL query language, and not shared through a repository as FnO (F2).

**Source code** : [https://github.com/LinkedEOData/GeoTriples](https://github.com/LinkedEOData/GeoTriples)
<br>
**Last accessed** : 10/11/2021

### KR2RML (2015)
KR2RML is based on R2RML with support for data transformations
through custom functions and conditions written in Python (F3).
The function's body and parameter values are integrated
in KR2RML mapping rules as a string (F5).
Functions can use builtin Python modules or
from [Python Package Index](https://pypi.org/) (F2).
Function parameters and return values are hardcoded
in the KR2RML mapping rules without a declarative description (F1, F4).
KR2RML functions are implemented in Karma-Web.

**Source code** : [https://github.com/usc-isi-i2/Web-Karma](https://github.com/usc-isi-i2/Web-Karma)
<br>
**Last accessed** : 10/11/2021

### Function Ontology (FnO, 2016)
The [Function Ontology](https://fno.io/spec/) (FnO)
is a semantic description of functions
without depending on their implementation (F4).
FnO describes each function's parameters and
return value to specify how the function should be used.
Moreover, FnO also describes the problem the function solves
to enable semantically re-use of functions.
Existing functions and their implementations in various languages
can be shared throughout the Function Hub (F2).
Values which are passed to a function are not hardcoded but referenced (F1).
Custom functions can be added by providing an FnO description
and optionally one or multiple implementations (F3).
FnO can be used standalone (F4),
but is aligned with RML to apply data transformations.
In RML, FnO descriptions can be added in the mapping rules
on any part of the schema transformation
through [`fnml:FunctionMap`](http://semweb.mmlab.be/ns/fnml#)
since `fnml:FunctionMap` is compatible with an R2RML Term Map.
Each Function Map refers to the function description
to execute the function (`fno:executes`)
and its parameters (example: `grel:inputString`) (F5).
An FnO function can be used as a data transformation
or as a condition in RML when performing the schema transformation.
Several materialization implementations for generating knowledge graphs
from heterogeneous using mapping languages incorporated support
for FnO functions.

**Specification**: [https://fno.io/spec/](https://fno.io/spec/)
<br>
**Last accessed**: 10/11/2021

### FunUL (2016)
FunUL extends RML by incorporating functions and conditions
inside the mapping rules.
FunUL function's body is a Literal,
specified with the `rrf:functionBody` property.
Its function's name is described with the property `rrf:functionName`.
Each function can be called through a `rrf:functionCall`
which references to a function (`rrf:function`)
and its parameters (`rrf:parameterBindings`) (F5).
FunUL is based on R2RML-F and broadens R2RML-F's scope
from relational databases to heterogeneous data.
FunUL is not stand-alone,
as it must be used together with RML mapping rules (F4).
FunUL's functions are written in JavaScript as a literal
in the RML mapping rules, but FunUL's approach is not depending
on a specific programming language as with KR2RML's data transformations.
FunUL's functions parameters and return values are not hardcoded
in the mapping rules for reusability (F1).
However, FunUL reuses `rr:column`, `rml:reference`, and `rr:constant`
from RML and R2RML for referencing values for function parameters,
therefore no other mapping language can be used.
FunUL's function return values are directly used to generate RDF
in a R2RML Predicate Object Map by the implementation
executing the RML mapping rules.
Built-in functions of a programming language can be used
and custom functions can be defined as well inside the mapping rules (F3).
Depending on the programming language and implementation,
functions can be shared and reused from repositories,
but there is no equivalent of FnO's Function Hub (F2).
FunUL is demonstrated in a forked version of the RML Processor.

**Source code**: [https://github.com/CNGL-repo/RMLProcessor](https://github.com/CNGL-repo/RMLProcessor)
<br>
**Last accessed**: 10/11/2021

### D2RML (2018)
D2RML extends R2RML for mapping heterogeneous data into RDF,
but also with `dr:Function` to support data transformations and conditions.
D2RML incorporates data transformations through `dr:Transformations`
in its declarative description for generating RDF
and are applied on the heterogeneous data retrieved
through D2RML's declarative data source description (Logical Source). 
D2RML's data transformations can only be described in a D2RML's Triples Map
to apply on the retrieved data,
they cannot be used on D2RML's abstracted intermediate format
or on the generated RDF.
D2RML conditions are located in R2RML's Term Maps
to generate an RDF triple based upon a certain condition (F5).
D2RML uses `dr:Function` to refer to a function
and `dr:ParameterBinding` to refer to function's parameters,
but the return value is not described (F1).
D2RML data transformations and conditions cannot be used standalone
because of tight integration with D2RML (F4).
D2RML provides a set of custom IRI generation functions
and allows the use of web services to apply custom transformations (F3).
D2RML can not leverage a function repository to share
and reuse existing functions (F2).
D2RML data transformations and conditions are available
as a [web service](https://apps.islab.ntua.gr/d2rml/).

### D-REPR (2019)
D-REPR integrates data transformations for pre-processing data.
Functions can be customized (F3),
and are shareable as with KR2RML through Python Package Index (F2).
Functions are written in Python with hardcoded parameters
of each function (F1, F4), following a similar principle as KR2RML.
These functions are only declaratively described for input data
in a `[preprocessing]` YAML block which contains a list of functions.
Each function has a function (`[type]`), its input parameters (`[input]`),
expected return values and its body (`[code]`).
Since these functions are described in the `[preprocessing]` block,
they cannot be applied on the intermediate JSON tree format
or on the generated RDF (F5).
D-REPR's data transformations are implemented in D-REPR.

**Source code** : [https://github.com/usc-isi-i2/d-repr](https://github.com/usc-isi-i2/d-repr)
<br>
**Last accessed** : 10/11/2021

