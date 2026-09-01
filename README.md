# Upgrade Carbonio Ansible Role

An Ansible role to upgrade Zextras Carbonio infrastructures.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Upgrade Confirmation](#upgrade-confirmation)
- [Behavior Notes](#behavior-notes)
- [Usage](#usage)
- [Non-Interactive / Automation Usage](#non-interactive--automation-usage)
- [License](#licenses)

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

## Upgrade Confirmation

Before starting the upgrade, the playbook displays:

- the upgrade playbook source and version;
- the Zextras repository configured for the infrastructure.

The playbook verifies that:

- a Zextras repository is configured on every host;
- only one Zextras repository is configured on each host;
- all hosts use the same Zextras repository.

The upgrade is stopped if the repository configuration is missing or inconsistent.

The user must confirm the displayed repository and upgrade playbook information by entering `yes`.

For non-interactive runs, this confirmation can be pre-answered with the `carbonio_auto_confirm_repository_and_playbook` extra-var.

On each application server, the playbook also checks `carbonio core getlicenseinfo` against the target Carbonio release. It warns and requires typing `IAMSURE` to proceed if no valid licence is active, the licence has expired, or the target release exceeds the licence's maximum allowed version (a blank maximum is treated as unlimited). For non-interactive runs, this can be pre-answered with the `carbonio_version_check_force` extra-var — see [Non-Interactive / Automation Usage](#non-interactive--automation-usage).

## Behavior Notes

The upgrade playbook applies the following automatically; no extra action is needed unless noted:

- **Memcached:** when multiple proxy servers are configured, `carbonio-memcached` is kept enabled only on the first proxy and disabled on the rest (memcached runs behind the service mesh, which currently supports a single instance).
- **Syslog after OS upgrade:** if a `syslogServer` host was upgraded from Ubuntu 22.04 to 24.04, the playbook re-checks and re-applies `rsyslog.conf` as needed.

## Usage

1. Clone or download this repository.
2. Create or update your inventory file following the guidelines in `carbonio-install-ansible`.
3. Place the necessary password files near the inventory file (see [Prerequisites](#prerequisites)).
4. Execute the upgrade playbook.

**From this repository:**

```
ansible-playbook -i inventoryname -u root carbonio-upgrade-ansible/playbooks/carbonio_upgrade.yml
```

**Or from Ansible Galaxy:**

```
ansible-galaxy collection install zxbot.carbonio_upgrade
ansible-playbook -i inventoryname -u root zxbot.carbonio_upgrade.carbonio_upgrade
```

### Skipping autoremove

To skip the `autoremove` step, pass `skip_autoremove=1` via `--extra-vars`:

**From this repository:**

```
ansible-playbook -i inventoryname -u root carbonio-upgrade-ansible/playbooks/carbonio_upgrade.yml --extra-vars "skip_autoremove=1"
```

**Or from Ansible Galaxy:**

```
ansible-galaxy collection install zxbot.carbonio_upgrade
ansible-playbook -i inventoryname -u root zxbot.carbonio_upgrade.carbonio_upgrade --extra-vars "skip_autoremove=1"
```

## Non-Interactive / Automation Usage

The repository and playbook confirmation can be skipped for automated runs with:

```
-e carbonio_auto_confirm_repository_and_playbook=true
```

The licence and version check confirmation (see [Licence and Version Check](#licence-and-version-check)) can be skipped for automated runs with:

```
-e carbonio_version_check_force=true
```

Both extra-vars can be combined for a fully non-interactive run.

Example from this repository:

```
ansible-playbook -i inventoryname -u root carbonio-upgrade-ansible/playbooks/carbonio_upgrade.yml \
  -e carbonio_auto_confirm_repository_and_playbook=true \
  -e carbonio_version_check_force=true
```

Example from Ansible Galaxy:

```
ansible-playbook -i inventoryname -u root zxbot.carbonio_upgrade.carbonio_upgrade \
  -e carbonio_auto_confirm_repository_and_playbook=true \
  -e carbonio_version_check_force=true
```

The repository and upgrade playbook information — and the licence/version check warning, if triggered — is still displayed when automatic confirmation is enabled.

## License(s)

See [COPYING](COPYING.md) file for detail.