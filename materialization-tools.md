---
layout: page
title: Materialization Tools
permalink: /materialization-tools/
---

## Characteristics

We compiled a list of common characteristics
which differ between implementations:

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

## Tools for dedicated mapping languages

### Linked Stream Middleware (2012)
Linked Stream Middleware (LSM) focuses on sensor data transformation
from relational databases and other data sources in a streaming fashion (T13b).
LSM leverages R2RML and D2R mapping languages (T5)
for accessing relational databases while a wrapper is required
to generate RDF from other data sources (T1, T2).
Data sources can either push messages onto LSM's message queue
for processing or LSM pulls data from data sources
through an Hadoop based cluster for generating RDF (T13a).
RDF graphs can be stored in a triple store or queried through
LSM's query interface with SPARQL or CQELS continuously
or in a pulling fashion (T3, T4).
LSM does not support data transformations,
only generating RDF from heterogeneous data sources (T6, T7).
LSM was publicly deployed, but this deployment is not available anymore.
LSM's Java source code and license are not publicly available,
therefore we cannot all characteristics (T8, T9, T10, T11, T12).

#### Morph-RDB v3.12.5 (2014)
Morph-RDB, previously known as ODEMapster,
implements the R2RML mapping language (T5) to generate RDF graphs
from SQL query results of relational databases and CSV files (T1, T2).
MorphRDB applies optimization techniques such as self-join and
subquery elimination when querying the relational databases
for generating RDF (T13a, T13b).
The RDF graphs are exported to a file, either in N-Triples,
Turtle, N3, or RDF/XML, specified in Morph-RDB's configuration file (T3, T4).
MorphRDB can also translate SPARQL queries into SQL queries (Section 5.4).
Morph-RDB is written in Scala (T8)
and does not support data transformations (T6, T7).
Morph-RDB is accessible as a CLI implementation
and provides a Docker image (T9, T10).
Morph-RDB is released on Github (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/oeg-upm/morph-rdb
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** :  08/05/2021

### RMLMapper v4.12.0 (2014)
RMLMapper is a Java implementation of an RML processor with support
for FnO functions and RML's Logical Target.
RMLMapper can also generate provenance metadata during
the schema and data transformation if enabled.
RMLProcessor, RMLMapper's predecessor,
was forked and extended with FunUL functions to provide data transformations.
The RMLMapper supports RML for schema transformations (T5),
FnO for data transformations (T6), and generation of metadata during execution.
It first retrieves all data, applies joins if needed,
executes FnO functions and generates RDF (T13a, T13b).
Thus, FnO functions are executed as part of the schema transformation (T7).
The RDF graphs are exported to the specified RML's Logical Targets (T3).
Currently, the RMLMapper supports N-Triples, N-Quads, Turtle, N3, RDF/XML,
JSON-LD, HDT, Trix and TriG as RDF output formats (T4).
It supports relational databases, SPARQL endpoints, files,
and data on the Web (T1).
The RMLMapper generates RDF graphs from SQL query results,
W3C Web of Things Web APIs, SPARQL query results,
XLSX, ODS, CSV, TSV, JSON and XML files (T2).
It exports the RDF graphs in N-Quads, Turtle, TriG, TriX, JSON-LD
and HDT to files, VoID datasets, and SPARQL UPDATE queries to SPARQL endpoints.
RMLMapper is available as a CLI implementation, a Docker image,
and a Java library (T9, T10).
The RMLMapper is released under MIT license (T11) on Github (T12).

**Source code** : https://github.com/RMLio/rmlmapper-java
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 11/03/2022

### Karma-Web v2.5 (2015)
Karma-Web implements KR2RML (T5) for transforming heterogeneous data sources
into RDF graphs through an intermediate format (Nested Relational Model).
Karma-Web transforms any heterogeneous data into NRM format
and applies joins if needed.
Afterwards, the transformation to RDF with KR2RML mapping rules
is applied (T13a, T13b).
Karma-Web supports KR2RML's data transformations written in Python (T6)
which are excuted during the schema transformation (T7).
Karma-Web is written in Java (T8)
and is integrated in Karma-Web's CLI implementation (T9, T10).
Karma-Web can access relational databases
and files (T1) and transform
SQL tables, CSV, TSV, JSON and XML files to RDF (T2).
The RDF is exported to a file specified as a CLI parameter (T3).
Karma-Web supports JSON-LD and N3 as RDF output formats (T4).
Karma-Web is publicly available (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/usc-isi-i2/Web-Karma
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 27/02/2022

### Morph-xR2RML v1.3.1 (2015)
Morph-xR2RML extends Morph-RDB (T13a, T13b) with support
for xR2RML mapping language (T5).
Morph-xR2RML is written in Scala (T8)
and supports relational and NoSQL databases, and files (T1).
Morph-xR2RML can transform SQL query results, NoSQL query results,
JSON, XML, CSV, and TSV files to RDF (T2).
Morph-xR2RML retrieves the data, applies joins if needed and generates RDF,
including RDFS Collections and RDFS Containers (T13b).
Morph-xR2RML does not provide data transformations,
such as FnO or FunUL (T6, T7).
Morph-xR2RML is configured with a configuration file and
provides a CLI implementation to export the RDF graphs
to a file or a SPARQL endpoint (T3, T6, T9, T10).
Morph-xR2RML supports N-Triples, Turtle, N3, RDF/XML,
and JSON-LD as RDF output format.
Morph-xR2RML is available on Github (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/frmichel/morph-xr2rml
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 13/01/2022

### TripleWave v2.1.1 (2016)
TripleWave generates RDF graphs in a streaming fashion (T13b)
using R2RML mapping rules (T5).
TripleWave consists of wrappers to access data sources
and currently supports JSON files (T1, T2).
R2RML mapping rules are only used to generate RDF from the retrieved data.
TripleWave scales vertically by the number of CPU cores (T13a).
TripleWave does not support data transformation,
but they can be hardcoded into the data access wrappers (T6).
Because of that, any data transformations is executed as a pre-processing step
when accessing the input data (T7).
It is configured with a configuration file to export
its RDF stream in JSON-LD format (T4) to a file
or publish it as a WebSocket or MQTT stream (T3).
TripleWave is written in NodeJS (T8) and
it is available under Apache License 2.0 (T11)
on Github (T12) as a CLI implementation (T9, T10).

**Source code** : https://github.com/streamreasoning/TripleWave
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 10/07/2019

### GeoTriples v1.2.1 (2018)
GeoTriples implements GeoTriples's GeoSPARQL extensions to RML (T5).
It is written in Java (T8) availablei
as a CLI implementation and webapp (T9, T10).
GeoTriples can access relational databases and files
and generates RDF from SQL query results, CSV, XML, JSON,
GeoJSON, KML, and shapefiles (T1, T2).
It implements geospatial transformations from GeoSPARQ and stSPARQL 
to handle geospatial data (T6).
These transformations are executed together with the schema transformation (T7).
It first fetches all geospatial data, applies transformations
and joins if needed and generates RDF graphs to a file (T13a, T13b),
RML's Logical Target is not supported yet (T3),
but it can export RDF in Turtle or RDF/XML format (T4).
GeoTriples is available as a CLI implementation or webapp (T9, T10)
and it is released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/LinkedEOData/GeoTriples
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 10/09/2021

### D2RML processor (2018)
D2RML processor implements D2RML mapping language (T5)
with support for data transformations (T6), conditions
and RDF generation from heterogeneous data.
D2RML processor's source code is not publicly available,
but can be used as a web service (T9, T10).
Since the source code is not publicly available (T12),
we cannot study or discuss characteristics T1, T2, T3, T4, T8, T13a, or T13b.

### RDF-Gen (2018)
RDF-Gen generates RDF in a streaming fashion
from multiple sources described by a custom syntax (T5).
RDF-Gen can access relational databases
and files in CSV, XML and JSON format (T1, T2).
RDF-Gen first transforms data of a data source into records,
these records are later on transformed into RDF
using a centralized cluster (T13a, T13b).
The authors claim that RDF-Gen support functions for data transformation,
but we have not been able to verify this
as the source is not publicly available (T6, T7).
RDF-Gen exports RDF in N-Triples or Turtle to a file specified
in its configuration file (T3, T4).
RDF-Gen is available as compiled Java Jar CLI implementation (T9, T10, T12)
under Creative Commons Attribution-NonCommercialNoDerivatives 4.0 International License (T11).

**Source code** : https://github.com/datAcron-project/RDF-Gen
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 18/07/2019

### RMLStreamer v2.1.1 (2019)
The RMLStreamer is RMLMapper's counterpart (section 5.3)
for generating RDF in a streaming fashion (T13b) using RML mapping rules (T5).
It can access files in CSV, JSON or XML format,
and Kafka, MQTT, TCP streams (T1, T2).
The RMLStreamer uses Apache Flink to scale horizontally
and vertically depending on the number of streams and input rate
when generating RDF.
Moreover, the RMLStreamer also leverages Apache Flink
for optimizing memory usage, high-availability, and fault-tolerance (T13b).
It leverages FnO to apply data transformations
during the schema transformation (T6, T7), and RML's Logical Target (T3).
The RMLStreamer can export RDF graphs in JSON-LD, N-Triples,
or N-Quads format (T4).
It is written in Scala (T8)
and available (T12) under MIT license (T11)
as a CLI implementation and Docker image (T9, T10).

**Source code** : https://github.com/RMLio/RMLStreamer
<br>
**Last accessed** : 23/03/2022
<br>
**Date last commit on default branch** : 25/02/2022

### MapSDI v1.0 (2019)
MapSDI preprocesses heterogeneous data to remove duplicates
and unnecessary data by exploiting RML mapping rules (T5),
and applies relational algebra to improve the execution of the mapping rules.
MapSDI leverages existing RML processors to execute the mapping rules,
therefore it inherits their characteristics (T13a, T13b, T3, T4, T5, T6, T7).
MapSDI can preprocess files in CSV format (T1, T2),
is written in Python (T8) and available (T12)
as a CLI implementation (T9, T10) under Apache License 2.0 (T11).

**Source code** : https://github.com/SDM-TIB/MapSDI
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 25/10/2021

### D-REPR v2.9.3 (2019)
D-REPR is a Python and Rust (T8) based mapping language processor
which generates RDF using the D-REPR mapping language (T5).
D-REPR can access CSV, JSON, XML, Spreadsheet, NetCDF files,
and relational & non-relational databases (T1, T2).
It applies data transformation with built-in or custom functions (T6).
D-REPR retrieves the data, infers classes and necessary joins,
applies pre-processing data transformations on the input data (T7),
and generates RDF (T13a, T13b).
D-REPR can export its RDF to a file as Turtle or a custom JSON format (T3, T4).
DREPR is available on Github (T12) under MIT license
as a CLI implementation and webapp (T9, T10, T11).

**Source code** : https://github.com/usc-isi-i2/d-repr/
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 14/06/2021

### RocketRML v1.11.3 (2019)
RocketRML is a NodeJS implementation (T8) of an RML processor (T5)
with FnO  support for data transformations (T6).
It can use two different XML parsers for performance
or XML specification compliance reasons (T13a) and supports files (T1)
in JSON, XML, or CSV format (T2).
RocketRML retrieves all data, applies FnO functions,
joins if necessary and generates RDF (T13b).
It executes the data transformation together
with the schema transformation (T7).
RDF is outputted to a file as RocketRML
does not support RML's Logical Target yet to specify how the RDF graphs
should be exported to one or multiple targets (T3).
It is available as a NodeJS package on NPM, CLI implementation,
Docker image, or through a web application (T9, T10).
RocketRML is released (T12) under
Creative Commons AttributionNonCommercial-ShareAlike 4.0 International
license (T11).

**Source code** : https://github.com/semantifyit/RocketRML
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 30/11/2021

### SDM-RDFizer v4.0 (2020)
SDM-RDFizer is a Python implementation (T8) of an RML processori
with a focus on efficient execution of RML mapping rules (T5).
SDM-RDFizer uses optimized data structures such as indexes,
relational algebra operators and multi-threading to improve the execution.
It also avoid generating duplicate RDF
and executing duplicate joins between data (T13a).
SDM-RDFizer can access files and relational databases (T1).
SDM-RDFizer can transform SQL query results,
CSV, TSV, JSON, and XML files to RDF (T2).
It does not support data transformations with FnO,
but it relies on FunMap to achieve this (T6). 
This way, the SDM-RDFizer can focus
only on the schema transformation and optimize it.
SDM-RDFizer incrementally parses the input data,
applies joins, and generates RDF graphs (T13b).
RDF graphs are exported to a file (T3).
SDM-RDFizer is available as a CLI implementation,
Docker container or a Python module on the Python Package Index (T9, T10)
and released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/SDM-TIB/SDM-RDFizer
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 18/03/2022

### FunMap v1.0 (2020)
FunMap is a Python-based (T8) FnO function processor
which pre-processes FnO functions in RML mapping rules (T5, T7).
This way, FunMap allows to use mapping rules containing RML and FnO
to be executed on RML processors which does not support
any FnO functions such as the SDM-RDFizer.
Moreover, it optimizes the function execution by avoiding
executing a function multiple times
when the function yields the same result (T6, T7, T13a).
FunMap leverages existing RML processors to execute
the mapping rules, therefore it inherits
their characteristics (T1, T2, T3, T13b).
FunMap is available as a CLI implementation (T9, T10)
and released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/SDM-TIB/FunMap
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 09/01/2021

### Chimera v2.2 (2020)
Chimera generates RDF graphs (uplifting) through RML mapping rules (T5)
and transforms RDF into various data formats (lowering)
with Apache Velocity Templates (T5).
Chimera uses uplifting for creating an RDF graph as intermediate format.
Afterwards, lowering is applied to export the data in various non-RDF formats.
This approach is common in public transportation use cases
where it is desired to publish the same in multiple formats.
Chimera leverages and extends the RMLMapper.
It improves RMLMapper's memory utilization by not caching subjects
and data records for mapping rules without joins,
executing mapping rules by data source, and incremental batches.
Chimera's optimizations differs from MapSDI and FunMap
because MapSDI and FunMap optimize the mapping rules
while Chimera optimizes the implementation to execute these mapping rules.
Chimera also adds multi-thread execution of mapping rules
to increase the RMLMapper's throughput and
access to remote RDF stores for storing the generated RDF graphs (T13a, T13b).
Since Chimera re-uses the RMLMapper,
it inherits its characteristics (T1, T2, T3, T4, T5, T6, T7, T8),
but it uses an older version of the RMLMapper
which did not implement RML's Logical Target
and W3C Web of Things for Web APIs yet.
Chimera is released (T12) as a CLI implementation
under Apache License 2.0 and the RMLMapper extension
under MIT license (T9, T10, T11).

**Source code** : https://github.com/cefriel/chimera
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 01/10/2021


## Tools for query-language-driven mapping languages

### SPARQL-Generate v2.0.9 (2017)
SPARQL-Generate is the reference implementation
of SPARQL-Generate mapping language (T5) on top of Apache Jena in Java (T8).
SPARQL-Generate leverages Apache Jena and
its SPARQL implementation with SPARQL-Generate's extensions
to process the SPARQL-Generate query.
SPARQL-Generate supports files, HTTP Web APIs, and streams (T1),
as well as joins and SPARQL Functions to apply data transformations (T6).
It can generate RDF from WebSocket streams, MQTT streams, HTTP Web APIs,
plain text with regular expressions, HTML, CSV, TSV, XML, JSON,
GeoJSON, CBOR, and HDT files into RDF (T2).
SPARQL-Generate fetches all data,
applies SPARQL Functions and joins if applicable,
generates RDF graphs (T13a, T13b) and exports them to a file (T3).
SPARQL Functions are executed by the underlying SPARQL engine together
with the schema transformation (T7).
SPARQL-Generate is available as a CLI implementation, a Java library,
a webapp, and inside the Sublime Text editor (T9, T10).
It is released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/sparql-generate/sparql-generate
<br>
**Last accessed** : 10/11/2021

### SPARQL-Anything v0.4.1 (2021)
SPARQL-Anything implements Facade-X's SPARQL SERVICE operator overriding (T5)
for generating RDF from heterogeneous data.
It can access files (T1) in CSV, JSON, HMTL, XML, RDF, and plain text formats.
SPARQL-Anything can also access data in archives, spreadsheets,
images, and encoded metadata data, e.g., EXIF data in images (T2).
It is implemented on top of Apache Jena SPARQL engine in Java (T8).
Since SPARQL-Anything re-uses an existing SPARQL engine,
support for data transformations depends on the underlying engine (T6).
Thus, the SPARQL Functions are executed together
with the schema transformation (T7).
SPARQL-Anything retrieves all data in memory
and transforms it to RDF (T13a, T13b).
The generated RDF graphs are exported to a file
or are available through a Fuseki SPARQL endpoint (T3).
SPARQL-Anything is available as a CLI implementation
or a SPARQL endpoint (T9, T10)
and released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/SPARQL-Anything/sparql.anything
<br>
**Last accessed** : 23/03/2022
<br>
**Date last commit on default branch** : 18/03/2022

## Tools for constraint-driven mapping languages

### ShExML v0.2.6 (2020)
ShExML is the reference implementation of the ShExML mapping language (T5)
in Scala (T8).
It generates RDF using ShExML mapping rules.
ShExML can also generate the ShEx validation shapes
and translate ShExML mapping rules into RML mapping rules (T6).
ShExML can access HTTP web APIs, files in XML, JSON, CSV, or TSV format,
and relational databases (T1, T2).
ShExML retrieves the data, applies joins if needed
and generates RDF graphs (T13a, T13b) which are exported to a file (T3).
ShExML does not provide any data transformations such as FnO (T6, T7).
ShExML is available as a CLI implementation, Java library,
and a webapp (T9, T10) and released on Github (T12) under the MIT license (T1) 

**Source code** : https://github.com/herminiogg/ShExML
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** 28/02/2022


## Tables

| T1: Datasource          | Karma-Web          | Morph-RDB          | Morph-xR2RML       | TripleWave         | GeoTriples         | RMLMapper          | RMLStreamer        | RDF-Gen            | MapSDI             | RocketRML          | SDM-RDFizer        | D-REPR             | FunMap             | Chimera            | SPARQL-Generate    | SPARGL-Anything    | ShExML             |
|-------------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|
| File                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| SQL RDB                 | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |
| NoSQL DB                |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |
| Kafka stream            |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| WebSocket stream        |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| MQTT stream             |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| TCP stream              |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| SPARQL endpoint         |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |
| Web API                 |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    | :heavy_check_mark: |
| Apache Hadoop           |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| T2: Data format         |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| CSV format              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| JSON format             | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| XML format              | :heavy_check_mark: |                    | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| TSV format              | :heavy_check_mark: |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    |                    |                    |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |
| ODS format              |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |
| XLSX format             |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |
| GeoJSON format          |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| KML format              |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| Shapefiles              |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| SQL query               | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |
| NoSQL query             |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |
| SPARQL query            |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |
| CBOR format             |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| HDT format              |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| RDF format              |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |
| plain text              |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: |                    |
| HTML format             |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |
| Archives                |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |
| EXIF encoded            |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |
| NetCDF                  |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    | :heavy_check_mark: |                    |
| T3: Output Data         |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| File                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Kafka stream            |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| WebSocket stream        |                    |                    |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| MQTT stream             |                    |                    |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| TCP stream              |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| SPARQL endpoint         |                    |                    |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |
| Web API                 |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    |
| T4: Output Data formats |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |                    |
| N-Triples               |                    | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :start:            |                    | :heavy_check_mark: |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| N-Quads                 |                    |                    |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :start:            | :heavy_check_mark: |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Turtle                  |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :start:            |                    | :heavy_check_mark: | :heavy_check_mark: | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| N3                      | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                    |                    | :start:            |                    |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| RDF/XML                 |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :start:            |                    |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| RDF/JSON                |                    |                    |                    |                    |                    |                    |                    |                    | :start:            |                    |                    |                    | :start:            |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| JSON-LD                 | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: |                    | :start:            | :heavy_check_mark: |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| HDT                     |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    | :start:            |                    |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: |                    |                    |
| TriX                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    | :start:            |                    |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| TriG                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                    | :start:            |                    |                    |                    | :start:            | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| D-REPR JSON             |                    |                    |                    |                    |                    |                    |                    |                    | :start:            |                    |                    | :heavy_check_mark: | :start:            |                    |                    |                    |                    |


| Materialization implementation | T5                             | T6                             | T7                                       | T8            | T9 and<br>T10                                  | T11          | T13a                                                                           | T13b                                  |
| ------------------------------ | ------------------------------ | ------------------------------ | ---------------------------------------- | ------------- | ---------------------------------------------- | ------------ | ------------------------------------------------------------------------------ | ------------------------------------- |
| Karma-Web                      | KR2RML                         | Python code snippets           | together, during schema transformation   | Python        | CLI                                            | Apache-2.0   | None                                                                           | ETL                                   |
| Morph-RDB                      | R2RML                          | No                             | NA                                       | Scala         | CLI                                            | Apache-2.0   | Self-join and subquery elimination                                             | ETL                                   |
| Morph-xR2RML                   | xR2RML                         | No                             | NA                                       | Scala         | CLI, SPARQL endpoint                           | Apache-2.0   | Inherited from Morph-RDB                                                       | ETL                                   |
| TripleWave                     | R2RML                          | Hardcoded                      | together, pre-processing of input data   | NodeJS        | CLI                                            | Apache-2.0   | Vertical scaling                                                               | Streaming                             |
| GeoTriples                     | RML with GeoTriples extensions | GeoSPARQL & stSPARQL functions | together, during schema transformation   | Java          | CLI, webapp                                    | Apache-2.0   | None                                                                           | ETL                                   |
| RMLMapper                      | RML                            | FnO                            | together, during schema transformation   | Java          | CLI, library, Docker                           | MIT          | None                                                                           | ETL                                   |
| RMLStreamer                    | RML                            | FnO                            | together, during schema transformation   | Scala         | CLI, Docker                                    | MIT          | Horizontal and vertical scaling                                                | Streaming                             |
| MapSDI                         | RML                            | NA                             | NA                                       | Python        | CLI                                            | Apache-2.0   | Removal of unused and duplicate data, relational algebra                       | Inherited from mapping rule processor |
| RocketRML                      | RML                            | FnO                            | together, during schema transformation   | NodeJS        | CLI, library, Docker, webapp                   | CC-BY-SA-4.0 | Multiple XML parsers                                                           | ETL                                   |
| SDM-RDFizer                    | RML                            | No                             | NA                                       | Python        | CLI, library, Docker                           | Apache-2.0   | Removal of unused and duplicate data, relational algebra, memory optimizations | Batch processing                      |
| D-REPR                         | D-REPR                         | Python code snippets           | together, pre-processing of input data   | Python & Rust | CLI, webapp, Docker                            | MIT          | Execution plans, core processing in native programming language                | ETL                                   |
| FunMap                         | RML                            | FnO                            | separately, before schema transformation | Python        | CLI                                            | Apache-2.0   | Function preprocessing, vertical scaling                                       | Inherited from mapping rule processor |
| Chimera                        | RML                            | FnO                            | together, during schema transformation   | Java          | CLI                                            | Apache-2.0   | Mapping rules without joins optimizations, vertical scaling                    | Batch processing                      |
| SPARQL-Generate                | SPARQL-Generate                | SPARQL Functions               | together, during schema transformation   | Java          | CLI, library, webapp, Sublime Text integration | Apache-2.0   | None                                                                           | ETL                                   |
| SPARQL-Anything                | Facade-X                       | SPARQL Functions               | together, during schema transformation   | Java          | CLI, SPARQL endpoint                           | Apache-2.0   | None                                                                           | ETL                                   |
| ShExML                         | ShExML                         | No                             | NA                                       | Scala         | CLI, library, webapp                           | MIT          | None                                                                           | ETL                                   |
