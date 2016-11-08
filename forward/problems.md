# Expect the Worst

The statement goes that one should always hope for the best, but plan for the worst.  This goes doubly so for CTFs.  It could be said that the true mark of success for a CTF is the uptime of the competition services.  The highest quality challenges in the world mean nothing if they are unavailible to competitors.  To this end we leveraged technologies such as Runit, Monit, custom local networks, proven wireless technologies, and complete full stack management with Ansible.


## Runit

Runit keeps track of all competition components and restarts them when necessary.  More information is available in the 'Exploits' section of this manual.


## Monit

Monit allowed us to keep an eye on not only the exploitable components, but also the network infrastructure.  When we diagnosed a network fault on the first day of the TexSAW conference, we quickly spun up an instance of Monit to keep an eye on the various hops in our network that we thought could be the source of the outage.  More information on Monit is available in the 'Monitoring' section of this manual.


## Custom LANs

We made use of a purpose built LAN for TexSAW.  This enabled us to permit conference attendees to have access to a 'sandbox' LAN without needing to handle 802.1X authentication for guests to our institution.  For our LAN we sourced a commodity desktop with two gigabit network adapters in it.  The machine ran OpenBSD which is renowned for its security and high speed implementation of the PF packet filter system.  Like the rest of our infrastructure, this router was managed using Ansible.

One of the key advantages of controlling the network during a CTF is the ability to create arbitrary custom DNS entries.  For TexSAW this was visible in the form of all of our challenges having a custom ".texsaw" TLD.  The custom TLDs made possible the illusion that there were more servers than there actually were running the challenges.  With multiple custom TLDs mapping back to challenges, competitors are able to have a more polished experience by typing in a domain name instead of an address/port tuple.  Of course, the custom network option is only possible when everone is in the same room.

Wireless gear is a very difficult thing to get absolutely right in a CTF.  For TexSAW, we used a SOHO access point which was able to cope with the traffic demands of our conference, but would not have been able to handle anything else.  For anyone attempting to duplicate our success, it is vital to secure the buy-in of your IT department.  Before standing up our wireless access point it was necessary to secure the approvals of our local department techs and the campus wide wireless team so that everyone was clear on what channels would be in use during what times by what organizations.

Of all the components used in our CTF, the LAN wound up being the only one with an issue over the 2 day run of the TexSAW conference.  In both cases, the router used in the custom LAN did not experience a fault and continued to work as designed.  Our specific issue is unlikely to be present at any other site, but is nonetheless described in detail in the 'Failures and Reflections' section of this manual.


## Ansible

Ansible was crutial to allowing a small number of people to manage and operate our CTF.  While the problems were written by a team of ~6 people, a team of only 2 managed all infrastructure for the CTF and conference.  More information about Ansible is available on the Ansible website at [https://ansible.com/](https://ansible.com).
