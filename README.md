# cluster-management
[![Ansible Validation](https://github.com/Naman1997/cluster-management/actions/workflows/main.yml/badge.svg)](https://github.com/Naman1997/cluster-management/actions/workflows/main.yml)

Ansible playbooks for [Arch Linux](https://archlinux.org/) VM management and setting up k8s

## Install the requirements
```
ansible-galaxy collection install -r requirements.yaml
```

## Prerequisites for running playbook k8s-setup
- Make sure you're able to SSH into all your VMs
- iptables will conflict with iptables-nft. Make sure all VMs have iptables-nft installed
- Make sure you have yay installed in your VMs
- Create vars.json by running: `cp vars.json.example vars.json` and update `vars.json` file

## Prerequisites for running playbook storage-setup
- Make sure you're able to SSH into all your VMs
- You have exactly one VM inside the nfs group in your inventory
- Name of your NFS VM is 'nfs-server' in your inventory
- You have already executed the 'k8s-setup' playbook[This is need for helm changes in the playbook]

## Prerequisites for running playbook metallb-setup
- Make sure you're able to SSH into all your VMs
- You have already executed the 'k8s-setup' playbook[This is need for helm changes in the playbook]

## Run different playbooks
```
ansible-playbook playbooks/<<Playbook Name>> -i path/to/hosts -e "@path/to/vars.json" -vv --user <<Username>> --ask-become-pass
```

You do not need to pass the argument hosts file with the `-i` argument if your hosts are configured in /etc/hosts

You do not need to pass the argument `--user` if your inventory follows the format below

```
{node_hostname} ansible_host={node_host} ansible_port={ansible_port} ansible_user={ansible_user}
```

You do not need to pass the argument `--ask-become-pass` if you've enabled [passwordless sudo](https://serverfault.com/a/160587) on all your VMs
