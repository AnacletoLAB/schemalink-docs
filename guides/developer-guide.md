---
title: Developer guide
parent: Guides
layout: default
---

The SchemaLink project is made up of a number of components, all of which fall
under [the SchemaLink GitHub organization](https://github.com/SchemaLink).

## The webapp

{: .important-title }
> In a glance
>
> - Repository: <https://github.com/SchemaLink/webapp>.
> - Main technologies: [Node](https://nodejs.org/docs/latest/api/),
>   [Vite](https://vite.dev/guide/),
>   [TypeScript](https://www.typescriptlang.org/docs/), JavaScript,
>   [React](https://react.dev/learn), [Redux](https://redux.js.org/usage/) and
>   [Semantic UI React](https://react.semantic-ui.com/).
> - Run locally - needs Node and npm:
>
>   ```shell
>   npm install
>   npx nx serve arrows-ts
>   ```

## The API

{: .important-title }
> In a glance
>
> - Repository: <https://github.com/SchemaLink/api>.
> - Main technologies: [Python](https://docs.python.org/3/) and
>   [FastAPI](https://fastapi.tiangolo.com/).
> - Run locally - needs Python:
>
>   ```shell
>   pip install -r requirements
>   fastapi dev main.py
>   ```

## The deployment

{: .important-title }
> In a glance
>
> - Repository: <https://github.com/SchemaLink/deploy>.
> - Main technologies:
>   [Ansible](https://docs.ansible.com/ansible/latest/index.html),
>   [Docker](https://docs.docker.com/),
>   [Traefik](https://doc.traefik.io/traefik/).

## The docs

{: .important-title }
> In a glance
>
> - Repository: <https://github.com/SchemaLink/docs>.
> - Main technologies: [Jekyll](https://jekyllrb.com/docs/),
>   [Markdown](https://www.markdownguide.org/), [Just the
>   Docs](https://just-the-docs.github.io/just-the-docs/).

The docs project is used to generate this website. To update this website, it's
enough that you commit and push your changes to the docs project. A GitHub
action will run on the latest commit on the main branch, building the website
using Jekyll and deploying it using GitHub pages.
