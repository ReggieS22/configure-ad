<p align="center">
<img width="1200" height="630" alt="File shares" src="https://github.com/user-attachments/assets/2d2ee3f6-7059-4634-9538-0751e3e50639" />

</p>

<h1>Network File Shares and Permissions (Azure)</h1>
This tutorial outlines the implementation of Network File Shares and Permissions in Azure.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: Network File Shares and Permissions](https://youtu.be/jk_TSwV443Q)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

## Step 1: Logging in to our DC-1 (Domain Controller) Virtual Machine

**Log into your domain controller as Jane Admin.**


<img width="970" height="652" alt="Screenshot 2025-09-12 124834" src="https://github.com/user-attachments/assets/268c2e01-3f5e-4168-aba4-0c8947a8c9a6" />



<p>


## Step 2: Create Folders in File explorer

**We'll create 4 folders.**

- The first file name will be Team Announcements (read-access)
- 2nd will be Office Supply List (read/write permissions)
- 3rd will be Scripts (No-access. Only for Admins able to access)
- 4th will be Accounts (We'll save for later to include it in a Security Group)



<img width="490" height="114" alt="Screenshot 2025-09-13 155728" src="https://github.com/user-attachments/assets/a992365d-d974-49ef-b468-86fb00a837d7" />



<p>




## Step 3: Give the "Team Announcements" folder read permission level

**Give the team announcements folder only read permissions for the domain users**

- Right click the folder > Select Properties
- Press the Sharing tab
- Click the Share button

<img width="356" height="475" alt="Screenshot 2025-09-13 160342" src="https://github.com/user-attachments/assets/26d885c2-6a8e-4122-ba14-82b23a722391" />


- Add the Domain Users to the box
- Click add

<img width="614" height="453" alt="Screenshot 2025-09-13 160428" src="https://github.com/user-attachments/assets/d1917d91-4ac3-4497-ad4d-8e949d46e9af" />


- Set the Permssion level to Read

<img width="610" height="451" alt="Screenshot 2025-09-13 160455" src="https://github.com/user-attachments/assets/3fdf3ee9-7f14-438d-b3f9-fe0764a3ce65" />




<p>
