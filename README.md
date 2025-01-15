<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Internet Information Services (IIS) WITH CGI and Common HTTP Features AND IIS Management Console
- From the [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) Directory in google drive:
  - PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  - Rewrite Module (rewrite_amd64_en-US.msi)
  - PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP  
  - VC_redist.x86.exe
  - MySQL 5.5.62 (mysql-5.5.62-win32.msi)

<h2>Installation Steps</h2>
<p>
  STEP 1: Create and deploy a Windows 10 virtual machine within the Azure portal(https://portal.azure.com) with at least 2 Virtual CPU cores and 8GiB of memory.
 
  - While creating the VM, simultaneously create a resource group for the VM to be deployed in and a new Virtual Network (Vnet).
  - Allow TCP port 3389 as an open inbound port on the created VM as this will enable an RDP (remote desktop protocol) connection to the VM in the cloud.
  - Provision the administrator account's credentials and make a note of them as these will be used to remotely login to the VM via RDP.
</p>

![image](https://github.com/user-attachments/assets/b26d7191-b638-462a-b96e-ab19c59c4b74)

<p>
<![image](https://github.com/user-attachments/assets/129f600e-d460-4ff3-93ae-76bce031b2a1)

  ![image](https://github.com/user-attachments/assets/8ed0666f-fbb9-406b-b388-c15fc2dd38b5)

![image](https://github.com/user-attachments/assets/422f17c1-d0f8-4bef-b770-f0445135bdd7)

   - Optionally, to enhance the security posture of the VM and reduce its attack surface you can restrict the source IP addresses (to known IP addresses) that can successfully establish an RDP connection to the VM over 
    the internet via TCP port 3389 by modifying the inbound port rule for RDP in the VM's Network Security Group

![image](https://github.com/user-attachments/assets/b164c754-b60a-4e65-89c4-b333509e003a)


>
</p>
<br />
<p>
STEP 2: (Start/Turn on the VM in the Azure portal) Then using your preferred Remote Desktop client (the Windows Remote Desktop Connection App was used for my lab), establish an RDP connection to the VM using its public IP address and the admin account credentials that were chosen during the VM's creation.
   
  - The VM's public IP address was provisioned during its deployment in Azure and can be observed in the VM's overview section in the Azure portal.
 
</p>
<br />
