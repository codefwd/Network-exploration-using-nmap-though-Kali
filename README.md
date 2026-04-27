
# Network exploration using nmap though Kali
Network exploration by searching networks and investigate any hosts we find
## Overview

Nmap offers many methods for network exploration. Zenmap is the GUI version of nmap. In this demonstration I’ll be using nmap in Kali on a virtual machine.
Nmap's main purpose is to search networks and investigate any hosts it finds. Either TCP or UDP protocols can be used for scanning. 
It can use a supply of usernames and passwords to get access to services, or it can employ brute force by guessing its way in.

## Let's start
The help section shown below makes it clear that there are many things you can perform with nmap. 
It can find hosts in a variety of ways. It has several methods for scanning. It features scripts that we may utilize and offers multiple methods for inspecting ports and services.


<img width="674" height="706" alt="nmap help" src="https://github.com/user-attachments/assets/12ee6624-189c-4ffe-8cab-8e48f3d7ae3d" />


Let us find out which hosts are on my network using nmap. The command is as follows:

$sudo nmap -sn  10.0.2.0/24

-sn is used for host discovery only. I'm skipping port scan and the host range i'm searching is a /24 subnet

Nmap provides the host's MAC address in addition to the IP address of the host that responded. Here are four outcomes.


<img width="557" height="317" alt="nmap pic" src="https://github.com/user-attachments/assets/f7f87776-2c58-44bb-af1d-25a94733a7e4" />


Let's now look at one of the hosts 10.0.2.5 on my network. It’s my metasploitable VM. 
We are using the -PS to see what TCP service are running:

$sudo nmap -PS 10.0.2.5

Nmap checks the most common ports to see if they're open on the host.  It does this by starting a connection to the service and then closing it down before the connection is completed. It’s called a TCP syn ping.
You can see by the results that metasploitable has quite a number of ports open:


<img width="569" height="553" alt="tcp service running" src="https://github.com/user-attachments/assets/1e9ca32b-0192-4e13-a627-439f9d741ad2" />

Let's now use nmap with an individual service. The SSH service.

$ sudo nmap -PS -sV -p 22 10.0.2.5

By using the –sV option, nmap will identify a version of software being used for the service. I’ll limit the testing by using one service by using the –P option
<img width="628" height="257" alt="service" src="https://github.com/user-attachments/assets/1aac6861-3775-4e4e-8189-8efd28a34e00" />

as you now see port 22 is running the ssh service with the software OpenSSH 4.7p1

If we go to the NIST vulnerability database and open a search on SSH there's over 100 vulnerabilities for SSH. Now we can review these vulnerabilities and make sure that we have the correct patches applied to open SSH
<img width="1560" height="232" alt="nist" src="https://github.com/user-attachments/assets/75d21158-746a-460c-8a88-47d366c71460" />

We can also use nmap to check for UDP services by using the -sU option. The -F is used to limit the amount of ports checked 


sudo nmap -sU -F 10.0.2.5
<img width="540" height="258" alt="UDP serach" src="https://github.com/user-attachments/assets/5222e161-c3e5-454c-9e4c-d420cac95d40" />
nmap shows four UPD ports that are open and the three open|filtered ports are undetermined.

# In closing

Nmap is a powerful and versatile tool for network exploration and security assessment. With its ability to scan networks, identify active hosts, and analyze services using either TCP or UDP protocols, it provides valuable insight into network environments. The availability of Zenmap as the graphical interface makes these features more accessible for users who prefer a GUI. As demonstrated using Kali Linux on a virtual machine, Nmap can also test authentication methods through supplied credentials or brute-force techniques.
