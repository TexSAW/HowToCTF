# The value of a LAN

It is incredibly benificial to have control of the network fabric when running a CTF.  This kind of control is generally only available if the group running the CTF is also the group running the routing infrastructure.  To this end TexSAW used a physically seperate LAN from the main university LAN.  This consisted of the router, switches, and WAP that were in use during the lecture component and during the CTF.

The router itself is simply a desktop computer with two network interfaces running OpenBSD configured with Ansible.  In general this machine should be capable of routing traffic at as close a rate as possible to 1 Gbps.  The router used for TexSAW was capable of routing traffic from the internal connection to the external connection at a rate of 600 Mbps.

The WAP used should be of enterprise quality if available.  Most small home and office (SOHO) equipment is generally suitable for up to 50 people.  Much beyond this threshold it is necessary to use solutions such as WDS and load sharing to ensure that no single WAP is overloaded.  The infrastructure team for TexSAW has used Ubiquiti UniFi hardware with great success in the past, but this would have been substantially overkill for TexSAW.

All switching gear should be ablet to handle gigabit traffic.  While it is acceptable to use slower switches at the edges of the network, it is a must that the core switches be able to handle a fully saturated network.  This is fortunately not an issue as switches are quite cheap and the average IT department has a decently large pile of slightly obsolete switches that while no longer valid for use on the university LAN would work quite well on a smaller conference LAN.

While the concepts of actually running a network are beyond the scope of this document, the entire configuration set for our gateway is applied using the SimpleGateway suite of Ansible roles.  Due to our extensive use of automation, the network is configured with a single file as shown below:

```
---
gw_network: 192.168.2.0

dhcp_self: 192.168.2.1
dhcp_lower: 192.168.2.2
dhcp_upper: 192.168.2.200

domain: texsaw
domain_address: 10.176.169.100
hostname: cardboard

dns_SOA: 2016110401

int_if: bge0
ext_if: re0

boot_fname:
boot_next:

ntp:
- pool.ntp.org

staticHosts:
  wap:
    mac: 44:94:fc:39:50:ea
    addr: 192.168.2.2
    name: wap
  exploitables:
    mac: ff:ff:ff:ff:ff:01
    addr: 10.176.169.101
    name: exploitables
    CNAME:
      - congratulations
      - nullserve
      - pizzacuts
      - seconddate
      - monit
  texsaw:
    mac: ff:ff:ff:ff:ff:00
    addr: 10.176.169.100
    name: ctf

stubZones:
  UTD:
    name: utdallas.edu
    private: true
    localZone: 10.in-addr.arpa
    addresses:
      - <redacted>
      - <redacted>
                              
```
