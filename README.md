# Installation

## Easy mode
```
apt-get update
apt install -y ansible
```

## Hard mode

"ansible-galaxy collection" installs the collections by default into ~/.ansible/collections/ansible_collections. This can be changed by setting the environment variable ANSIBLE_COLLECTIONS_PATHS.

You need to create a config file in ~/.ansible.cfg with the following content. 


```
apt update
apt install -y python3-pip
pip install -y vitualenv
virtualenv ansible_venv
source ansible_venv/bin/activate
pip install -r requirements.txt
ansible-galaxy collection install -r requirements.yml
```


# Quick start documentation for Ansible

- https://docs.ansible.com/ansible/latest/getting_started/index.html
- https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html


# How to run the playbook
To run the update against all hosts in the inventory file, run the following command:


```
ansible-playbook -i servers.yml apt-update.yml --ask-become-pass
```

"--ask-become-pass" is used to ask for the sudo password. It was renamed from "sudo" to "become" to be more generic across OSs.

# How to run the playbook on a specific host

```
ansible-playbook -i servers.yml apt-update.yml --ask-become-pass --limit <host>
```

OR

```
ansible-playbook -i servers.yml apt-update.yml --ask-become-pass --extra-vars "servers=<host or group name>"
```

"--extra-vars" is used to pass variables from the command line to the playbook. the variables are space delmited.

# How to run a role



