docker
======

[![Build Status](https://travis-ci.org/marvinpinto/ansible-role-docker.svg?branch=master)](https://travis-ci.org/marvinpinto/ansible-role-docker)

This Ansible role enables people to install the latest Docker on an Ubuntu-like
system. It also provides a handy library function to validate that the Docker
daemon is running and functional.

Requirements
------------

This role will only work on an Ubuntu-like system.

Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install marvinpinto.docker -p ./roles
```

Use it in a playbook as follows:
```yaml
- hosts: 'servers'
  tasks:
    - name: 'Ensure that we can connect to this host'
      ping:
  roles:
    - role: 'marvinpinto.docker'
      sudo: true
  tasks:
    - name: 'Ensure that the docker daemon is functional'
      sudo: true
      docker_ping:
      retries: 5
      delay: 10
      until: result|success
    - name: 'hello world'
      docker:
        name: 'helloworld'
        image: 'hello-world'
        state: 'started'
```

License
-------

[MIT](LICENSE.txt)

Author Information
------------------

- Marvin Pinto
