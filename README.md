# [cron](#cron)

Install cron and scedule jobs on your system.

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/robertdebock/ansible-role-cron/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-cron/actions)|[![gitlab](https://gitlab.com/robertdebock/ansible-role-cron/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-cron)|[![quality](https://img.shields.io/ansible/quality/39153)](https://galaxy.ansible.com/robertdebock/cron)|[![downloads](https://img.shields.io/ansible/role/d/39153)](https://galaxy.ansible.com/robertdebock/cron)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-cron.svg)](https://github.com/robertdebock/ansible-role-cron/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/verify.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Verify
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: ansible-role-cron
      cron_jobs:
        - name: requested job
          job: "ls -alh > /dev/null"
        - name: requested job by the minute
          minute: "23"
          job: "ls -alh > /dev/null"
        - name: requested job by the hour
          hour: "23"
          job: "ls -alh > /dev/null"
        - name: requested job by the weekday
          weekday: "1"
          job: "ls -alh > /dev/null"
        - name: requested job by specific user
          hour: "23"
          job: "ls -alh > /dev/null"
          user: "root"
        - name: requested job every 5 minutes
          minute: "*/5"
          job: "ls -alh > /dev/null"
```

The machine needs to be prepared in CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for cron

# The shell to use for running cronjobs.
cron_shell: /bin/bash

# The path to set for running jobs.
cron_path: /sbin:/bin:/usr/sbin:/usr/bin

# The address where mails should be sent to.
cron_mailto: root
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-cron/blob/master/requirements.txt).

## [Status of requirements](#status-of-requirements)

The following roles are used to prepare a system. You may choose to prepare your system in another way, I have tested these roles as well.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions)|[![Build Status GitLab ](https://gitlab.com/robertdebock/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/ansible-role-cron/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|alpine|all|
|amazon|Candidate|
|el|8|
|debian|buster, bullseye|
|fedora|all|
|opensuse|all|
|ubuntu|focal, bionic|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.



If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-cron/issues)

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.

- [cadusk](https://github.com/cadusk)
- [RealOrangeOne](https://github.com/RealOrangeOne)

## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
