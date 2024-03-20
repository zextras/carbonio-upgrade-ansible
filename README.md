# Upgrade Carbonio Ansible role

An ansible role to upgrade Zextras Carbonio infrastructures

To upgrade Carbonio using this role, you will need to use or create an inventory file from the [carbonio-install-ansible](https://github.com/zextras/carbonio-install-ansible) repository. Additionally, the upgrade playbook requires the Postgres, LDAP, Consul, and video server passwords. If you didn't use the [carbonio-install-ansible](https://github.com/zextras/carbonio-install-ansible) repository, make sure to place the respective password files (inventoryname_postgrespassword, inventoryname_consulpassword, inventoryname_ldap_password, inventoryname_videoserver_password) alongside your inventory file.

To perform the upgrade, follow these steps:

1. Clone or download this repository.
2. Create or update your inventory file following the guidelines in [carbonio-install-ansible](https://github.com/zextras/carbonio-install-ansible).
3. Place the necessary password files near the inventory file.
4. Execute the upgrade playbook using the following command:

```bash
ansible-playbook -i inventoryname sps-upgrade-carbonio-ansible-role/carbonio-upgrade/upgrade-carbonio.yml
```

## License(s)

See [COPYING](COPYING.md) file for detail.
