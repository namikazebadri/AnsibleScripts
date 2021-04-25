# Ansible Scripts

This repository contains Ansible playbooks to install Docker, Docker Compose and run any containers from docker-compose.yml files in __./vars/composes__ folder.

## Requirements

Make sure __public key__ in the local machine is registered to the __authorized_keys__ file in your server(s), so Ansible can do ssh to your servers.

## What You Need to Know About This Ansible Scripts

This Ansible project layout assumes these conditions:

1. The Ansible variables file is located at __~/ansible/vars.yml__ in the local machine (as stated in docker.yml files).
2. Default vault password is __the_fault_is_our_stars__ and vault file is assume t be stored at ~/.vault_pass.txt, change it with your own vault password with Ansible __rekey__ command or simply decrypt the files and encrypt with new vault password.
3. Environment variables file __to be set__ in remote machines is located at __./vars/vaults/envvars__.
4. Environment variables file for Docker compose is located at __./vars/vaults/.env__.
5. Docker compose files located at __./vars/composes__ directory.
6. You can add your own docker compose files at __./vars/composes__ directory and add them to __Run compose file(s)__ task's __vars__.

## Change Inventory

To change inventory, please edit __os-name__/inventory/host.yml to represent your servers inventory. Please refer to this [documentation](https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html) from Ansible for the syntax and rules.

## Executing The Playbook

Let's say we want to run Ansible for Ubuntu 20.04 server:

```shell
cd ubuntu20.04

ansible-playbook -i inventory \
    --vault-password-file ~/.vault_pass.txt \
    docker.yml
```

## Run Other Containers

You can add any other containers listed in the __compose__ folder in this repository. These files are come from [this](https://gist.github.com/namikazebadri) gist.