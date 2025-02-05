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

- osTicket Installation Files
- Azure Cloud Compute with VM Setup

  Here is an explanation detailing the dependencies and how it interacts with osTicket:

HeidiSQL: a free and open-source database management tool for MySQL (another dependency we will use) to create and maange the MySQL database that osTicket uses to store all ticket data, user information, configurations, etc.

MySQL: a database management system that osTicket uses to store and retrieve all of its data; essential for providing the backend storage of all osTicket information; allowing efficient querying and management of ticket data; enabling data persistence across server restarts

PHP Manager: a tool for configuring and managing PHP settings in IIS to allow easy configuratiion of PHP settings required by osTicket, and enables management of PHP extensions by osTicket such as php_imap.dll and php_intl.dll

URL Rewrite Module: allows the creation of cleaner, more user-friendly URLs

Visual C++ Redistributable: Contains runtime components of Visual C++ libraries; common to have installed on your home computer as it contains libraries of C++ functions such as math functions, input/output operations, and memory management.

<h2>Installation Steps</h2>

First, download the provided osTicket Installation files. This will contain the necessary dependencies osTicket requires for us to use it in our VM. We will download those files onto our desktop and extract the files there. Note: this tutorial is made for a VM test environment so some of the configurations are not ideal in a real-world enterprise setting

Next, we're going to enable IIS (Internet Information Services) Navigate to your Control Panel > Programs > Programs & Features

Make sure "Internet Information Services" is checked, and "CGI" is checked:<p>
![1](https://github.com/user-attachments/assets/3cf04257-1eda-4f19-99cf-6f1efc49bc36)
![2](https://github.com/user-attachments/assets/1c53ca90-81e6-4ffd-85f8-a007f101f320)
![3](https://github.com/user-attachments/assets/0db6c147-2c0e-48a5-bc32-c5dd805015cb)
</p>
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
![5](https://github.com/user-attachments/assets/33c7f276-1e03-4373-9401-c0e548bb3Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
