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
  
  <h2>
    
  STEP 1: Create and deploy a Windows 10 virtual machine within the [Azure Portal](https://portal.azure.com) with at least 2 Virtual CPU cores and 8GiB of memory.
  
  </h2>  
 
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
<h2> 
STEP 2: (Start/Turn on the VM in the Azure portal) Then using your preferred Remote Desktop client (the Windows Remote Desktop Connection App was used for my lab), establish an RDP connection to the VM using its public IP address and the admin account credentials that were assigned during the VM's creation.
</h2>
   
  - The VM's public IP address was provisioned during its deployment in Azure and can be observed in the VM's overview section in the Azure portal.

![image](https://github.com/user-attachments/assets/717a484f-161d-4a11-8c7f-fd1752d2b202)


 
</p>
<br />

<p>
  <h2>
STEP 3: Install/Enable IIS (Internet Information Services) in Windows WITH CGI and Common HTTP Features AND IIS Management Console    
  </h2>

 
  - Open the Control Panel and navigate to Programs & Features ----> Turn Windows Features On/Off
    - Internet Information Services --> Web Management Tools --> [x] IIS Management Console
    - Internet Information Services --> World Wide Web Services --> Application Development Features --> [X] CGI
    - Internet Information Services --> World Wide Web Services --> [X] Common HTTP Features 

![image](https://github.com/user-attachments/assets/c6f9b73c-b1bd-4485-8d06-2ff4366f82ea)

   - To test the successful installation of IIS, type the VM's loopback address (any ip address in the address space of 127.0.0.0/8) into the address bar of a web browser and a screen that looks similar to this should be generated.
![image](https://github.com/user-attachments/assets/409b7a50-7d1b-4d55-9fc3-fffbd533e5c4)

</p>
<h2>
STEP 4: 

Open the [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) Google Drive directory within the VM and begin downloading and installing the osTicket software dependencies.
</h2>
<p>
  This installation file directory contains the offline version of all the dependencies to ensure a consistent version is being used for all the files everytime this lab is done.
 
  ![image](https://github.com/user-attachments/assets/c6f33add-41ba-4013-9473-17b98fc396ee)

  - From the installation files:
    - Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
    - Download and install Rewrite Module (rewrite_amd64_en-US.msi)
    - Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
        - Create the directory "PHP" in the root directory of the C: volume (C:\PHP)
        - Unzip the contents into C:\PHP 
    - Download and install VC_redist.x86.exe
    - Download and install MySQL 5.5.62
      - Typical Setup
      - Launch Configuration Wizard (after installation)
      - Standard Configuration
      - Username: root
      - Password: (Assign your own password)
     
</p>


