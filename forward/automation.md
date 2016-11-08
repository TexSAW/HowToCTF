# Automation

There was at one time a reasonable expectation that an admin would stand up boxes manually and then spend hours configuring specialized software and services by hand.  This expectation is decidedly not reasonable anymore.  The modern way of building servers is to build up automation scripts and then deploy them rapidly onto boxes that are built out using deployment scripts to create repeatable infrastructure.


## Ansible

Since the Linux Users Group and the Computer Security Group are the two groups behind TexSAW's infrastructure at UTD, it made sense to use technology that the two groups were already using.  A large portion of infrastructure within the UTD is managed using RedHat's Ansible configuration management system.  This agent-less automation system is able to connect to a freshly installed box via SSH and apply information contained in _playbooks_ to achieve a desired state.

We leveraged Ansible to a high degree to create repeatable deployments of two key components of TexSAW's infrastructure.  First, Ansible was used to provision the primary webserver with nginx and CTFd.  By using Ansible, we were assured that the configuration on the webserver was actually what we expected it to be.  When we later added an additional package for systems monitoring (monit) we were able to simply include an existing role with a playbook and push the changes to the server.  The changes were seamlessly integrated without any further intervention from a systems administrator.

Our second large deployment of Ansible was part of the VM.  As TexSAW is geared more torwards undergraduate students getting a foothold in security competitions, we choose to provide contestants with a virtual machine that includes all the tools that are needed to solve the CTF challenges.  The VM itself is built by Packer from HashiCorp, but the installation of the software and customization of theme elements is handled by a combination of generic roles and site specific roles for Ansible.

As with the rest of the TexSAW configuration data, all of our Ansible playbooks are freely available from our GitHub page.  For more information about Ansible, consult the Ansible website: [https://ansible.com/](https://ansible.com)


## Packer

Packer was an integral part of our CTF.  For our VM we chose to use Packer to automate the process of building the complete Vagrant box which was later distributed to competitors.  The Vagrant box is ultimately just an Oracle VirtualBox VM packed in a specific format with a few additional control files, but this process is complex and error proned.

By using Packer is was possible to build a new version of the VM with a single command: `packer build template.json`.  This high degree of automation allowed us to work on other tasks while the VM was built fully hands free, on average saving roughly 30 minutes of time for a developer to work on other tasks.  The only issue we encountered with Packer pertained to machine output format.

Boxes built by Packer are hypervisor specific and so building a box for multiple hypervisors requires multiple parallel runs.  Since we chose to build our VM to support Vagrant, we chose to use Oracle VirtualBox to provide the backend hypervisor as it is freely available for macOS, all major versions of Windows, and all major distributions of Linux.

For more information on Packer, consult the HashiCorp website: [https://packer.io/](https://packer.io/).
