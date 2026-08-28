# Changelog

All notable changes to this project will be documented in this file. 


### [26.9.0] (2026-09-30)


### Features 
* Removed the obsolete carbonio-core < 4.2 compatibility block, including version detection and the related restart, wait, and stop sequence.
* Removed outdated Carbonio version references from task names that are not conditionally executed based on the installed Carbonio version.
* Added installation and database bootstrap support for the new carbonio-preview-db package.
* Refactored the playbook structure and standardized Ansible content across roles, including task names, module FQCNs, inventory group references, and task conditions.
* Added repository and upgrade playbook validation and confirmation before Carbonio upgrade, with repository consistency checks across all hosts and support for non-interactive confirmation.
* Updated the Notification Push installation logic to check Consul before installing the package.
* Added carbonio-license-service installation.


### [26.6.2] (2026-07-10)


### Bug Fixes
* Updated the carbonio-storages installation logic to install the package on all MTA nodes and, when configured, on dedicated Files nodes. This ensures that carbonio-storages is installed on MTA servers even when the filesServers inventory group is empty


### [26.6.1] (2026-07-08)


### Bug Fixes
* Added the missing Notification Push DB bootstrap for Standard RHEL installations.
* Limited the zmcontrol status advanced check to mailbox servers. Its output on non-mailbox servers is inconsistent and may return a non-zero exit code even when the relevant services are operating as expected.


### [26.6.0] (2026-07-07)


### Features
* Added pre-check task (rsyslog-config-check.yml) to detect and re-apply rsyslog.conf on syslogServer group after OS upgrade from Ubuntu 22.04 to 24.04.
* Added new pacakge carbonio-storage-ui for installation
* Added validation for inventory values (hostnames, domains, and IP addresses) to prevent misconfigurations caused by INI parsing
* Removed from the installation list deprecated carbonio-chats-ui
* Added netaddr dependency handling for inventory IP address validation

### Bug Fixes
* Fixed deprecated ansible_* facts usage by migrating to ansible_facts for compatibility with ansible-core 2.24
* Replaced ansible_facts.fqdn with inventory_hostname to avoid incorrect hostname resolution when hosts file entries are misconfigured
* Fixed Advanced module status detection for RHEL 9 and Ubuntu 24 by migrating to zmcontrol status, which replaces the deprecated getversion command
* Updated the `ansible.posix` dependency to version `2.2.0` to remove deprecation warnings related to the deprecated `to_native` import path in newer `ansible-core` versions
* Removed the legacy pgpool-related upgrade logic for Carbonio 24.9, as it is now considered a legacy release. This also prevents upgrade failures with an empty dbsConnectorServers group when using newer ansible-core versions
* Disabled the memcached service on additional proxy nodes when multiple proxy servers are configured. Memcached remains enabled only on the first proxy server
* Replaced the word "WSC" with "Chats" in the names of some tasks where necessary to avoid inconsistencies


### [26.3.2] (2026-04-13)


### Bug Fixes
* Removed deprecated zimbraMemcachedBindAddress reconfiguration


### [26.3.1] (2026-03-24)


### Bug Fixes
* Fixed an issue where inline comments in inventory variable examples were propagated as part of the value into generated configuration files, causing invalid Postfix configuration


### [26.3.0] (2026-03-11)


### Features
* Added new DBConnector package carbonio-videorecorder-db for DB-backed metadata storage and job management support
* Updated the Ansible playbook to install the carbonio-memcached package only on the first proxy, since memcached runs behind the service mesh and currently supports a single instance.

### Bug Fixes
* Removed message-dispatcher-migration steps (now handled by application)


### [25.12.1] (2025-12-23)


### Bug Fixes
* Fixed IndexError for empty groups in delegate_to (ansible-core 2.19 compatibility)


### [25.12.0] (2025-12-15)


### Features
* Removed carbonio-admin-ui package from the list of Proxy packages
* Introduced the allowerasing parameter into the RHEL upgrade procedure to handle package replacement conflicts
* Checked inventory to be sure that the workStreamServers server is defined in the inventory if videoServers server is defined
* Updated MongooseIM from version 6.3.1 to 6.3.2


### [25.9.0] (2025-9-30)


### Bug Fixes
* Added restart of MTA/Proxy services
* Reconfigured zimbraMemcachedBindAddress attribute as zimbraMemcachedBindAddress ""
* Made carbonio prov write values directly to LDAP without SOAP calls to the application server


### [25.6.1] (2025-7-11)


### Bug Fixes
* Added restart of carbonio-storages if this service was installed on servers from another group (not [filesServers] group)
* Moved videoServers upgrade after workStreamServers to maintain the order of server upgrades
* Reworked service restart to avoid multiple restarts for services


### [25.6.0] (2025-5-16)


### Features
* Added RHEL 9 and Ubuntu 24 support 

### Bug Fixes
* Added restart of missed services


### [25.3.0] (2025-3-11)


### Features
* Introduced support for upgrading WSC installations from previous Carbonio versions
* Added Notification Push Installation on WSC during the upgrade proccess
* Implemented Carbonio HA upgrade
* Added validation to ensure inventory password files reside in the same folder as the inventory file
* Implemented Consul-side checks for packages (carbonio-catalog, carbonio-storages, carbonio-user-management, carbonio-message-broker) added in previous versions and installed them if missing
* Added automatic installation of Proxy packages if not already installed
* Added a check for the presence of the [workStreamServers] group in the inventory
* Added carbonio-perl-mailtools on syslog server during the upgrade proccess


### Bug Fixes
* Added check if /etc/carbonio exists before saving this


# Changelog

All notable changes to this project will be documented in this file. 
