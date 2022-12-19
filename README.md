# EFK Stack with docker

This folder contains a configuration that deploys a EFK Stack with docker. 

You can also install individual stack components.
To do this, you need to change the value of the variable or run the desired playbook.

```yml
# what should be installed
# elasticsearch + kibana + fluentd
must_efk_installed: false

# elasticsearch + kibana
must_ek_installed: false

# fluentd
must_f_installed: false
```

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
cd /home/ubuntu/
git clone https://gitlab.com/adv-public/skillbox-diplom/infrastructure/ansible/install-docker.git
cd /home/ubuntu/install-docker
ansible-playbook playbooks/pl_install_docker_local.yml

# echo "Deploying Fluentd..."
cd /home/ubuntu/
git clone https://gitlab.com/adv-public/skillbox-diplom/infrastructure/ansible/setup-efk.git
cd /home/ubuntu/setup-efk/
ansible-playbook playbooks/pl_setup_f_local.yml
```



Clean up when you're done:

```shell
# echo "Destroy EFK Stack..."
cd /home/ubuntu/setup-efk/
ansible-playbook playbooks/pl_delete_efk_local.yml
```