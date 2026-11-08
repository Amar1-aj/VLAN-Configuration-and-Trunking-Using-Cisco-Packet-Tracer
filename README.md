VLAN Configuration and Trunking Using Cisco Packet Tracer

Project Overview

This project demonstrates VLAN configuration and trunking between two Cisco switches using Cisco Packet Tracer.
The network consists of two switches (S1 and S2) and four PCs. Two separate VLANs are configured: VLAN 10 for the IT department and VLAN 20 for the HR department.
A trunk link connects both switches, allowing devices belonging to the same VLAN to communicate across different switches.

Project Objectives

•	Create and configure VLAN 10 (IT) and VLAN 20 (HR).
•	Assign switch access ports to the appropriate VLANs.
•	Configure trunking between two Cisco switches.
•	Enable communication between devices in the same VLAN.
•	Verify VLAN and trunk configurations using Cisco IOS commands.

Network Topology

Devices Used:
•	2 Cisco 2960 switches (S1 and S2)
•	4 PCs
•	Copper straight-through cables for PC-to-switch connections
•	Switch-to-switch connection using GigabitEthernet interfaces

Network Connection:

•	S1 GigabitEthernet0/1 ↔ S2 GigabitEthernet0/1
•	IT-PC1 and HR-PC1 connected to S1
•	IT-PC2 and HR-PC2 connected to S2

IP Addressing Table

Device	IP Address	Subnet Mask	VLAN
IT-PC1	192.168.10.10	255.255.255.0	10
IT-PC2	192.168.10.11	255.255.255.0	10
HR-PC1	192.168.20.10	255.255.255.0	20
HR-PC2	192.168.20.11	255.255.255.0	20

VLAN Configuration

VLAN ID	VLAN Name	Network	Switch Ports

10	IT	192.168.10.0/24	Fa0/1–Fa0/12
20	HR	192.168.20.0/24	Fa0/13–Fa0/24

The same VLANs and port assignments are configured on both switches.

Switch Configuration
Switch S1
enable
configure terminal
hostname S1

vlan 10
name IT

vlan 20
name HR

interface range fa0/1-12
switchport mode access
switchport access vlan 10

interface range fa0/13-24
switchport mode access
switchport access vlan 20

end
copy running-config startup-config
Switch S2
enable
configure terminal
hostname S2

vlan 10
name IT

vlan 20
name HR

interface range fa0/1-12
switchport mode access
switchport access vlan 10

interface range fa0/13-24
switchport mode access
switchport access vlan 20

end
copy running-config startup-config
Trunk Configuration
Configure the GigabitEthernet0/1 interface on both switches.
enable
configure terminal

interface gigabitEthernet0/1
switchport mode trunk

end
copy running-config startup-config

Verification Commands

Use the following commands to verify the configuration:
show vlan brief
show interfaces trunk
show running-config
Connectivity Testing

Test communication between PCs belonging to the same VLAN.
IT VLAN:
•	IT-PC1 → 192.168.10.11 (IT-PC2)
HR VLAN:
•	HR-PC1 → 192.168.20.11 (HR-PC2)
Expected result: Successful ping communication between PCs in the same VLAN across both switches.
Communication between IT and HR devices is not expected because inter-VLAN routing is not configured.
Skills Demonstrated
•	Cisco Packet Tracer
•	VLAN Configuration
•	VLAN Segmentation
•	Access Port Configuration
•	Trunk Port Configuration
•	Cisco IOS CLI
•	IP Addressing and Subnetting
•	Network Connectivity Testing
•	Basic Network Troubleshooting
Conclusion
This project provides practical experience in configuring VLANs and trunk links across multiple switches. It demonstrates how network segmentation improves logical organization and how trunking enables communication between devices belonging to the same VLAN across different switches.
 
