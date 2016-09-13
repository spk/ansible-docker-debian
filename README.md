# Ansible Docker Debian

Provides Docker Debian packages from <https://apt.dockerproject.org/repo>.

Support also Ubuntu with systemd.

## Why

* No ` curl https://get.docker.com/ | sh`, fully predictable
    and idempotent installation.
* Ability to change daemon arguments with [systemd override](https://docs.docker.com/engine/admin/systemd/),
    see
    [docker_daemon_options](https://github.com/spk/ansible-docker-debian/blob/master/defaults/main.yml#L14)

## Installation

```
ansible-galaxy install spk.docker-debian
```

## Configurations

See
[defaults/main.yml](https://github.com/spk/ansible-docker-debian/blob/master/defaults/main.yml)

# Dependencies

None

# License

(c) 2016 Laurent Arnoud <laurent@spkdev.net>

BSD

---
[![Build](https://img.shields.io/travis-ci/spk/ansible-docker-debian.svg)](https://travis-ci.org/spk/ansible-docker-debian)
[![Ansible Galaxy](https://img.shields.io/ansible/role/11888.svg)](https://galaxy.ansible.com/spk/docker-debian/)
