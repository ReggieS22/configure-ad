<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://youtu.be/3ZM86XnAXdU)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Overview

<p>
<strong>Setting up Active Directory infrastructure, I will configure and interconnect two virtual machines. One acting as a domain controller with a static IP address for the DNS and one acting as a client machine with a dynamic IP address.</strong>
</p>
<img <img width="829" height="708" alt="Screenshot 2025-09-03 140121" src="https://github.com/user-attachments/assets/ae6e2329-5d49-4af7-921f-ae28db986c90"/>
<p>
</p>
<br />

<p>

- Step 2. Create two VMs (Azure)in the same VNET. One will be a Domain Controller, the other will be a Client machine.

  - Create a virtual machine (Domain Controller) on and another virtual machine (Client-1) on Azure.
  - Name them DC-1 for the Domain Controller and Client-1 for the client machine
  - For the Domain Controller: Select Windows Server 2022: Azure Edition - x64 Gen2 as the image
  - size (Standard_D2s_v3 - 2 vcpus, 8 GiB memory)
  - For ther Client machine: Select Windows 10 pro edition
  - size (Standard_D2s_v3 - 2 vcpus, 8 GiB memory)
</p>
<p>
<img width="2226" height="677" alt="Screenshot 2025-09-04 141758" src="https://github.com/user-attachments/assets/08d89516-e295-4263-84f7-a372e549d4f9"/>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
