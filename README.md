# Ansible-Project
Hosting webpage on servers using Ansible

# Installation of Ansible (run one-by-one)
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible

# Modify Host file
Path=> /etc/ansible/hosts

[devservers]
dev_1 ansible_host=52.91.160.153
---OR---
[prodservers]
prod_1 ansible_host=52.91.162.153
prod_2 ansible_host=52.91.162.154

[servers:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/.ssh/ansible-all-access-key.pem
---OR---
[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/.ssh/ansible-all-access-key.pem

# Inventory list
* can be use to check which servers are available and with which variable and keys.
ansible-inventory --list -y

# Command to run playbook
ansible-playbook <file_name.yml>
* To see console output - use verbos(-v)
ansible-playbook -v <file_name.yml>

# ad-hoc commands
* ad-hoc commands are great for tasks we repeat rarely.
* -a is used for ad-hoc commands.

ansible all-a "df-h" -u ubuntu
ansible servers-a "uptime" -u ubuntu

# Ansible modules are units of code that can control system resoureces or execute ststem commands.
* -m is used for modules
ansible all -m ping -u ubuntu 

