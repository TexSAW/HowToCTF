# vSphere

TexSAW was run within two vSphere virtual machines within our Computer Security Group's server. While vCenter is not the most user friendly software to use there were definite advantages and disadvantages to running it "in the cloud."

## Advantages
* Boxes could be provisioned at will (RAM, Disk space, etc.)
* Boxes could be managed "hands on" without having to be physically with them
* Boxes could back snapshoted to be recovered in case of emergency
* Boxes could easily attached to VLANs to physically change their availability within the network
* Boxes were hosted internally, meaning that even with issues with connectivity to the Internet, we still had a LAN connection

## Disadvantages
* vSphere makes the automated deployment of a new box somewhat obtuse
* vSphere requires a special client (or terrible web interface) to interact with
* Virtualization is not feasible within a vSphere box

Overall, I would consider it a good decision to host the CTF inside vSphere. It allowed us fine grained control over the number and state of boxes provisioned, as well as allowing easy collaboration with CS Technical Support, the primary on campus staff we worked with to run TexSAW. The main problem with vSphere is its lack of ability to utilize Docker or Virtualbox, meaning separate vSphere VMs would be needed for challenges. This will hopefully be remedied in the future with LXD.
