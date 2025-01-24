---
title: SchemaLink Deploy
parent: Developer Guide
layout: default
---

## SchemaLink Deploy

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

### Deploy a different/new version of the webapp/API

Which version of the webapp/API is currently deployed is specified in the
[`docker-compose.yml`](https://github.com/AnacletoLAB/schemalink-deploy/blob/main/roles/schema-link/templates/docker/docker-compose.yml)
file. To deploy a different/new version, update the `image` property of the
`webapp` or `api` service.

{: .warning }

Not all versions of the webapp are compatible with all versions of the API, and
viceversa.

After doing so, run the playbook as described in the
[README.md](https://github.com/AnacletoLAB/schemalink-deploy/tree/main) file.

### Deploy a new instance of SchemaLink

To deploy a new instance of SchemaLink, add a new entry to the
[`inventory/hosts.yml`](https://github.com/AnacletoLAB/schemalink-deploy/blob/main/inventory/hosts.yml)
file. Then, if needed, create a new configuration file in the
[host_vars](https://github.com/AnacletoLAB/schemalink-deploy/tree/main/host_vars)
directory. The filename should be the same as the hostname in the
`inventory/hosts.yml` file.

{: .info }

If you don't create a dedicated configuration file, the new instance will use
the variables defined in the
[`defaults/main.yml`](https://github.com/AnacletoLAB/schemalink-deploy/blob/main/roles/schema-link/defaults/main.yml)
file. Note that in creating a dedicated configuration file you don't have to
override all of the variables: you can specify some, and inherit the rest from
the defaults.

### Enable/disable OpenAI features

To enable/disable OpenAI features for a specific deployment, set the
`openai_enabled` variable in the appropriate configuration file of the
[host_vars](https://github.com/AnacletoLAB/schemalink-deploy/tree/main/host_vars)
directory.

### Change which ports to use for the webapp/API

To change which port the webapp/API should listen to, set the
`webapp_port`/`api_port` variable in the appropriate configuration file of the
[host_vars](https://github.com/AnacletoLAB/schemalink-deploy/tree/main/host_vars)
directory.

### Change secrets

This applies to:

- All of the OpenAI configuration variables:
  - `OPENAI_API_KEY`: the API key to interact with OpenAI.
  - `OPENAI_ASSISTANT_ID`: the ID of the assistant currently in use.
  - `OPENAI_THREAD_ID`: the ID of the assistant's thread currently in use.
- `GHCR_TOKEN`: the personal access token used to access the GitHub container
  registry.

Secrets are managed using
[`ansible-vault`](https://docs.ansible.com/ansible/latest/cli/ansible-vault.html).
To change a secret, you need to first encrypt it using:

```shell
ansible-vault encrypt_string --ask-vault-password <string-to-encrypt>
```

This command will prompt you to input the vault password.

{: .warning }

Only maintainers of the project should have access to the vault password!

Use the output of this command to replace the current value of the secret in the
appropriate configuration file.
