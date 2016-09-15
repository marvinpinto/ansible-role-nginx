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


Role Variables
--------------

``` yaml
# Directory that contains your default nginx html files (i.e. 50x.html,
# index.html, etc)
nginx_static_html_directory: 'default_static_files'

# Replace the contents of this variable with your actual nginx.conf file
nginx_config_file: |
  user root;
  worker_processes 1;
  error_log /var/log/nginx/error.log warn;
  pid /var/run/nginx.pid;
  events {
      worker_connections  1024;
  }
  http {
      include       /etc/nginx/mime.types;
      default_type  application/octet-stream;
      log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                        '$status $body_bytes_sent "$http_referer" '
                        '"$http_user_agent" "$http_x_forwarded_for"';
      access_log  /var/log/nginx/access.log  main;
      sendfile        on;
      keepalive_timeout  65;
      include /etc/nginx/conf.d/*.conf;
  }
```


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
