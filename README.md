# ansible-ubuntu-amp
install apache, mysql and php on a remote server using ansible

## Preamble
I often find myself having to setup a LAMP server and whilst this is fairly straightforward it seemed a good idea to automate the process to save time for the next time around.
This repository was developed on a linux desktop running Ubuntu 16.04 so if you are running on something else then the installation details will almost certainly be different.
The target server was also running ubuntu 16.04 and so for the moment this repo will only be tested against this flavour of server.

## Prerequisites
In the unlikely event that you don't have an ssh client on your control machine then you can install it using the following command:
```
sudo apt-get install openssh-client
```
You will also need ansible to be installed and you can find the instructions at: http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#id14
This repository was developed with ansible version 2.5.0 installed on the control machine.
You will need the username with sudo privileges on the target server.

## Information you need to provide
You will need to add your server IP to the XXX file.

## Example
```
ansible-playbook servers.yml -i production
```
