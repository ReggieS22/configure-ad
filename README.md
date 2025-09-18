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



## Step 7: Login to Client-1 as any user from Active Directory

**Pick any user from your Active Directory to login to our Client-1 machine.**

<img width="1155" height="552" alt="Screenshot 2025-09-13 162827" src="https://github.com/user-attachments/assets/836d9505-ae08-48f5-b989-af1e777bf8ed" />





<p>





## Step 8: Try to Access the folders as the domain user

**See if the Domain Users has certain access to specific files**

- Go to File Explorer
- On the top bar, type in \\DC-1
- This'll call from the files we made in DC-1


<img width="1124" height="632" alt="Screenshot 2025-09-13 163232" src="https://github.com/user-attachments/assets/81007ee5-595a-4ba1-bdad-7b69279c2a9c" />

<img width="1124" height="632" alt="Screenshot 2025-09-13 163520" src="https://github.com/user-attachments/assets/05bb8bf3-cf3c-49c9-9888-3f4e135a3401" />


- Open up Office Supply List
- The Domain User should be able to read and write in this folder
- I created a document as the Domain User

<img width="1123" height="630" alt="Screenshot 2025-09-13 163701" src="https://github.com/user-attachments/assets/1fffe298-9876-4684-9886-8b3b07bf44d7" />

- Open up Team Announcements
- The Domain User should be able to see and read what's inside this folder

<img width="1126" height="629" alt="Screenshot 2025-09-13 163920" src="https://github.com/user-attachments/assets/77af91d4-a95d-4567-90aa-50c56ed58832" />


- However, if the Domain User try to create documents inside, they recieve this error message
- Stating that they need permissions to perform this action

<img width="476" height="237" alt="Screenshot 2025-09-13 163957" src="https://github.com/user-attachments/assets/57870ab8-6971-4255-bb6a-069b431ea364" />


- Open up Scripts
- Notice how the Domain User can't even access the folder.
- This is due to this folder only be created to be able to access by Domain Admins

<img width="517" height="191" alt="Screenshot 2025-09-13 164426" src="https://github.com/user-attachments/assets/fe50b976-a5e6-4704-8a2c-f7a2eccb06ec" />




<p>







## Step 9: Go back to our DC-1 VM to create a Security Group

**We're going to assign our Accounts folder to a Security Group.**

- Open up Active Directory Users and Computers
- Right click on mydomain.com > New > Organizational Unit
- Name the OU, _GROUPS

<img width="434" height="375" alt="Screenshot 2025-09-13 165132" src="https://github.com/user-attachments/assets/e0f1e478-ec19-4cd6-bf5d-c1581cdc1a19" />

- In the right pane, right click
- Select New > Group
- Name the Group ACCOUNTANTS

<img width="435" height="376" alt="Screenshot 2025-09-13 165445" src="https://github.com/user-attachments/assets/de970bfd-d4e6-4f38-9213-7274ebe3b732" />





<p>



## Step 10: Share the Accounts folder to the ACCOUNTANTS Security Group

**We're assigning the Accounts folder to the ACCOUNTANTS Security Group**

- Go to File Explorer and find the Accounts folder
- Right click > Properties
- Go to the Sharing tab
- Press the Share button


<img width="357" height="477" alt="Screenshot 2025-09-13 165719" src="https://github.com/user-attachments/assets/5ca899be-9d91-4021-a802-da37f0c01a9b" />

- Add the Security Group, ACCOUNTANTS to the box
- Click Add
- Give it the Permission Level of Read/Write

<img width="610" height="448" alt="Screenshot 2025-09-13 170303" src="https://github.com/user-attachments/assets/b38f6e9c-cf0d-4042-ab91-c79b310edbd8" />









<p>




## Step 11: Try to access the "Accounts" folder as the Domain User

**We're going to see what happens if the Domain User tries to access the Accounts folder**

- Go to the File Explorer and click on the Accounts folder
- You'll see that the user can't access the folder
- This is due to the user not being assign to the Security Group named ACCOUNTANTS

<img width="1121" height="627" alt="Screenshot 2025-09-13 171027" src="https://github.com/user-attachments/assets/5edc4fd4-6f98-4970-b420-9809230495b5" />


<img width="516" height="191" alt="Screenshot 2025-09-13 171045" src="https://github.com/user-attachments/assets/be6968bb-0ec5-4fee-a3c0-410e09a9b3ea" />







<p>



## Step 12: Assign the Domain User to the Security Group

**We're going to assign the Domain User to the Security Group called ACCOUNTANTS to let the access the folder.**

- Go back to Active Directory Users and Computers on DC-1
- Double click the ACCOUNTANTS Security group
- Go to the Members tab > Click add
- Add the user's name > Check names > Hit OK


<img width="396" height="449" alt="Screenshot 2025-09-13 171607" src="https://github.com/user-attachments/assets/c7a7a632-2f32-48c2-ab0a-7c154b4fd49d" />


<img width="396" height="452" alt="Screenshot 2025-09-13 171631" src="https://github.com/user-attachments/assets/4a5c3f60-4fc5-42d7-95cb-715d7f99ac4c" />

- The User is now added to the Security Group







<p>




## Step 13: Try to access the "Accounts" folder again in Client-1

**You may have to sign out and sign back in as the user to let the folder and Security Group update.**

- Go to File Explorer and find the Accounts folder and open it

<img width="1123" height="630" alt="Screenshot 2025-09-13 172409" src="https://github.com/user-attachments/assets/612c6dfb-bc15-4b47-b590-e50e2cabe87f" />

- You should now be able to see the contents in this folder and edit them

<img width="1122" height="628" alt="Screenshot 2025-09-13 172445" src="https://github.com/user-attachments/assets/460a4955-51fb-4675-9915-0a024a7f9b30" />




- I hope this lab was very helpful on how Network File Shares and Permissions work :)


<p>


