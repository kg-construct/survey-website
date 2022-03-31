---
layout: page
title: Schema Transformations
permalink: /schema-transformations/
---

## Characteristics

### Declarative transformation description
Mapping languages declaratively describe in different ways
how schema and data transformations are applied on input data.
The following characteristics are considered:

- **S1: Schema transformation**
Schema transformations (re)model the input data,
describe relations between data, and which vocabularies to use.
For example, the schema transformation describes how
a person's age should be modelled by relating the person's age
from the input data, to the person, and use the appropriate vocabulary
such as `foaf:age`.
If the schema transformation
is declaratively described by the mapping language.
- **S2: Data transformation**
Data transformations describe how to change data into a new representation.
For example: the person's birth date is available
in the input data, but the schema transformation requires the person's age.
The data transformation describes how to transform the birth date
into the age which can be used then by the schema transformation.
If data can be transformed or conditions can be applied
with the schema transformation.
Some schema transformations leverages existing data transformations.
- **S3: Export description**
Export description describes to where and how the generated RDF is exported.
If the serialization format e.g. RDF/XML or Turtle, and target e.g.,
a file or a SPARQL of a generated RDF graph are described.
- **S4: End-to-End**
If a mapping language allows to describe the entire process declaratively
from accessing and transforming the data until exporting the generated RDF,
or relies on hard-coded parts to access, transform, or export RDF graphs.
- **S5: Web standards integration**
If a mapping language integrates with existing web standards
by relating to existing W3C recommendations.

### Data processing and composition
Mapping languages describe access to and how to process
input data in various ways. We consider the following characteristics:

- **S6: Joins**
If data joins are supported and
are declaratively described in the schema transformation.
- **S7: Intermediate representation**
If a mapping language uses heterogeneous data directly or transforms
it first into a homogeneous intermediate representation
before applying the schema and data transformations.
- **S8: Nester hierarchies**
Nested data structures such as XML or JSON are not tabular
like SQL databases or CSV, but hierarchical.
If a mapping language can handle hierarchical structures
and join these nested data structures or not.
- **S9: Multi-paths**
If multiple path expressions – such as JSON-Path or XPath –
can be used together for accessing nested data encoded
in heterogeneous formats, e.g., NoSQL databases
allow mixing formats such as JSON inside the NoSQL database.
If a mapping language can combine different path expressions or not.

### Coverage of the RDF(S) specification
We cover characteristics from the RDF 1.1 specification
and the other vocabularies from the RDF Schema (RDFS) specification.
These characteristics describe which parts
are typically described by each mapping language.

- **S10: RDF triples (subjects, predicates, and objects)**
If a mapping language can describe how RDF subjects, predicates
and objects should be generated.
- **S11: IRIs**
If a mapping language can describe
how a valid IRI conform RFC 3987 should be generated.
- **S12: Literals (including language tags and datatypes)**
If a mapping language can specify how a Literal
with optionally a language tag or datatype should be generated.
- **S13: Blank Nodes**
If a mapping language can describe the generation of RDF blank nodes.
- **S14: Named graphs**
If a mapping language can describe the generation 
of an RDF Named Graph to make statements about a set of RDF triples.
- **S15: Collections and containers**
If a mapping language can describe the generation 
of RDFS Collections and RDFS Containers.

## Mapping languages

### Dedicated mapping languages
Dedicated mapping languages are based upon dedicated
mapping language specifications such as R2RML or a custom syntax
such as YAML or JSON, for transforming heterogeneous data sources into RDF.

#### RDF Mapping Language (2013)
RDF Mapping Language ([RML](https://rml.io/specs/rml/))
describes how RDF is generated from heterogeneous data 
by extending the W3C recommendation R2RML (S5) to heterogeneous data sources.
RML introduces a Logical Source which describes
how the input data should be accessed
and referred to using reference formulations,
such as JSONPath for JSON or XQuery for XML data.
Currently, RML supports heterogeneous data sources,
such as relational databases, CSV/TSV, JSON, XML, Web APIs and streams.
RML is backwards compatible with R2RML (S1, S4)
and leverages R2RML's join support (S6), IRI description (S11),
subjects, predicates, objects (S10), named graphs (S14), 
literals with language tags, data types (S12) and blank nodes (S13).
The input data is used directly,
without transforming it into an intermediate format (S7).
RML is aligned with FnO (S2, S4) to describe data transformations
on the input data.
Recently, RML was extended with Logical Target
to describe how and where the generated RDF must be exported to (S3, S4).
RML cannot handle nested data structures (S8),
data structures consisting of multiple data formats (S9),
or collections and containers (S15),
but an approach is proposed to overcome these limitations.

#### xR2RML (2015)
[xR2RML](https://www.i3s.unice.fr/~fmichel/xr2rml_specification_v5.html)
extends R2RML (S1, S5, S10, S11, S12, S13, S14) and RML (S7)
with additional data sources such as NoSQL databases,
nested data structures such as XML or JSON (S8) with multiple data formats,
and collections and containers generation (S15).
xR2RML allows to combine multiple reference formulations
when referring to a data value (S9) which is common among NoSQL databases
where a key-value store may contain XML and JSON data as value.
xR2RML describes how multiple data sources should be joined (S6).
xR2RML also supports nested data structures (S8)
through xR2RML's Nested Term Maps which allows
to describe RDFS collections and containers (S15).
xR2RML describes the RDF Literal's language tag or data type (S12).
xR2RML allows to push down data values from a nested data structure
to make it accessible in lower levels of the nested data structure.
However, xR2RML does not describe where the generated RDF triples
must be exported to (S3, S4), or describe data transformations (S2, S4).

#### D2RML (2018)
D2RML extends R2RML with a Logical Source to define how the data source
should be accessed and additionally support for transformations,
conditions and custom IRI generation functions (S2).
D2RML abstracts the data model to use a column
and row approach instead of using the input data directly (S7).
D2RML supports HTTP Web APIs, CSVs, JSON, and XML data.
D2RML can describe the generation of subjects, predicates, objects (S10),
graphs (S14), blank nodes (S13),
literals with language tags and data types (S12), IRIs (S11),
and join multiple data sources during the schema transformation (S6),
because it extends R2RML (S1).
However, D2RML cannot handle nested data structures (S8),
heterogeneous data formats (S9),
describe the generation of collections and containers (S15),
or describe the output location (S3, S4).

#### Dataset Representation (D-REPR, 2019)
Dataset Representation (D-REPR) (2019)
is a mapping language based upon a custom YAML syntax (S5)
for transforming heterogeneous data into RDF.
D-REPR supports joins (S6) among CSV, XML, JSON, Spreadsheet,
relational and non-relational databases, and NetCDF files (S8).
D-REPR represents all data in a JSON tree based structure
instead of the NRM model used in KR2RML (S7).
D-REPR does not support multi-path expressions when referring to data (S9).
D-REPR fully describes the schema transformation (S1, S10, S11, S12, S13, S14)
and supports data transformations on the input data (S2).
However, the output description, named graphs, RDF collections and containers,
and RDF Literal language tags (S15)
are not specified in the D-REPR mapping rules (S3, S4).

### Repurposed mapping languages
Mapping languages repurposed syntax from existing specifications
such as W3C's SPARQL or W3C's ShEx,
for transforming heterogeneous data sources into RDF.

#### XSPARQL (2009)
[XSPARQL](https://www.w3.org/Submission/xsparql-language-specification/)
is a mapping language that combines XQuery, JSON-LD and R2RML
with the W3C recommended SPARQL query language (S5)
for transforming XML data, JSON data, and relational databasedata into RDF (S1).
XSPARQL not only transforms XML and relational databases into RDF (uplifting),
but also the other way around (lowering).
XSPARQL inherits all the features from SPARQL (S2, S10, S11, S12, S13, S14).
XSPARQL supports joining of nested hierarchy data sources
by building on top of SPARQL without an intermediate format (S6, S7, S8).
XSPARQL does not support multi-path expression (S9),
or specifies to where the generated triples are exported to (S3, S4).
Built-in and custom data transformations
are applied using SPARQL Functions (S2).
XSPARQL supports relational databases and XML, RDF, or JSON files.

#### SPARQL-Generate (2017)
SPARQL-Generate extends the W3C recommended SPARQL query language (S5)
to transform heterogeneous data into RDF.
SPARQL-Generate supports streaming and binary data sources
such as [HDT](https://www.rdfhdt.org),
[WebSockets](https://html.spec.whatwg.org/multipage/web-sockets.html#),
and [Kafka](https://kafka.apache.org/),
on top of the data sources supported by RML:
relational databases, XML, JSON, and CSV/TSV data sources.
SPARQL-Generate can be combined with SPARQL Template Transformation Language
which can transform RDF graphs into structured text.
SPARQL-Generate uses the input data directly
during its schema transformation (S7)
and can leverage SPARQL functions to execute data transformations
when applying its schema transformation (S2).
SPARQL-Generate relies on SPARQL to describe the schema transformation (S1),
to join heterogeneous data (S6), handle nested hierarchical data (S8),
generation of subjects, predicates, objects (S10), IRIs (S11),
named graphs (S14), literals with language tags and data types (S12),
and blank nodes (S13), collections and containers (S15).
However, SPARQL-Generate does not specify
how the RDF must be exported (S3, S4) or how to handle multi-paths (S9).

#### Shape Expressions Mapping Language (ShExML, 2020)
Shape Expressions Mapping Language
([ShExML](http://shexml.herminiogarcia.com/spec/))
is a mapping language based upon W3C's Shape Expressions (ShEx) (S5)
to transform heterogeneous data into RDF.
ShExML supports relational databases, CSV, XML and JSON files.
ShExML describes joins between data sources (S6).
It does not use an intermediate representation of the input data (S7)
and can handle nested data structures through its nested iterators (S8).
ShExML describes how subjects, predicates, objects (S10),graphs (S14),
RDF's literal language tags, data types (S12).
IRIs (S11), and blank nodes (S13) are generated.
ShExML describes the schema transformation (S1),
but it cannot describe collections or containers (S15, S4).
ShExML does not describe to where the generated RDF is exported to (S3, S4),
or how to handle multi-paths (S9).
ShExML does not describe data transformations
to apply on the heterogeneous data (S2, S4).

#### Facade-X (2021)
Facade-X overrides SPARQL's `SERVICE` operator (S5)
to generate RDF from heterogeneous data sources.
It supports JSON, CSV, HTML, XML, spreadsheets, binary data
and embedded data such as EXIF in images.
Facade-X uses the input data directly as
it follows the approach of W3C's Direct Mapping recommendation (S7).
As SPARQL-Generate, it relies on SPARQL for joins (S6) and functions (S2),
nested data structures (S8), RDF generation (S10, S11, S12, S13, S14),
and describes the schema transformation (S1).
However, Facade-X does not specify how the RDF should be exported (S3, S4),
or how to handle multi-paths (S9).

### Tables

| Mapping Language | S1                 | S2                 | S3                 | S4                 | S5                 | S6                 | S7                 | S8                 | S9                 | S10                | S11                | S12                 | S13                | S14                | S15                |
|------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|---------------------|--------------------|--------------------|--------------------|
| RML              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: |                    |
| xR2RML           | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| D2RML            | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: |                    |
| D-REPR           | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:* | :heavy_check_mark: |                    |                    |
| XSPARQL          | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| SPARQL-Generate  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| ShExML           | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: |                    |
| Facade-X         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
