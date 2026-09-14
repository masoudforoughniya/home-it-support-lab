Incident #001 — Evidence

This directory contains supporting evidence collected during the DNS troubleshooting incident.

Evidence Files

DNS Failure

dns-failure.png

Shows the failed DNS resolution after an invalid DNS server was configured.

Expected evidence:

* DNS request timeout
* DNS server: 192.0.2.1

DNS Restored

dns-restored.png

Shows successful DNS resolution after restoring the DNS configuration to DHCP.

Expected evidence:

* DNS server: 10.211.55.1
* Successful resolution of google.com
