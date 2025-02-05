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

- Windows 10 Pro (22H2)</b>

<h2>List of Prerequisites</h2>

- [osTicket Installation Files](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)
- Azure Cloud Compute with VM Setup 
<p>Here is an explanation detailing the dependencies and how it interacts with osTicket:</p>
<p>HeidiSQL: a free and open-source database management tool for MySQL (another dependency we will use) to create and maange the MySQL database that osTicket uses to store all ticket data, user information, configurations, etc.</p>
<p>MySQL: a database management system that osTicket uses to store and retrieve all of its data; essential for providing the backend storage of all osTicket information; allowing efficient querying and management of ticket data; enabling data persistence across server restarts</p>
<p>PHP Manager: a tool for configuring and managing PHP settings in IIS to allow easy configuratiion of PHP settings required by osTicket, and enables management of PHP extensions by osTicket such as php_imap.dll and php_intl.dll</p>
<p>URL Rewrite Module: allows the creation of cleaner, more user-friendly URLs</p> 
<p>Visual C++ Redistributable: Contains runtime components of Visual C++ libraries; common to have installed on your home computer as it contains libraries of C++ functions such as math functions, input/output operations, and memory management. </p>

<h2>Installation Steps</h2>

<p>
First, download the provided osTicket Installation files. This will contain the necessary dependencies osTicket requires for us to use it in our VM. We will download those files onto our desktop and extract the files there. 
  <B>Note: this tutorial is made for a VM test environment so some of the configurations are not ideal in a real-world enterprise setting</B>

</p>
<p>
Next, we're going to enable IIS (Internet Information Services) 
Navigate to your Control Panel > Programs > Programs & Features </p>
Make sure "Internet Information Services" is checked, and "CGI" is checked:
<br />

![1 IIS1](https://github.com/user-attachments/assets/8be9bc4d-8d6f-40eb-b2c9-12c1e2fa1c6d)
![1 IIS2](https://github.com/user-attachments/assets/3b6decd8-2e50-4ab6-a2db-b824385153a2)
![1 IIS3](https://github.com/user-attachments/assets/ab1baf2a-750a-4b91-a499-be65c21cdf59)


<p>
Next we will install PHPmanager and Rewrite Module. Go ahead and go through the installation process by clicking next (we don't need to worry about custom installs or extra files).
</p>

![2 PHP1](https://github.com/user-attachments/assets/88a74252-20ab-48c5-9c95-8ff945246a11)

<p>Next, we must create a directory in our C:\</p>
<p>Navigate to your C:\ and create a new folder titled 'PHP'. This is where we will unzip the php-7.3.8-nts-Win32-VC15-x86.zip file into our PHP folder. </p>

![2 PHP2](https://github.com/user-attachments/assets/a93188fb-ae5c-461f-9c81-46bb3827bd9b)
![2 PHP3](https://github.com/user-attachments/assets/92b38ff2-1773-47d1-9d14-797d3fc73ad3)


<p>
Next, we can go ahead and install our C++ Redistributable and MySQL.</p>
<p>For MySQL setup: Typical Setup > Launch Configuration Wizard (after install) > Standard Configuration > Root password: root ; Confirm: root </p>
<p><b>Note: Normally in an enterprise setting, you would use a much stronger password. In this case, we will simplify things by just using 'root' as our password.</b></p>
<br />

![3](https://github.com/user-attachments/assets/76117f7d-9541-440c-868f-64e4575156e3)
![4](https://github.com/user-attachments/assets/8b934434-d569-4ae8-b85a-e2d1781922c6)
![5](https://github.com/user-attachments/assets/33c7f276-1e03-4373-9401-c0e548bb39e1)


<p>Let's head to IIS and make some configurations. Go to your start menu > search IIS > run as administrator</p>

![6](https://github.com/user-attachments/assets/d2198950-ce5f-4581-9dd9-9a89dd1ad7c6)

<p>
Navigate to PHP Manager > Register new PHP version > browse > navigate to PHP folder and select php-cgi.exe</p>
What we're doing here is making our web server aware of the existence of PHP on the computer.

![7](https://github.com/user-attachments/assets/04823820-3355-4788-8ec3-e278cb152732)
![8](https://github.com/user-attachments/assets/32d2e46f-859e-4f66-88ce-fdcb306415d0)

Next, we will just restart our web server by right-clicking on the server > stop > start

![9](https://github.com/user-attachments/assets/f015999b-5565-4f87-9831-54cf639bb030)
![10](https://github.com/user-attachments/assets/308da89e-772b-4958-9d6b-efb55eea257d)

<br />

<p>
Next, navigate to this directory: C:\inetpub\wwwroot</p>
<p>Open our osTicket Installation Files folder in a separate File Explorer window > right-click 'osTicket-v1.15.8.zip' and extract all > copy the 'upload' folder into C:\inetpub\wwwroot </p>
<p><b>This next step is important: rename 'upload' to 'osTicket' exactly. DO NOT ADD A SPACE OR ALTER CAPITALIZATION</b></p>

![11](https://github.com/user-attachments/assets/42a75956-fe92-45b4-b73c-0ef8dcd46840)
![12](https://github.com/user-attachments/assets/35193668-4f51-4cc6-aa92-60b525e1097f)

<p>Reload IIS > Restart the server by stopping and starting</p>
<p>Next, let's browse our site. Navigate to sites > default > osTicket</p>
<p>On the right, click "Browse *:80"</p>

![13](https://github.com/user-attachments/assets/c32db7c3-b3d4-4085-9057-2c5d9b321440)
And it should look something like this:
![14](https://github.com/user-attachments/assets/19b38aec-3dfb-4870-a2ea-03309dcaf36b)

<p>
You will notice some extensions are disabled. Let's go and enable those.</p>
<p>Back in IIS, navigate to sites > Default > osTicket > Double-click PHP Manager > Click "Enable or disable an extension" > enable "php_imap.dll"; "php_intl.dll"; "php_opcache.dll" </p>
Refresh the osTicket site in your browser and observe the changes

![15](https://github.com/user-attachments/assets/93f17542-0b1e-401e-8bfe-7a07f68004d3)
![16](https://github.com/user-attachments/assets/9dc8c88c-b80c-42d3-a01d-c6b8f8a3381f)
![17](https://github.com/user-attachments/assets/2a481a90-518d-474b-98bd-ce2295f81369)


<br />

<p>Next, we will make changes to a file osTicket uses to make configurations. Open up your File Explorer and navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</p>
<p>
Change/Rename this file to <b>"ost-config.php"</b></p>
Make sure the file is named this exactly!

![18](https://github.com/user-attachments/assets/071cabb8-f34a-4378-8822-0cb2353e9155)

<p>Then we will right-click the file to change permissions. Click Properties > Security tab > Advanced > Disable Inheritance > Remove All > Add > >Select Principal > Everyone > Full Control </p>
Here we allow osTicket to make changes on the backend.
<p><B>Note: In a real-world enterprise setting, you would never give permissions to everyone on your network to make configurations to osTicket! We are just ensuring everything works in this lab setting</B></p>

![19](https://github.com/user-attachments/assets/84dde006-fa94-4455-810b-15eb4e28d48f)
![20](https://github.com/user-attachments/assets/a84db21f-3286-4f81-a05c-78d6120e45bc)

<br />

<p>
Navigate back to your osTicket website and continue on with the installation.</p>
<p>Set up simple system settings. Make sure you remember your username and password as that will be needed in a subsequent step.</p>

![image](https://github.com/user-attachments/assets/b76ceb57-3986-4421-b1a7-ad35503efdcb)
![image](https://github.com/user-attachments/assets/5478a606-5b37-4c81-b256-ff2e74d14b1d)
![image](https://github.com/user-attachments/assets/14e6ce3e-6906-4680-b163-fec5f0282c6c)


<p>Before we continue any further, let's install HeidiSQL. Navigate back to the osTicket Installation Files folder and install HeidiSQL.</p>

![22](https://github.com/user-attachments/assets/ab698524-77c9-47cb-a92a-e7bf3ec025ac)


<p>Create a new session > Type User and Password (from our MySQL Server: root/root) > Open </p>

![22](https://github.com/user-attachments/assets/ef9a7f66-abb1-4105-8cda-3a487fc87922)

<p>This is what we should see. Next, right-click on the new session > Create New > Database > Name: "osTicket" </p>

![23](https://github.com/user-attachments/assets/b7ecff5f-87ec-4ae4-8066-875007cc775b)
![24](https://github.com/user-attachments/assets/c912a3c7-7199-4354-8d22-55039eae0ade)

<br />


<p>
Lastly, we will finish up with our osTicket installation in the browser. </p>

<p>For MySQL Database: osTicket</p>

MySQL Username: root

MySQL Password: root
<p>Click "Install Now"</p>

![image](https://github.com/user-attachments/assets/b76ceb57-3986-4421-b1a7-ad35503efdcb)
![image](https://github.com/user-attachments/assets/5478a606-5b37-4c81-b256-ff2e74d14b1d)
![image](https://github.com/user-attachments/assets/14e6ce3e-6906-4680-b163-fec5f0282c6c)

<p>
We are all setup! If you followed the steps correctly, you should end up at this page.</p>

![26](https://github.com/user-attachments/assets/f6862947-dec2-42d2-af8c-af2829c7d648)


Browse to your help desk login page: http://localhost/osTicket/scp/login.php
![image](https://github.com/user-attachments/assets/0b65353b-2f19-4452-a442-933ea8cc2080)


End Users osTicket URL: http://localhost/osTicket/ 

![image](https://github.com/user-attachments/assets/8879bfd0-4d7a-4416-bcbd-5350f588b752)
![image](https://github.com/user-attachments/assets/63dbc619-96b3-4c3d-ac2f-daaa8999ad1a)



