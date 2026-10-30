<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2.8-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.3-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4?style=flat-square&labelColor=000000&logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Android-x86%209.0-3DDC84?style=flat-square&labelColor=000000&logo=android&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
</p>

---

## 📌 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network. Kali Linux acts as the attacker machine, and **Windows 10, Windows 11, and Android** virtual machines are added as targets for authorized security testing.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Build target machines: Windows 10, Windows 11, and Android.
- Verify communication between the attacker and target machines.
- Document the complete setup process, including problems and solutions.
- Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture

![Lab Architecture](./Lab%20Architecture.png)

*Lab architecture: the Kali, Windows 10, Windows 11, and Android VMs connected to the same NAT Network.*

The attacker machine (Kali Linux) and all target machines (Windows 10, Windows 11, Android) are connected to the same NAT Network. Additional target machines can be added to the same virtual network in future projects.

---

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------ |
| 🖥️ Host OS         | Windows 11         |
| 🧠 Host RAM        | 32 GB              |
| ⚡ Processor       | Intel Core Ultra 9 |
| 🧰 Hypervisor      | VirtualBox 7.2.8   |
| 🐉 Security OS     | Kali Linux 2026.3  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

### 🧮 Virtual Machine Resource Summary

| 💻 Virtual Machine | 🧠 Memory (RAM) | ⚙️ CPU Cores | 💾 Storage | 📡 IP Address |
| ------------------ | --------------- | ------------ | ---------- | ------------- |
| 🐉 Kali Linux      | 2048 MB         | 1            | 80.09 GB   | 10.0.0.2      |
| 🪟 Windows 10      | 4096 MB         | 1            | 30.00 GB   | 10.0.0.10     |
| 🪟 Windows 11      | 6144 MB         | 4            | 50.00 GB   | 10.0.0.11     |
| 🤖 Android         | 4096 MB         | 2            | 15.00 GB   | 10.0.0.9      |

---

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:

```text
Network Name: NatNetwork_1
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled
```

![NatNetwork_1 configuration](./0.%20NAT%20Network%20Config.png)

*NatNetwork_1 configuration in VirtualBox.*

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This allows the attacker and target VMs to communicate within the lab.

---

## Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork_1
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM RAM and CPU cores and storage allocations will be specified later on in a table.

A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---

## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Configuration:

```text
IP Address:  10.0.0.2
Subnet Mask: 255.255.255.0
Gateway:     10.0.0.1
DNS:         8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

![Kali VM Network Configuration](./1.%20kali%20VM%20network%20config.png)

*Kali VM network configuration.*

---

## Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Snapshot name:

```text
Clean Kali - Network Setup
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---

# 🐉 Kali Linux VM (Attacker Machine)

### 🧮 Allocated Resources

| 🧩 Resource     | ⚙️ Allocation |
| --------------- | ------------- |
| 🧠 Memory (RAM) | 2048 MB       |
| ⚙️ CPU Cores    | 1             |
| 💾 Storage      | 80.09 GB      |

### 🔎 Lab Verification

| ✅ Test                       | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | Correct Kali IP displayed       |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution        | `nslookup networkwalks.com`     | Domain resolves                 |
| 🧰 Verify Nmap                | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot            | Restore snapshot and run `ip a` | Baseline configuration restored |

### Example Results

```text
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```

![Kali VM Network set up verification](./1.1.Kali%20network%20verfication.png)

*Kali VM network setup verification.*

### 🐞 Problems Encountered & Solutions

**Problem: Kali Linux network issue**

Kali's network did not work correctly after rebooting the VM afterthe initial setup. The issue was resolved by following steps.
run these commands:
` sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0`
`sudo nmcli connection down "Wired connection 1"`
`sudo nmcli connection up "Wired connection 1"`

✅ **Status:** SOLVED

> **Important:** Network interface and connection names may differ between systems. Always identify your actual connection name before running network configuration commands.

---

# 🪟 Windows 10 VM (Target Machine #1)

The Windows 10 VM is used as a target machine for authorized security testing. It was set up using the same procedure as the other VMs: create the VM, attach the ISO, connect it to `NatNetwork_1`, install the OS, verify connectivity, and take a clean snapshot.

### 🧮 Allocated Resources

| 🧩 Resource     | ⚙️ Allocation |
| --------------- | ------------- |
| 🧠 Memory (RAM) | 4096 MB       |
| ⚙️ CPU Cores    | 2             |
| 💾 Storage      | 30.00 GB      |

### ⚙️ Configuration

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork_1
Adapter Type: Intel PRO/1000 MT Desktop

IP Address:   (TBD)
Gateway:      10.0.0.1
DNS:          8.8.8.8
```

![Windows 10 VM Network Configuration](./3.%20windows%2010%20vm%20network%20setup%20complete.png)

*Windows 10 VM network configuration after setup is complete.*

### 🔎 Testing

| ✅ Test                             | 🎯 Expected Result                                |
| ----------------------------------- | ------------------------------------------------- |
| 📡 Windows 10 pings Kali (10.0.0.2) | Successful replies                                |
| 🐉 Kali pings Windows 10            | Successful replies (after the firewall fix below) |
| 🌍 Windows 10 reaches the Internet  | Successful replies                                |

![Windows 10 VM pings Kali](./4.%20windows%2010%20vm%20can%20ping%20kali%20vm%20test.png)

*Windows 10 VM successfully pinging the Kali VM.*

<br>

![Kali VM can ping Windows 10 VM](./5.%20showing%20kalivm%20able%20to%20ping%20windows10%20vm%20-%20firewall%20rules%20change%20to%20allow%20recieving%20ipv4%20icmp%20packets%20change%20to%20allow%20this.png)

*Kali VM successfully pinging the Windows 10 VM after the firewall rules were changed to allow incoming IPv4 ICMP packets.*

<br>

![Windows 10 VM can reach the internet](./13.%20windows%2010%20reaches%20the%20internet.png)

*Windows 10 VM reaching the Internet.*

### 🐞 Problems Encountered & Solutions

**Problem: Kali VM cannot ping the Windows 10 VM, but Windows 10 can ping Kali**

The problem is most likely caused by the default Windows firewall settings, which block incoming ICMP (ping) requests.

**Solution:** The Windows firewall configuration was edited to allow the VM to receive ICMP packets.
The rules enabled and allowed are:
File and Printer Sharing (Echo Request - ICMPv4-In) Domain Yes
File and Printer Sharing (Echo Request - ICMPv4-In) Private Yes
File and Printer Sharing (Echo Request - ICMPv4-In) Public Yes

![Inbound firewall rules to enable on Windows 10](./5.%20showing%20kalivm%20able%20to%20ping%20windows10%20vm%20-%20firewall%20rules%20change%20to%20allow%20recieving%20ipv4%20icmp%20packets%20change%20to%20allow%20this.png)

*The inbound firewall rules to enable (shown in the right window) so the VM accepts ICMP echo requests.*

✅ **Status:** SOLVED

---

# 🪟 Windows 11 VM (Target Machine)

The Windows 11 VM is used as a second Windows target machine. It was set up using the same procedure as the Windows 10 VM.

### 🧮 Allocated Resources

| 🧩 Resource     | ⚙️ Allocation |
| --------------- | ------------- |
| 🧠 Memory (RAM) | 6144 MB       |
| ⚙️ CPU Cores    | 4             |
| 💾 Storage      | 50.00 GB      |

### ⚙️ Configuration

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork_1
Adapter Type: Intel PRO/1000 MT Desktop

IP Address:   (TBD)
Gateway:      10.0.0.1
DNS:          8.8.8.8
```

![Windows 11 VM Network Configuration](./10.%20Windows11%20vm%20network%20config.png)

*Windows 11 VM network configuration.*

### 🔎 Testing

| ✅ Test                             | 🎯 Expected Result                                |
| ----------------------------------- | ------------------------------------------------- |
| 📡 Windows 11 pings Kali (10.0.0.2) | Successful replies                                |
| 🐉 Kali pings Windows 11            | Successful replies (after the firewall fix below) |
| 🌍 Windows 11 reaches the Internet  | Successful replies                                |

![Windows 11 VM can ping Kali VM](./11.%20Win11%20vm%20can%20ping%20kali%20vm.png)

*Windows 11 VM successfully pinging the Kali VM.*

<br>

![Kali VM can ping Windows 11 VM](./12.%20Kali%20vm%20can%20ping%20windows11%20vm%20+%20showing%20the%20fix%20and%20changes%20in%20the%20win%2011%20firewall%20inbound%20ruling.png)

*Kali VM successfully pinging the Windows 11 VM, with the fix and changes to the Windows 11 firewall inbound rules shown.*

### 🐞 Problems Encountered & Solutions

**Problem: Kali VM cannot ping the Windows 11 VM, but Windows 11 can ping Kali**

This is the same issue encountered with the Windows 10 VM.

**Solution:** The Windows firewall inbound rules were changed in exactly the same way done for windows 10 vm, to allow incoming ICMP echo requests.

✅ **Status:** SOLVED

---

# 🤖 Android VM (Target Machine)

The Android VM (Android-x86 9.0 R2) is used as a mobile-platform target machine. It was set up using the same general procedure as the other VMs.

### 🧮 Allocated Resources

| 🧩 Resource     | ⚙️ Allocation |
| --------------- | ------------- |
| 🧠 Memory (RAM) | 4096          |
| ⚙️ CPU Cores    | 2             |
| 💾 Storage      | 15.00GB       |
| 🎮 Video Memory | 128 MB        |

### ⚙️ Configuration

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork_1
Adapter Type: Intel PRO/1000 MT Desktop

IP Address:   (TBD)
Gateway:      10.0.0.1
DNS:          8.8.8.8
```

![Android VM Network Configuration](./6.%20Android%20vm%20network%20config%20done.png)

*Android VM network configuration completed.*

### 🔎 Testing

| ✅ Test                          | 🎯 Expected Result |
| -------------------------------- | ------------------ |
| 📡 Android pings Kali (10.0.0.2) | Successful replies |
| 🐉 Kali pings Android            | Successful replies |
| 🌍 reaches the Internet          | Successful         |

![Kali VM can ping Android VM](./8.%20Can%20ping%20android%20vm%20from%20kali%20vm.png)

*Kali VM successfully pinging the Android VM.*

<br>

![Android VM can ping Kali VM](./9.%20Can%20ping%20kali%20vm%20from%20android%20vm.png)

*Android VM successfully pinging the Kali VM.*

<br>

![Android VM can reach the internet](./7.%20Android%20vm%20network%20test%20-%20can%20search%20using%20chrome.png)

*Android VM reaching the Internet (searching with Chrome as an example).*

### 🐞 Problems Encountered & Solutions

**Problem 1: Android VM crashes during installation**

The installer kept crashing with the default VM settings.

**Solution:** Graphics memory was set to the maximum, the VM was given 2 CPU cores, and more memory was allocated. After these changes the installation completed without crashing.

✅ **Status:** SOLVED

**Problem 2: Android VM keeps reinstalling on every reboot**

After installation, the VM booted back into the installer each time it was restarted.

**Solution:** The ISO file was removed from the VM's storage settings after installation was complete, so the VM boots from the virtual disk instead.

✅ **Status:** SOLVED

---

# 🐞 Summary of Problems & Solutions

Documenting problems is an important part of the project.

| #   | 🧩 Machine | ❗ Problem                                                | 🛠️ Solution                                         | Status    |
| --- | ---------- | --------------------------------------------------------- | --------------------------------------------------- | --------- |
| 1   | Kali Linux | Network issue                                             | Followed the provided PDF guide (details above)     | ✅ Solved |
| 2   | Windows 10 | Kali cannot ping Windows 10, but Windows 10 can ping Kali | Edited firewall to allow inbound ICMP echo requests | ✅ Solved |
| 3   | Windows 11 | Kali cannot ping Windows 11, but Windows 11 can ping Kali | Changed the inbound firewall rule the same way      | ✅ Solved |
| 4   | Android    | Installation crashes                                      | Maxed out graphics, 2 CPU cores, more memory        | ✅ Solved |
| 5   | Android    | Reinstalls on every reboot                                | Removed the ISO from VM settings after installation | ✅ Solved |

---

# 💡 What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. Host Firewalls and ICMP

I learned that connectivity can be one-directional: the Windows VMs could ping Kali, but Kali could not ping them because the Windows firewall blocks inbound ICMP by default.

### 5. VM Resource Allocation

I learned that VM settings such as CPU cores, memory, and graphics memory directly affect whether an operating system installs and runs reliably.

### 6. VM Snapshots

I learned that a clean snapshot should be created **before performing risky or experimental activities**.

This provides a known-good recovery point for future cybersecurity exercises.

### 7. Documentation

I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for education purposes only.

---

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **Windows 11 ISO:** [https://www.microsoft.com/en-us/software-download/windows11](https://www.microsoft.com/en-us/software-download/windows11)
- **Windows 10 ISO:** [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)
- **Android 9.0 R2 (Android-x86):** [https://sourceforge.net/projects/android-x86/](https://sourceforge.net/projects/android-x86/)

---

# 👤 Author

**Omar Amin**\
Cybersecurity Professional

LinkedIn: www.linkedin.com/in/omar-amin-0w31

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub
