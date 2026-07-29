
This role performs the configuration and service operations required after Carbonio packages have been upgraded.

## Responsibilities

The role:

- removes unused package dependencies unless autoremove is disabled;
- applies required post-upgrade configuration fixes;
- executes Carbonio pending setups;
- runs database bootstrap commands for HA and standard PostgreSQL deployments;
- restarts PostgreSQL, Patroni, Carbonio, and related services;
- removes temporary restart files created during the upgrade.

The role runs after package upgrade and installation tasks have completed.

## License

GPL-3.0-only

## Author Information

Zextras  
<https://www.zextras.com>