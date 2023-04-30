# Ansible-Homelab
A repository that collects the configuration of my home servers and the applications deployed on them. And some more side playbooks and roles, because I'm too lazy to create a separate repository and there are dependencies between roles.
Using

    One command to configure Proxmox hosts, configure DNS, create LXC containers and run services in them on Docker

ansible-playbook main.yml

    To reduce the runtime, you can run individual tasks using the
        pve - all tasks for Proxmox hosts
        pve_common - a separate task for Proxmox hosts
        svc - tasks for all docker containers at once.
        mgmt (host name) - tasks for a specific LXC host
        portainer (container name) - tasks for a specific docker container
        upgrade_packages - updates packages on all LXC hosts.
        dns - Tasks for the DNS server in the router

ansible-playbook main.yml -t svc

Ansible Vault

The line

ansible-vault encrypt_string --encrypt-vault-id default --vault-password-file .vault_password --stdin-name 'secret'

File

ansible-vault decrypt group_vars/all/vault.yml --vault-password-file .vault_password
ansible-vault encrypt group_vars/all/vault.yml

How to add a new application

    Configuration in Ansible
    DNS entries in deploy_homelab_set_static_dns.yml for local access via Traefik
    Hosting DNS entries for internet access
    Proxy host in Nginx Proxy Manager
    Users in the application group in FreeIPA

