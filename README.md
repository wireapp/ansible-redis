## ansible-redis

Ansible role to install a redis cluster supervised by systemd. Includes the following:

* disables swap.

* disables gettys when running in molecule.

* installs three nodes of redis in a master-slave-slave configuration. Failover using Sentinels is tested.

**Status: active development**

[![Build Status](https://travis-ci.org/wireapp/ansible-redis.svg?branch=master)](https://travis-ci.org/wireapp/ansible-redis)

<!-- vim-markdown-toc GFM -->

* [Ansible Requirements](#ansible-requirements)
* [Platforms](#platforms)
* [License](#license)
* [Development Setup](#development-setup)


## Ansible Requirements

- ansible >= 2.4 (>= 2.7.9 recommended) (2.7.1 tested)

For a list of all variables, see `defaults/main.yml`.

## Platforms

- Currently tested with ubuntu 18.04.

## License

AGPL. See [LICENSE](LICENSE)

## Development setup

Install [molecule](https://github.com/ansible/molecule). E.g. ensure you have docker installed, then, using a virtualenv, `pip install molecule ansible docker`.

* `molecule converge` to run the playbook against docker containers. If something fails, `molecule --debug converge` shows error details.
* `molecule lint` and `molecule syntax` can be used to get feedback on your yaml changes.
* `molecule test` to destroy + converge + converge again for idempotence + destroy

If you want 'mocule converge' to be run each time you save a file in this repository, install entr, then run 'make'.

* troubleshooting: [this issue](https://github.com/ansible/ansible/issues/43884) has been observed with molecule, ansible 2.7 and docker. Workaround was to downgrade to ansible 2.5.



