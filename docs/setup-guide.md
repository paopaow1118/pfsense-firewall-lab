# pfSense Firewall Lab - Setup Guide

## Overview

This guide documents the process of building a virtual firewall lab using pfSense and Oracle VirtualBox. The lab simulates a small enterprise network by separating WAN and LAN traffic and routing all client traffic through a pfSense firewall.

## Objectives

* Deploy a pfSense firewall in a virtual environment.
* Configure separate WAN and LAN interfaces.
* Enable DHCP on the LAN network.
* Connect a client VM to the firewall.
* Verify internet connectivity through pfSense.
* Gain hands-on experience with firewall administration and network troubleshooting.

---

# Lab Environment

| Component       | Configuration               |
| --------------- | --------------------------- |
| Hypervisor      | Oracle VirtualBox           |
| Firewall        | pfSense Community Edition   |
| Client          | Ubuntu Desktop              |
| WAN Network     | VirtualBox NAT              |
| LAN Network     | Internal Network (`LabNet`) |
| Firewall LAN IP | 192.168.1.1/24              |
| Ubuntu IP       | 192.168.1.101/24 (DHCP)     |

---

# Network Topology

```text
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
             Ubuntu Desktop
             192.168.1.101
```

---

# Virtual Machine Configuration

## pfSense

### Adapter 1

* Attached to: NAT
* Purpose: Internet connectivity (WAN)

### Adapter 2

* Attached to: Internal Network
* Network Name: LabNet
* Purpose: Private LAN for client devices

---

## Ubuntu

### Adapter 1

* Attached to: Internal Network
* Network Name: LabNet

The Ubuntu VM receives its IP address from the pfSense DHCP server.

---

# pfSense Configuration

The following configuration was completed after installation:

* Assigned WAN and LAN interfaces.
* Configured the LAN interface with a static address of **192.168.1.1/24**.
* Enabled the DHCP server on the LAN interface.
* Configured the DHCP address pool.
* Completed the pfSense web configuration wizard.
* Verified WAN connectivity.
* Verified NAT functionality.

---

# Connectivity Validation

The following tests were performed to verify the lab:

* Ubuntu successfully received a DHCP lease.
* Ubuntu accessed the pfSense web interface.
* Ubuntu successfully pinged the pfSense gateway.
* Ubuntu successfully pinged **8.8.8.8**.
* Ubuntu successfully resolved DNS by pinging **google.com**.

These tests confirmed that routing, DHCP, DNS, and NAT were functioning correctly.
