---
title: Example
parent: User Guide
layout: default
---

## A LinkML Schema for Representing Relationships Between Genes and Biological Processes

Suppose we want to create a LinkML schema that models interactions between genes and biological processes. A bio-curator may define such a schema to represent and standardize biological knowledge from heterogeneous sources. Additionally, this schema can act as a meta-model to be translated in targeted prompts for guiding a LLM in the extraction of entities and relationships involving genes and biological processes from scientific texts.

We begin by specifying (1) a schema name, and (2) a schema description. Moreover, we can include in the main canvas a new class  named "Gene" by clicking on the button (3).

![1](https://github.com/user-attachments/assets/c23556ea-8d9f-4ab2-9802-ef2cbc21b1ad)

The inspector panel on the right-hand side of the canvas is shown to the user when clicking on the class graphical artifact. By means of this interface, the class Gene can be enhanced by (1) adding a description. We also (2) annotate the class with the HGNC terminology, and (3) retrieve examples of gene instances from HGNC.

![2](https://github.com/user-attachments/assets/afa5e5fd-8c5c-4ec9-b3af-8d7a09bc376a)

The class Gene can be further refined by adding key attributes. For example, the attribute named "Symbol" is added (1) and improved by specifying its (2) description and (3) type. The required flag is added to Symbol (4): instances of class Gene **require** the Symbol attribute.

![3](https://github.com/user-attachments/assets/734472d3-7432-42a1-8259-1026ae0b453e)

Similarly, additional attributes can be defined for the Gene class.

We now introduce a class named "BiologicalProcess" for representing biological processes in our LinkML schema. Following the same steps as for the Gene class, we add the "BiologicalProcess" class with meaningful examples and attributes. 

![4](https://github.com/user-attachments/assets/0662cab8-707b-4f35-91a1-d02e8dbb4467)

Biological processes are represented using gene ontology terms. Therefore, we define a parent class named "GOterm", and specify that biological processes are a specialization of GO terms by using the ``INHERITANCE`` relationship type. Attributes and ontology annotations from the GOterm class are inherited by BiologicalProcess.

![5](https://github.com/user-attachments/assets/634320a3-613a-414f-8953-92d9bab76b08)

Finally,  "participates in" ``ASSOCIATION`` relationship between genes and biological processes can be specified. By hovering over the border of the Gene class we can connect it to the BiologicalProcess class.

![6](https://github.com/user-attachments/assets/84a8b215-d30f-44f1-8c46-9cfaff327088)

Attributes for the ``Gene-participates in-BiologicalProcess`` association relationship are added in the same way as class attributes.

![7](https://github.com/user-attachments/assets/6c558bd9-e8f6-4b38-8bd0-fc5a02ee71d2)

The schema can be further expanded by considering other subclasses such as molecular functions and cellular components and new relationships between classes. The schema can also be enhanced by considering attributes specific to subclasses (e.g. ``activity type`` for MolecularFunction and ``cellular location`` for CellularComponent).

![8](https://github.com/user-attachments/assets/b890452d-3d20-445d-8d8f-f2f57bc7f4af)

To export the schema in LinkML, click the ``Download / Export`` button in the top right corner of the canvas. A download panel will appear.

![9](https://github.com/user-attachments/assets/8f5ecd63-0517-47c5-a671-2a799a43c038)

The LinkML schema for representing relationships of type "participates in" involving genes and biological processes is reported below.

```yaml

id: https://schemalink.anacleto.di.unimi.it/gene_bio_process

default_range: string

name: gene_bio_process

title: GeneBioProcess

description: LinkML schema for representing the interactions between genes and GO terms.

prefixes:
  linkml: https://w3id.org/linkml/
  ontogpt: http://w3id.org/ontogpt/
  rdf: https://www.w3.org/1999/02/22-rdf-syntax-ns
  HGNC: http://identifiers.org/hgnc/
  GO: http://purl.obolibrary.org/obo/go/extensions/go-plus.owl

imports:
  - ontogpt:core
  - linkml:types

classes:
  GeneParticipatesInBiologicalProcessRelationship:
    is_a: Triple
    description: >-
      A triple where the subject is a Gene and where the object is a Biological
      Process. A participates in relationship between a gene and a
      biological process.
    slot_usage:
      subject:
        range: Gene
        annotations:
          prompt.examples: RELA,  BRCA1,  alpha-1-B glycoprotein
        minimum_cardinality: 0
        maximum_cardinality: 1
      object:
        range: BiologicalProcess
        annotations:
          prompt.examples: viral genome replication,  cellular homeostasis,  DNA repair
        minimum_cardinality: 0
      predicate:
        range: GeneParticipatesInBiologicalProcessPredicate
        annotations:
          prompt.examples: RELA participates in cell growth,  IL6 participates in homeostasis
      evidence:
        description: The experimental methods used for validating the relationship
        required: true
        identifier: false
        range: string
        multivalued: true

  GeneParticipatesInBiologicalProcessPredicate:
    is_a: RelationshipType
    attributes:
      label:
        description: >-
          The predicate for the GeneParticipatesInBiologicalProcess
          relationships.
      id:
        pattern: 'participates in'
    id_prefixes: []
    annotations: {}

  Gene:
    is_a: NamedEntity
    description: ''
    mixins: []
    attributes:
      symbol:
        description: The HGNC symbol of the gene.
        required: true
        identifier: false
        range: string
      hgnc_id:
        description: The HGNC identifier of the gene.
        required: true
        identifier: true
        range: integer
      synonym:
        description: Synonyms for the gene.
        required: false
        identifier: false
        range: string
        multivalued: true
    id_prefixes:
      - HGNC
    annotations:
      annotators: sqlite:obo:HGNC
      prompt.examples: RELA,  BRCA1,  alpha-1-B glycoprotein

  GOterm:
    is_a: NamedEntity
    description: >-
      A Gene Ontology (GO) term that represents a standardized concept
      describing a biological process, molecular function, or cellular
      component. GO terms provide a controlled vocabulary for annotating gene
      products and their roles in biology.
    mixins: []
    attributes:
      go_id:
        description: The GO term identifying the concept.
        required: true
        identifier: true
        range: string
      synonym:
        description: Synonyms for the GO term.
        required: false
        identifier: false
        range: string
        multivalued: true
      description:
        description: A description for the GO term.
        required: false
        identifier: false
        range: string
      label:
        description: A label for the GO term.
        required: true
        identifier: false
        range: string
    id_prefixes:
      - GO
    annotations:
      annotators: sqlite:obo:go
      prompt.examples: >-
        dolipore septum,  citrulline metabolic process,  peptide pheromone
        export

  BiologicalProcess:
    is_a: GOterm
    description: ''
    mixins: []
    attributes:
      biological_process_id:
        identifier: true
        description: A unique identifier for the BiologicalProcess class.
    id_prefixes: []
    annotations:
      prompt.examples: viral genome replication,  cellular homeostasis,  DNA repair

```
