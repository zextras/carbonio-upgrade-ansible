# Changelog

All notable changes to this project will be documented in this file. 


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
