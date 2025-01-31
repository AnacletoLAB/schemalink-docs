---
title: Home
layout: home
nav_order: 1
---

## SchemaLink

SchemaLink is a web application designed to assist LinkML developers in creating and curating schemas.
<!--- ema: io commento per non perdere ciò che modifico, quando abbiamo una versione da pubblicare occurrerà un "repulisti" dei commenti
that we are currently developing to assist compliant to our model. This interface was initially thought as a means for the specification of prompts for SPIRES. However, the interface can be exploited independently of that for generating LinkML schemas. -->

SchemaLink builds upon the functionality of Neo4j's [Arrows](https://arrows.app/), a web tool for drawing and editing property graphs. SchemaLink extends its capabilities to focus on LinkML schemas.
<!---SchemaLink converts Arrows to a UML-like tool for drawing LinkML schemas from scratch and importing and editing existing LinkML schemas specified in ``yaml``. Nodes correspond to classes and edges represent relationships between them. SchemaLink allows to create and edit classes, relationships, slots and attributes, ontology annotations, descriptions, examples, and customize the graphical style of the schema. -->
Nodes represent  schema classes, edges define relationships between classes. Properties can be easily specified both on classes and relationships. 
Users can easily add, remove, or update schema items and adjust their properties through an intuitive interface.

**Features**

- **Interactive Schema Creation and Editing**
  - Define classes, relationships, slots and attributes, and ontology annotations
  - Add descriptions, examples, and customize graphical styles
- **Flexible Import and Export**
  - Import existing LinkML schemas specified in YAML
  - Export schemas in LinkML (YAML), PNG, SVG, JSON
- **Applications**
  - Graphically representing relationships between bio-entities grounded in OBO ontologies
  - Develop schemas for performing named entity recognition (NER) and relation extraction (RE) tasks using the [OntoGPT](https://github.com/monarch-initiative/ontogpt) package
<!--- For the realization of SchemaLink, we decided to start from the web app Arrows. With Arrows, users can specify nodes and edges, assigning them
names, types, and additional properties. Moreover, it offers facilities for loading graphs (locally or from cloud infrastructures), exporting in different
forms (PNG, SVG, JSON, Cypher), easily adding/removing/updating nodes, edges, subgraphs, and their properties, and trivially changing the visual aspects of
the generated graph.
Even if the “visual quality” of the generated diagram is worse than the one obtained by widely adopted UML-like tools, its simplicity
of use makes Arrows a very promising tool for sketching conceptual schemas. -->
