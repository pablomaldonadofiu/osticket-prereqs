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

- All needed programs can be found in this google drive folder: https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6?usp=sharing 

<h2>Installation Steps</h2>


<p>
First of all, let's enable ISS in windows with CGI. To do this, open control panel, go to programs and features, click "Turn Windows features on or off".
Find Internet Information Services (IIS) and click the left box to turn it on. 
Then expand the folder by clicling + symbol. Now turn on "Web Management Tools" and "World Wide Web Services", expand "World Wide Web Services" to turn on
"Application Development Features", "Common HTTP Features", "Health and Diagnostics", "Performance Features", and "Security".
Lastly, expand "Application Development Features" and turn on "CGI" 
</p>
<p>
<img src="https://i.imgur.com/uX8xrFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From installation files install PHP Manager for ISS (PHPManagerForIIS_V1.5.0.msi).Now from the same file intall Rewrite Module (rewrite_amd64_en-US.msi)
In your local hard Drive create a directory call PHP, i.e C:\PHP 
</p>
<p>
<img src="https://i.imgur.com/nWWStSq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP (or whatever your hard drive disk name is)
From the Installation Files, download and install VC_redist.x86.exe.
From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi). After installing, run MySQL, when setting it up, select “Standard Configuration”, Then enter a password for the root. Note: Please do not forget this password! 
</p>
<p>
<img src="https://i.imgur.com/P0Bk05L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
At the search bar of windows, type IIS, then right click it and select “run as an administrator”. Inside, click “Sites” under vm-osticket on the left. Select PHP MANAGER, inside, click on “Register new PHP version”, click on the “…” symbol and select   php-cgi.exe inside PHP folder (i.e C:\PHP\php-cgi.exe). finally, click on the server name on the left (“vm-osticket”) then on the right click restart. 
</p>
<p>
<img src="https://i.imgur.com/UYLGVLm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From the Installation Files, download and install osTicket v1.15.8 and unzip it. Inside osTicket v1.15.8 there is a file called upload, move (drag) that file to  c:\inetpub\wwwroot, after it finished transferring, change the name of the folder “upload” to “osTicket” (make sure T is capital). Finally restart the server as indicated in the previous step. 
To check all previous step were done correctly, in your browser go to: localhost/osTicket/setup and you should see the following: 
</p>
<p>
<img src="https://i.imgur.com/hZL9B8s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Go back to IIS, again inside sites -> osTicket, select PHP manager, then select “Enable or disable an extension” under PHP Extensions. Inside, enable: php_imap.dll, php_intl.dll, php_opcache.dll. If you refresh the osTicket site in your browser, you should now see more green tickets if done correctly. 
Now go to  C:\ -> inetpub -> wwwroot -> osTicket -> include , inside “include” change the name of the “ost-sampleconfig.php” file to “ost-config.php” at the bottom of the file. Now right click on “ost-config.php”, select Properties -> security -> Advance. Now click on “Disable inheritance”, click Add and type “Everyone”, then click “Check Name” and “OK”, click “Full control” and “OK”  again and one last OK to close the window. 
Go back to the browser and you should be able to click continue. Now fill the information needed with your information. Remember that the username of MySQL is root, and the password was created when installing MySQL. Do not click install now! Wait until the steps say so. 
Now From the Installation Files, download and install HeidiSQL.
 *Note: Click the picture for better resolution
</p>
<p>
<img src="https://i.imgur.com/v7VRQNk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Open HeidiSQL, click “New” at the bottom left. For username user root, and for password use password used in MySQL installation. Then click open. 
Once inside, right click “Unnamed” and select create new -> Database and name it “osTicket” 
</p>
<p>
<img src="https://i.imgur.com/TwRFVyZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Now go back to the browser and click “Install now”, you should now see the same as the picture below, if not, make sure you follow every step correctly or re-do them if necessary.
And now we are done, let’s do some clean up. First, delete: C:\inetpub\wwwroot\osTicket\setup
then go back to C:\inetpub\wwwroot\osTicket\include\ost-config.php right click and select properties -> security -> Advace. Click in Everyone permission and click “Edit”, uncheck every box except “Read” and “Read & execute” Then click ok and apply. 
</p>
<p>
<img src="https://i.imgur.com/6kZl7gM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />



