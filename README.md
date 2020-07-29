# Redash

This [Ansible](https://www.ansible.com) role installs [Redash](https://redash.io) based on [Docker CE][https://www.docker.com]

## [Requirements](#requirements)

* Access to a repository containing packages, likely on the internet.
* A recent version of Ansible.
* Access to a [PostgreSQL](https://postgresql.org) server.

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- src: geerlingguy.pip
- src: geerlingguy.docker
```

## Example Playbook

```yaml
---
- name: Install redash
  hosts: all
  become: yes
  
  roles:
    - role: geerlingguy.pip
    - role: geerlingguy.docker
    - role: asabaini.redash
```

## License

BSD 2-Clause License

## TODO

* configure [mail server](https://redash.io/help/open-source/setup#Mail-Configuration)

## Author Information

[Alberto Sabaini](https://github.com/asabaini/)
