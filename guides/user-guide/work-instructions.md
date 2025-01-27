---
title: Work Instructions
parent: User Guide
layout: default
---

## Work Instructions

### Create a new schema from scratch

1. Open the main menu
2. Click on the ``New'' button
3. Click on ``Store in: Web Browser Storage``

### Import an existing schema

1. Open the main menu
2. Click on the ``Import`` button
3. Choose a file in your file system, or paste a valid schema in the text area
4. Click on the ``Import`` button at the bottom of the panel

{: .highlight }

Importing a schema doesn't override the current schema. Schemas will be merged.

{: .highlight }

Schemalink validates the schema you import, and return
validation errors. A non-valid schema can still be imported, but might lead to
unexpected results.

### Edit schema properties

1. Make sure the ``inspector`` panel is visible by clicking on any empty space in
   the canvas.
2. Within the ``inspector`` panel, edit:

   - The schema ``description``
   - The schema ``license``

### Change the schema name

1. Click on the schema ``name``
2. Edit the name
3. Click on Save

### Add a class

1. Make sure the ``inspector`` panel is visible by clicking on any empty space in
   the canvas.
2. Click on the ``Add Class`` button in the ``inspector`` panel
3. Specify a <!-- ema lo dici sotto (unique) --> class ``name``

{: .warning }

Classes without a name as well as classes with a non-unique name won't be
included in any LinkML export. This also applies relationships that involve
those classes.

### Add a relationship

1. Hover upon the perimeter of a class, until a dark blue circle appears
2. Drag the circle to another existing class, or to an empty space to create a
   new class at the same time

### Edit a class 

1. Select <!-- ema any number of --> a class or a set of classes (``cmd+click`` in Mac, ``ctrl+click`` in Linux and Windows)
2. Using the form in the detail inspector, edit:

   - The class ``description``
   - The class ``name``
   - The class ``ontologies`` and ``examples`` - details below
   - The class ``attributes`` - details below

{: .highlight }

Only some options will be available if more than one class is selected.

### Edit a relationship 

1. Select <!-- ema any number of --> a relationship or a set of relationships (cmd+click in Mac, ctrl+click in Linux and Windows)
2. Using the form in the detail inspector, edit:

   - The relationship ``description``
   - The relationship ``name``
   - The ``type`` of relationship (``association`` or ``inheritance``)
   - The relationship ``cardinality``
      - Expand the ``cardinality`` dropdown menu and select a
         predefined cardinality or ``Custom``.
      - If ``Custom`` is selected, specify ``minimum`` and ``maximum cardinality`` for both the
   source and the target.
   - The relationship ``ontologies`` and ``examples`` - details below
   - The relationship ``attributes`` - details below

{: .warning }

When ``Custom`` is selected, if the minimum cardinality is greater or equal than the
maximum cardinality, neither of them will be included in any LinkML export.

{: .highlight }

Only some options will be available if more than one relationship is selected.

#### Annotate classes and elationships with ontologies and provide examples for instances

1. Click on a single class or relationship
2. In the ``inspector``, expand the ``ontologies`` dropdown menu and select those that
   are relevant
3. In the ``inspector``, expand the ``examples`` dropdown menu and select those that
   are relevant

{: .highlight }

By default, the dropdown will show ten examples, randomly selected from selected ontologies' terms.

{: .highlight }

If no ontology is selected, the examples dropdown will be empty.

{: .highlight }

You can add new examples by just typing them in the input field.

{: .highlight }

Ontologies and examples are fetched from a EBI's [Ontology Look-up Service](https://www.ebi.ac.uk/ols4/). Every time
Schemalink is loaded or the set of ontologies for annotating a class is changed, you
have to wait for the dropdown menu to be enabled.

#### Add and edit attributes for classes and relationships

1. Select a class, a relationship, or a set taht includes classes and relationships
2. In the ``inspector``, click on the ``+ Attribute`` button
3. Provide a ``name`` for the attribute
4. Optional: click on the edit panel and add:

   - The attribute ``description``
   - The attribute ``range`` (i.e. the ``type`` of that attribute)
   - The attribute ``collection type``, if any
   - Whether the attribute is ``required``
   - Whether the attribute is the ``identifier`` of its class

### Export the schema

1. Click on the ``download/export`` button
2. Choose the format you want to export the schema to, by switching to the
   corresponding tab
3. Check the preview to make sure the export is correct
4. Click on the ``Download`` button

### Change the graphical style of the schema

Click on ``Style`` in the ``inspector`` panel to expand the style menu.
<!--
2. Use the form to change a variety of style options, such as:

{: .highlight }

The general inspector and the detail inspector offer different styling options.
Namely, the general inspector allows to perform global changes, while the detail
inspector allows to perform changes on a per-entity basis.
-->
