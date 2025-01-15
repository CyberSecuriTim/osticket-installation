<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation procedure of the open-source help desk ticketing system osTicket.<br />

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

   - Optionally, to enhance the security posture of the VM and reduce its attack surface you can restrict the source IP addresses that can successfully establish an RDP connection to the VM over 
    the internet via TCP port 3389 by modifying the inbound port rule for RDP in the VM's Network Security Group

![image](https://github.com/user-attachments/assets/b164c754-b60a-4e65-89c4-b333509e003a)


>
</p>
<br />
<p>
<h2> 
STEP 2: (Start/Turn on the VM in the Azure portal) Then using your preferred Remote Desktop client (I used the Windows Remote Desktop Connection App for my lab), establish an RDP connection to the VM using its public IP address and the admin account credentials that were assigned during the VM's creation.
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

  NOTE: Microsoft Edge (which is natively installed as part the VM's operating system image) should be able to facilitate the downloading process of all the 
  files but if any problems are experienced, just download and use the google chrome browser instead).
 
  ![image](https://github.com/user-attachments/assets/c6f33add-41ba-4013-9473-17b98fc396ee)

  - From the installation files:
    - Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
    - Download and install Rewrite Module (rewrite_amd64_en-US.msi)
    - Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)
        - Create the directory "PHP" in the root directory of the C: volume (C:\PHP)
        - Unzip the contents into C:\PHP
     
    ![image](https://github.com/user-attachments/assets/0421ee26-20c0-46c8-ada9-0e42dfd44295)

    - Download and install VC_redist.x86.exe
    - Download and install MySQL 5.5.62
      - Typical Setup
      - Launch Configuration Wizard (after installation)
      - Standard Configuration
      - Username: root
      - Password: (Assign your own password)
     

  - Open IIS Manager and run as administrator. Then open "PHP Manager" and register a new PHP version.
      - Provide the path to the downloaded PHP executable file (C:\PHP\php-cgi.exe)

  ![image](https://github.com/user-attachments/assets/57903f75-478d-4ec4-9a1f-1f06e1827275)

- Restart the IIS server within IIS manager (click restart on the right hand side in the actions panel) to ensure the PHP changes have taken effect. 

- Install osTicket v1.15.8
  - Download osTicket (osTicket-v1.15.8.zip) from the [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) Folder
  - Extract and copy “upload” folder to c:\inetpub\wwwroot
  - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
 
![image](https://github.com/user-attachments/assets/3a8b1d4e-b576-459a-b355-926d10bceef1)

- Restart the IIS server within IIS Manager to ensure the changes take effect.

- Within IIS Manager, in the connections panel on the left side, navigate to Sites ---> Default Web Site ---> osTicket
  - Then select "Browse *:80" to establish an http connection via port 80 on the local host address (127.0.0.0/8) to the osTicket server instance.
 
![image](https://github.com/user-attachments/assets/173eda31-78e2-4978-a94e-60de1520df6f)

![image](https://github.com/user-attachments/assets/8b63305c-6847-489f-b64e-e8398f68c1c3)

- Note that some extensions are not enabled by default.
  - To enable these extensions return to IIS manager and navigate to Sites ---> Default Web Site ---> osTicket
  - Then Open PHP Manager
  - Click "Enable or disable an extension"
    -  Enable: php_imap.dll
    -  Enable: php_intl.dll
    -  Enable: php_opcache.dll
  - Refresh the osTicket site in your browser and observe the changes.
 
![image](https://github.com/user-attachments/assets/7397d6c3-e7fe-441f-9c03-0d5d366690cd)

- Rename "C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php" to "C:\inetpub\wwwroot\osTicket\include\ost-config.php"

![image](https://github.com/user-attachments/assets/f8ca52af-e757-4205-83b2-ed24676cd607)


- Modify the permissions of the ost-config.php file
  - Disable Inheritance (Remove all inherited permissions from this object)
![image](https://github.com/user-attachments/assets/22b29a3f-7149-41b7-85c9-029d61fb6c1d)
  - Add New permission
    - Set the principal as "Everyone" and Basic permissions (Full control)
   
    ![image](https://github.com/user-attachments/assets/5d2aab0d-9e62-4149-8914-1673a1779c54)

- Continue configuring osTicket in the browser (click Continue)
  - Name the HelpDesk
  - Provide the default email address
    - This is the email address that will receive emails from the help desk customers/users

![image](https://github.com/user-attachments/assets/dfee36b6-c721-4b16-9693-099db62c408a)

- From the [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) download and install HeidiSQL
  - Run the HeidiSQL setup wizard (the default configurations can be left unchanged)
  - Launch HeidiSQL
  - Create a new session, use the username (root) and password that was assigned during the initial configuration of the MySQL server instance
    - Notice that TCP port 3306 is being used by the HeidiSQL client to establish the connection to the MySQL server instance (as this is the TCP/IP port that is used by default to connect to MySQL servers).
    
![image](https://github.com/user-attachments/assets/070288e4-89c0-40cd-94b9-fca927bb1bdb)
  - Connect to the session
  - Create a database called "osTicket"
    - Right click Unnamed, select "Create new" and select "Database"    
        

![image](https://github.com/user-attachments/assets/daf9edf2-c4bc-4163-bd63-e6134f880fe2)

- Continue configuring osTicket in the browser:
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: (whatever password was used during the intial creation of the MySQL server instance)   


![image](https://github.com/user-attachments/assets/e59037d2-87e5-495c-9e70-fcfeb8592980)

- Click "Install Now"

![image](https://github.com/user-attachments/assets/057c8d77-eaa8-4e08-a53a-20d1e527ecf7)

Congratulations!! You have now *hopefully* successfully installed osTicket.
</p>

<h2>
  FINAL STEP: Time to clean Up!
</h2>

<p>
  - Delete "C:\inetpub\wwwroot\osTicket\setup" folder
  
  ![image](https://github.com/user-attachments/assets/ddf25eeb-815b-4c45-857a-2b841fae4631)

  - Set permissions to "Read" only for the "C:\inetpub\wwwrooot\osTicket\include\ost-config.php" file

![image](https://github.com/user-attachments/assets/b78b4b88-55ae-467f-9101-266b58c4d248)

- Notes:
  - To browse to your help desk login page (within the VM): http://localhost/osTicket/scp/login.php
    - This is the portal that the help desk employees (agents) will use to receive and resolve tickets generated by the end users.  
  ![image](https://github.com/user-attachments/assets/3fa24fc8-f759-44ac-9a86-9cc815ce4bac)

  - To browse to the osTicket End Users ticket generation portal (within the VM): http://localhost/osTicket/
 
  ![image](https://github.com/user-attachments/assets/468653c5-4756-40f7-95b8-4e02d3b9a865)

</p>


