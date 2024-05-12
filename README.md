# ansible-docker-swarm
docker swarm installation with ansible

First create an ssh key  ``` ssh-keygen -t ed25519 -C "ansible"``` /home/aca/.ssh/ansible

Then copy it to all servers

```ssh-copy-id -i /home/aca/.ssh/ansible.pub aca@192.168.122.201``` etc

 test to see if we have a connection with all servers
 
  ```ansible all -m ping --key-file /home/aca/.ssh/ansible --ask-become-pass```
 
 ``` ansible-playbook playbook.yaml  -i inventory.yaml --key-file /home/aca/.ssh/ansible --ask-become-pass -u YourUser```
 
 here it asking for the user root password
