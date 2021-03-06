The goal of this project is to automate a series of deployment scripts by
using ansible language.

Premise:
- Machines are provisioned with a brand new Ubuntu 14.04 LTS installation.

Steps to deploy a target machine:

 1. Install Ansible on your local system. Follow [these instructions for
 Ubuntu](http://docs.ansible.com/intro_installation.html#latest-releases-via-apt-ubuntu)
 based systems:
 1. Clone this repo and create a file called `hosts` in the project root
 directory with the following content, where `host_name` is the target machine
 name, and `host_ip` is the target machine IP address.

      [webservers]
      <host_name1> ansible_ssh_host=<host_ip1>
      <host_name2> ansible_ssh_host=<host_ip2>
      ...

 3. Deploy with the following command, where `--user` sets the login user and
 `--ask-pass` provides the password for such user (can be skipped if using ssh
 keys).

      ansible-playbook -i hosts site.yml --user root --ask-pass

 Mysql: Use `MYSQL_ROOT_PASSWD` environment variable to set the root password.

 OBS: make sure to unset some local variables that could be sent to remote
 machine and fail some of the installations (e.g., Create PostgreSQL cluster).

      unset LANGUAGE LC_ALL LC_TIME LC_MONETARY LC_CTYPE LC_ADDRESS LC_TELEPHONE LC_NAME LC_MEASUREMENT LC_IDENTIFICATION LC_NUMERIC LC_PAPER LANG
