---
layout: page
title: Tools
permalink: /tools/
---

2 different tool categories exist for generating knowledge graphs:
1. [Materialization tools]({{ "/tools/materialization" | prepend: site.baseurl | prepend: site.url }})
2. [Virtualization tools]({{ "/tools/virtualization" | prepend: site.baseurl | prepend: site.url }})

Materialization tools in the form of an Extract-Transform-Load (ETL) process
transform complete datasets into a knowledge graph.
First all the data is extracted, then transformed into a knowledge graph,
and loaded to query and use the knowledge graph.
A complete overview of materialization tools analyzed 
in this Systematic Literature Review
is available on **[Materialization Tools]({{ "/tools/materialization" | prepend: site.baseurl | prepend: site.url }})** page.

Virtualization tools in the form of Ontology-Based Data Access (OBDA),
analyze and execute queries such as SPARQL queries to only transform parts
of a dataset into a knowledge graph to answer the query.
A complete overview of virtualization tools analyzed 
in this Systematic Literature Review
is available on **[Virtualization Tools]({{ "/tools/virtualization" | prepend: site.baseurl | prepend: site.url }})** page.
