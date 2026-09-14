# Home IT Support Lab

A hands-on IT support and troubleshooting lab built using Windows 11 ARM running in a Parallels virtual machine.

## Project Overview

This project simulates real-world IT support scenarios involving hardware, operating systems, networking, storage, and system troubleshooting.

The goal is to practice a structured troubleshooting methodology and document the investigation, root cause, resolution, and verification of each incident.

## Lab Environment

* Host: MacBook Air M1
* Virtualization: Parallels Desktop
* Guest OS: Windows 11 ARM
* Network Adapter: Parallels VirtIO Ethernet Adapter
* IPv4 Address: 10.211.55.5
* Default Gateway: 10.211.55.1
* DNS: 10.211.55.1

## Troubleshooting Methodology

Each incident follows a structured troubleshooting process:

1. Identify the problem
2. Establish a baseline
3. Gather evidence
4. Test possible causes
5. Identify the root cause
6. Apply a solution
7. Verify the fix
8. Document the results

## Incidents

### Incident #001 — DNS Resolution Failure

**Status: Resolved ✅**

**Reported Issue:**

The computer is connected to the network, but websites are not loading.

**Initial Investigation:**

The following tests were performed:

* Gateway connectivity test
* Internet connectivity test
* DNS resolution test

**Findings:**

* Default Gateway: Reachable
* Internet connectivity: Working
* DNS resolution: Failed

The DNS server had been incorrectly configured as `192.0.2.1`.

**Root Cause:**

Invalid DNS server configuration.

**Resolution:**

DNS configuration was restored to automatic configuration through DHCP.

**Verification:**

`nslookup google.com` successfully returned Google’s IP addresses after the configuration was restored.

**Documentation:**

[View Incident #001](incidents/incident-001-dns-failure.md)

**Evidence:**

[View Incident #001 Evidence](evidence/incident-001/README.md)

---

### Incident #002 — Missing Drive Letter

**Status: Resolved ✅**

**Reported Issue:**

A storage volume was no longer visible in Windows File Explorer.

**Initial Investigation:**

Disk Management and DiskPart were used to investigate the missing drive.

**Findings:**

* Disk 1 was Online
* The volume was detected by Windows
* File system was NTFS
* Volume status was Healthy
* The volume was not hidden or offline
* No drive letter was assigned

**Root Cause:**

The `IT-LAB-DISK` volume did not have a drive letter assigned.

**Resolution:**

The missing drive letter was restored using DiskPart:

```cmd
assign letter=E
```

**Verification:**

The restored drive was verified using:

```cmd
dir E:\
```

and:

```cmd
fsutil fsinfo volumeinfo E:
```

The volume was confirmed as NTFS and read/write.

**Documentation:**

[View Incident #002](incidents/incident-002-missing-drive.md)

**Evidence:**

[View Incident #002 Evidence](evidence/incident-002/README.md)

---

## Skills Demonstrated

### Operating Systems & Troubleshooting

* Windows 11 troubleshooting
* Disk Management
* DiskPart
* Storage troubleshooting
* Drive letter management
* Root cause identification
* Technical documentation

### Networking

* TCP/IP fundamentals
* DNS troubleshooting
* Network connectivity analysis
* `ipconfig`
* `ping`
* `nslookup`

## Future Incidents

Additional troubleshooting scenarios will be added to this lab, including:

* Windows performance troubleshooting
* Driver issues
* User account and permissions issues
* Hardware troubleshooting
* Additional networking scenarios

## Project Goals

This lab is continuously evolving as new IT support and infrastructure concepts are learned and practiced.

The long-term goal is to expand the lab toward networking, Linux administration, automation, and cloud infrastructure.
