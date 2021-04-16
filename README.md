# Ansible Scripts

This repository contains ansible playbook to install docker, docker-compose and run any containers from docker-compose.yml files in __compose__ folder.

# Requirements

Make sure __public key__ in your machine is registered to the __authorized_keys__ file in your server(s), so ansible can do ssh to your servers.

## Change Inventory

To change inventory, please edit __os-name__/inventory/host.yml to represent your servers inventory. Please refer to this [documentation](https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html) from ansible for the syntax and rules.

## Executing The Playbook

```shell
cd ubuntu20.04

ansible-playbook -i inventory docker.yml -u ubuntu # change the value for -u parameter with user in your server.
```

## Run Other Containers

You can any other containers listed in the __compose__ folder in this repository. These files are come from [this](https://gist.github.com/namikazebadri) gist.