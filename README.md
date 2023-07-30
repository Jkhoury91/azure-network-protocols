# azure-network-protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Create our Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
  

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I will start by creating a Resource Group in Azure.
Next, I will create a Windows 10 Virtual Machine (VM) and during the creation, I will select the previously created Resource Group.
While creating the VM, I will allow it to create a new Virtual Network (Vnet) and Subnet automatically.
Following that, I will create a Linux VM (Ubuntu) and select the previously created Resource Group and Vnet during the VM creation.
To ensure everything is set up correctly, I will observe my Virtual Network within Network Watcher.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I will use Remote Desktop to connect to the Windows 10 Virtual Machine.

Inside the Windows 10 VM, I will install Wireshark.
Upon opening Wireshark, I will filter for ICMP traffic only.
Then, I'll retrieve the private IP address of the Ubuntu VM and try to ping it from within the Windows 10 VM.
I will observe the ping requests and replies within Wireshark.
Next, from the Windows 10 VM, I will open the command line or PowerShell and attempt to ping a public website like www.google.com, while observing the traffic in Wireshark.
I'll initiate a perpetual/non-stop ping from the Windows 10 VM to the Ubuntu VM.
Inside the Network Security Group used by the Ubuntu VM, I will disable incoming (inbound) ICMP traffic.
I will observe the ICMP traffic in Wireshark and the command line Ping activity from the Windows 10 VM, which should show no replies due to the disabled inbound ICMP traffic.
I will re-enable ICMP traffic for the Network Security Group used by the Ubuntu VM.
After enabling ICMP traffic, I will observe the ICMP traffic in Wireshark and the command line Ping activity, which should now start working again.
Finally, I will stop the ping activity.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I will filter Wireshark for SSH traffic only.

From the Windows 10 VM, I'll "SSH into" the Ubuntu VM using its private IP address.
While connected via SSH, I will type commands (username, pwd, etc.) into the Linux SSH connection and observe SSH traffic in Wireshark.
I'll exit the SSH connection by typing 'exit' and pressing [Enter].
</p>
<br />


<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I will filter Wireshark for DHCP traffic only.

From the Windows 10 VM, I'll attempt to issue a new IP address for the VM using the command "ipconfig /renew."
I will observe the DHCP traffic appearing in Wireshark.
</p>
<br />

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the Windows 10 VM's command line, I'll use nslookup to see the IP addresses of google.com and disney.com.
I'll observe the DNS traffic being shown in Wireshark.
I will filter Wireshark for RDP traffic only (tcp.port == 3389).

I will observe the constant stream of traffic, as RDP is continually transmitting data between the computers during the session.To wrap up, I'll close my Remote Desktop connection to the VMs.

I will then proceed to delete the Resource Group(s) created at the beginning of this lab.
As a final step, I will verify the deletion of the Resource Group to ensure a clean environment.

</p>
<br />
