---
title: Example
parent: User Guide
layout: default
---

## A LinkML Schema for Representing Relationships Between Genes and Biological Processes

Suppose that we want to create a LinkML schema that models interactions between genes and biological processes.

We begin by specifying (1) a schema name, (2) a schema description and (3) a class named "Gene".

![1](https://github.com/user-attachments/assets/c23556ea-8d9f-4ab2-9802-ef2cbc21b1ad)

The class Gene is enhanced by (1) adding a description. We also (2) annotate the class with the HGNC terminology, and (3) retrieve examples of gene instances from HGNC.

![2](https://github.com/user-attachments/assets/afa5e5fd-8c5c-4ec9-b3af-8d7a09bc376a)

The class Gene is further refined by adding key attributes. For example, the attribute named "Symbol" is added (1) and improved by specifying its (2) description and (3) type. The required flag is added to Symbol (4): instances of class Gene **require** the Symbol attribute.

![3](https://github.com/user-attachments/assets/734472d3-7432-42a1-8259-1026ae0b453e)

Similarly, additional attributes can be defined for the Gene class.

We now introduce a class named "BiologicalProcess" for representing biological processes in our LinkML schema. Following the same steps as for the Gene class, we add the "BiologicalProcess" class with meaningful examples and attributes. 

![4](https://github.com/user-attachments/assets/0662cab8-707b-4f35-91a1-d02e8dbb4467)

Biological processes are represented using gene ontology terms. Therefore, we define a parent class named "GOterm", and specify that biological processes are a specialization of GO terms by using the ``INHERITANCE`` relationship type. Attributes and ontology annotations from the GOterm class are inherited by BiologicalProcess.

![5](https://github.com/user-attachments/assets/634320a3-613a-414f-8953-92d9bab76b08)

Finally, we specify the "participates in" ``ASSOCIATION`` relationship between genes and biological processes. By hovering over the border of the Gene class we can connect it to the BiologicalProcess class.

![6](https://github.com/user-attachments/assets/84a8b215-d30f-44f1-8c46-9cfaff327088)

Attributes for the ``Gene-participates in-BiologicalProcess`` association relationship are added in the same way as class attributes.

![7](https://github.com/user-attachments/assets/6c558bd9-e8f6-4b38-8bd0-fc5a02ee71d2)

The schema can be further expanded by considering other subclasses such as molecular functions and cellular components and new relationships between classes. The schema can also be enhanced by considering attributes specific to subclasses (e.g. ``activity type`` for MolecularFunction and ``cellular location`` for CellularComponent).

![8](https://github.com/user-attachments/assets/b890452d-3d20-445d-8d8f-f2f57bc7f4af)

To export the schema in LinkML, click the ``Download / Export`` button in the top right corner of the canvas. A download panel will appear.

![9](https://github.com/user-attachments/assets/8f5ecd63-0517-47c5-a671-2a799a43c038)
