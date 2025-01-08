
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Observing Network Traffic and Network Security Groups Effects</h1>
  
<p>In this walkthrough, we will observe various network traffic to and from Azure Virtual Machines using PowerShell and Wireshark as well as see how traffic is affected with the use of Network Security Groups.</p>
  <br/>


<h2>Pre-requisite: Creating Azure Virtual Machines</h2>

- ### https://github.com/anakamura1/VM-creation

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop (Windows) / Windows App (Mac)
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: 
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<div style="display: flex; justify-content: space-between;">
<img alt="Screenshot 2025-01-08 at 3 20 21 PM" src="https://github.com/user-attachments/assets/c653d1d7-37ca-446a-9b11-4b6bbf912d1d" width="70%"/>
  <img alt="Screenshot 2025-01-08 at 3 23 08 PM" src="https://github.com/user-attachments/assets/f789a2c3-cc16-4a26-a3f1-1ab061ed8b3e" width="25%"/>
</div>
<p>
In Azure, click into the Windows VM and copy the public IP address of the Windows VM and add a new PC in Remote Desktop or Windows App. This will allow us to log in to the Wndows VM</p>
<br /><br>

<div style="display: flex; justify-content: space-between;">
<img width="65%" alt="Screenshot 2025-01-08 at 3 38 52 PM" src="https://github.com/user-attachments/assets/ef7ece98-6bd2-4f65-8a7d-f413cb0df0cb" />
<img width="30%" alt="Screenshot 2025-01-08 at 3 39 23 PM" src="https://github.com/user-attachments/assets/3f96cb86-ac44-4764-83df-455c3c79bede" />
</div>
<p>
  After logging into the Windows VM with the username and password we assigned it at creation, go to the browser to install Wireshark. Be sure to download the Windows x64 version and run the Setup installer to finish installing Wireshark.
</p>
<br /><br>

<div style="display: flex; justify-content: space-between;">
<img width="45%" alt="Screenshot 2025-01-08 at 3 45 54 PM" src="https://github.com/user-attachments/assets/e1541369-cf1d-4ff4-89ac-44c3b1662fe1" />
  <img width="45%" alt="Screenshot 2025-01-08 at 3 48 52 PM" src="https://github.com/user-attachments/assets/7c3159f6-6aee-4ef2-a878-0d305ae4e0a9" />

</div>
<p>
  Once Wireshark has been installed, open it and begin observing the packet capture by clicking on "Ethernet". In the top search bar, type in icmp and hit enter to begin filtering for ICMP traffic. ICMP traffic is the network protocol that ping uses. A ping is simply a connection test between two devices, in our case it is between our Windows VM and our Linux VM. It sends a small packet of data over the internet to see if we can establish a connection.
</p>
<br /> <br>

<p>
  <img width="1000" alt="Screenshot 2025-01-08 at 3 55 45 PM" src="https://github.com/user-attachments/assets/8584006e-756a-4945-851b-de7b665b772f" />
</p>
<p>
  Next, go back to the Linx VM we created in Azure and find the PRIVATE IP address within the configurations. Open up PowerShell and type in "ping 10.0.0.5". Since 10.0.0.5 is the private IP address of our Linux VM, we will be using it to ping our Linux VM from our Windows VM. Observe that after we hit enter in PowerShell, Wireshark shows us the network traffic that occurred when we pinged our Linux VM. We can see from the traffic that appears a "request" from our Windows VM and "reply" from the Linux VM occurs. Hooray for network traffic!
</p>
<br>

**BONUS:** From PowerShell, ping a public website like Google.com. Enter ping google.com and observe the network traffic!
