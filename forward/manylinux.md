# Of many distros

When setting up a CTF, there are many operating systems available for running the competition servers on.  While there is an established track of running CTFs on established distros such as CentOS, Debian, and Ubuntu, we chose to eschew these older distros in favor of a newer system called Void Linux.


## Why Void?

Void has several design features that make it uniquely suited to CTFs.  First, Void is incredibly compact.  This makes it possible to spin up a large number of small VMs that can all live in a single vSphere cluster or similar virtualization solution.  These small VMs can aid in separating security domains for better isolation with server-side exploitable challenges and similar concerns.  Additionally, in environments where a powerful virtualization server is not available Void can run satisfactorily on very low powered servers or even commodity desktops.

UTD has high involvement with the upstream project for Void Linux ranging from several students that actively contribute to the distro to an on-campus mirror.  The mirror aided greatly in the development of the software that bootstrapped and ran the competition as it greatly shortened the time needed to build a new server and thus allowed more iterations in a shorter time when working out bugs.


## Runit

In early 2014 there was a great buzz in the Linux community around the concept of systemd's process supervision.  While this was heralded as a new feature, long standing members of the community may recall an earlier init called runit with process supervision.  Runit is the default init for Void Linux and is incredibly well suited to CTFs.  Service scripts for runit are simple shell scripts that can be written in any language that supports the `#!` interpreter notation on the first line.  An example runit service for CTFd is quite short:

```
#!/bin/sh

chpst -u ctfd:ctfd exec uwsgi --ini /opt/ctfd/ctfd.ini -s /srv/ctfd/ctfd.socket

```

This file is written in POSIX `sh` and performs a few simple functions.  The `chpst -u ctfd:ctfd` command sets the UID/GID for the process to that of the CTFd user.  In our environment this is an unprivileged user that has limited access to things outside of the CTF itself.  The next token of interest is the `exec` call.  This causes the running process to be replaced by the executable called by `exec`.  In our deployment we chose to use the `uwsgi` system to run the Python based executable components including CTFd.  Our deployment placed the code at `/opt/ctfd` and the control socket for the uwsgi process at `/srv/ctfd/`.  Since the control socket must be readable and writable by the `nginx` user, it should be kept separate from the installed code-base.  The paths in the above example are template variables with Ansible and had we chosen to, we could have changed the directories with very little difficulty.

The run scripts for the additional competition services are of similar complexity.  This in itself is a significant feature when setting up a CTF with a large number of individual services that are not standard processes.
