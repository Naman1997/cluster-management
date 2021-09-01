# cluster-management
Ansible playbooks for VM management

## Install the requirements
```
ansible-galaxy collection install -r requirements.yml
```

## Run different playbooks
```
ansible-playbook ./playbooks/<<Playbook Name>> --user <<Username>> --ask-become-pass
```
