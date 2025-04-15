# PROJECTNAME
redteam-lab-environment
## Objective

The goal of this project was to configure a secure and isolated virtual environment that supports cyber operations. This involved setting up virtual network interfaces in VMware Workstation Pro, configuring network settings on multiple virtual machines (Kali Linux, Metasploitable2, and Windows XP), and verifying communication between the systems. This environment allows for safe experimentation and simulation of attacks and defenses within a contained lab setup.
### Skills Learned

- Virtual networking with VMware Workstation Pro

- Manual configuration of VM interfaces and subnets

- Static IP assignment and MAC address validation

- Troubleshooting inter-VM connectivity

- Understanding virtual broadcast domains and subnet segmentation

### Tools Used
[Bullet Points - Remove this afterwards]

- VMware Workstation Pro

- Kali Linux (Attacker Machine)

- Metasploitable2 (MS2 - Bridge System)

- Windows XP (Target Machine)

- ifconfig / ipconfig / ping for network diagnostics

- Nano (text editor) for interface configuration

## Steps
Part 1: Configure VMware Virtual Network
Ref 1: Virtual Network Editor

Added VMnet10 as a custom host-only network and configured the subnet to 172.16.100.0/24, with DHCP disabled for full manual control.

Ref 2: VMnet10 Config

Verified that VMnet10 appeared in the editor and confirmed the new subnet configuration.

Part 2: Configure Metasploitable2 (MS2)
Ref 3: Dual Network Adapters

Attached two adapters: one to "Host-Only" (Kali side) and one to "VMnet10" (XP side) to serve as a network bridge.

Ref 4: MAC Address Validation

Matched MAC addresses from VMware with ifconfig output to ensure correct interface mapping (eth0 & eth1).

Ref 5: Interfaces Configuration

Manually edited /etc/network/interfaces to bring up eth1 with a static IP.

Ref 6: Successful Reboot and IP Assignment

Restarted MS2 and confirmed both eth0 and eth1 came online with expected IPs.

Part 3: Configure Windows XP
Ref 7: XP Network Adapter Assigned to VMnet10

Reassigned adapter to VMnet10 and applied static IP settings.

Ref 8: GUI IP Configuration

Configured TCP/IP settings via the control panel to match lab subnet requirements.

Ref 9: ipconfig Output

Verified correct IP assignment via command line.

Part 4: Verify Connectivity
Ref 10: Kali → MS2 Ping

[Screenshot showing Kali successfully pinging MS2]

Ref 11: MS2 → Kali Ping

![image](https://github.com/user-attachments/assets/1c38721b-e9f0-4fee-b8c0-60b7b4572951)


[Screenshot showing MS2 pinging Kali]

Ref 12: MS2 → WinXP Ping
![image](https://github.com/user-attachments/assets/1968f8f4-be98-4858-9310-8b5c2a4aed61)



[Screenshot showing MS2 pinging Windows XP]

Ref 13: WinXP → MS2 Ping
![image](https://github.com/user-attachments/assets/d6c5bb36-4f05-4576-829d-fecc9f7193b9)


[Screenshot showing Windows XP pinging MS2]
![image](https://github.com/user-attachments/assets/a7e8084b-3575-45c0-b803-f7b35296149a)



