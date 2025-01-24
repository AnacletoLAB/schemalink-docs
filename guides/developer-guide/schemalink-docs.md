---
title: SchemaLink Docs
parent: Developer Guide
layout: default
---

## SchemaLink Docs

{: .info }

> - Repository: <https://github.com/AnacletoLAB/schemalink-docs>
> - Main technologies: [Jekyll](https://jekyllrb.com/docs/),
>   [Markdown](https://www.markdownguide.org/), [Just the
>   Docs](https://just-the-docs.github.io/just-the-docs/).
> - Run locally - needs Ruby:
>
>   ```shell
>   gem install jekyll bundler
>   bundle exec jekyll serve
>   ```

### Change the content of the website

To change the content of the website, edit the corresponding markdown file.

{: .info }

> You can use GitHub online editor to edit the content of the website:
>
> - Navigate to the corresponding markdown file.
> - Click on the pencil icon to edit the file.
> - When you're finished editing, click on the "Commit changes" button.

### Deploy a new version of the website

The website is built and deployed automatically by a GitHub action on the latest
commit of the `main` branch. To deploy a new version of the website, commit your
changes and merge/push the to the `main` branch.

### Configure the website

All of the configuration for this website is stored in the
[`_config.yml`](https://github.com/AnacletoLAB/schemalink-docs/blob/main/_config.yml)
file. For extensive details on which configurations options are available, refer
to:

- the [Jekyll documentation](https://jekyllrb.com/docs/configuration/).
- the [Just the Docs
  documentation](https://just-the-docs.github.io/just-the-docs/docs/configuration/).
