# Домашнее задание к занятию "8.4 Работа с Roles"

## Подготовка к запуску

### inventory
1. Добавить ip хостов в inventory/elk/hosts.yml
2. Указать версию ELK стека inventory/elk/group_vars/all.yml
3. Загрузить роли:
> ansible-galaxy install -r requirements.yml -p roles --force
4. Запустить plabook:
> ansible-playbook -i inventory/elk site.yml

### site.yml

```yml
---
- name: Add Elasticsearch # Разворачиваем роль elasticsearch на группу хостов elasticsearch
  hosts: elasticsearch
  roles:
    - elastic-role
- name: Add Kibana # Разворачиваем роль kibana на группу хостов kibana
  hosts: kibana
  vars:
    elastic_host: "{{ hostvars['el-instance']['ansible_facts']['default_ipv4']['address'] }}" # передаем ip адрес хоста с elasticsearch
  roles:
    - kibana-role
- name: Add filebeat # Разворачиваем роль filebeat на группу хостов app
  hosts: app
  vars:
    elastic_host: "{{ hostvars['el-instance']['ansible_facts']['default_ipv4']['address'] }}" # передаем ip адрес хоста с elasticsearch
    kibana_host: "{{ hostvars['k-instance']['ansible_facts']['default_ipv4']['address'] }}" # передаем ip адрес хоста с kibana
  roles:
    - filebeat-role
```

P.S. Необязательная часть задания пропущена.
