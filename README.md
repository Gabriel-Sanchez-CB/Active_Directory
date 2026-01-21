# Active Directory Home Lab

## Project Overview

In this project, I implemented an Active Directory home lab in a virtualized environment, designed to simulate a basic enterprise Windows infrastructure. My main objective was to build a fully functional domain from scratch to understand the architecture, core services, and administrative processes commonly found in real corporate environments.

To accomplish this, I used VMware as the virtualization platform, where I deployed a Windows Server configured as a Domain Controller along with a client machine joined to the domain. I configured essential network services, including DNS, DHCP, Active Directory Domain Services (AD DS), and Remote Access (RAS/NAT), ensuring proper internal communication and controlled external connectivity. (Oracle VirtualBox can also be used as an alternative virtualization platform without issues.)

## Network Diagram
In this lab, I designed a network topology where the Domain Controller (DC) uses two network interfaces to separate internal domain communication from external connectivity. The first interface is connected to a NAT network provided by VMware, allowing the server and lab environment to access the Internet for updates and external services without directly exposing the internal network. The second interface is connected to an isolated internal network, dedicated exclusively to communication between the Domain Controller and the client machines within the domain.

![Architecture Diagram](image/Screenshots/diagram.png)

The Domain Controller provides essential services within the internal network, including DNS, DHCP, Active Directory Domain Services (AD DS), and Remote Access/NAT, ensuring that client machines receive IP addressing, resolve domain names, and successfully join the domain. This architecture replicates a real-world enterprise network design, offering a controlled, secure, and functional environment for practicing Active Directory administration.

## User Creation Automation with Power Shell Script
Once the domain was fully configured and network connectivity was verified, I implemented automated user creation in Active Directory. To achieve this, I used PowerShell along with a script that imports a list of names from a text file and generates multiple user accounts automatically within the domain.

![Demo del script](video/PowerShell%20Script/PowerShellScriptMP4.gif) 

This process replicates a common task in enterprise environments, where administrators must provision large numbers of user accounts efficiently and consistently. Automation not only reduces setup time but also minimizes human error and ensures a standardized account structure across Active Directory.



## DHCP Server Configuration

To ensure that client machines received IP addressing automatically within the internal network, I configured the DHCP server on the Domain Controller. I defined a scope with an address range from 172.16.0.100 to 172.16.0.200, using a subnet mask of 255.255.255.0.

I also set the default gateway to 172.16.0.1, corresponding to the server’s internal network interface, and configured the DNS server with the same address to allow proper domain name resolution. This setup ensured stable network assignment and seamless integration of client machines into the Active Directory environment.


