# Pre Carbonio Upgrade

This role performs validation and backup operations before the Carbonio upgrade starts.

## Responsibilities

The role:

- validates the required Consul and PostgreSQL password files;
- validates required inventory groups and inventory values;
- validates the public IP address configured for VideoServer nodes;
- creates backups of LDAP and Carbonio configuration files;
- checks the rsyslog remote listener configuration;
- restores the rsyslog listener configuration when required.

The role does not upgrade or install Carbonio packages.

## License

GPL-3.0-only

## Author Information

Zextras  
<https://www.zextras.com>