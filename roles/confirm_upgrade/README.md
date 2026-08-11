# Confirm Carbonio Upgrade

This role performs the initial checks and confirmation before starting the Carbonio upgrade.

It validates the upgrade collection version and the Zextras repository configuration before any Carbonio packages are upgraded.

## Responsibilities

The role:

- retrieves the upgrade collection source and version;
- detects the configured Zextras repository on each host;
- verifies that a Zextras repository is configured on all hosts;
- verifies that the same repository is used across the infrastructure;
- displays the repository and upgrade playbook information;
- requests confirmation before continuing with the upgrade.

## Non-Interactive Confirmation

Repository and playbook confirmation can be automated with:

```
carbonio_auto_confirm_repository_and_playbook: true

When enabled, the repository and playbook information is still displayed, but the interactive confirmation prompt is skipped.

## License

GPL-3.0-only

## Author Information

Zextras  
<https://www.zextras.com>