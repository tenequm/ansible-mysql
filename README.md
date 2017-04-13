Ansible Role: MySQL
=========

This simple role installs MySQL 5.7 on Ubuntu Xenial and sets password for `root` user.

Role Variables
--------------

There are only two variables:
```
mysql_root_password: ''
```
You can set preferred password for MySQL `root` user.
```
mysql_root_hosts: []
```
You can define from which hosts can be gained access with `root` user.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: 1nfinitum.mysql, mysql_root_password: toor }

License
-------

MIT

Author Information
------------------

This role was created in 2017 by [Mykhaylo Kolesnik](http://github.com/1nfinitum).
