# Ansible Scripts

This repository contains Ansible playbook to install Docker, docker-compose and run any containers from docker-compose.yml files in __./others/composes__ folder.

## Requirements

Make sure __public key__ in your machine is registered to the __authorized_keys__ file in your server(s), so Ansible can do ssh to your servers.

## What You Need to Know About This Ansible Project

This Ansible project layout assumes these conditions:

1. The Ansible variables file is located at __~/ansible/vars.yml__ in the local machine.
2. Docker compose files located at __./others/composes__.
3. Environment variables file __to be set__ in remote machines is located at __./others/vaults/envvars__.
4. Environment variables for Docker compose is located at __./others/vaults/.env__.
5. You can add your own docker compose files at __./others/composes/__ and add them to __Run compose file(s)__ task's __vars__.
6. Default vault password is __the_faults_is_our_stars__ change it with your own vault password with Ansible __rekey__ command.

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

You can any other containers listed in the __compose__ folder in this repository. These files are come from [this](https://gist.github.com/namikazebadri) gist.