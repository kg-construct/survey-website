---
layout: page
title: Survey Methodology
permalink: /survey-methodology/
---

## Criteria

We consider the following inclusion and exclusion criteria 
during our systematic literature review to include or exclude an article:

### Inclusion criteria

- Articles published from the first published recommendation of RDF in 1999
  until 2021.
- Articles written in English.
- Articles describing approaches and implementations related to:
  - Generating knowledge graphs from heterogeneous data sources.
  - Describing implementations and optimizations of existing knowledge 
    graph generation approaches.
  - Specifying schema or data transformation for heterogeneous data.

### Exclusion criteria

- Articles which are not published or peer-reviewed.
- Articles written in another language than English.
- Technical reports, demo papers, posters, PhD consortium papers, and 
  presentations.
- Commercialized approaches and implementations.

This systematic literature review was performed independently by 3 authors.

## Step 1: Collecting articles

We created a list of terms by breaking down our research sub-questions into 
individual facets and their alternative spelling, synonyms and abbreviations. 
These terms were combined together with Boolean `AND` and `OR` operators
and used by each reviewer when searching for relevant articles.
We avoided to use these terms individually because they were too broad
which resulted in an enormous number of results.
The following terms and combinations were considered in this systematic review:

- `("knowledge graph" OR "knowledge graphs") AND ("definition" OR "definitions")`
- `("RDF" OR "Resource Description Framework") AND "heterogeneous data"`
- `("transformation" OR "transformations") AND "heterogeneous data"`
- `("answer" OR "answers" OR "answering") AND ("query" OR "queries")`
- `("Resource Description Framework" OR "RDF") AND ("stream" OR "streams" OR "streaming")`
- `("Linked Data" OR "Linked Open Data" OR "LOD" OR "knowledge graph" OR "knowledge graphs") AND "generation"`
- `("Linked Data" OR "Linked Open Data" OR "LOD" OR "knowledge graph" OR "knowledge graphs") AND "construction"`
- `"SPARQL" AND ("generation" OR "construction")`
- `("mapping language" OR "mapping languages") AND ("RDB" OR "relational database" OR "relational databases")`
- `("mapping language" OR "mapping languages") AND "heterogeneous data"`
- `("mapping language" OR "mapping languages") AND ("function" OR "functions")`
- `("mapping language" OR "mapping languages") AND ("transformation" OR "transformations")`
- `("mapping language" OR "mapping languages") AND ("RDF" OR "Resource Description Framework")`
- `("mapping language" OR "mapping languages") AND ("knowledge graph" OR "knowledge graphs" OR "Linked Data" OR "Linked Open Data" OR "LOD")`
- `("mapping language" OR "mapping languages") AND ("knowledge graph" OR "knowledge graphs" OR "Linked Data" OR "Linked Open Data" OR "LOD") AND ("generation" OR "construction")`
- `("mapping language" OR "mapping languages") AND "SPARQL"`
- `("Linked Data" OR "Linked Open Data" OR "LOD") AND ("mapping language" OR "mapping languages")`
- `("mapping language" OR "mapping languages") AND "R2RML"`
- `("generation" OR "construction") AND "R2RML" AND ("knowledge graph" OR "knowledge graphs" OR "Linked Data" OR "Linked Open Data" OR "LOD")`
- `("stream" OR "streams" OR "streaming") AND ("RDF" OR "Resource Description Framework") AND "SPARQL"`

### Collections

- Digital Libraries: 
- Journals: 
- Conferences: 
- Workshops: 

## Step 2: Review titles & abstracts
We searched for these terms in the article's title and abstract 
to avoid a high number of irrelevant articles in comparison 
to searching in the article's full text.
An article is selected when at least one of the combined terms has been found
in the title or abstract of an article.
We searched for our terms in 42 sources ranging from journals, conferences and 
digital libraries.
We retrieved 1884 articles which are potentially relevant for this survey paper. 
After removing duplicates, 1729 articles were added to the review list.

The following sources were used to search for relevant articles
for this survey paper:

### Journals

- Semantic Web Journal (SWJ)
- Journal of Web Semantics (JoWS)
- International Journal of Web Information Systems (IJWIS)
- Future Generation Computer Systems (FGCS)
- Journal on Data Semantics (JDS)
- International Journal on Semantic Web and Information Systems (IJSWIS)
- PeerJ Computer Science
- Information
- International Journal on Digital Libraries (IJDL)
- International Journal of Applied Mathematics and Computer Science (IJAMCS)
- International Journal of Software Engineering and Knowledge Engineering (IJSEKE)

### Conferences

- International Semantic Web Conference (ISWC)
- European Semantic Web Conference (ESWC)
- International Conference on Semantic Systems (SEMANTiCS/I-SEMANTICS)
- International Conference on Semantic Computing (ICSC)
- International Conference on Knowledge Engineering and Knowledge Management (EKAW)
- International Conference on Knowledge Capture (K-Cap)
- Conference on Information and Knowledge Management (CIKM)
- Knowledge Graph and Semantic Web Conference (KGSWC)
- The Web Conference (WWW)
- Ontologies, Databases and Applications of Semantics (ODBASE)
- Language, Data and Knowledge (LDK)
- International Conference on Web Intelligence (WI-IAT)
- International Conference on Web Information Systems and Technologies (WEBIST)
- International Conference on Web Intelligence, Mining and Semantics (WIMS)
- International Conference on Web Engineering (ICWE)

### Workshops

- Knowledge Graph Construction Workshop (KGCW)
- Knowledge Graph Building Workshop (KGB)
- Consuming Linked Data Workshop (COLD)
- Large Scale RDF Analytics Workshop (LASCAR)       
- Semantic Big Data Workshop (SBD)
- International Semantic Sensor Networks Workshop (SSN)
- Workshop on Linked Data on the Web (LDOW)

### Digital Libraries

- IEEE Explore
- Springer Link
- Science Direct
- ACM Digital Library
- Google Scholar

## Step 3: Applying additional search strategies

We also enriched our review list by following additional search strategies 
to include more relevant articles:

1. reviewing references of potentially relevant articles
2. adding manually relevant articles.

We searched for potentially relevant articles through the references 
of other relevant articles. 
This way, we discovered 3 more potentially relevant articles. 
We also manually added 3 more articles which we found relevant for this survey.
This result in 1735 articles in total.
We indicated these 6 articles in the tables below with a '*'.

| Title                                                                                                     | Author(s)                  | Scope      |
| --------------------------------------------------------------------------------------------------------- | -------------------------- | ---------- |
| A middleware framework for scalable management of linked streams*                                         | Le-Phuoc D. et al.         | MT         |
| Exploiting Declarative Mapping Rules for Generating GraphQL Servers with Morph-GraphQL*                   | Chaves-Fraga D. et al.     | VT         |
| Implementation-independent function reuse*                                                                | De Meester B. et al.       | DT         |
| LDScript: A Linked Data Script Language*                                                                  | Corby O. et al.            | DT         |
| Querying the Web of Data with XSPARQL 1.1*                                                                | Dell'Aglio D. et al.       | ML, DT     |
| Turning Transport Data to Comply with EU Standards While Enabling a Multimodal Transport Knowledge Graph* | Scrocca M. et al.          | MT         |

## Step 4: Reviewing potential articles for inclusion

We manually reviewed the retrieved potentially relevant articles
among reviewers.
The reviewers verified the article's relevance
for this systematic literature review and
applied our inclusion and exclusion criteria. 
This resulted in 52 relevant articles for this survey paper.
18 articles introduce or extend a mapping language (ML) for 
transforming heterogeneous data into a knowledge graph.
16 articles introduce data transformations (DT) or align them
with a mapping language for heterogeneous data.
21 articles describe a materialization tool (MT),
and 18 articles a virtualization tool (VT)
for transforming heterogeneous data into a knowledge graph.
12 articles were submitted to workshops, 27 to conferences, and 13 to journals.

| Title                                                                                                     | Author(s)                  | Scope      |
| --------------------------------------------------------------------------------------------------------- | -------------------------- | ---------- |
| A Generic Mapping-based Query Translation from SPARQL to Various Target Database Query Languages          | Michel F. et al.           | ML, DT, VT |
| A middleware framework for scalable management of linked streams*                                         | Le-Phuoc D. et al.         | MT         |
| A SPARQL Extension for Generating RDF from Heterogeneous Formats                                          | Lefrançois M. et al.       | ML, DT, MT |
| DAFO: An Ontological Database System with Faceted Queries                                                 | Pankowski T. et al.        | VT         |
| Declarative Data Transformations for Linked Data Generation: The Case of DBpedia                          | De Meester B. et al.       | DT, VT     |
| Detailed Provenance Capture of Data Processing                                                            | De Meester B. et al.       | ML         |
| D2RML: Integrating Heterogeneous Data and Web Services into Custom RDF Graphs                             | Chortaras A. et al.        | ML, MT     |
| D-REPR: A Language for Describing and Mapping Diversely-Structured Data Sources to RDF                    | Vu B. et al.               | ML, MT, DT |
| Enabling Ontology-Based Access to Streaming Data Sources                                                  | Calbimonte J. et al.       | VT         |
| Enabling RDF Stream Processing for Sensor Data Management in the Environmental Domain                     | Llave A. et al.            | VT         |
| Executing SPARQL queries over Mapped Document Store with SparqlMap-M                                      | Unbehauen J. et al.        | VT         |
| Exploiting Declarative Mapping Rules for Generating GraphQL Servers with Morph-GraphQL*                   | Chaves-Fraga D. et al.     | VT         |
| Flexible RDF Generation from RDF and Heterogeneous Data Sources with SPARQL-Generate                      | Lefrançois M. et al.       | ML, DT, MT |
| Formalisation and Experiences of R2RML-Based SPARQL to SQL Query Translation Using Morph                  | Priyatna F. et al.         | DT, MT     |
| FunMap: Efficient Execution of Functional Mappings for Knowledge Graph Creation                           | Jozashoori, S. et al.      | DT         |
| FunUL: A Method to Incorporate Functions into Uplift Mapping Languages                                    | Crotti Junior A. et al.    | DT         |
| GeoTriples: a Tool for Publishing Geospatial Data as RDF Graphs Using R2RML Mappings                      | Kyzirakos K. et al.        | ML, MT     |
| GeoTriples: Transforming geospatial data into RDF graphs using R2RML and RML mappings                     | Kyzirakos K. et al.        | ML, MT     |
| Implementation-independent function reuse*                                                                | De Meester B. et al.       | DT         |
| KR2RML: An Alternative Interpretation of R2RML for Heterogeneous Sources                                  | Slepicka J. et al.         | MT         |
| LDScript: A Linked Data Script Language*                                                                  | Corby O. et al.            | DT         |
| Leveraging Web of Things W3C Recommendations for Knowledge Graphs Generation                              | Van Assche D. et al.       | ML         |
| Linked Data Integration Framework                                                                         | Schultz A. et al.          | MT         |
| Machine-Interpretable Dataset and Service Descriptions for Heterogeneous Data Access and Retrieval        | Dimou A. et al.            | ML         |
| MapSDI: A Scaled-Up Semantic Data Integration Framework for Knowledge Graph Creation                      | Jozashoori, S. et al.      | MT         |
| Mapping between RDF and XML with XSPARQL                                                                  | Bischof S. et al.          | ML, DT     |
| Mapping Hierarchical Sources into RDF Using the RML Mapping Language                                      | Dimou A. et al.            | ML, MT     |
| Obi-Wan: Ontology-Based RDF Integration of Heterogeneous Data                                             | Buron M. et al.            | VT         |
| Ontario: Federated Query Processing against a Semantic Data Lake                                          | M. Endris K. et al.        | VT         |
| Ontology–based access to temporal data with Ontop: A framework proposal                                   | Güzel Kalayci E. et al.    | VT         |
| Ontology-Based Data Access: Ontop of Databases                                                            | Rodríguez-Muro M. et al.   | VT         |
| Ontop: Answering SPARQL Queries over Relational Databases                                                 | Calvanese D. et al.        | VT         |
| Ontop-spatial: Ontop of geospatial databases                                                              | Bereta K. et al.           | VT         |
| On the semantics of heterogeneous querying of relational, XML, and RDF data with XSPARQL                  | Lopes N. et al.            | ML, DT     |
| Optique: Towards OBDA Systems for Industry                                                                | Kharlamov E. et al.        | VT         |
| Optique: Zooming in on Big Data                                                                           | Giese M. et al.            | VT         |
| Parallel RDF Generation from Heterogeneous Big Data                                                       | Haesendonck G. et al       | MT         |
| Querying the Web of Data with XSPARQL 1.1*                                                                | Dell'Aglio D. et al.       | ML, DT     |
| RDF-Gen: Generating RDF from Streaming and Archival Data                                                  | Santipantakis G. M. et al. | MT         |
| RocketRML - A NodeJS implementation of a use-case specific RML mapper                                     | Umutcan Ş. et al.          | MT         |
| RML: A Generic Language for Integrated RDF Mappings of Heterogeneous Data                                 | Dimou A. et al.            | ML, MT     |
| R2RML-F: Towards Sharing and Executing Domain Logic in R2RML Mappings                                     | Debruyne C. et al.         | DT         |
| SDM-RDFizer: An RML Interpreter for the Efficient Creation of RDF Knowledge Graphs                        | Iglesias E. et al.         | MT         |
| ShExML: improving the usability of heterogeneous data mapping languages for first-time users              | García-González H. et al.  | ML         |
| Sustainable Linked Data Generation: The Case of DBpedia                                                   | Maroy W. et al.            | DT         |
| Squerall: Virtual Ontology-Based Access to Heterogeneous and Large Data Sources                           | Mami M. et al.             | VT         |
| The Virtual Knowledge Graph System Ontop                                                                  | Guohui X. et al.           | ML, VT     |
| Toward the Web of Functions: Interoperable Higher-Order Functions in SPARQL                               | Atzori M. et al.           | DT         |
| Translation of Relational and Non-relational Databases into RDF with xR2RML                               | Michel F. et al.           | ML, MT, VT |
| TripleWave: Spreading RDF Streams on the Web                                                              | Mauri A. et al.            | MT         |
| Turning Transport Data to Comply with EU Standards While Enabling a Multimodal Transport Knowledge Graph* | Scrocca M. et al.          | MT         |
| XGSN: An Open-source Semantic Sensing Middleware for the Web of Things                                    | Calbimonte J. et al.       | VT         |
