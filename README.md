# Redash

This [Ansible](https://www.ansible.com) role installs [Redash](https://redash.io) based on [Docker CE][https://www.docker.com]

## [Requirements](#requirements)

* Access to a repository containing packages, likely on the internet.
* A recent version of Ansible.
* Access to a [PostgreSQL](https://postgresql.org) server.
* docker
* docker-compose

## Role Variables

* `redash_install_path`: defaults to `/opt/redash`
* `redash_docker_image`: defaults to `redash/redash`, but it could be a fork such as `mozilla/redash`
* `redash_version`: check for available tags on [Redash official Docker Hub](https://hub.docker.com/r/redash/redash/tags) or [Mozilla Docker Hub](https://hub.docker.com/r/mozilla/redash/tags)
* `postgres_user`: defaults to `postgres`
* `postgres_url`: defaults to `localhost`
* `postgres_db_name`: defaults to `postgres`
* `initialize_database`: defaults to `true` **WARNING: This option will delete any existing data from previous redash installation.**

The following secrets should not be committed in the repository. Use `--extra-vars` to set them at runtime.

* postgres_password
* cookie_secret
* secret_key

## Example Playbook

```yaml
---
- name: Install redash
  hosts: all
  become: yes
  
  roles:
    - role: asabaini.redash
```

```bash
export POSTGRES_PASSWORD=$(pwgen -1s 32)
export COOKIE_SECRET=$(pwgen -1s 32)
export SECRET_KEY=$(pwgen -1s 32)
ansible-playbook -i inventory --extra-vars "postgres_password=${POSTGRES_PASSWORD} cookie_secret=${COOKIE_SECRET} secret_key=${SECRET_KEY}" playbook.yml
```

## License

BSD 2-Clause License

## TODO

* configure [mail server](https://redash.io/help/open-source/setup#Mail-Configuration)
* external redis
* local postgres

## Author Information

[Alberto Sabaini](https://github.com/asabaini/)
