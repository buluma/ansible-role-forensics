# Ansible role [forensics](https://galaxy.ansible.com/ui/standalone/roles/buluma/forensics/documentation)

Install and configure forensics on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-forensics/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-forensics/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-forensics.svg)](https://github.com/buluma/ansible-role-forensics/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-forensics.svg)](https://github.com/buluma/ansible-role-forensics/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-forensics.svg)](https://github.com/buluma/ansible-role-forensics/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/forensics)](https://galaxy.ansible.com/ui/standalone/roles/buluma/forensics/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-forensics/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.forensics
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-forensics/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-forensics/blob/master/defaults/main.yml):

```yaml
---
# defaults file for forensics

# A directory where collected data can be stored locally.
forensics_local_storage_path: /tmp/forensics

# A list of commands to run.
forensics_command_list:
  - "journalctl -xe"
  - "ps -ef"
  - "lsof"
  - "systemctl status"
  - "netstat -an"
  - "netstat -tulpen"

# A list of directories to collect all files from.
forensics_directory_list:
  - "/var/log"
  - "/tmp"
  - "/var/tmp"
  - "/var/spool/cron"
  - "/var/spool/anacron"
  - "/etc/cron.d"
  - "/etc/cron.daily"
  - "/etc/cron.hourly"
  - "/etc/cron.monthly"
  - "/etc/cron.weekly"
  - "/var/spool/at"

# A list of files to collect.
forensics_file_list:
  - "/etc/passwd"
  - "/etc/group"
  - "/etc/shadow"

# A list of directories and patterns to collect.
forensics_specific_file_list:
  - path: "/root"
    pattern: ".authorized_keys"
  - path: "/root"
    pattern: ".bash_history"
  - path: "/root"
    pattern: ".history"
  - path: "/home"
    pattern: ".authorized_keys"
  - path: "/home"
    pattern: ".bash_history"
  - path: "/home"
    pattern: ".history"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-forensics/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-forensics/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/repository/docker/buluma/alpine/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/buluma/amazonlinux/general)|Candidate|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|8|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|all|
|[opensuse](https://hub.docker.com/repository/docker/buluma/opensuse/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-forensics/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-forensics/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-forensics/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

