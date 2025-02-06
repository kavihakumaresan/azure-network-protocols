# azure-network-protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<p>
Go to Azure Portal. Create a Resource Group, then proceed to create a Windows 10 Virtual Machine and a Linux Virtual Machine. While setting up each VM, ensure that you select the previously created Resource Group. Additionally, create a new Virtual Network (VNet) and Subnet during the VM setup process.
</p>

![image](https://github.com/user-attachments/assets/a299e51b-b0e7-4f9e-bf3f-29e3fcff1e7c)


![image](https://github.com/user-attachments/assets/edd98fd7-dd78-49b3-9048-9a553b9c8ce2)

<p>
  go to  Remote Desktop to connect to our Windows 10 Virtual Machine.Within your Windows 10 Virtual Machine, Install Wireshark-->Open Wireshark and start packet capture.
</p>

![image](https://github.com/user-attachments/assets/00016c6d-f69d-434c-bea4-25a7927888e2)

![image](https://github.com/user-attachments/assets/75d65009-4913-4310-aef7-24a95fa466fa)

<p>
In Wireshark, apply a filter to capture ICMP traffic only. Retrieve the private IP address of the Ubuntu VM (Linux-VM) and initiate a ping to it from the Windows 10 VM. Observe the ping requests and replies within Wireshark to verify network communication.
</p>

![image](https://github.com/user-attachments/assets/8511c962-a638-4703-9e35-cc8e977840ca)

![image](https://github.com/user-attachments/assets/ffb712c3-251f-4eb5-b59a-8115f9202c26)

<p>
Log back into the Windows VM. Open Wireshark, start a packet capture, and apply a filter for SSH traffic only. From the Windows 10 VM, initiate an SSH connection to the Ubuntu Virtual Machine using its private IP address. To do this, open PowerShell and enter the following command: ssh username@private_ip_address.Replace "username" with the actual username of the Ubuntu VM and "private_ip_address" with its private IP.
</p>

![image](https://github.com/user-attachments/assets/967e2b32-d03c-4ad4-8b04-84ec4479b21a)

<p>
  go to Wireshark and observe for DHCP traffic only.From our Windows 10 VM, attempt to issue your VM a new IP address from the command lineOpen PowerShell as admin and run: ipconfig /renew
Observe the DHCP traffic appearing in WireShark.we need to create ipconfig release and ipconfig renew in notebad.and save it as dhcp.bat in C:\programdata.
</p>

![image](https://github.com/user-attachments/assets/1ff21d91-89f2-4ff2-b09a-577035555304)

<p>
  go to Wireshark, filter for DNS traffic only from our Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark.
</p>

![image](https://github.com/user-attachments/assets/5f7a8adb-b721-45e9-85f1-d9985a1332de)

<p>
  go to Wireshark, filter for RDP traffic only (tcp.port == 3389).Observe the immediate non-stop traffic in RDP.Because the RDP (protocol) is constantly showing us a  live stream from one computer to another, therefor traffic is always being transmitted.
</p>

![image](https://github.com/user-attachments/assets/24a8b317-7683-4ef9-a555-071c5ffb93c6)



















