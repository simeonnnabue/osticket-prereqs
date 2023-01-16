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

<h2>Prerequisites</h2>

- Microsoft Azure
- Virtual Machine
- osTicket Installation Files [link](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)


<h2>Installation Steps</h2>


<h3>Step 1: Create an Azure Virtual Machine (Windows 10), Connect to your VM with Remote Desktop</h3>


<h3>Step 2: Install / Enable Internet Information Services (IIS) in Windows</h3>

- At the bottom left, search control panel.
- Select Programs.
- select Turn Windows features on or off (Left column)
- Make sure Internet Information Services is checked, and select OK.


<p align="center">
<img src="https://i.imgur.com/a3XQ6FM.png" height="80%" width="80%" alt="Azure Free Account"/> 
</p>


<h3>Step 3:  Download Lab files
</h3>

- Download and install the following from within the lab files: [link](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
  - PHP Version 7.3.8
  - PHP Manager 1.5.0 for IIS 10
  - VC_redist.x86.exe
  - osTicket v1.15.8


<p align="center">
<img src="https://i.imgur.com/oEyFJjg.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>


<h3>Step 4: Install osTicket v1.15.8</h3>
     
- Go to Downloads in File Manager, find osTicket v1.15.8 
- Right click on the file and select extract all
	- Open the new osTicket folder
		- Copy the “upload” folder INTO c:\inetpub\wwwroot
		- Rename “upload” to “osTicket”


<p align="center">
<img src="https://i.imgur.com/BpL8IJE.png" height="80%" width="80%" alt="Azure Free Account"/> <img src="https://i.imgur.com/xSJD7yk.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>
 
     

<h3>Step 5: Reload IIS (Open IIS, Restart the server)
</h3>

- Search for Internet Information Services (IIS) and select open
	- Select restart on right hand side 
- On the left, select vm-osticket -> Sites -> Default Website -> osTicket
- On the right, click “Browse *:80”
	- This should open osTicket in your web browser
- Before continuing, reopen IIS.


<p align="center">
<img src="https://i.imgur.com/B8HALYr.png" height="80%" width="80%" alt="Azure Free Account"/> <img src="https://i.imgur.com/DUGnzNk.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>

<h3>Step 6:  Enable Extensions in IIS: Note that some extensions are not enabled
</h3>

- Go back to IIS, Sites -> Default Web Site -> osTicket
- Double-click PHP Manager
- Click “Enable or disable an extension” at the bottom under “PHP Extensions”
- Right click and enable the following
    - php_imap.dll (Might be already enabled)
    - php_intl.dll
    - Php_opcache.dll

 
     
 <p align="center">
<img src="https://i.imgur.com/JYliJVw.png" height="80%" width="80%" alt="Azure Free Account"/> 
</p>

<h3>Step 7:   Refresh the osTicket site in your browser, observe the changes
</h3>

- Intl Extension should now have a green check mark next to it


<p align="center">
<img src="https://i.imgur.com/ByfN2Fd.png" height="80%" width="80%" alt="Azure Free Account"/>



<h3>Step 8: Rename</h3>
 
- Open Windows Explorer and select C:-> inetpub-> wwwroot-> osTicket-> Include and rename.
	- From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
	- To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


<p align="center">
<img src="https://i.imgur.com/DDTR8CD.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Step 9: Assign Permissions: ost-config.php</h3>

- Right click ost-config.php, 
- Open Properties -> Security -> Advanced -> Permissions 
- Select Disable inheritance -> Remove all inherited permissions from this object 

<p align="center">
<img src="https://i.imgur.com/pcFvK9d.png" height="80%" width="80%" alt="Azure Free Account"/>

- Afterwards, Select add -> Select a principal  -> type in "everyone" -> check names-> Select OK
	- Allow everyone full control (check all boxes) -> Select apply -> OK

<p align="center">
<img src="https://i.imgur.com/vUlpzTb.png" height="70%" width=70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/WZrk1F7.png" height="80%" width="80%" alt="Azure Free Services"/>
</p>

  
<h3>Step 10: Continue Setting up osTicket in the browser</h3>

- Go back to browser and click continue
  - Name: Helpdesk
  - Email: whichever email you want
  - First Name: your first name
  - Last Name: your last name
  - Email Address: whichever email you want (needs to be different from the Default Email)
  - Username: user_admin 
  - Password: Password1 
  
<p align="center">
<img src="https://i.imgur.com/1GfpPLs.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Step 11: Download and Install HeidiSQL</h3>

- Head to osTicket Installation Files [link](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
	- Download and install HeidiSQL
- Open HeidiSQL -> Select new at the bottom left corner 
   - User: root
   - Password : Password
- Select Open
- On the left side, right click “Unamed” -> “Create New” -> “Database
- Name it “osTicket” and select OK

 <p align="center">
<img src="https://i.imgur.com/mDBWQ5k.png" height="70%" width="70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/ADJYQyB.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>

<h3>Step 12:  Go back to the browser and continue setting up osTicket by filling out the fields.</h3>


- MySQL Database: osTicket (the one you just created in HeidiSQL)
- MySQL Username: root
- MySQL Password: Password1
- Finally, click Install Now

<p align="center">
<img src="https://i.imgur.com/Npqj9Us.png" height="80%" width="80%" alt="Azure Free Account"/>


🎉Congratulations! You have sucessfully installed osTicket!🎉

<p align="center">
<img src="https://i.imgur.com/F52ypHn.png" height="80%" width="80%" alt="Azure Free Account"/>

<h3>Tips!</h3>

- To create tickets as a user: http://localhost/osTicket/
- To log in as an Admin or help desk professional: http://localhost/osTicket/scp

<h3>Step 13: Cleanup.</h3>

- Go to C: -> inetpub->wwwroot->osTicket->setup
    - Delete the contents in the setup folder
    - Afterwards, delete the setup folder
- Go to C:-->Inetpub-->wwwroot-->osTicket-->include
    - Right click on ost-config.php 
    - Select securities -> Advanced -> Click on everyone -> edit to change permissions
	- Allow everyone to only have read and execute, then select OK -> Apply -> OK
	
 <p align="center">
<img src="https://i.imgur.com/wucT3UN.png" height="70%" width="70%" alt="Azure Free Account"/> <img src="https://i.imgur.com/cPSx6VL.png" height="70%" width="70%" alt="Azure Free Services"/>
</p>	


Click [here](https://github.com/miquelmanaois/osTicket-post-installing) to move on to part 2 of this tutorial!

