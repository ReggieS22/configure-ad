<p align="center">
<img width="300" height="168" alt="Active Directory" src="https://github.com/user-attachments/assets/ab43591a-2189-41f9-875f-b6e6c8971685" />


</p>

<h1>Network File Shares and Permissions (Azure)</h1>
This tutorial outlines the implementation of pre-installation of Active Directory within Azure Virtual Mahcines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: Prerequisites for Active Directory](https://youtu.be/3ZM86XnAXdU)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

## Step 1: Setting up Active Directory Infrastructure

- First we will configure and interconnect two virtual machines, each with distinct roles. The first virtual machine will be a designated Domain Controller. The second virtual machine will be configured as the Client.


<img width="829" height="708" alt="Screenshot 2025-09-03 140121" src="https://github.com/user-attachments/assets/60af5984-77a3-4a42-ac63-111dda0ce365" />




<p>


## Step 2: Create the Virtual Machines

**Create two VMs (Azure) in the same VNET. One will be a Domain Controller, the other will be a Client machine**

- Create a VM for the Domain Controller on Azure.
- Name it DC-1
- Select Windows Server 2022 Datacenter: Azure Edition -x64 Gen2 as the Image
- Size (Standard_D2_v3 - 2 vcpus, 8 GiB memory)
- Create a username and password for your VM DC-1


<img width="738" height="428" alt="Screenshot 2025-09-18 104915" src="https://github.com/user-attachments/assets/8f9134be-eaf9-4db2-80d6-7039f48289bc" />

**Create a VM for the client machine**

- Create a new VM
- Name it Client-1
- Slect Windows 10 Pro as the image
- Select at least 2 vcpus and 16 GiB memory
- Create a username and password for your VM Client-1
- Make sure to select the same resource group and Virtual network from the DC-1 VM


<img width="767" height="443" alt="image" src="https://github.com/user-attachments/assets/3fc81412-8f1b-431b-930a-2f0b97801b4f" />





<p>




## Step 3: Set the Domain Controller's Private IP to static

**We don't want the IP to change so that the client-1 machine can join the Domain**

- Once the VM has been deployed, proceed to the VM overview page and select "Networking" > network settings on the left side.

<img width="771" height="444" alt="Screenshot 2025-09-04 142451" src="https://github.com/user-attachments/assets/df88c968-13d6-4f79-a582-0f17864679da" />


- Select Network Interface Card > IP configurations > ipconfig1 and set Private IP addess allocation to static.

<img width="769" height="442" alt="Screenshot 2025-09-04 142507" src="https://github.com/user-attachments/assets/56ae10dd-ee06-402f-b428-52d20ff8dd85" />







<p>



## Step 4: Login to DC-1 and configure the firewall settings

**We don't want the IP to change so that the client-1 machine can join the Domain**

- Once the VM has been deployed, proceed to the VM overview page and select "Networking" > network settings on the left side.

<img width="771" height="444" alt="Screenshot 2025-09-04 142451" src="https://github.com/user-attachments/assets/df88c968-13d6-4f79-a582-0f17864679da" />


- Select Network Interface Card > IP configurations > ipconfig1 and set Private IP addess allocation to static.

<img width="769" height="442" alt="Screenshot 2025-09-04 142507" src="https://github.com/user-attachments/assets/56ae10dd-ee06-402f-b428-52d20ff8dd85" />







<p>





