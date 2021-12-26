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
| filebeat_version | "7.14.0" | Параметр, который определяет какой версии kibana будет установлен |
| elastic_host | "localhost | IP адрес хоста elasticsearch |
| kibana_host | "localhost | IP адрес хоста kibana |

Dependencies
------------



Example Playbook
----------------


    - hosts: all
      roles:
         - { role: filebeat-role }

License
-------

MIT

Author Information
------------------
