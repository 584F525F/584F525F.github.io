!!! example ""

	```bash
	FOR Ethernet Switching SETUP <ge-0/0/4 unit 0 family ethernet-switching>
	show configuration interfaces | display set | match "ethernet-switching"
	show configuration interfaces | display set | match "vlan-tagging"

		Update the VLAN Number
		Update VLAN Name
		Update the Zones
		Update the Subnet and DHCP Pool
		Update the DHCP Group Number

	#Create zone for the VLAN
	set security zones security-zone Guest interfaces irb.1234 host-inbound-traffic system-services ping
	set security zones security-zone Guest interfaces irb.1234 host-inbound-traffic system-services dhcp
	set security zones security-zone Guest interfaces irb.1234 host-inbound-traffic system-services dns

	#Create policies for the VLAN to define access
	set security policies from-zone Guest to-zone Internet policy Guest_to_Internet match source-address any
	set security policies from-zone Guest to-zone Internet policy Guest_to_Internet match destination-address any
	set security policies from-zone Guest to-zone Internet policy Guest_to_Internet match application any
	set security policies from-zone Guest to-zone Internet policy Guest_to_Internet then permit

	#Create Source Nat to Internet
	set security nat source rule-set default_srcnat from zone Guest

	#Create the VLAN
	set interfaces irb unit 1234 family inet address 172.20.0.1/20

	#Create DHCP
	set access address-assignment pool Guest family inet network 172.20.0.1/20 range Guest low 172.20.1.1 high 172.20.15.250
	set access address-assignment pool Guest family inet dhcp-attributes maximum-lease-time 86400
	set access address-assignment pool Guest family inet dhcp-attributes name-server 9.9.9.9
	set access address-assignment pool Guest family inet dhcp-attributes name-server 1.1.1.1
	set access address-assignment pool Guest family inet dhcp-attributes name-server 8.8.8.8
	set access address-assignment pool Guest family inet dhcp-attributes router 172.20.0.1

	#Define VLAN number
	set vlans Guest vlan-id 1234

	#Assign vlan to a L3 Interface
	set vlans Guest l3-interface irb.1234

	#Assign physical port for the VLAN - what Port it will be used on
	set interfaces ge-0/0/4 unit 0 family ethernet-switching vlan members Guest

	#Create the DHCP Group for the VLAN number  >>>>>>>>> UPDATE THE GROUP NUMBER
	set system services dhcp-local-server group g1 interface irb.1234
	```