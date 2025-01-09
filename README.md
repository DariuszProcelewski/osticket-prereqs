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

- Web Server: Apache or IIS installed on your server.
- PHP: Version 7.4 or higher.
- MySQL Database: MySQL version 5.5 or later, or MariaDB equivalent.
- osTicket Installation Files: Download the latest version of osTicket from the [official website.](https://osticket.com/)
- Access to Admin Privileges: Required for setting up server configurations.

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

Step 3: Install osTicket
1. Download osTicket
Visit the official osTicket website and download the installation files.
Transfer the files to your VM (e.g., using SCP for Linux or RDP file transfer for Windows).

