# Forensics

Forensics tends to be one of the most broad topics and difficult to prepare for in a small CTF. Many times, potentially obscure tools are required to complete challenges, which is simply not practical for many CTFs. We chose to somewhat get around this by providing a VM to our contests that contained all the tools needed, what we believe is an optimal solution for an entry-level CTF.

# Packet Captures
Packet Captures make for good forensics problems. PCAPs tend to be easy enough to navigate with tools like Wireshark, and the difficulty range can vary based on the obscurity of the protocol used. Good entry level problems can be as easy as finding a password sent over HTTP, while more advanced problems can involve retrieving files from the captured packets and continuing forensics on the discovered files. The only important note to make is to ensure no actually confidential data is captured in the problem PCAP file.

# Steganography
Hiding data in images and files is possibly one of the most cliche forensics problems. However, these problems have value when done properly. Generic steganography (OutGuess) is great for low value problems when given good direction. It becomes tedious when forced to try every possible steganography tool available. Other interesting avenues of steganography include hiding text in the wave form of sound files, in a single frame of video files, or other "hacker movie"-esque manners. Data hiding is certainly one of the most flashy problem types, but must be done with care lest all the contestants are sent down a fruitless rabbit hole.

# Disk Dumps
Disk dumps are likely the most practical of forensics problems. For *nix users, it is fairly trivial to put a "secret" file on a flash drive, delete it, and then `dd` the drive to a file to be distributed. Contestant can then use tools like Autopsy or DFF to recover these files and thus the flag. These are generally best coupled with other problems to extend the challenge past using a single tool

# Meta data
Some of the best forensics challenges involving looking at the data about the data you've been given. The holding company of SSL Certificates, a random TXT record, the geotag in a picture, the possibilities are endless. These problems can also tend to the more obscure, as the data included with each medium is generally well defined and can be found with a bit of research.
