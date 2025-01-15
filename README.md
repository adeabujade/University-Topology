<p align="center">
</p>

<h1>Cisco Packet Tracer |  University Topology<h1>
  
This report outlines the design and implementation of a network topology to support a main campus and a smaller campus. The network will serve various departments, faculties, and labs, ensuring efficient communication, security, and scalability. Both campuses will be interconnected, with an external cloud-hosted email server integrated into the network.

<h2>Environments and Technologies Used</h2>

- Cisco Packet Tracer

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Objectives</h2>

-Provide seamless and secure communication across departments and faculties.
-Ensure logical separation using VLANs and IP subnetting.
-Support dynamic IP address allocation for devices in Building A.
-Implement RIPV2 for internal routing and static routes for external communication with the cloud-hosted email server.
-Optimize network performance, scalability, and security.


<h2>Network Design Implementation</h2>

<p>

</p>
<p>
<h2>1. Network Topology</h2>

![image](https://github.com/user-attachments/assets/19edbb68-332c-4787-9952-e0efb0b3f4e1)


Building A: Administrative Staff and Faculty of Business
  
Departments: Management, HR, Finance, and the Faculty of Business.

Network VLANs:

Devices will be assigned to separate VLANs for each department and the Faculty of Business. Separate IP networks will be assigned to each faculty. Switches will be configured with VLANs for traffic segmentation.

VLANs:

VLAN 10: Admin

VLAN 20: HR

VLAN 30: Finance

VLAN 40: Business

Building B: Faculty of Engineering and Computing, Faculty of Art and Design

Network VLANs:

VLAN 50: Faculty of Engineering and Computing

VLAN 60: Faculty of Art and Design

Building C: Student Labs and IT Department

Network VLANs:

VLAN 70: Student Labs

VLAN 80: IT Department

![image](https://github.com/user-attachments/assets/0636ba53-bf6a-4cf3-b0d4-4a1264295489)


Smaller Campus: Faculty of Health and Sciences

Network VLAN:

VLAN 90: Staff Lab

VLAN 100: Student Lab

![image](https://github.com/user-attachments/assets/27ae2b76-3018-4d34-93b1-7e913b802b96)

A router-based DHCP server will provide dynamic IP addresses for all devices in Building A. Switches will be configured to support VLAN tagging and inter-VLAN communication. 

The IT department will host critical servers, including the university web server and other internal servers. Port security will be configured on the switches to prevent unauthorized access to the servers.

VLANs will be created for each department within the Faculty of Health and Sciences. Separate IP networks will be assigned to each department. The smaller campus router will use RIPV2 for routing internal traffic and static routing for communication with the main campus and the external email server.



</p>
<br />

<p>

</p>
<p>
<h2>2. Routing Protocol</h2>
  
Routing and IP Configuration
RIPV2 for Internal Routing
RIPV2 will be implemented on the routers within the main and smaller campuses to handle dynamic routing of internal traffic.
This ensures efficient route updates and supports scalability for future expansion.
Static Routing for External Communication
A static route will be set up on both campus routers to facilitate communication with the cloud-hosted email server.

Each VLAN will have a unique subnet to ensure efficient IP allocation and avoid conflicts. 

VLAN 10: 192.168.1.0/24 (Management)

VLAN 20: 192.168.2.0/24 (HR)

VLAN 30: 192.168.3.0/24 (Finance)

VLAN 40: 192.168.4.0/24 (Faculty of Business)

VLAN 50: 192.168.5.0/24 (Faculty of Engineering and Computing)

VLAN 60: 192.168.6.0/24 (Faculty of Art and Design)

VLAN 70: 192.168.7.0/24 (Student Labs)

VLAN 80: 192.168.8.0/24 (IT Department)

VLAN 90: 192.168.9.0/24 (Staff Lab)

VLAN 100: 192.168.10.0/24 (Student Lab)

Configurations:

On both routers RIP was configureed for their respective VLANS.

Router> enable

Router# configure terminal

Router(config)# router rip

Router(config-router)# version 2

Router(config-router)# no auto-summary

Router(config-router)# network ip address of respective VLAN

Router(config-router)# exit

<h2>IP Route Tables</h2>

Cloud Router

![image](https://github.com/user-attachments/assets/c7dedc7e-e98f-405f-b0d2-bc1986ad4656)

Router0

![image](https://github.com/user-attachments/assets/758c998b-17dc-4075-a99f-721fcdfe82fd)

Router1

![image](https://github.com/user-attachments/assets/a2a44421-3657-4f0d-88d1-f7bfb29524e3)

-Inter-VLAN communication will be verified using ping tests between devices in different VLANs.

In this ping, PC3 from the business VLAN 40 from the main campus is pinging PC8 from the Staff VLAN 90 from the branch campus.

![image](https://github.com/user-attachments/assets/32ca9c7d-669d-450b-9ec5-f2ff9c6f0972)


</p>
<br />
</p>
<br />

<p>

</p>
<p>
<h2>3. Switch and VLAN Security Settings</h2>
  
Switch and VLAN Security Settings
VLAN tagging and trunking will be configured to ensure inter-VLAN communication via the routers.
Port security will be implemented to:
Limit the number of MAC addresses per port.
Prevent unauthorized devices from accessing the network.

Configurations: ON Multilayer switch

Switch(config)# interface respective interface

Switch(config-if)# switchport mode access

Switch(config-if)# switchport access respective VLAN

Switch(config-if)# switchport port-security

Switch(config-if)# switchport port-security maximum 1

Switch(config-if)# switchport port-security violation shutdown

Switch(config-if)# switchport port-security mac-address sticky

Switch(config-if)# exit
  

</p>
<p>
<h2>Conclusion</h2>
This network topology provides a robust and secure framework for the university’s main and smaller campuses. By leveraging VLANs, RIPV2, and static routing, the design ensures efficient communication and scalability. Security measures, such as port security and ACLs, further protect critical resources from unauthorized access.
</p>
<br />
