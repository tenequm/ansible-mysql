Ansible Role: MySQL
=========
[![Build Status](https://travis-ci.org/tenequm/ansible-mysql.svg?branch=master)](https://travis-ci.org/tenequm/ansible-mysql)

This simple role installs MySQL 5.7 on Ubuntu Xenial and sets password for `root` user.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:
```
    - hosts: database
      roles:
        - role: tenequm.mysql
          become: yes
```
Role Variables
--------------
```
mysql_users:  # List
  - name: username # Username
    host: localhost # The 'host' part of username. Default is localhost.
    password: '' # User password as a string, can be omitted.
    priv: '' MySQL privileges. Can be omitted.
    state: absent # Whether user should exist. Default is `present`.
```
List of users to add. 
MySQL privileges string should be in the format: db.table:priv1,priv2. Multiple privileges can be specified by separating each one using a forward slash: db.table:priv/db.table:priv. The format is based on MySQL GRANT statement. Database and table names can be quoted, MySQL-style. If column privileges are used, the priv1,priv2 part must be exactly as returned by a SHOW GRANT statement. If not followed, the module will always report changes. It includes grouping columns by permission (SELECT(col1,col2) instead of SELECT(col1,SELECT(col2))).
```
mysql_databases: # List
  - name: dbname # Database name
    encoding: '' # Database encoding, can be omitted
    collation: '' # Database collation, can be omitted
    state: '' # Whether database should exist. Default is `present`.
```
List of databases to add. Takes `name`, `encoding`, `collation` and `state` parameters.
```
mysql_root_password: ''
```
You can set preferred password for MySQL `root` user. Default is `root`.
```
mysql_root_hosts: []
```
You can define from which hosts can be gained access with `root` user.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
    - hosts: servers
      roles:
         - { role: tenequm.mysql, mysql_root_password: toor }
```
License
-------

MIT

Author Information
------------------

This role was created in 2017 by [Mykhaylo Kolesnik](http://github.com/tenequm).
