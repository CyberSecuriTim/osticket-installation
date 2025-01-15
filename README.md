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


>

</p>
<p>
STEP 2: 
</p>
<br />
