!!! info ""

FOR VLAN TAGGING SETUP
show configuration interfaces | display set | match "ethernet-switching"
show configuration interfaces | display set | match "vlan-tagging"


	Update the VLAN Number
	Update VLAN Name
	Update the Zones
	Update the Subnet and DHCP Pool
	Update the DHCP Group Number


```bash
#Create Source Nat to Internet
set security nat source rule-set DEFAULT_SRCNAT from zone FreeInternet

#Create policies for the VLAN to define access
set security policies from-zone FreeInternet to-zone INTERNET policy FreeInternet-to-INTERNET match source-address any
set security policies from-zone FreeInternet to-zone INTERNET policy FreeInternet-to-INTERNET match destination-address any
set security policies from-zone FreeInternet to-zone INTERNET policy FreeInternet-to-INTERNET match application any
set security policies from-zone FreeInternet to-zone INTERNET policy FreeInternet-to-INTERNET then permit

#Create zone for the VLAN
set security zones security-zone FreeInternet interfaces reth2.1234 host-inbound-traffic system-services ping
set security zones security-zone FreeInternet interfaces reth2.1234 host-inbound-traffic system-services dhcp
set security zones security-zone FreeInternet host-inbound-traffic system-services ping
set security zones security-zone FreeInternet host-inbound-traffic system-services dhcp

#Create DHCP
set access address-assignment pool FreeInternet family inet network 172.24.0.1/20
set access address-assignment pool FreeInternet family inet range FreeInternet low 172.24.0.10
set access address-assignment pool FreeInternet family inet range FreeInternet high 172.24.15.200
set access address-assignment pool FreeInternet family inet dhcp-attributes maximum-lease-time 86400
set access address-assignment pool FreeInternet family inet dhcp-attributes name-server 1.1.1.1
set access address-assignment pool FreeInternet family inet dhcp-attributes name-server 8.8.8.8
set access address-assignment pool FreeInternet family inet dhcp-attributes name-server 9.9.9.9
set access address-assignment pool FreeInternet family inet dhcp-attributes router 172.24.0.1

#Create the VLAN
set interfaces reth2 unit 1234 family inet address 172.24.0.1/20
set interfaces reth2 unit 1234 vlan-id 1234
set interfaces reth2 unit 1234 description FreeInternet
```