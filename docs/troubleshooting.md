# Troubleshooting

This document records the issues encountered while building the pfSense firewall lab and the steps taken to resolve them.

---

# Issue 1: VirtualBox Could Not Detect the pfSense ISO

## Symptoms

* The downloaded pfSense installer did not appear in VirtualBox when selecting an optical disk.

## Cause

The downloaded file was still recognized as a compressed archive instead of an ISO image.

## Resolution

* Extracted the downloaded archive.
* Selected the extracted `.iso` file when configuring the virtual optical drive.

## Lesson Learned

Always verify that the installer is an actual ISO image before attaching it to a virtual machine.

---

# Issue 2: Ubuntu Received a 169.254.x.x Address

## Symptoms

* Running `ip a` displayed an address in the `169.254.x.x` range.
* Ubuntu could not initially communicate with the firewall.

## Cause

Ubuntu was unable to obtain an IP address from the pfSense DHCP server.

## Resolution

* Verified that the pfSense LAN interface was configured with a static IP address (`192.168.1.1/24`).
* Confirmed the DHCP server was enabled on the LAN interface.
* Restarted the virtual machines after applying the configuration.

## Lesson Learned

A `169.254.x.x` address (APIPA) indicates that a client failed to obtain a DHCP lease.

---

# Issue 3: Internal Network Configuration

## Symptoms

The client VM was unable to communicate with the pfSense LAN interface.

## Cause

Virtual machines must be connected to the same VirtualBox Internal Network.

## Resolution

Configured the virtual network adapters as follows:

* pfSense Adapter 2 → Internal Network (`LabNet`)
* Ubuntu Adapter 1 → Internal Network (`LabNet`)

## Lesson Learned

All devices intended to communicate on the virtual LAN must be attached to the same Internal Network.

---

# Issue 4: pfSense Web Interface Inaccessible

## Symptoms

The pfSense web interface could not initially be reached from the Ubuntu VM.

## Cause

The client had not yet received a valid DHCP lease.

## Resolution

After confirming the LAN configuration and DHCP service, Ubuntu received a valid address (`192.168.1.101/24`), allowing access to:

* `https://192.168.1.1`

## Lesson Learned

Always verify client IP configuration before troubleshooting web services.

---

# Issue 5: Internet Connectivity Verification

## Validation

Connectivity was confirmed by performing the following tests:

* Successful ping to `192.168.1.1`
* Successful ping to `8.8.8.8`
* Successful DNS resolution using `google.com`

## Result

The tests confirmed:

* DHCP functioning correctly
* NAT operational
* DNS resolution working
* Internet access routed successfully through pfSense

