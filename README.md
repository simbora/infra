The goal of this project is to automate a series of deployment scripts by
using [puppet](https://puppetlabs.com/learn) language instead.

A brand new Ubuntu 14.04 LTS installation will be provided.

An agreement was made to use Ansible instead of Puppet because it does not require client installed on target machine, it only requires python which is one of the basic packets installed on clean machine.

Steps to provision target machine:

1. Install Ansible on your local system. Follow these instructions for Ubuntu based systems:
http://docs.ansible.com/intro_installation.html#latest-releases-via-apt-ubuntu

2. Clone this repo and create file called hosts in the project root directory with the following content:
'''
test1 ansible_ssh_host=178.62.144.132
'''
  - where:
    - test1 is ansible name for target machine
    - ansible_ssh_host is the target machines IP address

You can create as many as you wish separate target machines that you can use in later steps. You can also provision one machine from those defined at a time.

3. With terminal, go to the root directory of the project and issue the following command:
'''
ansible-playbook -i hosts playbooks/bootstrap.yml --user root --ask-pass
'''
There is documentation for ansible-playbook [here](http://linux.die.net/man/1/ansible-playbook)

In the example above, I have used the following switches:

  * --user - User on the remote machine
  * --ask-password - Providing the password for the remote machine using secured interactive shell

You can skip these switches if you manage to get ssh key access to target machines.
