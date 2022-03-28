---
layout: page
title: Virtualization Tools
permalink: /virtualization-tools/
---

#### Morph-RDB extension (2010)
Morph-RDB extension enables Ontology-Based Data Access to streaming data sourcesby extending R2O mapping rules with streaming support (S2O mapping rules) (T5) and querying these data sources with SPARQLStream (T13a).
Morph-RDB’s SPARQLStream is inspired by C-SPARQL and SNEEql but with support for streaming windows and SPARQL 1.1 aggregates.
Morph-RDB transforms SPARQLStream queries into SNEE queries (SNEEql), the SNEE engine executes the query on the data sources.
Morph-RDB generates the triples to answer the SPARQLStream query and returns them (T3, T4).
The S2O mappings are used to transform the SNEE query results back into RDF (T4). Morph-RDB supports files in CSV format, SQL query results of relational databases and sensor streams (T1, T2).
Morph-RDB does not support any data transformations (T6) or federation (T13b).
and is written in Scala (T8). Morph-RDB is accessible as a CLI implementation and provides a Docker image (T9, T10).
MorphRDB’s extension is released38 (T12) under the Apache License 2.0 (T11).

**Source code** : https://github.com/oeg-upm/morph-rdb
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** :  08/05/2021


#### Ontop v4.1.1 (2013)
Ontop virtualizes access to relational SQL databases and OpenGIS by translating SPARQL queries into SQL queries.
It leverages R2RML mapping rules or Ontop Mapping Language (T5) to perform this translation, and extensions for accessing OpenGIS data (T1, T2).
Generated triples are returned as SPARQL query results (T3, T4).
Ontop does not support data transformations (T6), advanced SPARQL features such as property path, existential queries with NOT EXIST, or basic query federation with SERVICE (T13b).
However, efforts such as [Denodo](https://ontop-vkg.org/tutorial/federation/denodo/), [Dremio](https://ontop-vkg.org/tutorial/federation/dremio/), or [Teiid](https://ontop-vkg.org/tutorial/federation/teiid/) extend Ontop with federation support (T13b).
Ontop uses an Intermediate Query language (T13a) with well known SQL optimizations, such as (i) redundant join elimination and pushing down joins to the datalevel, and (ii) virtualization-specific optimizations for SQL derived from the OPTIONAL and MINUS SPARQL constructs (T10e).
Ontop translates SPARQL aggregates to SQL aggregates for the database engine to perform the aggregation (T13a).
Ontop supports ontological entailment by relying on a mapping saturation approach: in an offline phase, the mapping rules are saturated with the ontology rules, meaning additional mapping rules are generated for entailed triples.
In previous generations of Ontop, ontological entailment was supported with a query rewriting approach using the PerfectRef algorithm, but that was abandoned as mapping saturation proved more efficient.
Ontop supports entailment for RDFS and OWL 2 QL, and has experimental support for entailment with SWRL rules (T13a).
Ontop is available as a CLI implementation and Docker image (T9, T10).
Ontop is written in Java (T8) and released42 (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/ontop/ontop
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 21/03/2022

#### Optique (2013)
Optique leverages R2RML mapping rules  (T5) to access data such as relational databases, triple stores, temporal databases, data streams, etc.
Optique uses STARQL as query language for streaming data which is translated into SQL queries (T1, T2).
These SQL queries are executed on Optique’s DSMS ExaStream.
Optique’s DSMS allows custom data transformations using User Defined Functions (T6) which are leveraged in Optique to access external data sources, windowing, and data mining.
Optique is not publicly available, therefore we cannot evaluate characteristics T7, T9, T10, T11, T12, T13a, and T13b.


#### XGSN v2.0.1 (2014)
XGSN leverages Global Sensor Networks (GSN) middleware to provide virtualization over Internet of Things sensors using the W3C recommended SSN ontology (T5).
XGSN uses wrappers to interface with sensors such as UDP, serial, HTTP, MQTT, etc. (T1, T2, T6).
Data transformations are applied in the data wrappers when accessing the input data (T7).
XGSN configures each sensor using a custom XML document to specify the wrapper, sampling rate, storage size, and which sensor values to expose through the SSN ontology.
While XGSN can access heterogeneous data from various sensors, it is limited to sensor data only.
XGSN allows to use different RDF stream processors (T13a) – such as CQELS – which provide a SPARQL interface to access the RDF graphs (T3, T4).
XGSN does not support federation (T13b).
XGSN is written in Java (T8) as a CLI implementation and can be accessed through a webapp and an API (T9, T10).
XGSN is available on Github (T12) under the GNU General Public License v3.0 (T11).

**Source code** : https://github.com/LSIR/gsn
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 12/03/2017

#### Morph-RDB v3.12.5 (2014)
Morph-RDB – also discussed in section 5.3 as materialization implementation – supports virtualization for relational databases such as MySQLPostgresSQL, H2, and MonetDB or files in CSV format (T1, T2) through R2RML mapping rules (T5).
Morph-RDB translates unions, filters and aggregation from SPARQL to SQL to reduce the client-side processing (T13a).
MorphRDB applies two types of well-known optimizations (T13a) on SQL queries: (i) self-join elimination, and (ii) subquery elimination.
Morph-RDB does not use an intermediate query language, nor does it supports data transformations (T6, T7), ontology entailment (T13a), and federation (T13b).
MorphRDB is accessible as a CLI implementation written in Scala (T8) and provides a Docker image (T9, T10).
Morph-RDB is released (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/oeg-upm/morph-rdb
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 08/05/2021

#### Morph-xR2RML v1.3.1 (2015)
Morph-xR2RML, also discussed in Section 5.3 as ETL implementation, is a fork or Morph-RDB which translates SPARQL queries into SQL queries and MongoDB queries using xR2RML mapping rules (T1, T2, T5, T13a). Morph-xR2RML does not
support data transformations (T6) and not all operators of SPARQL such as joins and some filters, therefore the query is translated in two steps: (i) an abstract query is generated from the SPARQL query using the xR2RML mapping rules.
(ii) the abstract query is translated into MongoDB queries.
Untranslated parts of the query are processed by xR2RML client-side. 
Morph-xR2RML provides a CLI implementation written in Scala (T8) or as a SPARQL endpoint (T9, T10) and is available (T12) under Apache License 2.0 (T11).

**Source code** : https://github.com/frmichel/morph-xr2rml
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 13/01/2022

#### SparqlMap-M v0.7.4 (2016)
SparqlMap-M is an extension of SparqlMap to provide virtualization over CSV files, relational databases, and non-relational databases using R2RML mapping rules (T5).
SparqlMap-M extends R2RML to support data transformations and conditions (T6) which are executed during the schema transformation (T7).
SparqlMap-M analyses SPARQL queries to reduce the R2RML mappings to the minimum for answering the query and translates to SQL to execute the query on the the database engine (T13a).
SparqlMap-M does not implement support for SPARQL Federated Queries (T13b).
SparqlMap-M is written in Java (T8) and available as a CLI implementation or SPARQL endpoint on Github without a license (T9, T10, T11, T12).

**Source code** : https://github.com/tomatophantastico/sparqlmap
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 31/08/2017

#### Morph-streams++ v1.0.10 (2016)
Morph-streams++ is the successor of the extended Morph-RDB and leverages SPARQLStream queries.
Morph-streams++ uses existing Distributed Stream Management Systems (DSMS) to execute SPARQLStream queries with R2RML mapping rules (T5).
The SPARQLStream queries are first translated into queries supported by the underlying DSMS and its results are translated into RDF with R2RML mapping rules (T13a).
Generated RDF graphs are returned as SPARQLStream query results (T3, T4).
Supported data sources and formats in Morphstreams++ depend on the underlying DSM: currently the [Esper](http://www.espertech.com/esper) and Global Sensors Network (GSN) (T1, T2) are supported by Morph-streams++.
Morph-streams++ does not support any data transformations (T6, T7), or federation (T13b).
Morph-streams++ is written in Scala (T8) and released (T12) as a CLI implementation without license (T9, T10, T11).

**Source code** : https://github.com/jpcik/morph-streams
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** :  28/09/2016

#### Squerall v0.2 (2019)
Squerall answers SPARQL queries over heterogeneous data sources that are mapped to RDF with RML (T5) and FnO functions (T6).
Squerall leverages the distributed data processing systems Spark or Presto: both systems use an internal tabular data format into which different data sources can be (virtually) integrated.
Spark and Presto allow the manipulation of multiple heterogeneous data sources in a uniform, SQL(-like) manner.
Squerall translates SPARQL queries into Spark’s or Presto’s SQL queries for execution (T13a).
Squerall applies FnO functions during its schema transformation with RML mapping rules (T7).
Squerall only supports translation of SPARQL aggregations; other SPARQL operators are considered future work (T13a).
Squerall can access Apache Parquet, CSV files, relational databases with JDBC connectors, and nonrelational databases, such as MongoDB, Elasticsearch, or Couchbase (T1, T2).
Squerall is written in Java (T8) and available under Apache License 2.0 (T12) as a CLI implementation and via a GUI (T9, T10).

**Source code** : https://github.com/EIS-Bonn/Squerall
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** :  10/09/2021

#### Ontario (2019)
Ontario provides virtualization over a set of SPARQL endpoints and non-SPARQL database interfaces using RML mapping rules (T5).
It translates queries into star shapes subqueries (T13a) and are combined with RML mapping rules to select the right SPARQL endpoint to answer the subquery.
The results of each subquery are joined locally (T13a).
Ontario supports SPARQL endpoints, relational databases, such as MySQL, files (locally or on Apache Hadoop) in CSV, TSV, and XML format, and non-relational databases such as MongoDB and graph databases, such as Neo4J (T1, T2).
It implements SPARQL Federated Queries via SPARQL’s SERVICE operator (T13b), but it does not support data transformations (T6).
Ontario is written in Python (T8) available as CLI implementation under the General Public License 2.0 (T9, T10, T11 T12).

**Source code** : https://github.com/SDM-TIB/Ontario
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 09/03/2021

#### Obi-Wan (2020)
Obi-Wan is a Java-based (T8) virtualization implementation for data stored in relational and non-relational databases.
Obi-Wan uses a custom GlobalLocal As View (GLAV) mapping language (T5) to link heterogeneous data to an RDF representation. Obi-Wan supports relational databases e.g. PostgreSQL, non-relational databases e.g. MongoDB, Redis, and triple stores e.g. Jena TDB (T1, T2).
Obi-Wan supports multiple entailment strategies such as query rewriting, mapping saturation, and hybrid rewriting-saturation (T13a).
Obi-Wan returns the generated triples as SPARQL query results (T3, T4).
To the best of our knowledge, Obi-Wan does not support data transformations (T6, T7), or SPARQL Federated Queries (T13b).
ObiWan is available as CLI implementation and webapp on Gitlab under MIT license (T9, T10, T11 T12).

**Source code** : https://gitlab.inria.fr/cedar/obi-wan
<br>
**Last accessed** : 23/02/2022
<br>
**Date last commit on default branch** : 22/10/2021


Table 6

| Ontop               | R2RML or Ontop Mapping Language | No                     | NA                                     | Java   | CLI                   | Apache-2.0 | SQL & virtualization optimizations, aggregation on databases, ontological entailement | with Denodo, Dremio or Teiid |
| ------------------- | ------------------------------- | ---------------------- | -------------------------------------- | ------ | --------------------- | ---------- | ------------------------------------------------------------------------------------- | ---------------------------- |
| Morph-RDB           | R2RML                           | No                     | NA                                     | Scala  | CLI, Docker           | Apache-2.0 | SQL optimizations                                                                     | No                           |
| Morph-xR2RML        | xR2RML                          | No                     | NA                                     | Scala  | CLI, SPARQL end-point | Apache-2.0 | Inherited from Morph-RDB                                                              | No                           |
| SparqlMap-M         | R2RML                           | R2RML custom extension | together, during schema transformation | Java   | CLI, SPARQL end-point | No license | Query normalization & analysis, mapping binding, execute on database engine           | No                           |
| Squerall            | RML                             | FnO                    | together, during schema transformation | Java   | CLI, GUI              | Apache-2.0 | Spark or Presto processing, aggregation on data sources                               | with Spark or Presto         |
| Ontario             | RML                             | No                     | NA                                     | Python | CLI                   | GPL-2.0    | Star shape subqueries on data sources, locally joined                                 | SPARQL federation            |
| Morph-RDB extension | S 2 O                           | No                     | NA                                     | Scala  | CLI, Docker           | Apache-2.0 | Inherited from Morph-RDB                                                              | with SNEEql                  |
| XGSN                | SSN ontology                    | Hardcoded in wrapper   | together, pre-processing of input data | Java   | CLI, webapp, API      | GPL-3.0    | Access delegated to RDF stream processor                                              | No                           |
| Obi-Wan             | custom GLAV mapping             | No                     | NA                                     | Java   | CLI, webapp           | MIT        | Ontology entailment                                                                   | with Tatooine                |

Table 7

| Characteristic             | Morph-streams++    | Ontop              | Morph-RDB          | Morph-xR2RML       | SparqlMap-M        | Squerall           | Ontario            | Morph-RDB extension | Obi-Wan            | XGSN               |
|----------------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|---------------------|--------------------|--------------------|
| T1: Data source            | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| File                       |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  |                    |                    |
| SQL RDB                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: |                    |
| NoSQL DB                   |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                     | :heavy_check_mark: |                    |
| OpenGIS                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                    |                     |                    |                    |
| Graph DB                   |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                     |                    |                    |
| Triple Store               |                    |                    |                    |                    |                    |                    |                    |                     | :heavy_check_mark: |                    |
| Kafka stream               |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| WebSocket stream           |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| MQTT stream                |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                     |                    |                    |
| TCP stream                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| UDP stream                 |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| SPARQL endpoint            |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| Web API                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                    |                     |                    |                    |
| Apache Hadoop              |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                     |                    |                    |
| Esper                      | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| GSN                        | :heavy_check_mark: |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| Apache Parquet             |                    |                    |                    |                    |                    | :heavy_check_mark: |                    |                     |                    |                    |
| Serial                     |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| CoAP                       |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| USB                        |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
|                            |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| T2: Data format            |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| CSV format                 |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  |                    | :heavy_check_mark: |
| JSON format                |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                     |                    |                    |
| XML format                 |                    |                    |                    | :heavy_check_mark: |                    |                    | :heavy_check_mark: |                     |                    |                    |
| TSV format                 |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                     |                    |                    |
| ODS format                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| XLSX format                |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| GeoJSON format             |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| KML format                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| Shapefiles                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| SQL query                  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: |
| NoSQL query                |                    |                    |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                     | :heavy_check_mark: |                    |
| SPARQL query               |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                     | :heavy_check_mark: |                    |
| CBOR format                |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| HDT format                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| RDF format                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| plain text                 |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| HTML format                |                    |                    |                    | :heavy_check_mark: |                    |                    |                    |                     |                    |                    |
| Archives                   |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| Neo4J graph                |                    |                    |                    |                    |                    |                    | :heavy_check_mark: |                     |                    |                    |
| EXIF encoded               |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| RSS                        |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| ESRI Grid ASCII            |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
| Images                     |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
|                            |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| "T3: Output Data & T4:     |
| Output Data formats"       |                    |                    |                    |                    |                    |                    |                    |                     |                    |                    |
| SPARQL Stream query result | :heavy_check_mark: |                    |                    |                    |                    |                    |                    | :heavy_check_mark:  |                    |                    |
| SPARQL query result        |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                     | :heavy_check_mark: | :heavy_check_mark: |
| CQELS query result         |                    |                    |                    |                    |                    |                    |                    |                     |                    | :heavy_check_mark: |
