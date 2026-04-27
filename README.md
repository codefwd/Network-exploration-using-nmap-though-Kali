# Network exploration using nmap though Kali
Network exploration by searching networks and investigate any hosts we find
## Overview

Nmap offers many methods for network exploration. Zenmap is the GUI version of nmap. In this demonstration I’ll be using nmap. Nmap's main purpose is to search networks and investigate any hosts it finds. Either TCP or UDP protocols can be used for scanning. 
It can use a supply of usernames and passwords to get access to services, or it can employ brute force by guessing its way in.

## To start
The help section shown below makes it clear that there are many things you can perform with nmap. 
It can find hosts in a variety of ways. It has several methods for scanning. It features scripts that we may utilize and offers multiple methods for inspecting ports and services.


<img width="674" height="706" alt="nmap help" src="https://github.com/user-attachments/assets/12ee6624-189c-4ffe-8cab-8e48f3d7ae3d" />


Let us find out which hosts are on my network using nmap. The command is as follows:

$sudo nmap -sn  10.0.2.0/24 

-sn is used for host discovery only. I'm skipping port scan and the range is a /24 subnet

Nmap provides the host's MAC address in addition to the IP address of the host that responded. Here are four outcomes.


<img width="557" height="317" alt="nmap pic" src="https://github.com/user-attachments/assets/f7f87776-2c58-44bb-af1d-25a94733a7e4" />


Let's now look at one of the hosts 10.0.2.5 on my network. It’s my metasploitable VM. 
We are using the -PS to see what TCP service are running:

$sudo nmap -PS 10.0.2.5

Nmap checks the most common ports to see if they're open on the host.  It does this by starting a connection to the service and then closing it down before the connection is completed. It’s called TCP syn ping.
You can see by the results that metasploitable has quite a number of ports open:


<img width="569" height="553" alt="tcp service running" src="https://github.com/user-attachments/assets/1e9ca32b-0192-4e13-a627-439f9d741ad2" />
