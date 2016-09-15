nginx
=====

[![Build Status](https://img.shields.io/travis/marvinpinto/ansible-role-nginx/master.svg?style=flat-square)](https://travis-ci.org/marvinpinto/ansible-role-nginx)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-nginx-blue.svg?style=flat-square)](https://galaxy.ansible.com/marvinpinto/nginx)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.txt)

Ansible Galaxy role to install and manage [NGINX](https://nginx.org).


Requirements
------------

This role has been tested on Ubuntu 14.04 and will likely only work on an
Ubuntu-like system.


Examples
--------

Install this module from Ansible Galaxy into the './roles' directory:
```bash
ansible-galaxy install marvinpinto.nginx -p ./roles
```

Use it in a playbook as follows:
```yaml
- hosts: '127.0.0.1'
  roles:
    - role: 'marvinpinto.nginx'
      become: true
```


Development
-----------
Use the supplied `Vagrantfile` for local development and testing (hint: `vagrant up --provision`)
