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


- Set the Permssion level for the Domain Users to Read
- Hit Share

<img width="610" height="451" alt="Screenshot 2025-09-13 160455" src="https://github.com/user-attachments/assets/3fdf3ee9-7f14-438d-b3f9-fe0764a3ce65" />




<p>



## Step 4: Give the "Office Supply List" folder read/write permission level

**Give the Office Supply List folder read/write permissions for the domain users.**


- Right click the folder > Select Properties
- Press the Sharing tab
- Click the Share button

<img width="356" height="473" alt="Screenshot 2025-09-13 161414" src="https://github.com/user-attachments/assets/6da21699-f038-44ee-913a-a087533f124a" />



- Add the Domain Users to the box
- Click add

<img width="614" height="452" alt="Screenshot 2025-09-13 161432" src="https://github.com/user-attachments/assets/ba437fe9-3999-4414-b1c1-227af128abc7" />



- Set the Permission level for the Domain Users to Read/Write
- Hit Share

<img width="614" height="454" alt="Screenshot 2025-09-13 161446" src="https://github.com/user-attachments/assets/09845777-5832-4108-854f-9160ea3a70f0" />




<p>



## Step 5: Give the "Scripts" folder read/write permission level for Domain Admins ONLY

**Give the Scripts folder read/write permission level for Domain Admins ONLY. No domain users will be able to access this file.**

- Right click the folder > Select Properties
- Press the Sharing tab
- Click the Share button

<img width="360" height="476" alt="Screenshot 2025-09-13 162146" src="https://github.com/user-attachments/assets/32b26a16-0ec7-4881-89c3-e14472162721" />




- Add the Domain Admins to the box
- Click Add

<img width="616" height="451" alt="Screenshot 2025-09-13 162208" src="https://github.com/user-attachments/assets/7234c440-7a8a-42c8-a442-e273d3bfe85a" />



- Set the Permission level for the Domain Admins to Read/Write
- Hit Share
- This folder can be only access to Domain Admins and not to regular domain users

<img width="615" height="453" alt="Screenshot 2025-09-13 162227" src="https://github.com/user-attachments/assets/420ff7a9-f607-4d50-bd4f-b53c39828305" />





<p>



## Step 1: Login to Client-1 as any user from Active Directory

**Pick any user from your Active Directory to login to our Client-1 machine.**

<img width="1155" height="552" alt="Screenshot 2025-09-13 162827" src="https://github.com/user-attachments/assets/836d9505-ae08-48f5-b989-af1e777bf8ed" />





<p>

