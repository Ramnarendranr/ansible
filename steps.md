Getting started with ansible:


Prerequisite for ansible:
1. enable password less authentication

First create 2 EC2 instances
one for main ansible and one tager ansible

connect to the ec2 instance

install ansible in the machine

**sudo apt update**
**sudo apt install ansible**


enable password less authentication to conncet to a target server
**ssh-keygen**

ls /home/ubuntu/.ssh/
authorized_keys  id_rsa  id_rsa.pub  known_hosts

**id_rsa-> private key**
**id_rsa.pub -> public key**

share only the public key.

connect to second ec2 instance:
create a public key in second instance
**ssh-keygen**

Now you have public keys in both the instances.
copy the content of public key id_rsa.pub from first instance to the /home/ubuntu/.ssh/authorized_keys file in second instance

once you've copied the key, connect to second ec2 instance in first instance

in first instance:
ssh <private_ip_of_target_ansible_instance>

Now you should be able to connect to the target ansible ec2 instance from first instance ,

come back to first instance

How to write ansible Playbook:
create inventory file to store private ip of the target server

ansible adhoc commands is for one or two commands and ansible playbook is for multiple ansible commands

cat inventory
10.0.6.224

ansible adhoc commands:

**ansible -i inventory all -m "shell" -a "touch devopsclass"**
create a file in target servor

to execute ansible playbook
use
ansible-playbook -i inventory <playbook_file.yml>