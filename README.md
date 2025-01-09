<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation (including creating VM in Azure) </h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

Before you begin, ensure you have the following prerequisites in place:

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- MySQL
- Heidi SQL
- osTicket - download the latest version of osTicket from the [official website.](https://osticket.com/)
- Access to Admin Privileges: Required for setting up server configurations.
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
  
<h2>Installation Steps</h2>

Step 1: Create a Virtual Machine in Azure:

  1) Log in to Azure Portal
  Navigate to the Azure Portal and sign in with your credentials.
![Screenshot 2025-01-07 062310](https://github.com/user-attachments/assets/e93a28a9-928c-4f34-8a04-5ee871db16c6)

  2) Create a New Virtual Machine
  Click on Create a resource > Compute > Virtual Machine.
  
  3) Configure VM Basics - fill out the required fields:
  
  - Resource Group: Create a new resource group or use an existing one.
  
  - Subscription: Select your subscription.
  
  - Virtual Machine Name: Enter a name (e.g., osticket-vm).
  
  - Region: Choose a region.
  
  - Image: Select an image (e.g. Windows Server 2022).
  
  - Size: Select the VM size (e.g., Standard_B1s for small-scale deployment - I recommend with at least 2 vcpus).
  - Set Up Administrator Account. Set a username and password for RDP
    
![image](https://github.com/user-attachments/assets/e8115245-5801-49aa-8efc-70fe6cd0dbeb)
![image](https://github.com/user-attachments/assets/4e44002c-36a6-44b3-a531-030c9b023b0e)
![image](https://github.com/user-attachments/assets/bba86bde-45be-407e-9e15-0b14871a0d91)

  3) Configure Networking

   Ensure the VM is accessible:
  - Set a Public IP address.
  - Add Inbound Port Rules to allow HTTP (port 80), HTTPS (port 443), and SSH/RDP (ports 22/3389, depending on the OS).
    
  4) Review and Create. Review your configuration, click Create, and wait for the VM to deploy.

![Screenshot 2025-01-07 064816](https://github.com/user-attachments/assets/0f0c86c3-ccd4-4f12-aaed-3962ef5fa774)

Step 2: Connect to Your VM
 1) Connect to the VM:
- Open in Azure Virtual Machines section
- Copy Public IP adress
- Go to Windows Search Tab, open Remote Desktop Connection and paste IP adress and press connect

![Screenshot 2025-01-09 063602](https://github.com/user-attachments/assets/67d6be5f-612c-451f-86fa-da776aaf227c)

- Click Use different account
- Type in your Username and Password which you create durring creating your VM in Azure
- Follow next easy steps

![Screenshot 2025-01-09 062853](https://github.com/user-attachments/assets/e56bba28-8e61-4a21-85e1-e6e727b00cef)

![Screenshot 2025-01-09 064717](https://github.com/user-attachments/assets/7174b3b3-067d-42f8-928f-9cb2a564c36b)

![Screenshot 2025-01-09 065056](https://github.com/user-attachments/assets/69c4fae5-86ce-4bcb-9eed-c7ccc63f6b17)

Well done! We connect to our VM! :)

<h2>Step 3: Install osTicket</h2>
Download osTicket
Visit the official osTicket website and download the installation files.
Transfer the files to your VM (e.g., using SCP for Linux or RDP file transfer for Windows).

<h2>Enabling IIS</h2>

Before beginning the installation, ensure that Internet Information Services (IIS) is enabled, as osTicket requires it to function. To enable IIS:

1) Open the Control Panel.
 
2) Navigate to Programs > Turn Windows Features On or Off.

4) Expand Internet Information Services and Web Management Tools, then enable IIS Management Console.

5) Expand World Wide Web Services > Application Development Features, enable CGI, and click OK to confirm.

<h2>Installing PHP Manager and Rewrite Module</h2>

1) Download and install PHP Manager for IIS (PHPManagerforIIS_V1.5.0.msi) from the installation files.
 
2) Download and install the Rewrite Module (rewrite_amd64_en-US.msi) after completing the PHP Manager installation.
   
<h2>Setting Up PHP</h2>

1) Create a new folder: C:\PHP on the C: drive.
 
2) Extract the contents of the php-7.3.8-nts-Win32-VC15-x86.zip file (from the installation files) into the C:\PHP folder.

<h2>Installing Visual C++ Redistributable</h2>

- Download and install VC_redist.x86.exe from the installation files.

<h2>Installing MySQL</h2>

1) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files.

2) During the setup wizard:
   
 - Accept the license agreement.
 - Select Typical Install and proceed with the installation.
   
3) Launch the Configuration Wizard:
   
 - Select Standard Configuration.
 - Choose Install as Windows Service and ensure Launch MySQL Server Automatically is checked.
 - Use root as the username and Password1 as the password (for this lab)
   
4) Complete the configuration.

<h2>Configuring IIS for osTicket</h2>

1) Open IIS as an administrator and select PHP Manager.
 
2) In PHP Manager, choose Register New PHP Version and locate the php-cgi.exe file in the C:\PHP folder.
 
3) After registering, reload the IIS server from the management console.

<h2>Preparing osTicket Files</h2>

1) Download osTicket v1.15.8 from the installation files.
 
2) Extract the "upload" folder to C:\inetpub\wwwroot.

3) Rename the "upload" folder to osTicket.
 
4) Reload the IIS server.

<h2>Enabling PHP Extensions</h2>

1) In IIS, navigate to Sites > Default > osTicket.

2) Click *Browse :80, which will display the osTicket installation page.

3) Return to IIS, open PHP Manager, and select Enable or Disable an Extension.
 
4) Enable the following extensions:

 - php_imap.dll
 - php_intl.dll
 - php_opcache.dll

<h2>Configuring osTicket Files</h2>

1) Navigate to C:\inetpub\wwwroot\osTicket\include.

2) Rename ost-sampleconfig.php to ost-config.php.

3) Update file permissions:
   
 - Right-click ost-config.php and open Properties.
 - Disable inheritance, remove all permissions, and set new permissions: Everyone with Full Control.

<h2>Setting Up the Database</h2>

1) Download and install HeidiSQL from the installation files.

2) Open HeidiSQL, create a new session using the MySQL credentials (root/Password1).
 
3) In the new session, right-click Unnamed and create a new database named osTicket.

<h2>Finalizing osTicket Installation</h2>

1) Return to the osTicket installation page in the browser.

2) Enter the required details to configure osTicket. Use the database credentials created earlier.
 
3) Once installation is complete, perform the following cleanup steps:

 - Delete the setup folder from C:\inetpub\wwwroot\osTicket.
 - Update permissions for ost-config.php in C:\inetpub\wwwroot\osTicket\include: remove Full Control for Everyone and set it to Read-Only.

<h2>osTicket Ready!</h2>
osTicket is now successfully installed and ready for use. This setup was used to understand the basics of ticketing systems and their role in IT support. It provides a foundation for managing and resolving IT issues effectively through a structured ticketing process.
