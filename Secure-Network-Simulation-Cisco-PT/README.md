### Secure Network Simulation — Cisco Packet Tracer

A simulated enterprise network built to demonstrate secure network design principles.

**Highlights:**
- 3 PCs connected to a switch
- Database server connected through an internal ASA firewall
- Internal firewall connected to switch → router → external firewall → internet
- IP addressing and subnetting applied correctly
- Firewalls configured with VLANs, nameifs, and ACLsPings from firewall to DB successful; pings from PCs timed out due to routing/ACL path issues

**Weaknesses in the Design**
1. Single path/no redundancy:
-  There's only one route from PCs to the database and internet, and if any single device (router, firewall, or switch) fails, the entire connection breaks

2. Limited segmentation:
- All PCs share the same subnet
- No VLAN segmentation for groups of users or services

3. No monitoring or intrusion detection:
- No logging, IDS/IPS, or SNMP implemented
- Traffic flows are not being inspected for anomalies or attacks

4. ICMP used for testing only:
- Real applications (SQL, HTTP, etc.) aren't simulated
- Network appears functional, but security enforcement is shallow

**Suggested Improvements**
1. Segmentation:
- Separate PCs into VLANs by role (e.g., finance, HR), and add subnets per VLAN to better contain internal threats

2. Monitoring & Visibility:
- Deploy SNMP-based monitoring tools, and configure ASA logging to observe traffic and events

3. Redundancy:
- Add a second router and switch, and use link aggregation for failover and load balancing

4. Security Enhancements:
- Apply stricter ACLs to allow only specific ports/protocols and implement DMZ for public-facing services
