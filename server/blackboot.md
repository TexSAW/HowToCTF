# Blackboot

## Spooks and Scares
Malicious actors, while not necessarily in play in small competitions, should be planned for. It is clearly in a contestant's best interest to disrupt other users if they can do so without being caught. The CTF should be planned as such. Even without a malicious actor, hardware fails, software breaks, and everything that can go wrong will go wrong. Preparing for this, and being able to blackboot (spin up the competition from nothing) is a necessary last ditch effort to keep the CTF successful.

## Software Backups
If the CTF is run in any sort of virtualization environment, it is strongly recommended to make a software backup of the machines in use. This will allow the entirety of an exploitable server or the CTFd server to fail, but then be replaced in minutes. As we ran TexSAW CTF in vSphere this (should have been) our easy solution to backing up the servers. In general, software backups have little overhead and large payoffs if needed.

## Automated Deployment
Software backups aren't always an option and are of no use if the hypervisor fails as well. Configuration management is key if this happens. The ability to reproduce the entire deployment from a single line in the terminal should be a goal during preparation. With automated deployment, hardware can fail, software can break, but as long as you can find a box to run the software, the CTF can continue after a quick redeployment.
