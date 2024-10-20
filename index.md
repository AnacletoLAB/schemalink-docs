---
title: Home
layout: home
nav_order: 1
---

SchemaLink is a web application that we are currently developing to assist
LinkML developers in drawing schemas compliant to our model. This interface was
initially thought as a means for the specification of prompts for SPIRES.
However, the interface can be exploited independently of that for generating
LinkML schemas. For the realization of SchemaLink, we decided to start from the
web app Arrows. Arrows is a very flexible and easy-to-use web tool for drawing
property graphs. With Arrows, users can specify nodes and edges, assigning them
names, types, and additional properties. Moreover, it offers facilities for
loading graphs (locally or from cloud infrastructures), exporting in different
forms (PNG, SVG, JSON, Cypher), easily adding/removing/updating nodes, edges,
subgraphs, and their properties, and trivially changing the visual aspects of
the generated graph. In our case, Arrows is used as a UML-like tool for
conceptual schema design where nodes correspond to classes, while edges
represent relation types. Even if the “visual quality” of the generated diagram
is worse than the one obtained by widely adopted UML-like tools, its simplicity
of use makes Arrows a very promising tool for sketching conceptual schemas.
Several are the features that have been integrated into SchemaLink for importing
LinkML yaml file, drawing schemas, and exporting them. In the remainder of the
section, we will detail these characteristics. An initial version of SchemaLink
is live at the following link: <https://fl-14-97.zhdk.cloud.switch.ch/>.
