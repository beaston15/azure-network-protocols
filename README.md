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

<h2>High-Level Steps</h2>

- Create the Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>
<p>
Step 1: Create 2 virtual machines using Microsoft Azure (1 VM using Windows 10, 1 VM using Linux)
</p>

<p>
<img src="https://i.imgur.com/Mu8gQdB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 1b: Open Microsoft Azure and click on "Virtual Machines" 
</p>

<br />

<p>
<img src="https://i.imgur.com/S6MCvyO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 1c: Click on "Create" and choose "Azure Virtual Machine". While creating the VM there will be an option to create a Resource Group, use that option to make a Resource Group. Create 1 VM for Windows 10 and another VM for Ubuntu (Linux), make sure both VM are in the resource group and in the same Virtual Network.
</p>

<br />

<p>
<img src="https://i.imgur.com/JJNRS52.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 1d: Go to the Virtual Machines homepage and copy the Windows VM IP address. 
</p>

<br />

<p>
<img src="https://i.imgur.com/BrwyIJH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 1e: In the start menu search for "Remote Desktop Connection" and open that application. Once it opens, paste the IP address, then press connect and use the username and password to log into the VM.
</p>

<br />

<p>
<img src="https://i.imgur.com/rypI0La.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 1f: Open an internet browser, search for "wireshark", and then download the windows version of wireshark.
</p>

<br />

<p>
<img src="https://i.imgur.com/xaIQCZH.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
<img src="https://i.imgur.com/6IskQIU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 2a: Open wireshark
</p>

<br />

<p>
<img src="https://i.imgur.com/M6TXF3C.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 2b: Type "icmp" into the display filter and press enter. (notice: all the traffic will now only be in the ICMP protocol)
</p>

<br />

<p>
<img src="https://i.imgur.com/3JEHcBu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 2c: In Microsoft Azure go to your Linux VM. Copy the Private IP Address. 
</p>

<br />

<p>
<img src="https://i.imgur.com/1O17I2E.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 2d: In the start menu, search and open "Command Prompt". In Command Prompt type "ping (private IP address)" and also type "ping -t <private IP address>". (The first ping should ping back and forth a couple of times and stop. The second ping should be a continuous ping called a perpetual ping."
</p>

<br />

<p>
<img src="https://i.imgur.com/C7T8lNq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 3: Filter for "ssh" traffic. Open "Powershell" from the start menu, once Powershell opens login using "ssh labuser@(private IP address) and use the password you created when making the VM (the password will not show up in Powershell when typing). You can use commands such as id, ls, pwd to observe the traffic in Wireshark.
</p>

<br />

<p>
<img src="https://i.imgur.com/nqnqeYJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 4: Filter for DHCP traffic. In Command Prompt type "ipconfig /renew" and observe the DHCP traffic in Wireshark.
</p>

<br />

<p>
<img src="https://i.imgur.com/sjS4ZNk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 5: Filter for DNS traffic. In Command Prompt type "nslookup www.google.com" and "nslookup www.disney.com". In wireshark you can see your VM and the websites sending information back and forth.
</p>

<br />

<p>
<img src="https://i.imgur.com/HuCgDl9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Step 6: Filter for RDP traffic by typing "tcp.port == 3389". The traffic will be non stop because RDP traffic is a live stream from one computer to another.
</p>
