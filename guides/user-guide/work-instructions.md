---
title: Work Instructions
parent: User guide
layout: default
---

## Work Instructions

### Create a new schema from scratch

1. Open the main menu.
2. Click on the New button.
3. Select where to store the new schema.

### Import an existing schema

1. Open the main menu.
2. Click on the Import button.
3. Choose a file in your file system, or paste a valid schema in the text area.
4. Click on the Import button.

{: .highlight }

Importing a schema doesn't override the current schema.

{: .highlight }

Schemalink will validate the schema you are trying to import, and return any
validation errors. A non-valid schema can still be imported, but might lead to
unexpected results.

### Edit schema properties

1. Make sure the general inspector is visible by clicking on any empty space in
   the canvas.
2. Using the form in the general inspector, edit:

   - The schema description.
   - The schema license.

### Change the schema name

1. Click on the schema name.
2. Edit the name.
3. Click on Save.

### Add a new class

1. Make sure the general inspector is visible by clicking on any empty space in
   the canvas.
2. Click on the Add Class button in the general inspector.
3. Specify a (unique) class name.

{: .warning }

Classes without a name as well as classes with a non-unique name won't be
included in any LinkML export. The same is true for relationships that involve
those classes.

### Add a new relationship

1. Hover over the perimeter of a class, until a dark blue circle appears.
2. Drag the circle to another existing class, or to an empty space to create a
   new class at the same time.

### Edit details of a class

1. Select any number of classes.
2. Using the form in the detail inspector, edit:

   - The class description.
   - The class name.
   - The class ontologies and examples - see dedicated section below.
   - The class attributes - see dedicated section below.

{: .highlight }

Only some options will be available if more than one entity is selected,
especially when the selection includes both classes and relationships.

### Edit details of a relationship

1. Select any number of relationships.
2. Using the form in the detail inspector, edit:

   - The relationship description.
   - The relationship name.
   - The type of relationship, choosing between association and inheritance.
   - The relationship cardinality - see dedicated section below.
   - The relationship ontologies and examples - see dedicated section below.
   - The relationship attributes - see dedicated section below.

{: .highlight }

Only some options will be available if more than one entity is selected,
especially when the selection includes both classes and relationships.

#### Edit ontologies and examples

1. Click on a single class or relationship.
2. In the detail inspector, expand the ontologies dropdown and select those that
   are relevant.
3. In the detail inspector, expand the examples dropdown and select those that
   are relevant. Note that:
   - By default, the dropdown will show ten examples, randomly selected from
     those coming from the selected ontologies.
   - If no ontology is selected, the examples dropdown will be empty.
   - You can add new examples by just typing them in the input field.

{: .highlight }

Ontologies and examples are fetched from a remote repository: every time
Schemalink is loaded, or the list of ontologies for an entity is changed, you'll
need to wait for multiple requests to complete before the dropdown are enabled.

#### Add/edit attributes

1. Select any number of classes or relationships.
2. In the detail inspector, click on the + Attribute button.
3. Specify a name for the attribute.
4. To further edit the attribute, click on it to expand the edit form.
5. Using the form, edit:

   - The attribute description.
   - The attribute range.
   - The attribute collection type, if any.
   - Whether the attribute is required.
   - Whether the attribute is the identifier for its class.

#### Edit relationship cardinality

1. Select any number of relationships.
2. In the detail inspector, expand the cardinality dropdown and select a
   predefined cardinality or Custom.
3. If Custom is selected, specify minimum and maximum cardinality for both the
   source and the target.

{: .warning }

When Custom is selected, if the minimum cardinality is greater or equal than the
maximum cardinality, neither of them will be included in any LinkML export.

### Export the schema

1. Click on the download/export button.
2. Choose the format you want to export the schema to, by switching to the
   corresponding tab.
3. Check the preview to make sure the export is correct.
4. Click on Download.

### Change the style of the schema

1. Click on the Style accordion in the inspector to expand the style menu.
2. Use the form to change a variety of style options, such as:

{: .highlight }

The general inspector and the detail inspector offer different styling options.
Namely, the general inspector allows to perform global changes, while the detail
inspector allows to perform changes on a per-entity basis.
