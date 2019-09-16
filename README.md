# geppa_ansible

## Purpose

This playbook has been made to ensure easy and simple deployoment of new sites for geppa infrastructure.
It is still a work in progress, since right now (2019-09-16) is still able to install varnish, and deploy certificates and site configs.
The goal will be to implemente a full playbook to install from scratch a new frontend for Geppa sites.

## Installation

You just need to have git and ansible (2.0 +) installed on your machine/server, and then you just have to clone the repo like so:
```bash
$ git clone <GIT_SERVER_URL>/geppa_ansible.git
```

## Configuration

The playbook is already structured in a way which can easily executed on both staging and production environment.

Inventories for the 2 envs have been already created and configured.

To configure the hosts on which the playbook is run against, you have to modify the file _*inventories/< ENV >/hosts*_ , specifiying on which group the server should reside.

The groups are:

|Group   	|Function   	|
|---	|---	|
|LB   	|LoadBalancer group, the server(s) in here are the one that usually just do reverse proxy for each one of the Geppa Sites   	|
|FE   	|FrontEnd group, in which servers that populates it are the one on which PHP runs   	|
|Gatewayed   	|Group dedicated solely for the hosts that need a bastion hosts to connect through to be reached. 	|

Each one of this groups have their own configuration yaml file in _*inventories/< ENV >/group_vars/< GROUP >.yml*_ , in which group specific configuration are explicitely set.

You should modify them as you need it, and then execute the playbook

## Usage

To execute the playbook, you have to have full sudo powers on the target server, since the playbook need to become root to be completed, and you have to specify the env's dedicated inventory, and input your neen user to ansible-playbook.

For production:

~~~bash
$ ansible-playbook -i inventories/production provision.yml -u <NEEN_USER>
~~~

and for staging:

~~~bash
$ ansible-playbook -i inventories/staging provision.yml -u <NEEN_USER>
~~~