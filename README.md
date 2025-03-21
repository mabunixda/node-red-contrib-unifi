node-red-contrib-unifi is a Node-RED module that allows to query/control [UniFi devices](http://www.ubnt.com/) via the official UniFi-Controller API. Based on npm package node-unifi

## New functions
Version 0.3.22
* New command to send ping requests to a specific device, results are retrieved via Websocket

## Supports the following Commands
* SitesStats : Site stats
* SiteSysinfo : Site sysinfo
* ClientDevices : Online client device(s)
* AllUsers : All client devices ever connected to the site
* UserGroups : User groups
* Health : Health metrics
* Dashboard : Dashboard metrics
* AccessDevices : Access points
* RogueAccessPoints : Rogue access points
* Events : Events
* Alarms : Alarms
* WlanSettings : Wlan Settings
* ListPortProfiles : List Port Profiles

## Special Commands: (No GUI)
* disableWlan : Disable/Enable Wlan { command: "disableWlan", wlan_id: "use _id from command WlanSettings", disable: true }
* blockClient : Block Client { command: "blockClient", mac: "client MAC address" }
* unblockClient : Unblock Client { command: "unblockClient", mac: "client MAC address" }
* reconnectClient : Reconnect Client { command: "reconnectClient", mac: "client MAC address" }
* authorizeGuest : Authorize Client { command: "authorizeGuest", mac: "client MAC address", minutes: "minutes until authorization expires" }   
* unauthorizeGuest : Unauthorize Client { command: "unauthorizeGuest", mac: "client MAC address" }
* restartAP : Reboot an Access point { command: "restartAP", mac: "device MAC address" }
* enableAP : Enable an Access point { command: "enableAP", device_id: "24 char device id" }
* disableAP : Disable an Access point { command: "disableAP", device_id: "24 char device id" }
* setAPLed : Set LED for Access point { command: "setapled", device_id: "24 char device id", mode: "off/on/default" }
* setSiteLed : Set LED for Site { command: "setsiteled", mode: true/false }
* site : Connect to site name { site: "site name"}
* getFirewallGroups: Get list of firewall groups { command: "getFirewallGroups" }
* addFirewallGroup: Add firewall group { command: "addFirewallGroup", group_name: "group-name", group_type: "address-group|ipv6-address-group|port-group", group_members: ["CIDRs", "IPs"] }
* editFirewallGroup: Edit firewall group { command: "editFirewallGroup", group_id: "group id", group_name: "group-name", group_type: "address-group|ipv6-address-group|port-group", group_members: ["CIDRs", "IPs"] }
* deleteFirewallGroup: Delete firewall group { command: "deleteFirewallGroup", group_id: "group id" }
* getFirewallRules: Get a list of firewall rules { command: "getFirewallRules" }
* getFirewallRule: Get a firewall rule { command: "getFirewallRule, rule_id: "id" }
* getFirewallRuleByName: Get a firewall rule by its name{ command: "getFirewallRuleByName, rule_name: "name" }
* enableFirewallRule: Enable a firewall rule { command: "enableFirewallRule", rule_id: "id" }
* disableFirewallRule: Disable a firewall rule { command: "disableFirewallRule", rule_id: "id" }
* getPoePortState: Get the PoE state of port x { command: "getPoePortState", device_id: "id", port: "port number" }
* enablePoePort: Enable POE on port x { command: "enablePoePort", device_id: "id", port: "port number", poe_mode: "off|auto|pasv24|passthrough" }
* disablePoePort: Disable POE on port x { command: "disablePoePort", device_id: "id", port: "port number"  }
* forceProvision : Force provision { command: "forceProvision", mac: "device MAC address" }
* setPortProfiles: Set overrides for multiple ports of a device { command: "setPortProfiles", device_id: "24 char device id", port_overrides: [ {"port_idx": 1, "portconf_id": "id of the port profile", "name": "friendly name of the port", "poe_mode": "off|auto" }, ... ] }
* setLocate : Enable flash device LED (or other indication based on device) { command: "setLocate", mac: "device MAC address" }
* unsetLocate : Disable flash device LED (or other indication based on device) { command: "unsetLocate", mac: "device MAC address" }
* setOutletPortState : Set power outlet state for a specific port { command: "setOutletPortState", mac: "device MAC address", index: "port index", relay_state: "true|false", cycled_enabled: "true|false" }
* setWLanPassword : Change WLan password { command: "setWLanPassword", wlan_id: "SSID ID", x_passphrase: "New password" }
* getVouchers : Get available Vouchers from Guest Portal { command: "getVouchers" }
* createVouchers: Create new Vouchers for Guest Usage { command: "createVouchers", minutes: "expiration time in minutes", count: "number of vouchers", quota: "'0' is for multi-use, '1' is for single-use", note: "note added to voucher", up: "upload speed limit in kbps (remove if not used)", down: "download speed limit in kbps (remove if not used)", mbytes: "data transfer limit in MB (remove if not used)"}
* revokeVouchers: Revoke voucher { command: "revokeVouchers", voucher_id : "24 char _id of the voucher" }
* clientDevices: Returns a single client device { command: "clientDevices", mac: "device MAC address" }
* enableTrafficManagementRule: Enable a traffic management rule { command: "enableTrafficManagementRule", rule_id: "id" }
* disableTrafficManagementRule: Disable a traffic management rule { command: "disableTrafficManagementRule", rule_id: "id" }
* getTrafficManagementRule : Get traffic management rules, optional add rule_id { command: "getTrafficManagementRule", rule_id: "id" }
* enableTrafficRouteRule: Enable a traffic route rule { command: "enableTrafficRoutetRule", rule_id: "id" }
* disableTrafficRouteRule: Disable a traffic route rule { command: "disableTrafficRouteRule", rule_id: "id" }
* getTrafficRouteRule : Get traffic route rules, optional add rule_id { command: "getTrafficRouteRule", rule_id: "id" }
* getWLanSetting : Get WLan setting for selected WLan { command: "getWLanSetting", wlan_id: "id" }
* setWLanFilter : Set Device Access Filtering { command: "setWLanFilter", wlan_id: "id", policy: "allow|deny", mac: ['MAC Address'] }
* setDNSServer : Set DHCP DNS Server 1 and 2 { command: "setDNSServer", network_id: "id", dns1: "x.x.x.x", dns2: "x.x.x.x" }
* getNetworkConf : Get network configuration { command: "getNetworkConf" }
* setAPLedColor : Set LED color for Access point { command: "setapledcolor", device_id: "24 char device id", color: "Color Hex code", brightness: 1-100 }
* getRadiusUsers : Get all radius users { command: "getRadiusUsers" }
* getRadiusProfiles : Get all radius profiles { command: "getRadiusProfiles" }
* createRadiusUser : Create radius user { command: "createRadiusUser", name: "account name", x_password: "password", tunnel_type: "optional 1-13", tunnel_medium_type: "optional 1-15", vlan: "optional vlan id" }
* updateRadiusUser : Update radius user { command: "updateRadiusUser", user_id: "24 char string _id of the user", name: "optional account name", x_password: "optional password", tunnel_type: "optional 1-13", tunnel_medium_type: "optional 1-15", vlan: "optional vlan id" }
* deleteRadiusUser : Delete radius user { command: "deleteRadiusUser", user_id: "24 char string _id of the user" }
* getDPIstats : Get array of DPI stats { command: "getDPIstats" }
* getCustomDNS : Get array of Custom DNS entries { command: "getCustomDNS" }
* setCustomDNS : Create new Custom DNS entry { command: "setCustomDNS", record_type: "A|AAAA|MX|TXT|SRV", value: "IP address|Text|Domain name", key: "Domain name", priority: 0-65535, weight: 0-65535, ttl: 1-86400, port: 1-65535, enabled: true|false, _id: "_id of current Custom DNS entry if you want to update" }
* getFirewallZones : Get array of Firewall Zones { command: "getFirewallZones" }
* getNetworks : Get array of Networks { command: "getNetworks" }
* setFirewallZone : Create, Update or Delete Firewall Zone { command: "setFirewallZone", name: "Zone name - create or update", network_ids: "Network Id - create or update", _id: "Zone id - update or delete", remove: "true - delete" }
* getFirewallPolicies : Get array of Firewall Policies { command: "getFirewallPolicies" }
* setFirewallPolicy : Set status of Firewall Policy { command: "setFirewallPolicy", enabled: "true | false", _id: "Firewall Policy Id" }
* powerCyclePoEPort : Power-Cycle Switch PoE port { command: "powerCyclePoEPort", port: "Port Id", mac: "Switch MAC address" }
* startPingDevice : Send 30 ping requests to a specific device, results are retrieved via Websocket { command: "startPingDevice", mac: "Device MAC address" }
* stopPingDevice : Stop pinging a specific device { command: "stopPingDevice", mac: "Device MAC address" }

## Tips
* Use the command SiteStats to get your Unifi Site Name
* Use msg.payload = { site: "site name"}; to add the site name dynamically
* Use the command AccessDevices to get an Access Points Device ID
* Use the command ListPortProfile to get Profile ID
* Use the command GetWLanSettings to get SSID ID
* Use the command getNetworkConf to get network ID
* Use the command getRadiusUsers to get radious user ID
* See working examples in the examples folder

## Requirements
* Installed [UniFi-Controller](https://www.ubnt.com/download/unifi) version v4, v5, v6, v7, v8 or v9
* Unifi controller user must have at least 'administrator' rights (not read-only)

## Installation recommended
The recommended way to install this module is from the Node-RED GUI itself.
Menu/manage palette/Install/search for unifi and then click install.

## Installation manual
If Node-RED has been installed according to the instructions on https://nodered.org/docs/getting-started/installation, 
then the installation command for node-red-contrib-unifi has to be done from inside the Node-RED 
user-directory (default $HOME/.node-red) and prefixed with sudo.

## Contributors
* Thanks to all contributors.
* And a special thanks to Nokomis

## License
MIT License

Copyright (c) 2025 Kristoffer Isaksson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.