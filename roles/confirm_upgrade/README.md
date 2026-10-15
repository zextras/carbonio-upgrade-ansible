# Confirm Carbonio Upgrade

This role performs the initial checks and confirmation before starting the Carbonio upgrade.

It validates the upgrade collection version, the Zextras repository configuration, and the Carbonio licence/version compatibility before any Carbonio packages are upgraded.

## Responsibilities

The role:

- retrieves the upgrade collection source and version;
- detects the configured Zextras repository on each host;
- verifies that a Zextras repository is configured on all hosts;
- verifies that the same repository is used across the infrastructure;
- checks the current Carbonio licence and version against the target release;
- requests explicit confirmation when a licence or version risk is detected;
- displays the repository and upgrade playbook information;
- requests confirmation before continuing with the upgrade.

## Non-Interactive Confirmation

Repository and playbook confirmation can be automated with:

```yaml
carbonio_auto_confirm_repository_and_playbook: true
```

When enabled, the repository and playbook information is still displayed, but the interactive confirmation prompt is skipped.

Licence and version risk confirmation can be automated with:

```yaml
carbonio_version_check_force: true
```

When enabled, the licence/version warning is still displayed when a risk is detected, but the `IAMSURE` confirmation prompt is skipped.

Only `true` and `false` are supported values for extra vars.

## License

GPL-3.0-only

## Author Information

Zextras  
<https://www.zextras.com>
