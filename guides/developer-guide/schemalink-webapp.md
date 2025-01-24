---
title: SchemaLink Webapp
parent: Developer Guide
layout: default
---

## SchemaLink Webapp

{: .info }

> - Webapp: <https://schemalink.anacleto.di.unimi.it/>
> - Repository: <https://github.com/AnacletoLAB/schemalink-webapp>
> - Main technologies: [Node](https://nodejs.org/docs/latest/api/),
>   [Vite](https://vite.dev/guide/),
>   [TypeScript](https://www.typescriptlang.org/docs/), JavaScript,
>   [React](https://react.dev/learn), [Redux](https://redux.js.org/usage/) and
>   [Semantic UI React](https://react.semantic-ui.com/)
> - Run locally - requires Node and npm:
>
>   ```shell
>   npm install
>   npx nx serve arrows-ts
>   ```

### The [React-Redux app](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/apps/arrows-ts)

### The [`model` library](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/libs/model)

#### Add/change properties for the schema, the classes, or the relationships

To add or change a property for the schema, the classes, the relationships, or
any other entity used by the webapp, locate the appropriate TypeScript file.
Within the file, locate the `interface` for that entity, and change it
accordingly.

For example, to add a property to a relationship:

- Head to
  [libs/model/src/lib/Relationship.ts](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/model/src/lib/Relationship.ts).
- Add a new property to the `Relationship` interface.

{: .warning }

Changing properties for models may result into breaking changes to the webapp!
Lookout for TypeScript errors: those will guide you in updating the codebase
accordingly.

### The [`graphics` library](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/libs/graphics)

#### Change arrows behavior

To change how arrows behave based on the content of the schema, head to
[libs/graphics/src/lib/arrowDimensions.ts](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/graphics/src/lib/arrowDimensions.ts)
and change how the different parameters of an arrow are calculated, based on the
type of the relationship.

{: .highlight }

Different layouts on the canvas might result into different arrows being
rendered. For example, when only one relationship exists between two classes, a
[`StraightArrow`](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/graphics/src/lib/StraightArrow.ts)
is rendered. When multiple relationships exist, a
[`ParallelArrow`](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/graphics/src/lib/ParallelArrow.ts)
is rendered. When changing the behavior of arrows, make sure to update all of
the arrow types.

### The [`linkml` library](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/libs/linkml)

#### Change LinkML export logic

To change how the conversion from the webapp schema to a LinkML schema is done,
head to the
[`linkml/src/index.ts`](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/linkml/src/index.ts)
file. The `fromGraph` function takes a collection of classes, a collection of
relationships, and some metadata about the schema - e.g. schema name,
description, license. The returned object is a LinkML object, which can be
converted to a YAML string. A LinkML object is a TypeScript object typed such
that it can store a valid LinkML schema.

#### Change LinkML import logic

To change how the conversion from a LinkML schema to the webapp schema is done,
head to the
[`linkml/src/index.ts`](https://github.com/AnacletoLAB/schemalink-webapp/blob/main/libs/linkml/src/index.ts)
file. The `toGraph` function takes a collection of classes, a collection of
ontologies, and some metadata about the schema - e.g. description. The returned
object is a LinkMLGraph object, which can be imported in the webapp Redux store.
A LinkMLGraph object is a TypeScript object typed such that it can store a valid
subset of the properties from a Graph object: the type used for the webapp
schema. Namely, a LinkMLGraph object contains only classes and relationships,
along with some metadata.
