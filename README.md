# ansible-docker-swarm
Docker swarm installation with ansible, for several different Linux distros.
It is tested with Rocky,CentOS , RedHat and Ubuntu

For Ubuntu I added my user to docker group

- name: Ensure the current user (aca in this case) is added to Docker group if not already a member
  user:
    name: aca  # Replace with the actual username 
    group: docker
    append: true
  become: true



In inventory  file ***inventory.yaml*** you should change the IP addresses of your servers

First create an ssh key  ``` ssh-keygen -t ed25519 -C "ansible"``` /home/aca/.ssh/ansible  # I wrote my users home folder but you will write your user

Then copy it to all servers
I am using one Manager and two worker nodes

```ssh-copy-id -i /home/aca/.ssh/ansible.pub aca@192.168.1.25``` 
```ssh-copy-id -i /home/aca/.ssh/ansible.pub aca@192.168.1.26``` 
```ssh-copy-id -i /home/aca/.ssh/ansible.pub aca@192.168.1.27``` 

 test to see if we have a connection with all servers
 
  ```ansible all -m ping --key-file /home/aca/.ssh/ansible --ask-become-pass```

  Below is the command with which you start the playbook
 
 ```ansible-playbook playbook.yaml  -i inventory.yaml --key-file /home/aca/.ssh/ansible --ask-become-pass```
 
 Here you have to change ***YourUser*** with some real user name.

 This command will ask for the user's root password
