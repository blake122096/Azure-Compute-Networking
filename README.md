<p align="center">
<img src="https://i.imgur.com/VvEfgCC.jpeg" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />

<h1>Azure Virtual Machines and Networking</h1>



<h2>Description</h2>
This project involves setting up a virtual network in Microsoft Azure with two virtual machines. I'll then use Wireshark to analyze the network traffic within this environment.

<br />


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b> 
- <b>Wireshark</b>
- <b>Various Network Protocols (ICMP, SSH, DHCP, DNS)</b>
- <b>Command-Line Tools</b>

<h2>Operating Systems Used </h2>

- <b>Windows 10</b>
- <b>Ubuntu 24.04</b>

<h2>Project Guide</h2>

<p>
  In Microsoft Azure, create a new resource group.
</p>
  
  <br/>
<img src="https://github.com/user-attachments/assets/409c1a87-7780-403b-a167-b324b46b2a31" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br/>
<p>
  Next, create the first virtual machine within the resource group.
</p>
<br/>
<img src="https://github.com/user-attachments/assets/981014fe-b39f-4389-8289-8452381387d7" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />


<p>Configuring the First Virtual Machine</p>  <br/>
<img src="https://github.com/user-attachments/assets/1d52369c-4c8c-43cc-96a9-ce5980440d69" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/81528466-5c73-4a10-bef7-38c72c6db83b" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Keep all other settings at their default values, and  proceed to create the VM.</p>  
<br/>
<img src="https://github.com/user-attachments/assets/28c1722a-4340-44ec-8078-3b2fb7d900b3" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Azure has created a virtual machine and all its necessary components, including a network interface, disk storage, and security settings.</p>  <br/>
<img src="https://github.com/user-attachments/assets/116ce8c7-1611-45fc-9766-14d037ef4ee1" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Setting up the Second Virtual Machine</p>
  <br/>
<img src="https://github.com/user-attachments/assets/bacbe41d-77e8-43b5-8674-57cba8671f97" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/03e9ef59-8dbb-4926-b0df-56e48563c4df" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p>
  In the "Networking" tab, select the existing virtual network created for "VM1" to ensure both VMs reside on the same network.
</p>
  <br/>
<img src="https://github.com/user-attachments/assets/de1402ea-2066-4f39-a8c2-66d288eb57a4" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Returning to the resource group, you'll see that Azure has provisioned resources for VM2, similar to VM1.  Note that there's only one virtual network, as both VMs share the same network. </p>
  <br/>
<img src="https://github.com/user-attachments/assets/f020ebb3-9a75-462b-a311-b2eeab57828c" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Connect to VM1 via RDP using its public IP address. </p>
  <br/>
<img src="https://github.com/user-attachments/assets/64b35628-4f76-4764-8589-64a9265dc430" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
 <p> After connecting to VM1, download and install Wireshark. </p>  <br/>
<img src="https://github.com/user-attachments/assets/4202ca6d-7f9a-42aa-8d15-058378f375b1" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Once Wireshark is installed, open the application. You'll see a list of network interfaces. Choose "Ethernet" from this list to start capturing packets. </p>
  <br/>
<img src="https://github.com/user-attachments/assets/b915a450-5477-430d-8e86-b77b68e0d56a" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Filter for ICMP traffic by typing "ICMP" in Wireshark's filter bar.  Then, ping VM2's private IP address from PowerShell to generate ICMP traffic.</p>
  <br/>
<img src="https://github.com/user-attachments/assets/6c8f682f-2615-43d2-ae4d-f7d95bfe0980" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<img src="https://github.com/user-attachments/assets/f19cea4e-41d7-4ec0-bb26-73f95996970c" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p>  We can make some firewall configurations to deny any ICMP traffic. In order to do this,  enter a perpetual ping command into PowerShell </p> 
 <br/>
<img src="https://github.com/user-attachments/assets/39d08859-ba32-48e8-bd2f-541f2908fd3f" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> In VM2's network security group, create a high-priority inbound rule to deny all ICMP traffic. </p>


  <br/>
<img src="https://github.com/user-attachments/assets/fe8e4d4d-0d47-4399-9e74-12bc33a4b924" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> The firewall rule is now active. Observe in VM1 that the ping requests to VM2 are no longer receiving responses.

 </p>
 <br/>
<img src="https://github.com/user-attachments/assets/6ed46ea7-6980-428e-ab8e-9bd8deb03d70" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p>To allow ICMP traffic again, either change the inbound rule to "Allow" or delete it.</p>
<br/>
<img src="https://github.com/user-attachments/assets/2d0b12b1-9b6d-4a2f-95c6-01fa2343c4da" height="80%" width="80%" />
<br />
<br />
<p> With the firewall rule reverted, ICMP traffic is allowed, and the ping requests are once again receiving replies.</p>
  <br/>
<img src="https://github.com/user-attachments/assets/73c0751c-aa32-4874-8391-947d454058b6" height="80%" width="80%" />
<br />
<br />
<p> Filter for SSH traffic in Wireshark by typing "SSH" in the filter bar. Then, initiate an SSH connection to VM2 using PowerShell. </p>
 <br/>
<img src="https://github.com/user-attachments/assets/493396c9-1de7-42fa-99b3-ca10ac88d4c5" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Execute commands within the SSH session, such as 
pwd (print working directory), and observe the resulting SSH traffic in Wireshark.</p>
  <br/>
<img src="https://github.com/user-attachments/assets/e0ecec13-ab34-42fb-858c-59111436024e" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> After filtering for DHCP traffic in Wireshark, I attempted to renew the IP address by executing the command 
ipconfig /renew in the command prompt.</p>
 <br/>
<img src="https://github.com/user-attachments/assets/87b8ae59-bdca-426f-ab92-3039be7a2821" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p> Filter for DNS traffic in Wireshark and then use 
nslookup to resolve domain names like "www.google.com" and "www.amazon.com," observing the DNS queries and responses. </p>
  <br/>
<img src="https://github.com/user-attachments/assets/c6588a3c-0cb6-48a2-9a53-68f18335225c" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
<p>To observe RDP traffic, filter Wireshark by entering "tcp.port == 3389" in the filter bar. Notice the ongoing traffic; this is due to the active RDP session between your computer and the VM, which maintains a constant stream of updates.</p>
 <br/>
<img src="https://github.com/user-attachments/assets/58f0e4be-e3ba-430b-9043-ba12a5069076" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
