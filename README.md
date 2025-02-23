<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com/watch?v=wuIE4p4io7Q)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory
- Create a Domain Admin user within the domain
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

  

<h2>Preparing AD Infrastructure in Azure</h2>

<p>
<img width="464" alt="image" src="https://github.com/user-attachments/assets/33bb637f-2515-4c04-a168-b8a89ea3a6cc" />
<img width="463" alt="image" src="https://github.com/user-attachments/assets/af95891c-4db1-486f-a957-23f6924c65f3" />
</p>
<p>
  Setup Domain Controller in Azure
Create a Resource Group, Then make a Virtual Network and Subnet 
  Create the Domain Controller VM (Windows Server 2022) named “DC-1”
  (After VM is created, set Domain NIC Private IP address to be static)
</p>
<br />

<p>
<img width="372" alt="image" src="https://github.com/user-attachments/assets/bdd89c8f-9b39-46cf-82d5-1f9bae1b4fd9" />
</p>

<p>
Setup Client-1 in Azure
Creat the Client VM  (Windows 10) named “Client-1”
Attach it to the same region and Virtual Network as DC-1 
  After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address
  From the Azure Portal, restart Client-1

</p>
<br />

<p>
<img width="372" alt="image" src="https://github.com/user-attachments/assets/bdd89c8f-9b39-46cf-82d5-1f9bae1b4fd9" />
</p>

<p>
Login to Client-1
Attempt to ping DC-1’s private IP address
Ensure the ping succeeded
From Client-1, open PowerShell and run ipconfig /all
The output for the DNS settings should show DC-1’s private IP Address

</p>
<br />

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="713" alt="image" src="https://github.com/user-attachments/assets/c4f36b43-572e-48ec-b58c-bb82bc544f70" />
</p>

<p>
Login to DC-1 and install Active Directory Domain Services
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Restart and then log back into DC-1 as user: mydomain.com\labuser
</p>
<br />
