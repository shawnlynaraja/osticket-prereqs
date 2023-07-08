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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>


1.) The first thing you are going to want to do is create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Note, you will want to create a virtual machine with atleast 2 vcpus and 16 gbs of memory.

2.) Once you have created your virtual machine you will want to connect to it by using the public ip address the VM is setup with. You will connect using the remote desktop connection app. 
</p>
<br />

<p>
<img src="https://imgur.com/MAhXK2e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://imgur.com/Zf2jw07.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
3.) Once you have connected to your virtual machine you will want to go to your control panel. From the control panel open up programs. Select, Turn Windows features on and off.

<p>
<img src="https://imgur.com/fGXMpx4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/LBGkAw6.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
4.) You will want to install / enable IIS in Windows with CGI and Common HTTP Features
  - World Wide Web Services -> Application Development Features -> 
[X] CGI
[X] Common HTTP Features
  
<p>
<img src="https://imgur.com/LQjw9le.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/pbPeHb1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
***NOTE*** Make sure all Common HTTP Features are checked.
 
 To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1 
  It should look something like this. 
  
<p>
<img src="https://imgur.com/eICujoq.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
  
  
5.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
  Go through the install wizard and complete the install.
  
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/9012cd7d-03f3-4a06-b386-cba05bc86d77)

  
6.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/7621c255-df8c-4d78-b5ec-d6ac4f803bf5)

7.) Create a folder in the C drive called PHP. Create the directory C:\PHP
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/ea227d37-585e-47eb-962d-d00d612963a9)

  
8.) From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86) and unzip the contents into C:\PHP
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/672bb8ce-0518-4412-a522-523a1b3855e8)
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/0e3c1690-ea60-4372-b820-164f9f80d29d)


  
  !! ATTENTION !!
If this appears, choose to “Keep” the file:
  
<p>
<img src="https://imgur.com/xZv1Yhw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/YwBhqo0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

9.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe. 

![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/733c2cf8-70b1-492a-9a1c-85cea3b749b2)


  
10.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/e8b680d5-9304-4fb1-923d-9abbc85498d4)

![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/fc013cfb-0b42-4282-b6b9-7ff7c5d1058a)



  Your Username is Root & Make the new root password: Password1
  
<p>
<img src="https://imgur.com/KxcUy7C.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Execute the process on the next page.
  
<p>
<img src="https://imgur.com/i7sn6hT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Open ISS as an Administrator, and you can see the installations you have downloaded such as the PHP Manager, URL Rewrite, etc

11.) Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator.
  The program should look like this.
  
<p>
<img src="https://imgur.com/rgdZwmM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
12.) We will now want to register PHP from within IIS.
  Click on PHP Manager
  
<p>
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Register new PHP version.
  
<p>
<img src="https://imgur.com/qdbn5zQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
You will want to provide a path to the php executable file (php-cgi.exe)). 
  Go to C Drive -> PHP -> click on php-cgi file.
  
<p>
<img src="https://imgur.com/oJZ0gp9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/5b4e5328-2724-4224-9542-68d4770202bc)


  Restart the IIS server.
  
<p>
<img src="https://imgur.com/CJ3RUbG.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
13.) Install osTicket v1.15.8
  -Download osTicket from the Installation Files Folder
  -Extract and copy "upload" folder to c:\inetpub\wwwroot
  -Within c:\inetpub\root, Rename "upload" to "osTicket"
  

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/235a6d34-ac63-46e1-9123-2c849f199d3c)
  

  
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/68c731de-6336-4a0e-9898-090af530eda0)

  
  
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/20d2757b-7abc-4ac9-9b08-edc44bb95f62)
  
  

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/9b2fb617-c64c-48b9-b5df-97afff3ed76d)
  


  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/4e7bdf41-7f13-419c-ac5c-2d075ef321f9)


Rename the "upload" to osTicket


![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/0fbd4bc5-07a2-478b-97ea-91db9be31310)



  Restard the IIS software again.

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/e7525809-b3ed-4228-8ac6-9c9111353fec)

  

  
14.) On IIS go to sites -> Default -> osTicket
  -On the right, click “Browse *:80”
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/ddaaca95-d92d-4d0c-8844-f331679e3c31)


  
  After clicking that, a link will appear in the browser "osTicket." 
  However, you will notice that some extensions are not enabled on the osTicket browser yet.

![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/5ddce2b6-bfa7-4e17-b8c1-5c9dfb2f96ab)

  
  To enable the extensions:
  -Go back to IIS, sites -> Default -> osTicket
  -Double click PHP manager
  -Click "Enable or disable an extension"
  
<p>
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/uigyKjb.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  We will want to enable three extensions from here.
  
  1.) php_imap.dll
 
  2.) php_intl.dll
  
  3.) php_opcache.dll
  
<p>
<img src="https://imgur.com/cOem7Nb.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  After that, if you refresh the osTicket on your browser, we can see more green color, meaning that they are enabled.
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/1dc05b16-6d6f-4ca5-88ac-da0d4ae429d3)


15.) Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
  Go into the file explorer and search for C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  We are going to rename the ost-sampleconfig.php to ost-config.php

![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/05870d01-6346-4c64-a2f0-157fe3cf85dd)


![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/8a1e9677-d052-4890-aeb2-a5d9ff77ce94)

  
  
  Now that we have renamed the files, right click on the file "ost-config.php and go to properties.
  From there click security, click on advance, and disable the inheritance.
  
  
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/d8e97342-873f-45ca-94a1-9f8e164d6b6e)


  
  Then select Remove all inherited permissions from this object.
  
  Now we will add new permissions.
  
  Click Add
  
<p>
<img src="https://imgur.com/VPZvOdo.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Select a principal
  
<p>
<img src="https://imgur.com/PoGk34d.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
 Type "Everyone" in the box & click "check names" & click ok.
  
<p>
<img src="https://imgur.com/F4H3ppM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Make sure Full Control and all the other boxes are checked.
  
<p>
<img src="https://imgur.com/rbbGqwB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click Apply and Ok.
  
<p>
<img src="https://imgur.com/saRO3y5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
16.) Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
  
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/ea4a65b9-cde0-4dc0-9872-ef280e45ac4b)
  

  Fill out everything in the information-page as required 
  but except the Database Settings at the bottom of the page 
  because we have to install HeidiSQL first. 
  So pause the osTicket Browser installation page for now,
  and come back to it once you installed the HeidiSQL.
  ![ss](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/3c8d5f3d-a294-465c-9e49-a48d86486479)

  Also, make sure you wrote down all your log-in information in a notepad, so you won't forget.

  
  17.) We will want to download and install HeidiSQL from the Installation Files. 
  
<p>
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  When the program is open we will create a new session in it.
  
<p>
<img src="https://imgur.com/g5M1i61.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  We want to make sure the username is root and the password is Password1 then click open.
  
<p>
<img src="https://imgur.com/LEAZNOc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once we are connected to the session we will go back to the browser to finish setting everything up. 
  Under the Database Settings in the browser the username will be root and the password will be Password1.
  
  
  18.) We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". 
  
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/ff7e6719-6430-46f7-8962-1fd11ebdebc2)

  
  
  Name the new database osTicket. 
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/43db0e97-be94-46ff-8ee2-de978f79cae6)
  

  19.) Once we have the new database setup, go back to the osTicket installation browser and under MySQL Database type in "osTicket" and then click Install.

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/0e8897cb-cc16-418e-b0d5-a96cc8125c4e)

  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/7d170c95-e673-4528-9016-cb72feac7e55)



  20.) The last step is to do some clean up. We will want to delete the setup folder in our system. 
  -Delete: C:\inetpub\wwwroot\osTicket\setup
  Only delete the setup folder and nothing else.
  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/6400e982-89be-4dab-833a-03940e12732e)

  
  21.) We then will want to set the permissions back to "Read" only in the ost-config.php file 
  by right clicking it, select properties, select security, click advanced, 


  ![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/8979aa3a-aec9-4b9a-aa1c-2c924bf3490c)
  
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/254c80c8-3369-401a-8f15-c4167d4705ac)

  click everyone, click edit 

  
<p>
<img src="https://imgur.com/wFr0pkK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  only checked Read & Execute, Read, and click apply and ok.
<p>
<img src="https://imgur.com/jsJOPyn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The last step after that is to login to osTicket on the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Congratulations, You have now successfully installed and setup osTicket!
![image](https://github.com/shawnlynaraja/osticket-prereqs/assets/138860791/980705d6-922b-4353-a07a-f9609131ff3f)


Browse to your help desk login page: http://localhost/osTicket/scp/login.php (This is for the Admin log-in & do admin things.)


End Users osTicket URL:
http://localhost/osTicket/ (This is for End-Users, who want to create tickets inside of osTickets. 

 
