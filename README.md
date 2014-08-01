Kippo Ansible Playbook
----------------------

This is an Ansible playbook to install [Kippo](
https://github.com/desaster/kippo) on Debian hosts.

The playbook will setup a node as a database server for kippo hosts to log
incoming attacks and will also setup multiple kippo hosts.

Process:
* download the latest Kippo version from desaster's repo
* create a `kippouser` account to run kippo
* change sshd port to 22422
* add an iptable rule to forward traffic from port 2222 to 22
* transfer kippo.cfg from this host to the remote hosts
* setup a database server so all kippo hosts log to that server

This is a very basic skeleton, feel free to mess around with it. I've only
tested it with Debian Wheezy and it seems to work. Keep in mind this is a proof
of concept playbook, so some stuff could be improved (e.g. mysql security).

How to use
----------

Edit the vars `db_host` and `db_password` in `group_vars/all` to reflect your
setup and run the playbook.