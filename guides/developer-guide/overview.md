---
title: Overview
parent: Developer Guide
layout: default
---

## Overview

SchemaLink repositories are available within the [AnacletoLAB
organization](https://github.com/AnacletoLAB). Each repository provides a README
to explain its characteristics.

### The webapp

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

The webapp code was originally forked from Neo4j's [Arrows
repository](https://github.com/neo4j-labs/arrows.app). It maintains the same
structure although we introduced new features. The repository is structured as a
`monorepo`, hosting both apps and libraries in the same codebase.

#### Apps

SchemaLink uses only one app, stored in the [`apps/arrows-ts`
directory](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/apps/arrows-ts).
The `arrows-ts` app contains (mostly) `TypeScript` code that handles the
visual `React` components, as well as the `Redux` store.

#### Libraries

There are many libraries hosted in the webapp repository, in the [`libs`
directory](https://github.com/AnacletoLAB/schemalink-webapp/tree/main/libs).
Specifically:

- The `api` library is an adapter to the [`schemalink-api`
  project](https://github.com/AnacletoLAB/schemalink-api)
- The `graphics` library provides the logic for rendering and interacting with
  the canvas
- The `linkml` library handles LinkML schemas, converting the graph in the
  SchemaLink's canvas from and to this language
- The `model` library implements the data model for the main entities that are
  needed to run the webapp
- The `ontology-search` library is an adapter to an ontology search engine.
  Right now the search engine that the library uses is
  <https://www.ebi.ac.uk/ols4/>
- The `selectors` library gathers some `Redux` selectors that are generic
  enough to be useful for any app

### The API

{: .info }

> - Swagger docs: <https://schemalink.anacleto.di.unimi.it/api/docs>
> - Repository: <https://github.com/AnacletoLAB/schemalink-api>
> - Main technologies: [Python](https://docs.python.org/3/) and
>   [FastAPI](https://fastapi.tiangolo.com/)
> - Run locally - requires Python:
>
>   ```shell
>   pip install -r requirements
>   fastapi dev main.py
>   ```

The API project runs alongside the webapp and provides useful endpoints to
enable the webapp's features. This includes exposing useful functionalities from
the [linkml python library](https://pypi.org/project/linkml/), to assist the
webapp in handling linkml schemas.

### The deployment

{: .info }

> - Repository: <https://github.com/AnacletoLAB/schemalink-deploy>
> - Main technologies:
>   [Ansible](https://docs.ansible.com/ansible/latest/index.html),
>   [Docker](https://docs.docker.com/),
>   [Traefik](https://doc.traefik.io/traefik/).

SchemaLink is deployed as a docker compose project. To achieve that, both the
webapp and the api offer a `Dockerfile`. On each tag on the main branch, the
docker image is built by a GitHub action and pushed to the GitHub container
registry. A `Traefik` container can also be included in the docker compose
project, acting as a reverse proxy and taking care of routing and securing the
connection. The deployment is automated using an `Ansible` playbook.

### The docs

{: .info }

> - Repository: <https://github.com/AnacletoLAB/schemalink-docs>
> - Main technologies: [Jekyll](https://jekyllrb.com/docs/),
>   [Markdown](https://www.markdownguide.org/), [Just the
>   Docs](https://just-the-docs.github.io/just-the-docs/).
> - Run locally - requires Ruby:
>
>   ```shell
>   gem install jekyll bundler
>   bundle exec jekyll serve
>   ```

`Just the Docs` is used to generate this website. To update this website, it
is enough to commit and push changes to the docs project. A GitHub action will
run on the latest commit on the main branch, building the website using
`Jekyll` and deploying it using `GitHub pages`.
