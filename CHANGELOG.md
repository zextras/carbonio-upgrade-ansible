# Changelog

All notable changes to this project will be documented in this file. 

### [25.3.0] (2025-2-17)


### Features
* Introduced support for upgrading WSC installations from previous Carbonio versions
* Implemented Carbonio HA upgrade
* Added validation to ensure inventory password files reside in the same folder as the inventory file
* Implemented Consul-side checks for packages (carbonio-catalog, carbonio-storages, carbonio-user-management, carbonio-message-broker) added in previous versions and installed them if missing
* Added automatic installation of Proxy packages if not already installed
* Added a check for the presence of the [workStreamServers] group in the inventory


### Bug Fixes
* Added check if /etc/carbonio exists before saving this

# Changelog

All notable changes to this project will be documented in this file. 
