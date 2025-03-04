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

- Make a free Microsoft Azure account to create a virtual machine
- Download osTicket and it's prerequisites 
- Install and configure osTIcket and it's prerequisites
- Configure IIS

<h2>Installation Steps</h2>


![image](https://github.com/user-attachments/assets/b85147ba-b2f4-4bc0-be53-c4a96ff858b0)

<p>
Install osTicket and it's prerequisites from a reliable source. If you don't know where to get all of the prerequisites, you can get them <a href="https://drive.usercontent.google.com/download? id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0">here</a>☺</h2> (Disclaimer: Includes os ticket and prerequisites; Always scan for viruses to ensure safety; I am not the owner of the link, but have used it and can confidently say that it's a safe link.)
</p>
<br />

![image](https://github.com/user-attachments/assets/438ff77d-8983-4588-b750-7a30562ac71f)

<p>
In the Windows Search Bar, search up Windows Features. You should see a control panel search named "Turn Windows features on or off". Click it and once it opens, navigate to "Internet Information Services" and check the box. Then click the drop down button ("+") and ensure the same boxes are checked as the ones in the photo. Also, enable another prerequisite within the "Internet Information Services": World Wide Web Services -> Application Development Features -> [X] CGI. After you apply the changes, you can verify by searching the loopback address in the search bar: "127.0.0.1" You should see an actual page instead of a "Site can't be reached" page.
</p>
<br />

![image](https://github.com/user-attachments/assets/5daa1349-836d-47f5-875e-a4839a9657b5)

<p>
Install the dependences and follow the installation wizards for each. 
  
From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

![image](https://github.com/user-attachments/assets/34326578-278f-4fb6-87f5-fc00b068e974)

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root 
Password: root

![image](https://github.com/user-attachments/assets/5fa6b201-c534-44e8-8445-1f27eb31b65c)

![image](https://github.com/user-attachments/assets/66b8875e-e7e5-49fa-9cba-25043b7c3782)

![image](https://github.com/user-attachments/assets/57fb77b8-406d-49e0-9943-971ffc7b5b66)

![image](https://github.com/user-attachments/assets/12ce466b-18be-4550-976a-262e453f62b2)

![image](https://github.com/user-attachments/assets/17fb605f-7c1c-4e86-b944-e785e6f59009)

Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

![image](https://github.com/user-attachments/assets/f9b8d1dc-848a-43ef-ad8e-2261e5fd9a76)

![image](https://github.com/user-attachments/assets/00e95b0d-e742-4703-96ac-83ae92d9efc8)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

![image](https://github.com/user-attachments/assets/5e94f1bb-acc7-45fd-bb50-5ece765db251)

![image](https://github.com/user-attachments/assets/cf0f0d29-246b-4b01-a739-286e1677c2b5)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

![image](https://github.com/user-attachments/assets/be8e14fd-c412-4d4d-a340-933ed423e5f5)

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php


</p>
<br />


