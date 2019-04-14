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
  version: 'v3.3.0'
```

## Configurations

See
[defaults/main.yml](https://github.com/spk/ansible-docker-debian/blob/master/defaults/main.yml)

The defaults will install package from docker.com if you want to use
[Debian](https://packages.debian.org/buster/docker.io) official package use:

```
docker_use_debian_repository: true
docker_package: docker.io
docker_debian_version: "{{ docker_version }}+dfsg1-5+b10"
docker_dockerd_path: /usr/sbin/dockerd
```

## Dependencies

None

## License

BSD

Copyright (c) 2016-2019 Laurent Arnoud <laurent@spkdev.net>

---
[![Build](https://img.shields.io/travis/spk/ansible-docker-debian.svg)](https://travis-ci.org/spk/ansible-docker-debian)
[![Ansible Galaxy](https://img.shields.io/ansible/role/11888.svg)](https://galaxy.ansible.com/spk/docker-debian/)
