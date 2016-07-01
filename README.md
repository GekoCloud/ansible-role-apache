apache
======

This role installs and configures apache using [ondrej repo](https://launchpad.net/~ondrej/+archive/ubuntu/apache2)

Role Variables
--------------

- `apache_init_system`: OS init system. Docker phusion/baseimage uses 'runit'. (default 'upstart')
- `apache_user`: User apache will run as (default: 'www-data')
- `apache_group`: Group apache will run as (default: apache_user)
- `apache_listen_port`: Port apache will listen (default: '80')
- `apache_timeout`: The number of seconds before receives and sends time out (default: '300')
- `apache_enable_keepalive`: Whether or not to allow persistent connections (default: True)
- `apache_maxkeepaliverequests`: The maximum number of requests to allow during a persistent connection (default: '100')
- `apache_keepalivetimeout`: Number of seconds to wait for the next request from the same client on the same connection (default: '5')
- `apache_enable_hostnamelookups`: Whether or not to log the names of clients (default: False)
- `apache_loglevel`: Severity of messages logged to the error_log (default: ''warn')
- `apache_docroot`: Document root (default: '/var/www')
- `apache_mods_enabled`: List of apache modules to enable (default: [])
- `apache_mods_disabled`: List of apache modules to disable (default: [])
- `apache_confs_enabled`: List of apache confs to enable (default: [])
- `apache_confs_disabled`: List of apache confs to disable (default: [])
- `apache_sites_enabled`: List of apache sites to enable (default: [])
- `apache_sites_disabled`:List of apache sites to disable (default: [ '000-default' ])

Example Playbook
----------------

    - hosts: servers
      vars:
        mods_enabled:
          - userdir
      roles:
        - { 
          role: 'apache',
          apache_docroot: '/mnt/www',
          apache_mods_enabled: '{{ mods_enabled }}'
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-apache.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-apache)
