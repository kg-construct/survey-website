---
layout: page
title: Characteristics
permalink: /characteristics/
---

## Characteristics

### Schema transformations

We created a list of characteristics for schema transformations and divided
them in 3 categories:

1. Declarative transformation description
2. Data processing and composition
3. Coverage of the RDF(S) specification

#### Declarative transformation description
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

#### Data processing and composition
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

#### Coverage of the RDF(S) specification
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

### Data transformations
We derived a set of characteristics and divided them in 2 categories:

1. Description
2. Alignment

#### Description
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

#### Alignment
How the data transformations are aligned with mapping languages
and if they can be used standalone or not.

- **F4: Independence**
The data transformation description depends 
on certain mapping languages or implementations.
- **F5: Integration with mapping languages**
How mapping languages integrate the data transformations,
interact with them and describe them in the mapping rules.

### Tools

We compiled a list of common characteristics
which differ between implementations.
We divided them in 4 categories:

1. Input/Output
2. Data transformation
3. Implementation
4. Materialization-specific characteristics

The first 3 categories are shared with the virtualization tools.

### Input/Output

These characteristics are related to the input data,
output data and which schema and data transformations
are used by each implementation:

- **T1: Input Data**:
Which data sources are accessible and data can be retrieved from.
- **T2: Input Data formats**:
Which data formats are supported for the input data.
- **T3: Output Data**:
How the generated knowledge graphs are exported
to a specific location in a certain format.
- **T4: Output Data formats**:
Which data formats are supported for the output data.
- **T5: Schema transformation language**: 
Which mapping language(s) are supported by an implementation.

### Data transformation

Each implementation may have support for data transformations
besides schema transformations.
The following characteristics are used to validate how
and which data transformations are supported by a given implementation:

- **T6: Data transformation language**:
Which data transformation language(s) are supported by an implementation.
- **T7: Applicability**:
Where during the execution process does 
the implementation apply data transformations to the data:
(i) pre-processing, during the input data retrieval,
(ii) during schema transformation into RDF,
(iii) post-processing, after the schema transformation?

### Implementation

Each implementation has specific characteristics
regarding the implementation itself such as
the programming language or how it integrates with other implementations.

- **T8: Programming language**: 
The programming language of the implementation.
- **T9: Integration**:
How a implementation can be integrated with other implementations.
- **T10: Interface**:
How a implementation can be used.
- **T11: License**:
The license of an implementation.
- **T12: Repository**:
The location of the implementation's code repository, if available.

### Materialization-specific characteristics
We studied each materialization implementation and created
a list of characteristics specific for materialization which
greatly differ between these implementations:

- **T13a: Optimizations**
Which optimizations are applied to the materialization process?
- **T13b: Scaling**
Which approaches are used to scale the materialization process?

### Virtualization-specific characteristics

We studied each virtualization implementation
and created a list of characteristics which are specific
for virtualization tools:

- **T13a: Features**
Each implementation has its own set 
of features regarding virtual access to its heterogeneous data sources.
Which features are applied to the virtualization process?
- **T13b: Federation**
Virtualization systems access multiple data sources typically using federation.
Does the implementation support federation or not?
