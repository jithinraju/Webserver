# APACHE webserver setup on Redhat based Server

Playbook for installing apache and PHP along with the index pages

```bash

---
- name: 'install'
  hosts: amazon
  become: yes
  tasks:
    - name: 'lamp'
      yum: name=httpd,php  state=present

    - name: 'index.html'
      copy: content='<h1>It Works</h1>' dest=/var/www/html/index.html

    - name: 'index.php'
      copy: content='<?php phpinfo(); />' dest=/var/www/html/index.php

    - name: 'restart'
      service: name=httpd state=restarted enabled=yes


```
