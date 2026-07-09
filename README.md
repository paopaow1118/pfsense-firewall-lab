# pfsense-firewall-lab

# Project Overview
Built a pfSense firewall in Oracle VirtualBox to simulate an enterprise network. Configured separate WAN/LAN interfaces, DHCP, NAT, and firewall services. Connected an Ubuntu client through an isolated internal network and verified secure internet connectivity through the firewall.

# Skills Demonstrated
- pfSense Firewall Administration
- VirtualBox Virtualization
- Network Segmentation
- DHCP Configuration
- NAT Configuration
- LAN/WAN Interface Configuration
- Linux Administration
- Network Troubleshooting

# Lab Topology
                Internet
                    │
             VirtualBox NAT
                    │
             pfSense Firewall
          WAN              LAN
                         192.168.1.1
                    │
             Internal Network
               (LabNet)
                    │
          Ubuntu Desktop VM
             192.168.1.101

# Configuration Summary
| Component       | Configuration     |
| --------------- | ----------------- |
| Hypervisor      | Oracle VirtualBox |
| Firewall        | pfSense CE        |
| WAN             | VirtualBox NAT    |
| LAN             | 192.168.1.1/24    |
| DHCP            | Enabled           |
| Ubuntu          | DHCP Client       |
| Internet Access | Verified          |

# Challenges Solved
- Resolved VirtualBox ISO detection issues.
- Configured Internal Network (LabNet) for VM communication.
- Diagnosed DHCP failures resulting in APIPA (169.254.x.x) addresses.
- Correctly configured pfSense DHCP services to restore client connectivity.
- Verified NAT and DNS functionality.
