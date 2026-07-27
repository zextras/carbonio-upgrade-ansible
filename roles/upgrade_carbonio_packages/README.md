# Upgrade Carbonio Packages

This role upgrades the installed Carbonio packages on supported Ubuntu and RHEL systems.

## Responsibilities

The role:

- updates the package repository cache;
- collects the list of packages available for upgrade;
- upgrades installed packages to their latest available versions;
- restores the required network bind capability on the Directory Server binary;
- restarts Directory Server services when the Directory Server package is upgraded;
- manages the restart flag used by the post-upgrade role.

The role does not install additional Carbonio components introduced by newer releases.

## License

GPL-3.0-only

## Author Information

Zextras  
<https://www.zextras.com>