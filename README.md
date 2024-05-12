# ansible-docker-swarm
Docker swarm installation with ansible, for several different LInux distros.
It is tested with Rocky,CentOS , RedHat and Ubuntu

In inventory  file ***inventory.yaml*** you should change the IP addresses of your servers

First create an ssh key  ``` ssh-keygen -t ed25519 -C "ansible"``` /home/aca/.ssh/ansible

Then copy it to all servers

```ssh-copy-id -i /home/aca/.ssh/ansible.pub aca@192.168.122.201``` etc

 test to see if we have a connection with all servers
 
  ```ansible all -m ping --key-file /home/aca/.ssh/ansible --ask-become-pass```
 
 ```ansible-playbook playbook.yaml  -i inventory.yaml --key-file /home/aca/.ssh/ansible --ask-become-pass -u YourUser```
 
 Here you have to change ***YourUser*** with some real user name.

 This command will ask for the user's root password
