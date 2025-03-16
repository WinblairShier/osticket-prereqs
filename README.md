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

- Azure Virtual Machine (VM) (Linux or Windows) to host osTicket
- Azure Database for HeidiSQL or install HeidiSQL on the VM
- Azure Storage for attachments/logs
  

<h2>Installation Steps</h2>

  
<p>

 First, we log in to the Azure Portal and go to "Create a resource" → Select "Virtual Machine." Here, we'll set up our VM. Name it "osticket-vm", then choose Windows 10 Pro as the OS and pick a size with 2vCPU (2-4 vCPUs) to handle the workload. After that, we begin setting up the login details. Once everything looks good, we click Review + Create, then Create. We wait a few minutes while Azure sets up our VM. Once it’s ready, we go to the Virtual Machines section and note down the Public IP Address, which will be needed for the next step.
<img src="https://i.imgur.com/MuXTzbj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On our local computer, we open Remote Desktop Connection (RDP), type in our VM’s Public IP Address, and hit Connect. When prompted, we enter our login credentials. We should now be inside our Azure VM, ready to install osTicket. If you are a Mac user, you will need to download Microsoft Remote Desktop(RDP).


</p>
<br />

<p>
<img src="https://i.imgur.com/PVturKJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
okay now that we are in VM, we need to enable IIS with CGI. To do so we press Win + R on our keyboard, type appwiz.cpl, and press Enter. This will open the Programs and Features window. On the left side, we’ll click on Turn Windows features on or off. In the list of Windows features, scroll down and find Internet Information Services (IIS). We’ll expand it, and under World Wide Web Services, expand Application Development Features. Here, let’s check the box next to CGI. Once that’s done, we’ll click OK to apply the changes.Finally, we open a browser and visit http://localhost to ensure IIS is working correctly. This process will help us set up IIS with CGI on our VM and get it ready for web applications like osTicket.
</p>
<br />

<p>
<img src="https://i.imgur.com/VulpV9S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We then install MySQL choosing "Typical Setup". We open IIS as an admin, register PHP by using PHP Manager and pointing it to C:\PHP\php-cgi.exe, and reload IIS by stopping and starting the server. After that, we install osTicket and copying the "upload" folder into C:\inetpub\wwwroot. We renamed the "upload" folder to "osTicket" and reload IIS again by stopping and starting the server. Finally, we go to Sites → Default → osTicket in IIS and click *Browse :80 on the right. Note that some extensions may not be enabled.

<p>
<img src="https://i.imgur.com/7UV0KQi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
We then go back to IIS, then Sites → Default → osTicket. Double-click PHP Manager, then click “Enable or disable an extension”. We enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll. After enabling them, we refresh the osTicket site in our browser to observe the changes.


<p>
<img src="https://i.imgur.com/Vjjm675.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Rename: ost-config.php>From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php>To: C:\inetpub\wwwroot\osTicket\include\ost-config.php>Assign Permissions: ost-config.php>Disable inheritance -> Remove All>New Permissions -> Everyone -> All
Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)


<p>  
<img src="https://i.imgur.com/jE4j0Fa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  From the “osTicket-Installation-Files” folder, install HeidiSQL.Open Heidi SQL
Create a new session,> Connect to the session> Create a database called “osTicket”> Continue Setting up osTicket in the browser
MySQL Database: osTicket >
MySQL Username & Password >
Click “Install Now!”

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 


</p>
<br />
