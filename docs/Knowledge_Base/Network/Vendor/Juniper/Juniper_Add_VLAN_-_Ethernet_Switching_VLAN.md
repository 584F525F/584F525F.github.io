!!! example ""

	```bash

	FOR VLAN TAGGING SETUP <ge-0/0/2 vlan-tagging>
	show configuration interfaces | display set | match "ethernet-switching"
	show configuration interfaces | display set | match "vlan-tagging"

		Update the VLAN Number
		Update VLAN Name
		Update the Zones
		Update the Subnet and DHCP Pool
		Update the DHCP Group Number

	#Create zone for the VLAN
	set security zones security-zone GUEST interfaces ge-0/0/2.1234
	set security zones security-zone GUEST interfaces ge-0/0/2.1234 host-inbound-traffic system-services ping
	set security zones security-zone GUEST interfaces ge-0/0/2.1234 host-inbound-traffic system-services dhcp
	set security zones security-zone GUEST interfaces ge-0/0/2.1234 host-inbound-traffic system-services dns

	#Create policies for the VLAN to define access
	set security policies from-zone GUEST to-zone INTERNET policy GUEST_to_INTERNET match source-address any
	set security policies from-zone GUEST to-zone INTERNET policy GUEST_to_INTERNET match destination-address any
	set security policies from-zone GUEST to-zone INTERNET policy GUEST_to_INTERNET match application any
	set security policies from-zone GUEST to-zone INTERNET policy GUEST_to_INTERNET then permit

	########## TRY WITHOUT THIS FIRST ##########
	set security policies from-zone GUEST to-zone junos-host policy GUEST_To_Junos-host match source-address any
	set security policies from-zone GUEST to-zone junos-host policy GUEST_To_Junos-host match destination-address any
	set security policies from-zone GUEST to-zone junos-host policy GUEST_To_Junos-host match application any
	set security policies from-zone GUEST to-zone junos-host policy GUEST_To_Junos-host then permit
	############################################

	#Create Source Nat to Internet
	set security nat source rule-set DEFAULT_SRCNAT from zone GUEST

	#Create the VLAN
	set interfaces ge-0/0/2 unit 1234 description GUEST
	set interfaces ge-0/0/2 unit 1234 vlan-id 1234
	set interfaces ge-0/0/2 unit 1234 family inet address 172.20.0.1/20

	#Create DHCP
	set access address-assignment pool GUEST family inet network 172.20.0.1/20
	set access address-assignment pool GUEST family inet range GUEST low 172.20.0.10
	set access address-assignment pool GUEST family inet range GUEST high 72.20.15.250
	set access address-assignment pool GUEST family inet dhcp-attributes maximum-lease-time 14400
	set access address-assignment pool GUEST family inet dhcp-attributes name-server 9.9.9.9
	set access address-assignment pool GUEST family inet dhcp-attributes name-server 1.1.1.1
	set access address-assignment pool GUEST family inet dhcp-attributes name-server 8.8.8.8
	set access address-assignment pool GUEST family inet dhcp-attributes router 172.20.0.1

	#Create the DHCP Group for the VLAN number
	set system services dhcp-local-server group DHCP interface ge-0/0/2.1234
	```
