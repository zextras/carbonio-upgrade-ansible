# Upgrade Carbonio Ansible Role

An Ansible role to upgrade Zextras Carbonio infrastructures.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Behavior Notes](#behavior-notes)
- [Usage](#usage)
- [License](#license)

## Prerequisites

- An inventory file from (or created following the guidelines in) the [`carbonio-install-ansible`](../carbonio-install-ansible) repository.
- The Postgres, LDAP, and Consul passwords for the environment being upgraded.
  - If you used `carbonio-install-ansible` to build the inventory, these are generated automatically.
  - If not, place the following password files alongside your inventory file:
    - `inventoryname_postgrespassword`
    - `inventoryname_consulpassword`
    - `inventoryname_ldap_password`
- The netaddr Python module (installed automatically by Ansible on the control node — if you're running Ansible from a Python virtual environment, install it manually with pip install netaddr inside that venv). Used to validate inventory hostnames, domains, and IP addresses.
- If `videoServers` is defined in your inventory, `workStreamServers` must also be defined — the playbook validates this and will fail otherwise.

## Behavior Notes

The upgrade playbook applies the following automatically; no extra action is needed unless noted:

- **Memcached:** when multiple proxy servers are configured, `carbonio-memcached` is kept enabled only on the first proxy and disabled on the rest (memcached runs behind the service mesh, which currently supports a single instance).
- **Syslog after OS upgrade:** if a `syslogServer` host was upgraded from Ubuntu 22.04 to 24.04, the playbook re-checks and re-applies `rsyslog.conf` as needed.

## Usage

1. Clone or download this repository.
2. Create or update your inventory file following the guidelines in `carbonio-install-ansible`.
3. Place the necessary password files near the inventory file (see [Prerequisites](#prerequisites)).
4. Execute the upgrade playbook:

**From this repository:**

```
ansible-playbook -i inventoryname carbonio-upgrade-ansible/playbooks/carbonio_upgrade.yml
```

**Or from Ansible Galaxy:**

```
ansible-galaxy collection install zxbot.carbonio_upgrade
ansible-playbook -i inventoryname zxbot.carbonio_upgrade.carbonio_upgrade
```

### Skipping autoremove

To skip the `autoremove` step, pass `skip_autoremove=1` via `--extra-vars`:

**From this repository:**

```
ansible-playbook -i inventoryname carbonio-upgrade-ansible/playbooks/carbonio_upgrade.yml --extra-vars "skip_autoremove=1"
```

**Or from Ansible Galaxy:**

```
ansible-galaxy collection install zxbot.carbonio_upgrade
ansible-playbook -i inventoryname zxbot.carbonio_upgrade.carbonio_upgrade --extra-vars "skip_autoremove=1"
```

## License

See `COPYING` file for detail.
