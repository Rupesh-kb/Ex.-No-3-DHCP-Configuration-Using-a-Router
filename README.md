## Ex. No: 3  DHCP Configuration Using a Router

________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>

________________________________________
# Output (Screenshots)
<img width="900" height="750" alt="Screenshot 2026-10-24 102332" src="https://github.com/user-attachments/assets/d054885e-1135-4f36-ba78-00afde9d5962" />
<img width="877" height="873" alt="image" src="https://github.com/user-attachments/assets/3f6126a3-e4a1-45aa-9cc5-0c5adb3a4d6f" />
<img width="877" height="873" alt="image" src="https://github.com/user-attachments/assets/2dd0a266-3463-4535-ad09-0fc211280041" />
<img width="500" height="300" alt="Screenshot 2026-10-27 155210" src="https://github.com/user-attachments/assets/1afbb780-c19e-453f-83d5-26ce21231b92" /> <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/aa83e53d-e305-468c-9252-53550297bb0c" />

# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>

<img width="1205" height="512" alt="image" src="https://github.com/user-attachments/assets/4955be59-f5ff-4b55-ade5-26425fbcc81d" /> 

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/4bac77a7-b64f-474e-98c1-b45f520b09df" />   <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/8736351c-13fc-4e51-8330-6c24e785f48f" />

# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
