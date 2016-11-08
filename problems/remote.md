# Problems on Remote Systems

Problems that you connect to using tools like netcat can be very fun and rewarding to solve and can be very difficult to write.  A good example of this category is a problem whose hint is simply an address and port pair.  The implication is that its something that you can connect to with netcat.


## Netcat

Problems that can be solved with netcat include fake telnet servers, systems that are "old", and text I/O based problems where the program that reads input and dispenses the flag is not to be given to the user.  These problems can be easily written with python and specifically the twisted stack.  The biggest concern to be dealt with is that the system must absolutely be backed by a socket server.  Without a functioning socket server, there is not a mechanism for having multiple people connect to solve at once.

It is also possible to take an existing compiled executable and attach the input and output of the program to network streams.  This is most easily done with `xinetd` which will take care of threading concerns as well as ensuring that multiple clients can connect to the served executable at once.


## Other Network Protocols

There are some other network protocols that may be of interest when writing challenges.  These include mechanisms like web-sockets which require debugging tools with browsers,  things hidden in game protocols for chat, chatter-bot systems and so on.

---

Challenges that require persistent running code on a remote server are some of the hardest to deploy as they require additional infrastructure.  These challenges are best assigned to someone who has extensive experience with network programming and will require special attention to setting up security groups to ensure that the challenge itself does not become a security risk.
