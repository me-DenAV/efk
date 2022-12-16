# Web Server denav.net

This folder contains a configuration that deploys a monitoring of web servers 

## Pre-requisites

* You must have [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) installed on your computer.

## Quick start

Config the Web-Server with Ansible:

Ansible code one that deploys everything you need to run service - docker and related.

```bash
# echo "Install Ansible ..."
# exec > >(tee /var/log/user-data.log|logger -t user-data -s 2>/dev/console) 2>&1
cd /home/ubuntu/
sudo apt update -y
sudo apt install python3-pip -y
sudo apt install ansible -y

# echo "Install Docker ..."
git clone https://gitlab.com/adv-public/skillbox-diplom/infrastructure/ansible/install-docker.git
cd /home/ubuntu/install-docker
ansible-playbook playbooks/pl_install_docker_local.yml

# echo "Deploying application..."
cd /home/ubuntu/
git clone https://gitlab.com/adv-public/skillbox-diplom/infrastructure/ansible/setup-monitoring.git
cd /home/ubuntu/setup-monitoring/
ansible-playbook playbooks/pl_monitoring_local.yml
```
