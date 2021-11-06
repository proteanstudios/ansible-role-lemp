Pros - LEMP roles (PHP 8)
========

This repo temporary support Centos 7 and 8 only. 
We are plaining to add Ubuntu 20.04 ASAP! 

In here, you'll got strong support. So, don't hesitate to write down your issue.

How to run script 
==========

- Create an `requirements.yml` file with bellowed content
```
- geerlingguy.composer
- geerlingguy.mysql
- pros.lemp
```
- Run `ansible-galaxy install -r requirements.yml`
- Create a file, for exam: `install_lemp.yml` with bellowed content
```
---
- hosts: "{{ host }}"
  gather_facts: yes
  vars: 
    - mysql_db: t8tv
    - mysql_user: t8tv
    - mysql_pass: Lsj*63$&eUd
  roles: 
    - role: lemp
```
- Create corresponding .env file, e.g: `files/.env.staging` or `files/.env.production`, ect.. in here `staging` or `production` is host name.
- Run: `ansbile-playbook install_lemp.yml -e "host=staging"` // you can change host variable to anything that suitable for you.


Requirement
=========

This role includes
- geerlingguy.composer
- geerlingguy.mysql

so, you might need to install those roles as mentioned in `How to run script` section.

Default variables: 
========
```
load_nginx_confs: false // indicates whether to load nginx configs j2 template files or not 
create_mysql_db: true   // indicates to create new user and db 
install_composer: true  // indicates to install composer

# geerlingguy.mysql variables
mysql_root_password: Le%3(2kjsAD^K // default one. I strongly recommend you to change it per project.

#geerlingguy.mysql variables
composer_version_branch: '--2'
```

NOTE: 
===
- when `create_mysql_db: true`, you'll need define bellowed extra variables. It's required to create mysql user and database: 
```
mysql_db: <db_name>
mysql_user: <db_username>
mysql_pass: <db_user_password>
```