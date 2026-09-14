Incident #001 — DNS Resolution Failure

Incident Summary

A Windows 11 workstation was reported to have network connectivity issues. The user reported that websites were not loading.

Environment

* Operating System: Windows 11 ARM
* Virtualization: Parallels Desktop
* Network Adapter: Parallels VirtIO Ethernet Adapter
* IPv4 Address: 10.211.55.5
* Default Gateway: 10.211.55.1

Reported Symptom

The computer is connected to the network, but websites are not loading.

Troubleshooting Process

1. Test Default Gateway

Command:

ping 10.211.55.1

Result:

4 packets sent
4 packets received
0% packet loss

Conclusion: The workstation could successfully communicate with its default gateway.

⸻

2. Test Internet Connectivity

Command:

ping 8.8.8.8

Result:

4 packets sent
4 packets received
0% packet loss

Conclusion: IP connectivity to the Internet was working.

⸻

3. Test DNS Resolution

Command:

nslookup google.com

Result:

DNS request timed out.
Server: UnKnown
Address: 192.0.2.1

Conclusion: DNS resolution was failing.

Root Cause

The workstation was configured to use an invalid DNS server:

192.0.2.1

The system still had working network and Internet connectivity, but DNS queries could not be resolved.

Resolution

The DNS configuration was restored to automatic configuration through DHCP.

The Parallels-provided DNS server was restored:

10.211.55.1

Verification

After restoring the DNS configuration:

nslookup google.com

successfully returned multiple IP addresses for google.com.

Final Status

Resolved ✅

Key Takeaways

This incident demonstrated the importance of testing different layers of network connectivity rather than assuming that an Internet-related problem is necessarily an Internet connection problem.

The troubleshooting process isolated the issue to DNS by verifying:

1. Local gateway connectivity
2. Internet IP connectivity
3. DNS name resolution

Skills Practiced

* ipconfig
* ping
* nslookup
* DNS troubleshooting
* TCP/IP fundamentals
* Root cause analysis
* Technical documentation
