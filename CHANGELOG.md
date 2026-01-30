# Changelog

All notable changes to this project will be documented in this file. 

### [26.3.0] (2026-03-10)


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
