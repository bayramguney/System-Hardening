# System-Hardening

# 🛡️ Applied Lab: System Hardening

> Strengthen Windows and Linux systems by managing device drivers, removing unnecessary software and services, and controlling hostname resolution through the hosts file.

---

## 📖 Overview

In this lab, I performed several system hardening tasks designed to reduce the attack surface and improve overall security. The exercises included managing Windows device drivers, removing unnecessary applications and insecure services, and modifying the Linux `/etc/hosts` file to control local DNS resolution.

These activities demonstrate common hardening techniques used by security administrators to secure enterprise systems.

---

## 🎯 Objectives

This lab aligns with the following **CompTIA Security+ (SY0-701)** objectives:

- **2.5** Explain the purpose of mitigation techniques used to secure the enterprise.
- **3.2** Apply security principles to secure enterprise infrastructure.
- **4.1** Apply common security techniques to computing resources.

---

## 🖥️ Lab Environment

| Virtual Machine | Operating System | Purpose |
|-----------------|-----------------|---------|
| **MS10** | Windows Server 2016 | Windows system hardening |
| **KALI** | Debian Linux (Kali) | Linux hosts file management |

---

# Part 1 – Managing Device Drivers

## Objective

Practice managing Windows device drivers to improve system security and remove unnecessary hardware support.

---

## Tasks Completed

- Scanned the system for hardware changes.
- Updated the **Microsoft Virtual DVD-ROM** driver.
- Disabled the device.
- Re-enabled the device.
- Uninstalled the device driver.
- Reinstalled the device using **Scan for hardware changes**.

---

## Key Commands & Tools

- Device Manager
- Scan for Hardware Changes
- Update Driver
- Disable Device
- Enable Device
- Uninstall Device

---

## Security Importance

Proper driver management helps:

- Remove vulnerable or unnecessary drivers.
- Prevent unauthorized hardware usage.
- Reduce the system attack surface.
- Troubleshoot malfunctioning devices.

---

## Key Finding

**Disabling** a device prevents it from functioning even after rebooting or rescanning for hardware.

---

# Part 2 – Removing Unnecessary Applications & Services

## Objective

Reduce the attack surface by uninstalling unused software and insecure services.

---

## Applications Removed

### CPUID CPU-Z

Removed using:

- Programs and Features

---

## Windows Service Removed

### FTP Server (IIS)

Removed using:

- Server Manager
- Remove Roles and Features Wizard

---

## Why Remove FTP?

FTP:

- Sends credentials in plaintext
- Lacks encryption
- Is vulnerable to packet sniffing
- Should be replaced by:
  - SFTP
  - FTPS

---

## Security Benefits

Removing unnecessary software:

- Eliminates vulnerabilities
- Reduces maintenance
- Lowers attack surface
- Improves compliance

---

# Part 3 – Editing the Linux Hosts File

## Objective

Control local hostname resolution without relying on DNS.

---

## View Hosts File

```bash
cat /etc/hosts
```

---

## Edit Hosts File

```bash
nano /etc/hosts
```

---

## Original Entry

```text
203.0.113.228 juiceshop.local
```

---

## Introduce False Mapping

```text
203.0.113.249 juiceshop.local
```

Result:

- DNS lookup was overridden.
- Connection failed because the IP was invalid.

---

## Restore Correct Mapping

```text
203.0.113.228 juiceshop.local
```

Result:

- Website resolved correctly.
- `wget` successfully downloaded the page.

---

## Verify Resolution

```bash
wget juiceshop.local
```

Expected result:

```
index.html saved
```

---

## Hosts File Format

```text
IP_Address    Hostname
```

Example:

```text
127.0.0.1 localhost
192.168.1.10 fileserver.local
```

---

# Security Benefits of the Hosts File

Editing the hosts file allows administrators to:

- Force a hostname to resolve to a specific IP.
- Redirect users to another server.
- Block access by mapping domains to invalid or loopback addresses.
- Override DNS responses locally.

---

## Example Blocking Entry

```text
127.0.0.1 malicious-site.com
```

This prevents the system from reaching the real website.

---

# Skills Demonstrated

- Windows Device Manager
- Driver management
- Driver updates
- Hardware rescanning
- Windows Server Manager
- Removing Windows roles
- Removing Windows features
- FTP service removal
- Linux terminal
- Nano editor
- Linux hosts file management
- Local DNS override
- System hardening
- Attack surface reduction

---

# Key Security Concepts

- Principle of least functionality
- Attack surface reduction
- Driver management
- Secure configuration
- Service hardening
- Software removal
- Local DNS resolution
- Hosts file precedence
- Enterprise system hardening

---

# Lab Outcome

Successfully hardened Windows and Linux systems by:

- Managing and troubleshooting device drivers.
- Removing unnecessary software and insecure services.
- Controlling local hostname resolution using the Linux hosts file.
- Demonstrating how reducing unnecessary components strengthens enterprise security and minimizes potential attack vectors.

---

## 🛠️ Tools Used

- Windows Server 2016
- Kali Linux
- Device Manager
- Server Manager
- Programs and Features
- Remove Roles and Features Wizard
- Nano
- Wget
- `/etc/hosts`

---

## 🚀 Technologies & Concepts

- Windows Administration
- Linux Administration
- Device Drivers
- System Hardening
- Secure Configuration
- FTP Removal
- DNS Resolution
- Hosts File
- Network Security
- Endpoint Security
- CompTIA Security+ (SY0-701)
```
