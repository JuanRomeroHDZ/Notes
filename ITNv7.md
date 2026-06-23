**CCNAv7  
Introduction to Networks**

**ITN Practice Skills Assessment - Packet Tracer**

A few things to keep in mind while completing this activity:

1. Do not use the browser Back button or close or reload any exam windows during the exam.

2. Do not close Packet Tracer when you are done. It will close automatically.

3. Click the Submit Assessment button in the browser window to submit your work.

**Introduction**

In this assessment, you will configure devices in an IPv4/IPv6 network. For the sake of time, you will not be asked to perform all configurations on all network devices as you may be required to do in a real network or other assessment. Instead, you will use the skills and knowledge that you have learned in the labs and packet tracers in this course to configure the Building 1 router. In addition, you will address the hosts on two LANs with IPv4 and IPv6 addresses and activate and address the management interface of the Second Floor Switch.

You will receive one of several topologies.

You are not required to configure the First Floor Switch, and you will not be able to access it in this practice skills assessment activity.

All IOS device configurations should be completed from a direct terminal connection to the device console. In addition, many values that are required to complete the configurations have not been given to you. In those cases, create the values that you need to complete the requirements. For values that have been supplied to you, they must be entered exactly as they appear in order for you to get full credit for your configuration.

If the network is configured correctly, all hosts should be able to connect to each other.

You will practice and be assessed on the following skills:

=   Configuration of initial IOS device settings

=   Design and calculation of IPv4 addressing

=   Configuration of IOS device interfaces including IPv4 and IPv6 addressing when appropriate

=   Addressing of network hosts with IPv4 and IPv6 addresses

=   Enhancing device security, including configuration of the secure transport protocol for remote device management

=   Configuration of a switch virtual management interface

Requirements by networking device:

**Building 1 router:**

=   Configuration of initial router settings

=   Interface configuration and IPv4 and IPv6 addressing

=   Device security enhancement, or device hardening

=   Secure transport for remote configuration connections as covered in the labs and Packet Tracers in the course.

**Second Floor Switch:**

=   Enabling basic remote management by Telnet

=   PC and Server hosts:

o   IPv4 full addressing

o   IPv6 addressing

**Addressing Table**

| **Device**          | **Interface** | **IP Address/Mask**    | **Default Gateway** |
| ------------------- | ------------- | ---------------------- | ------------------- |
| Building 1          | G0/0          |                        | N/A                 |
| _Router0_           | _G0/0_        | 2001:db8:acad:a::1/64  | N/A                 |
| _Router0_           | _G0/0_        | fe80::1                | N/A                 |
| _Router0_           | G0/1          |                        | N/A                 |
| _Router0_           | _G0/1_        | 2001:db8:acad:b::1/64  | N/A                 |
| _Router0_           | _G0/1_        | fe80::1                | N/A                 |
| Second Floor Switch | SVI           |                        |                     |
| Host 1              | NIC           |                        |                     |
| _PC1_               | _NIC_         | 2001:db8:acad:a::ff/64 |                     |
| Host 2              | NIC           |                        |                     |
| _PC2_               | _NIC_         | 2001:db8:acad:a::15/64 |                     |
| Host 3              | NIC           |                        |                     |
| _PC3_               | _NIC_         | 2001:db8:acad:b::ff/64 |                     |
| Server              | NIC           |                        |                     |
| _TFTP Server_       | _NIC_         | 2001:db8:acad:b::15/64 |                     |

**Instructions**

**Step 1: Determine the IP Addressing Scheme.**

Design an IPv4 addressing scheme and complete the Addressing Table based on the following requirements.

a.      Subnet the 192.168.1.0/24 network to provide 30 host addresses per subnet while wasting the fewest addresses.

b.      Assign the fourth subnet to the First Floor LAN.

c.      Assign the last network host address (the highest) in this subnet to the G0/0 interface on Building 1.

d.      Starting with the fifth subnet, subnet the network again so that the new subnets will provide 14 host addresses per subnet while wasting the fewest addresses.

e.      Assign the second of these new 14-host subnets to the Second Floor LAN.

f.       Assign the last network host address (the highest) in the Second Floor LAN subnet to the G0/1 interface of the Building 1 router.

g.      Assign the second to the last address (the second highest) in this subnet to the VLAN 1 interface of the Second Floor Switch.

h.      Configure addresses on the hosts using any of the remaining addresses in their respective subnets.

**Step 2: Configure Host Addressing**

Use the IPv4 addressing from Step 1 and the IPv6 addressing values provided in the Addressing Table to configure all host PCs with the correct addressing.

a.      Use the router interface link-local address as the IPv6 default gateways on the hosts.

b.      Complete the configuration of the server using the IPv4 addressing values from Step 1 and the values in the addressing table

**Step 3: Configure the Building 1 Router.**

a.      Configure the Building 1 router with all initial configurations that you have learned in the course so far:

o        Configure the router hostname: **Building-1**

o        Protect device configurations from unauthorized access with the encrypted privileged exec password.

o        Secure all access lines into the router using methods covered in the course and labs.

o        Require newly-entered passwords to have a minimum length of 10 characters.

o        Prevent all passwords from being viewed in clear text in device configuration files.

o        Configure a banner warning message for unauthorized users.

o        Configure the router to only accept in-band management connections over the protocol that is more secure than Telnet, as was done in the labs and PT activities. Use the value **1024** for encryption key strength.

o        Configure local user authentication for in-band management connections. Create a user with the name **netadmin** and a secret password of **Cisco_CCNA7**.

b.      Configure the two Gigabit Ethernet interfaces using the IPv4 addressing values that you calculated and the IPv6 values provided in the addressing table.

o        Reconfigure the link local addresses to the value shown in the table.

o        Document the interfaces in the configuration file.

**Step 4: Configure the Second Floor Switch.**

Configure Second Floor Switch for remote management over Telnet.

a.      Configure VLAN 1 as the SVI.

b.      Configure IPv4 addressing according to your work in Step 1.

c.      Be sure that the switch is able to accept connections from hosts on other networks.

Last Updated: September, 2025

ID:11

**Answers:**

https://itexamanswers.net/ccna-1-v7-0-itn-practice-pt-skills-assessment-ptsa-answers.html