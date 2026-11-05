# Networkwalks – Week 1 Project

## Cybersecurity Testing Lab Setup Using Kali Linux and VirtualBox

### Project Overview

This project documents the setup of a cybersecurity testing laboratory using Oracle VirtualBox and Kali Linux as part of the Networkwalks Cybersecurity Internship Program.

The objective was to establish a functional virtual environment with network connectivity, shared-folder access, and essential virtual machine integration features. This lab will serve as the foundation for subsequent practical cybersecurity exercises.

### Project Objectives

* Install and configure Kali Linux in Oracle VirtualBox.
* Configure a VirtualBox NAT Network.
* Assign the required static IP address to the Kali Linux virtual machine.
* Establish internet connectivity.
* Enable shared clipboard and drag-and-drop functionality.
* Configure and verify shared-folder access between the host and virtual machine.
* Create a baseline virtual machine snapshot.

### Tools and Technologies

| Tool                       | Purpose                                |
| -------------------------- | -------------------------------------- |
| Oracle VirtualBox          | Virtualisation platform                |
| Kali Linux                 | Cybersecurity testing operating system |
| NAT Network                | Virtual network configuration          |
| VirtualBox Guest Additions | Virtual machine integration            |
| Linux Terminal             | Network configuration and verification |

### Lab Network Configuration

The project requirements specify the following network configuration:

| Parameter             | Configuration |
| --------------------- | ------------- |
| Network Type          | NAT Network   |
| Network Address       | 10.0.0.0/24   |
| Kali Linux IP Address | 10.0.0.2/24   |
| Network Interface     | eth0          |

### Implementation and Verification

#### 1. Kali Linux Installation

Kali Linux was installed and configured as a virtual machine using Oracle VirtualBox.

#### 2. Network Configuration

The virtual machine was connected to the configured NAT Network.

The assigned IP address was verified using:

```bash
ip a
```

The interface displayed the required address:

```text
10.0.0.2/24
```

#### 3. Internet Connectivity

Internet connectivity was tested using:

```bash
ping -c 4 google.com
```

The test returned four successful replies with zero packet loss, confirming internet and DNS connectivity.

#### 4. VirtualBox Integration

The following integration settings were configured:

* Shared Clipboard
* Drag and Drop
* VirtualBox Guest Additions

Guest Additions modules were verified using:

```bash
lsmod | grep vbox
```

#### 5. Shared Folder Configuration

A shared folder named `Downloads` was configured in VirtualBox.

The folder was verified inside Kali Linux using:

```bash
ls /media/sf_Downloads
```

The host files were successfully displayed from within the virtual machine.

#### 6. Virtual Machine Snapshot

A baseline snapshot will preserve the configured lab environment for future recovery and practical exercises.

Snapshot status: completed.

### Troubleshooting

**Issue: Kali Linux initially failed to obtain an IPv4 address and internet connectivity.**

**Solution:** The IPv4 Duplicate Address Detection timeout was adjusted using the NetworkManager command provided in the project guide.

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
```

The network connection was then restarted:

```bash
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

After applying the changes, Kali Linux obtained the required IP address and internet connectivity was restored.

### Screenshots and Evidence

Screenshots documenting the installation, network configuration, connectivity tests, shared-folder access, and final snapshot are available in the `screenshots/` directory.

### Conclusion

The Networkwalks Week 1 cybersecurity testing laboratory has been configured with Kali Linux running inside Oracle VirtualBox.

Network addressing, internet connectivity, Guest Additions, and shared-folder access were successfully verified. The environment provides a foundation for the practical cybersecurity activities in the upcoming internship modules.

### Internship Information

* **Program:** Networkwalks Cybersecurity Internship
* **Project:** Week 1 – Project Module 1
* **Participant:** Korede Oluwakayode
* **Platform:** Oracle VirtualBox
* **Operating System:** Kali Linux
