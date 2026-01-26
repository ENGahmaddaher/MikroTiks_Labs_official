# MikroTiks_Labs_official
MikroTik Ansible Labs 🚀
Infrastructure Automation with Ansible & RouterOS API
This repository contains a collection of real-world MikroTik network labs automated using Ansible and the community.routeros collection.
The goal of this project is to demonstrate clean architecture, idempotent automation, and enterprise-style network design, covering multiple networking technologies such as PPPoE, OSPF, WireGuard, CAPsMAN, VLANs, Load Balancing, and more.
📌 Key Features
✅ Modular Ansible architecture (Roles / Playbooks / Inventories)
✅ Per-LAB isolated inventories
✅ RouterOS API automation (no CLI scraping)
✅ Idempotent execution (changed = 0 on re-run)
✅ Realistic enterprise network scenarios
✅ Ready for EVE-NG / GNS3 / physical MikroTik devices
🗂️ Project Structure
Text
mikrotik-ansible-labs/
├── ansible.cfg
├── requirements.yml
├── roles/
│   ├── pppoe/
│   ├── ospf/
│   ├── wireguard/
│   ├── capsman-vlan/
│   ├── loadbalancing/
│   └── base/
├── playbooks/
│   ├── pppoe/
│   ├── ospf/
│   ├── wireguard/
│   ├── vlan-capsman/
│   └── loadbalancing/
├── inventories/
│   ├── pppoe/
│   ├── ospf/
│   ├── wireguard/
│   ├── vlan-capsman/
│   └── loadbalancing/
├── pppoe.png
├── ospf.png
├── wireguard.png
├── vlan-capsman.png
├── loadbalancing.png
└── README.md
Each LAB has:
Its own inventory
Its own playbook
Shared and reusable roles
⚙️ Requirements
Ansible ≥ 2.14
Python ≥ 3.9
MikroTik RouterOS ≥ 7.x
RouterOS API enabled
Install required collections:
Bash
ansible-galaxy collection install -r requirements.yml
🧪 Available Labs
🟢 PPPoE ISP Lab
(pppoe_server_client.png)['pppoe'] 
Description
Simulates an ISP environment using MikroTik routers:
Core router acting as ISP
Multiple PPPoE servers
Multiple PPPoE clients
Profiles, secrets, pools, and authentication
Fully automated via RouterOS API
Run the Lab
Bash
ansible-playbook playbooks/pppoe/pppoe.yml \
  -i inventories/pppoe/hosts.yml
🔵 OSPF Routing Lab
 (ospf.png)['ospf']
Description
Enterprise-grade OSPF deployment featuring:
Loopback interfaces for Router-ID
OSPF instance, area, and interface-template
Passive and point-to-point interfaces
Idempotent configuration (no duplicates)
Run the Lab
Bash
ansible-playbook playbooks/ospf/ospf.yml \
  -i inventories/ospf/hosts.yml
🟣 WireGuard VPN Lab
 (wireguard.png)['wg']
Description
Secure site-to-site VPN using WireGuard:
Encrypted tunnels
Peer automation via API
Ready for dynamic routing integration
Clean and minimal configuration
Run the Lab
Bash
ansible-playbook playbooks/wireguard/wireguard.yml \
  -i inventories/wireguard/hosts.yml
🟠 VLAN + CAPsMAN Wireless Lab
 (capsman.png)['caps']
Description
Enterprise wireless architecture:
Router as Gateway + CAPsMAN Controller
MikroTik Switch (Bridge VLAN Filtering)
Multiple VLANs (MGMT / GUEST / SALES)
VLAN-based SSIDs
DHCP per VLAN
Zero-touch CAP provisioning
Run the Lab
Bash
ansible-playbook playbooks/vlan-capsman/vlan-capsman.yml \
  -i inventories/vlan-capsman/hosts.yml
🔴 Load Balancing Lab
 
Description
Multi-ISP load balancing scenario:
Multiple WAN links
Policy routing
NAT per ISP
Scalable and extendable design
Run the Lab
Bash
ansible-playbook playbooks/loadbalancing/loadbalancing.yml \
  -i inventories/loadbalancing/hosts.yml
🔐 Connection Method
All devices are managed using RouterOS API:
Yaml
ansible_connection: network_cli
ansible_network_os: community.routeros.routeros
No SSH CLI scraping is used.
♻️ Idempotency Guarantee
Every LAB is designed so that:
First run → changed > 0
Second run → changed = 0
This is achieved using:
API queries before creation
Conditional tasks
Proper object matching
🧠 Learning Objectives
This project helps you learn:
Network automation best practices
MikroTik RouterOS internals
Scalable Ansible architecture
Real ISP & enterprise designs
Infrastructure as Code (IaC)
📌 Future Labs (Planned)
BGP (iBGP / eBGP)
MPLS + LDP
RADIUS + WPA2-Enterprise
Captive Portal (Hotspot)
QoS per user / per VLAN
🤝 Contributions
Contributions, suggestions, and improvements are welcome.
Feel free to open an issue or submit a pull request.
📜 License
MIT License
