# percona_toolkit

[![License](https://img.shields.io/badge/license-New%20BSD-blue.svg?style=flat)](https://raw.githubusercontent.com/saucelabs-ansible/percona_toolkit/master/LICENSE)
[![Build Status](https://travis-ci.org/saucelabs-ansible/percona_toolkit.svg?branch=master)](https://travis-ci.org/saucelabs-ansible/percona_toolkit)

[![Platform](http://img.shields.io/badge/platform-ubuntu-dd4814.svg?style=flat)](#)

[![Project Stats](https://www.openhub.net/p/saucelabs-ansible-percona_toolkit/widgets/project_thin_badge.gif)](https://www.openhub.net/p/saucelabs-ansible-percona_toolkit/)

Ansible role to setup the [Percona Toolkit for MySQL](https://www.percona.com/software/mysql-tools/percona-toolkit).


## Tests

| Family | Distribution | Version | Test Status |
|:-:|:-:|:-:|:-:|
| Debian | Ubuntu  | Trusty  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |


## Requirements

- ansible >= 1.9.4


## Role Variables

- **debug**: flag to run debug tasks (default: false).
- **percona_toolkit_configuration**: percona toolkit tools default configuration.
- **percona_toolkit_version**: the version to be installed.

Unless stated otherwise
a default value is provided for each of the variables mentioned above
in `defaults/main.yml`.


## Dependencies

- [percona_apt](https://github.com/saucelabs-ansible/percona_apt)


## Playbooks

Example:

    - hosts: servers
      vars:
        debug: yes

      roles:
         - role: percona_toolkit
           percona_toolkit_configuration:
             pt-summary: |
               user=the_user
               password=secret
           tags: [ percona, toolkit ]


## Tags

- **configuration**: configuration tasks.
- **debug**: role variables debug task.
- **installation**: installation tasks.
- **validation**: role variables validation task.


## Test

To run the tests you will need to install:

- [tox](https://tox.readthedocs.org/)
- [vagrant](https://www.vagrantup.com/)

To run all tests against all pre-defined OS/distributions * ansible versions:

```
$ tox
```

To run tests for `trusty64`:

```
$ cd tests
$ bash test_idempotence.sh --box trusty64.vagrant.dev
# log file will be stores under tests/log
```

To perform debugging on a specific environment:

```
$ cd tests
$ vagrant up trusty64.vagrant.dev

# to provision using the test.yml playbook (as many time as you need)
$ vagrant provision trusty64.vagrant.dev

# to access the Vagrant box
$ vagrant ssh trusty64.vagrant.dev
```


## Links

- [Percona Toolkit for MySQL](https://www.percona.com/software/mysql-tools/percona-toolkit)


## Author Information

- [steenzout](https://github.com/steenzout/)
