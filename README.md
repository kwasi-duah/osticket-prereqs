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

<h2>Important Prerequisites</h2>

- Establish a Virtual Machine connection with Remote Desktop
- Install Internet Information Server in Windows
- Download Web Platform Installer
- Download and Setup lattest versionof osTicket
- Install HeidiSQL
- Setup Database for osTicket
- Clean up Files
- Set File Permission

<h2>Installation Steps</h2>

<p>
Create a Virtual Machine and Resource Group
search for "Virtual Machine" in Azure. When creating the Virtual Machine (VM), you’ll see an option to create a Resource Group. Think of a Resource Group as a folder that keeps everything for this project in one place.

Click Create New and name the Resource Group RG-osTicket (this is like naming your folder).
Follow the steps to set up the Virtual Machine using the settings shown below.

Create a Windows 10 Virtual Machine with 2 or 4 virtual cpus to ensure that there are no slowdowns and eveything runs smootly in the lab. Let the VM create a vnet which should be done by default.
This step gets everything ready so we can build and run osTicket on the Virtual Machine!

<img width="1438" alt="Screenshot 2025-01-10 at 6 56 29 PM" src="https://github.com/user-attachments/assets/5e2bc818-64f9-44f2-a9fe-7d1b45cd6f38" />

</p>
<br />

<p>
We will need connect to our Virtual Machine with Remote Desktop using the VM's public IP address.
  
  <img width="1439" alt="Screenshot 2025-01-10 at 7 26 18 PM" src="https://github.com/user-attachments/assets/aab4c4cb-f92d-4504-ba49-b548ee26e67c" />
  
</p>

<p>
Connect to the Virtual Machine
On your computer, search for "Remote Desktop Connection" (or download it if you don’t have it).
Open the Remote Desktop app. Click add a PC a window will pop up where you can type something.
Copy the public IP address of your Virtual Machine and paste it into the box.
Click the Connect button, and you’re now connected to your Virtual Machine!

<img width="1282" alt="Screenshot 2025-01-10 at 7 43 36 PM" src="https://github.com/user-attachments/assets/24a169ca-daf6-4e6a-aaa3-218d5efb5d40" />

</p>

<p>
  Install and Enable IIS in Windows
here’s how to turn on IIS (Internet Information Services) on your computer:

Go to the Search Bar and type "Control Panel".
Open Control Panel and click on "Programs".
Click "Turn Windows features on or off" (you’ll see a list of features).
Scroll down and find "Internet Information Services (IIS)".
Check the box next to IIS, then click OK to install it.

![image](https://github.com/user-attachments/assets/4cf2cd9c-0ae6-4339-a50f-9c5aadcddcfd)

</p>

<p>
Enable CGI for IIS
After turning on IIS, find "Internet Information Services" in the list and click the little arrow to expand it.
Next, expand "World Wide Web Services".
Then, expand the "Application Development Features" tab.
Check the box next to "CGI" and click OK.
You need CGI so you can install PHP Manager, which helps IIS run PHP. PHP is like the "engine" that makes osTicket work in a web browser.

![image](https://github.com/user-attachments/assets/7d6010c9-ea42-4264-b0ee-a6e3aee71ace)  
</p>

<p>
 Now i'ts time to download all our dependencies <a href="https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD">osTicket Installation Files</a> click the link download and unzip the file.
Download the PHP Manager file.
Open it and agree to all the terms (just click "Next" and "Agree").
That’s it! Now PHP Manager is installed on your computer.
PHP Manager helps the web server (IIS) understand and run PHP, which is super important for osTicket to work!
  
  ![image](https://github.com/user-attachments/assets/e8a58a58-b0d1-4eea-98d2-326d1b17648e)
</p>
<p>
 Install Rewrite Module
Download the Rewrite Module file.
Open it and agree to all the terms (just click "Next" and "Agree").
That’s it! The Rewrite Module is now installed on your computer.
The Rewrite Module helps the web server (IIS) handle links and URLs properly, which is important for running web applications like osTicket!

![image](https://github.com/user-attachments/assets/244b8eda-bdb0-4876-9fb6-99ab1c6dadf7)


</p>
<p>
  Create a PHP Folder and Extract PHP Files
Open File Explorer and type "C:" in the search bar at the top.
Right-click anywhere in the window and choose "New Folder".
Name the folder "PHP".
Next:

Download the php-7.3.8-nts-Win32-VC15-x86.zip file.
Go to where the file was downloaded, right-click on it, and choose "Extract".
Extract the files into the PHP folder you just created.

![image](https://github.com/user-attachments/assets/27fd7b0c-02cf-45be-89fb-d4a7c0fe1a2c)

</p>
<p>
  Install VC_Redist
Download the VC_Redist file.
Open it, agree to any terms (just click "Next" or "Agree").
Finish the installation by following the steps.
  
  ![image](https://github.com/user-attachments/assets/8ac74088-d744-41a5-8ab2-4e6887a12bb0)

</p>
<p>
  Install MySQL
Download the MySQL file and open it.
Agree to the terms (just click "Next" or "Agree") until you reach the password section.
Here, create a username (like "root") and a password (something you can remember). This will be used to store all the ticket information for osTicket.
Now MySQL is ready to use for storing your osTicket data.
  
  ![image](https://github.com/user-attachments/assets/6488efec-28e8-4df6-99ef-cfd4fa582bd6)
  <br>
  ![image](https://github.com/user-attachments/assets/ef248d6f-c617-4b06-bccc-123c1d42befc)

</p>
<p>
  Install osTicket v1.15.8
Download the osTicket file (from the lab files provided).
Open the downloaded file and extract it.
Find the "upload" folder and copy it.
Go to C:\inetpub\wwwroot on your computer and paste the "upload" folder there.
This sets up the files needed to run osTicket on your web server

  ![image](https://github.com/user-attachments/assets/1bcd1f49-5934-490d-8a0a-382427a1db55)
  ![image](https://github.com/user-attachments/assets/c3b2ba69-486a-49be-be0b-10fc15369b69)


</p>
<p>
  Go to C:\inetpub\wwwroot.
Find the folder named "upload".
Right-click on it and select "Rename".
Change the name to "osTicket".
This helps the server know where to find the osTicket files.

  ![image](https://github.com/user-attachments/assets/fd1867ad-8769-449b-bcaf-a3d6eecae13c)

</p>

<p>
  Reload IIS and Open osTicket
Open IIS (Internet Information Services).
Stop the server, then start it again (this is like turning it off and back on to refresh it).
Next:

In IIS, go to Sites -> Default -> osTicket.
Now you’re ready to see osTicket in action.

![image](https://github.com/user-attachments/assets/c7257e0e-2c08-4f13-b28b-6179951dc12f)

</p>
<p>
  Open osTicket in Your Browser
In IIS, look to the right side of the screen.
Click on "Browse *:80".
This opens osTicket in your web browser so you can start setting it up

  ![image](https://github.com/user-attachments/assets/734c902b-53e4-463d-bd79-d904031a639b)

</p>

<p><strong>Enable Extensions in IIS:</strong> Note that some extensions are not enabled.</p>

<p>1. Go back to IIS and navigate to <strong>Sites -> Default -> osTicket</strong>.</p>  
<p>2. Double-click on <strong>PHP Manager</strong>.</p>  
<p>3. Click <strong>“Enable or disable an extension”</strong>.</p>  
<p>4. Enable the following extensions:  
   - <strong>php_imap.dll</strong>  
   - <strong>php_intl.dll</strong>  
   - <strong>php_opcache.dll</strong>
    
  ![image](https://github.com/user-attachments/assets/f3d9ffc7-ea62-4c44-8a3c-f1e1c16bbdb4)
  
![image](https://github.com/user-attachments/assets/3fe1e688-1a8a-4e7a-b23c-0d90f96769bb)
</p>  
<p>5. Refresh the osTicket site in your browser and observe the changes.

![image](https://github.com/user-attachments/assets/4c3daf1c-cdc8-43ef-9622-0615ece8372c)

</p>  

<p><strong>Rename Configuration File:</strong></p>  
<p>1. Navigate to <strong>C:\inetpub\wwwroot\osTicket\include</strong>.</p>  
<p>2. Rename <strong>ost-sampleconfig.php</strong> to <strong>ost-config.php</strong>.
  
  ![image](https://github.com/user-attachments/assets/bef887bc-ba01-49e0-8fc9-840276dad7c8)
</p>  

<p><strong>Assign Permissions to ost-config.php:</strong></p>  
<p>1. Disable inheritance for the file and remove all existing permissions. 
  
  ![image](https://github.com/user-attachments/assets/fd051068-2fad-433e-b9bd-63ed6502349b)
</p>  
<p>2. Add new permissions:  
   - Assign <strong>Everyone</strong> with <strong>Full Control</strong>.
  
  ![image](https://github.com/user-attachments/assets/de16901b-59a9-4eb7-9b6e-debbae07ce3e)

  ![image](https://github.com/user-attachments/assets/f17bf9f4-0002-4a76-a709-cd0471119f7c)

</p>  

<p><strong>Set Up osTicket in the Browser:</strong></p>  
<p>1. Continue the setup by filling in the required details, like:  
   - Helpdesk Name  
   - Default email address (to receive customer emails).
  
  ![image](https://github.com/user-attachments/assets/496b7027-1069-4a83-81d4-4eb9957ca524)
  ![image](https://github.com/user-attachments/assets/ac33a6f9-c164-4604-8bcb-03ed97a77575)
</p>  

<p><strong>Download and Install HeidiSQL:</strong></p>  
<p>1. Install HeidiSQL on your system.
  
  ![image](https://github.com/user-attachments/assets/16477e69-6b12-4f14-8a39-059d509c8ecc)
</p>  
<p>2. Open HeidiSQL and create a new session using the credentials:  
   - Username: <strong>root</strong>  
   - Password: <strong>Password1</strong>.
  
  ![image](https://github.com/user-attachments/assets/44fa044e-7bd0-4ada-9f2d-02aeee4acd16)
</p>  
<p>3. Connect to the session and create a new database called <strong>“osTicket”</strong>.
  
  ![image](https://github.com/user-attachments/assets/437092ea-3eab-46b7-b3bb-e65be75d43c3)
</p>  

<p><strong>Finish Setting Up osTicket in the Browser:</strong></p>  
<p>1. Enter the following database information:  
   - MySQL Database: <strong>osTicket</strong>  
   - MySQL Username: <strong>root</strong>  
   - MySQL Password: <strong>Password1</strong>.
  
  ![image](https://github.com/user-attachments/assets/808bf3e5-f56e-43b4-8deb-8f93f75dd34d)
</p>  
<p>2. Click <strong>“Install Now!”</strong> and complete the installation.
  
  ![image](https://github.com/user-attachments/assets/eebd72c4-1a05-4b07-a0bf-751e51b55c4b)
</p>  

<p><strong>Clean Up:</strong></p>  
<p>1. Delete the <strong>C:\inetpub\wwwroot\osTicket\setup</strong> folder.
  
  ![image](https://github.com/user-attachments/assets/fc0bf2a9-4f8c-45d1-bbcf-01b0a44b50e0)
</p>  
<p>2. Set the permissions of <strong>C:\inetpub\wwwroot\osTicket\include\ost-config.php</strong> to <strong>Read Only</strong>.
  
  ![image](https://github.com/user-attachments/assets/1c32f49c-f5c2-4287-a112-57fc1e0101f4)
</p>  

<p><strong>Log In to osTicket Admin Panel:</strong></p>  
<p>1. Go to <strong>http://localhost/osTicket/scp/login.php</strong> in your browser.
  
  ![image](https://github.com/user-attachments/assets/2117adba-6275-430a-9573-ff6195b3e47a)
</p>  

<p><strong>Congratulations!</strong> You've successfully installed osTicket.</p>
