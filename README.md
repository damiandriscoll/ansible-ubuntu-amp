# ansible-ubuntu-amp
install apache, mysql and php on a remote server using ansible

## Preamble
This repository was developed on a linux desktop running Ubuntu 16.04 so if you are running on something else then the installation details will almost certainly be different.
The target server was also running ubuntu 16.04 and so for the moment this repo will only be tested against this flavour of server.

## Prerequisites
In the unlikely event that you don't have an ssh client on your control machine then you can install it using the following command:
```
sudo apt-get install openssh-client
```
You will also need ansible to be installed and you can find the instructions at: http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#id14
This repository was developed with ansible version 2.5.0 installed on the control machine.
You will need a username with sudo privileges on the target server.

## Information you need to provide
You will need to add your server IP(s) to a 'hosts' file.

**Example hosts file**
```
[webservers]
127.0.0.1

[dbservers]
127.0.0.1
```
You can copy hosts.example to hosts and then edit it as required.

You will also need the name of user on the remote machine that has sudo acess. This information is stored in the **ansible.cfg** file.

**Example ansible.cfg file**
```
[defaults]
remote_user=some-user-name
```
You can copy ansible.cfg.example to ansible.cfg and then edit it as required.

## Customisation

You may wish to install and / or enable more apache modules than just mom-php and mod-rewrite, and if so you
should edit **roles/apache/tasks/main.yml** as required.

You may wish to install more (or less) PHP libraries than the list provided by default, and if so you
should edit **roles/php/tasks/main.yml** as required.

If your MySQL configuration is different to the default installation then edit **roles/templates/my.cnf.j2** as required.

## Usage example
```
ansible-playbook amp.yml -i hosts --check --ask-pass --ask-become-pass
```
If you set up passwordless logins using ssh keys then you should omit the **--ask-pass** and **--ask-become-pass** arguments above.
