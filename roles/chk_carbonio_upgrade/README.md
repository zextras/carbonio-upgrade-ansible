# Check Carbonio Upgrade

This role verifies the state of Carbonio services after the upgrade has completed.

## Responsibilities

The role:

- checks the `zmcontrol` status on Application Server nodes;
- displays the status of Carbonio services;
- displays the status of Consul services;
- checks VideoServer services when VideoServer nodes are configured;
- displays the installed Carbonio version.

The role performs verification only and does not modify the Carbonio configuration.

## License

GPL-3.0-only

## Author Information

Zextras
<https://www.zextras.com>