# Docker Ansible Role

This Ansible role installs and configures Docker on Ubuntu hosts.

## Create the Role

Create the role directory using Ansible Galaxy:

```bash
ansible-galaxy role init docker
```

## Tasks

This role performs the following tasks:

* Updates the APT package cache.
* Installs the required dependencies:

  * `ca-certificates`
  * `curl`
* Creates the `/etc/apt/keyrings` directory.
* Downloads the official Docker GPG key.
* Detects the system architecture using `dpkg --print-architecture`.
* Configures the Docker APT repository using a Jinja2 template.
* Updates the APT package cache when the repository configuration changes (via a handler).
* Installs the following Docker packages:

  * `docker-ce`
  * `docker-ce-cli`
  * `containerd.io`
  * `docker-buildx-plugin`
  * `docker-compose-plugin`
* Enables and starts the Docker service.
* Adds the specified user to the `docker` group.

## Variable

| Variable      | Description                             | Required |
| ------------- | --------------------------------------- | :------: |
| `docker_user` | User to be added to the `docker` group. |    Yes   |

Example:

```yaml
docker_user: ubuntu
```

## Check Playbook Syntax

Before running the playbook, validate its syntax:

```bash
ansible-playbook --syntax-check playbook.yml
```

## Run the Playbook

Execute the playbook with:

```bash
ansible-playbook -i inventory.ini playbook.yml
```

