Project Summary: MAC Matrix Inc Network Infrastructure
📌 Project Overview
This project involves the design and implementation of a scalable, secure, and highly available 
network infrastructure for MAC Matrix Inc - 
a fictional Bangladeshi corporate services provider. 
The network spans three office floors and supports approximately 2,500+ users with provisions to double capacity by 2025.

🏢 Organization Details
Aspect	Details
Company	MAC Matrix Inc
Industry	Business Consulting, Financial Advisory, Strategic Management
Location	3rd, 4th, and 5th Floors
Total Users	~2,500+ (growing to 5,000+ by 2025)
Floor-wise Distribution:
Floor	Departments	Users
3rd	Reception, Guest Area, Administrative Support, Document Management	~1,200
4th	Executive Management, Consulting, Procurement, HR, Finance	~500
5th	Internal Auditors, Corporate Strategy, IT Team	~420
IT Team Structure:
Brand & Digital Marketing

IT Support
System/Network Administration
Network Security Engineers
Cybersecurity Analysts
Software Engineers
Cloud Engineers
IT Management

🖥️ Technology Infrastructure
Component	Technology Used
ISP	INWI
Firewall	Cisco ASA 5500-X Series
Router	Cisco WAN Router
Core Switches	Catalyst 3850 (Multilayer)
Access Switches	Catalyst 2960
Servers	HP ProLiant DL380 Gen10 (2x) + VMware ESXi
Storage	NetApp (2x)
VoIP	Cisco Voice Gateway, 2811 Router
Wireless	Cisco WLC 2504 + LAPs
Cloud	AWS (EC2, S3, RDS)

🏗️ Network Design Highlights
1. Hierarchical Design (Three-Tier)
Core Layer: Multilayer switches with redundancy
Distribution Layer: Inter-VLAN routing, HSRP
Access Layer: End-device connectivity

2. VLAN Segmentation
VLAN ID	Name	Purpose
10	LAN	Wired users, printers
50	WLAN	Wireless users
99	VoIP	IP Phones
3. Security Implementation

✅ Cisco ASA Firewall with security zones (INSIDE:100, DMZ:70, OUTSIDE:0)
✅ ACLs controlling inter-zone traffic
✅ NAT for internet access
✅ PortFast + BPDUguard on access ports
✅ SSH enabled for secure remote management

4. High Availability & Redundancy
✅ HSRP - Virtual gateway redundancy (Active/Standby)
✅ EtherChannel (LACP) - Link aggregation with 4 links
✅ Dual Servers - Primary + Secondary failover
✅ Rapid-PVST - Loop prevention with fast convergence

5. Routing Protocol
OSPF Area 0 - Dynamic route advertisement across all devices

6. IP Addressing Scheme
Network	Subnet	Range
WLAN	10.10.0.0/16	10.10.0.1 - 10.10.255.254
LAN	192.168.0.0/20	192.168.0.1 - 192.168.15.254
VoIP	172.16.0.0/20	172.16.0.1 - 172.16.15.254
DMZ	10.20.10.0/26	10.20.10.1 - 10.20.10.62

📋 Key Configurations Implemented
Configuration	Details
DHCP	Configured on ESXi servers for LAN & WLAN; VoIP router for phones
Inter-VLAN Routing	SVIs on Core Multilayer Switches
STP	Rapid-PVST with PortFast + BPDUguard
Trunking	802.1Q on inter-switch links
Wireless	WLC managed with SSIDs per department
VoIP	Cisco 2811 router with 20 extensions (3001-3020)
Sniffer/SPAN	VLAN 10 traffic monitoring

✅ Testing & Validation Results
Test	Status
End-to-end connectivity (LAN ↔ Internet)	✅ PASS
Wireless connectivity (all SSIDs)	✅ PASS
VoIP call between extensions	✅ PASS
HSRP failover	✅ PASS
Firewall ACL enforcement	✅ PASS
DHCP IP assignment	✅ PASS
OSPF neighbor adjacency	✅ PASS
EtherChannel bundling	✅ PASS

🎯 Project Achievements
Goal	Achievement
Scalability	✅ Supports current users + ready for 2x growth
Security	✅ Multi-layer security (Firewall, ACLs, VLANs, SSH)
High Availability	✅ Redundant links, HSRP, dual servers
Performance	✅ LACP for bandwidth, OSPF for dynamic routing
Service Integration	✅ Data + Voice + Wireless all in one design
Cloud Readiness	✅ AWS integration for business continuity

🛠️ Tools Used
Cisco Packet Tracer - Network design & simulation
Cisco IOS - Device configuration
VMware ESXi - Server virtualization
AWS - Cloud services

📈 Future Scope
📌 Double user capacity by 2025

📌 Implement SD-WAN for multi-site connectivity

📌 Deploy Zero Trust Network Access (ZTNA)

📌 Integrate SIEM for advanced threat monitoring

📌 Automate network provisioning using Ansible/Python

🏁 Conclusion
The network infrastructure designed for MAC Matrix Inc successfully achieves:

✅ Optimal Performance

✅ Complete Redundancy

✅ Robust Security

✅ Scalability for Future Growth

The design ensures data confidentiality, integrity, and availability while supporting the company's ambitious expansion plans.

Project Completed By: MAC Matrix
Role: Security IT and Digital Trust Student
Platform: Cisco Packet Tracer

Total Configuration Files Created: Basic Settings | VLANs | STP | EtherChannel | Subnetting | HSRP | DHCP | OSPF | Firewall | NAT | ACLs | Sniffer | Wireless | VoIP

Network is fully functional and validated! 🎉