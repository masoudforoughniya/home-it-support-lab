Home IT Support Lab

A hands-on IT support and troubleshooting lab built using Windows 11 ARM running in a Parallels virtual machine.

Project Overview

This project simulates real-world IT support scenarios involving hardware, operating systems, networking, and system troubleshooting.

The goal is to practice a structured troubleshooting methodology and document the investigation, root cause, resolution, and verification of each incident.

Lab Environment

* Host: MacBook Air M1
* Virtualization: Parallels Desktop
* Guest OS: Windows 11 ARM
* Network Adapter: Parallels VirtIO Ethernet Adapter
* IPv4 Address: 10.211.55.5
* Default Gateway: 10.211.55.1
* DNS: 10.211.55.1

Troubleshooting Methodology

Each incident follows a structured troubleshooting process:

1. Identify the problem
2. Establish a baseline
3. Gather evidence
4. Test possible causes
5. Identify the root cause
6. Apply a solution
7. Verify the fix
8. Document the results

Incidents

Incident #001 — DNS Resolution Failure

Status: Resolved ✅

Reported Issue:

The computer is connected to the network, but websites are not loading.

Initial Investigation:

The following tests were performed:

* Gateway connectivity test
* Internet connectivity test
* DNS resolution test

Findings:

* Default Gateway: Reachable
* Internet connectivity: Working
* DNS resolution: Failed

The DNS server had been incorrectly configured as 192.0.2.1.

Root Cause:

Invalid DNS server configuration.

Resolution:

DNS configuration was restored to automatic configuration through DHCP.

Verification:

nslookup google.com successfully returned Google’s IP addresses after the configuration was restored.

Skills Demonstrated

* Windows 11 troubleshooting
* TCP/IP fundamentals
* DNS troubleshooting
* ipconfig
* ping
* nslookup
* Network connectivity analysis
* Root cause identification
* Technical documentation

Future Incidents

Additional troubleshooting scenarios will be added to this lab, including:

* Hardware / USB troubleshooting
* Windows performance troubleshooting
* Driver issues
* Storage and disk problems
* User account and permissions issues
