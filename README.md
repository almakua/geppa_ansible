# geppa_ansible

Teh variables and configurations are divided in staging and production inventories.

You should modify them as you need it, and then execute the playbook

~~~bash
$ ansible-playbook -i inventories/production provision.yml -u <NEEN_USER>
~~~

or for staging

~~~bash
$ ansible-playbook -i inventories/staging provision.yml -u <NEEN_USER>
~~~


