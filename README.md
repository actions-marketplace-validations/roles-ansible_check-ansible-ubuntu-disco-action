[![Github Marketplace](https://raw.githubusercontent.com/roles-ansible/check-ansible-ubuntu-disco-action/master/.github/marketplace.svg?sanitize=true)](https://github.com/marketplace/actions/check-ansible-ubuntu-disco)
[![MIT License](https://raw.githubusercontent.com/roles-ansible/check-ansible-ubuntu-disco-action/master/.github/license.svg?sanitize=true)](https://github.com/roles-ansible/check-ansible-ubuntu-disco-action/blob/master/LICENSE)

 Check Ansible Ubuntu disco
=======================
This action allows you to test your ansible role or your playbook in a Docker Container with ``ubuntu:disco``.

```
ATTENTION

This action check currently does not work anymore.
Looks like Ubuntu disco is END OF Support.

Please feel free to fix it, if you need it!
```

## Usage
To use the action simply create an ``ansible-ubuntu-disco.yml`` *(or choose custom ``*.yml`` name)* in the ``.github/workflows/`` directory.

For example:

```yaml
name: Ansible check ubuntu:disco  # feel free to pick your own name

on: [push, pull_request]

jobs:
  build:

    runs-on: ubuntu-disco

    steps:
    # Important: This sets up your GITHUB_WORKSPACE environment variable
    - uses: actions/checkout@v2

    - name: ansible check with ubuntu:disco
      # replace "master" with any valid ref
      uses: roles-ansible/check-ansible-ubuntu-disco-action@master
      with:
        targets: "./"
        #  [required]
        #   Paths to your ansible role or playboox.yml you want to test
        #   Some Examples:
        #   targets: "role/my_role/"
        #   targets: "site.yml"
        #
        # group: ""
        #  [optional]
        #   When testing playbooks you have to tell ansible
        #   the group you that we write in our hosts file.
        #   example:
        #   group: 'servers'
        #
        # hosts: ""
        #  [optional]
        #   When testing playbooks you have to give one example
        #   host this action should use to test your playbook.
        #   > We only spawn one docker container that mean
        #   > we can only test one host at the time. Sorry
        #   some examples:
        #   hosts: 'localhost'
        #   hosts: 'srv01.example.com'
        #
        # requirements: ""
        #  [optional]
        #   When testing playbooks and you are using ansible galaxy,
        #   you may be interested in installing your requirements
        #   from ansible galaxy.
        #   To do this please provide us either the role name directly
        #   requirements: 'do1jlr.ansible_version'
        #   or your requiements.yml file.
        #   requirements: 'requirements.yml'
```

Alternatively, you can run the ansible check only on certain branches:

```yaml

on:
  push:
    branches:
    - stable
    - master
    - release/v*
```

or on various [events](https://help.github.com/en/articles/events-that-trigger-workflows)

<br/>

 Contributing
-------------
If you are missing a feature or see a bug. Please report it. Or - if you like - open a pull-request.

 License
----------
The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).

 Credits
--------------
The initial GitHub action has been created by [Stefan St??lzle](/stoe) at
[stoe/actions](https://github.com/stoe/actions).<br/>
It was used by ansible for lint checks at [ansible/ansible-lint-action](https://github.com/ansible/ansible-lint-action.git)<br/>
It was modified from [L3D](github.com/do1jlr) to check ansible roles.
