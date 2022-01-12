Role Name
=========

Роль для установки kibana на хостах с ОС: Debian, Ubuntu, CentOS, RHEL.

Requirements
------------

Поддерживаются только ОС семейств debian и EL.

Role Variables
--------------

| Variable name | Default | Description |
|-----------------------|----------|-------------------------|
| kibana_version | "7.14.0" | Параметр, который определяет какой версии kibana будет установлен |
| elastic_host | "localhost | IP адрес хоста elasticsearch |

Dependencies
------------



Example Playbook
----------------


    - hosts: all
      roles:
         - { role: kibana-role }

License
-------

MIT

Author Information
------------------
