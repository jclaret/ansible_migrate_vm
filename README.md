# Ansible  - Playbook to migrate vms to migrate cross-cluster

Playbook was created to migrate vm between RHV Clusters. 

NOTE: Although migrate vms between clusters is not recommended, it may be useful in some circumstances

## Requirements

The following software must be installed/present on your local machine before you can use Packer to build the Vagrant box file:

  - [Ovirt pyhton SDN](https://pypi.org/project/ovirt-engine-sdk-python/)
  - [Ansible](http://docs.ansible.com/intro_installation.html) > 2.4
  - [Red Hat Virtualization](https://www.redhat.com/es/technologies/virtualization/enterprise-virtualization)

## Usage

  - Make sure all the required software is installed.
  - git clone repository
  - Create ansible variables file vars/rhv.yml, with your RHV Engine information. it is recommended create a [ansible-vault](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vault.html) file
```
---
rhv_api: "https://manager.local.net"
rhv_user: "admin@internal"
rhv_pass: "password"
```

- Run playbook as follows:
```
    $ ansible-playbook migrate_vm.yml --ask-vault -e "vms_to_migrate=HostedEngine" -e "cluster_migrate_to=Cluster" -e "host_migrate_to=rhv02.local.net"
    $ ansible-playbook migrate_vm.yml --ask-vault -e "vms_to_migrate=HostedEngine" -e "cluster_migrate_to=L1"

```

Arguments:
- vms_to_migrate: vm to migrate
- cluster_migrate_to: cluster where you want to migrate vm
- host_migrate_to: host where you want to migrate vm (host from another cluster)

## License
Apache License 2.0
