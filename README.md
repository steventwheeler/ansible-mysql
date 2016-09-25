MySQL vendors for Debian Ansible role
======================================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-HanXHX.mysql-blue.svg)](https://galaxy.ansible.com/HanXHX/mysql) [![Build Status](https://travis-ci.org/HanXHX/ansible-mysql.svg?branch=master)](https://travis-ci.org/HanXHX/ansible-mysql)

Install and configure MySQL or MariaDB or Percona Server. Manage replication (master/slave). Create users and databases.

Requirements
------------

None.

Role Variables
--------------

- `mysql_origin`: origin of the package ("default" or "upstream")
- `mysql_vendor`: "mysql", "mariadb", "mariadb\_galera" (only with MariaDB upstream 10.1) or "percona"

### Configuration

- `mysql_root_password`: root password (should be protected with [vault](http://docs.ansible.com/playbooks_vault.html))

If you need a feature you can't configure, you can use this list. These config will go to `/etc/mysql/conf.d/01-extra`.

- `mysql_extra_config`: key/value hash see [default vars file](defaults/main.yml)

### Databases

- `mysql_databases`: list...


### Users

Example:

```
mysql_users:
  - name: 'kiki'
    password: '123'
    priv: hihi.*:ALL
    host: '%'
```

Check "priv" syntax in [mysql_user module documentation](http://docs.ansible.com/mysql_user_module.html)

### Packaging

- `mariadb_version`: 10.0 / 10.1 / 10.2
- `mariadb_repository`: MariaDB upstream APT repository (see: [MariaDB repositories tool](http://mariadb.org/mariadb/repositories/))
- `percona_version`: 5.5 / 5.6 / 5.7
- `percona_repository`: Percona upstream APT repository (see: [Percona APT doc](http://www.percona.com/doc/percona-server/5.5/installation/apt_repo.html))

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: HanXHX.mysql, mysql_origin: 'upstream', mysql_vendor: 'mariadb' }

License
-------

GPLv2

Author Information
------------------

- You can find many other roles in my GitHub "lab": https://github.com/HanXHX/my-ansible-playbooks
- All issues, pull-request are welcome :)
- Few code come from [geerlingguy](https://github.com/geerlingguy)

