# Ansible Docker Debian

Provides Docker Debian packages from <https://download.docker.com/linux/>.

Support also Ubuntu with systemd.

## Why

* No `curl | sh`, fully predictable and idempotent installation.
* Ability to change daemon arguments with
    [systemd override](https://docs.docker.com/engine/admin/systemd/), see
    [docker_daemon_options](https://github.com/spk/ansible-docker-debian/blob/master/defaults/main.yml#L14)

## Installation


### Command line

```
ansible-galaxy install spk.docker-debian
```

### Requirements

```
- src: spk.docker-debian
  version: 'v3.1.0'
```

## Configurations

See
[defaults/main.yml](https://github.com/spk/ansible-docker-debian/blob/master/defaults/main.yml)

## Dependencies

None

## License

BSD

Copyright (c) 2016-2018 Laurent Arnoud <laurent@spkdev.net>

---
[![Build](https://img.shields.io/travis-ci/spk/ansible-docker-debian.svg)](https://travis-ci.org/spk/ansible-docker-debian)
[![Ansible Galaxy](https://img.shields.io/ansible/role/11888.svg)](https://galaxy.ansible.com/spk/docker-debian/)
