# osticket-prereqs

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
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>
Welcome to my first in-depth IT tutorial! To begin we will have to create a Virtual machine using the Microsoft Azure portal(portal.azure.com). We will be using a VM(virtual machine) which is a remote computer. We are using a VM in order to protect our physical machine just in case something malfunctions, and also have a clean slate computer to continually replicate the lab on. Create a resource group and title it "osTicket". Afterwards create a VM with 2-4 CPUs. In this example I will be using 4 CPUs.

<p>
<img src="https://camo.githubusercontent.com/a79d5d7d8a79061b1a47c8b9af68edfd8dc5a12ddf855cc8ac150047ea804332/68747470733a2f2f692e696d6775722e636f6d2f4f506149476f4e2e706e67"Disk Sanitization Steps"/>
</p>

<p>

  Next simply connect to your newly created VM using RDP using the public IPv4 address. If you are a Mac user you will have to download Microsoft Remote Desktop(RDP).
</p>
<br />

<p>
<img src="https://camo.githubusercontent.com/42dd9887098b27ff54b58f5009e143937e72a7fe2bb22f2d1a5e0428d537c9d2/68747470733a2f2f692e696d6775722e636f6d2f754c564b7a78532e706e67"Disk Sanitization Steps"/>
</p>
<p>
Alright, now that you are connected to your VM you will have to enable IIS. Simply access the control panel then select uninstall a program. Off to the left select "Turn windows features on or off". A list will appear then you will enable Internet Information Services.
</p>
<br />

<p>
<img src="https://camo.githubusercontent.com/5b33636bf9631e4dd4a359fbe3658f491b42c3c43cb787638537c13b5b7358d8/68747470733a2f2f692e696d6775722e636f6d2f7174456e7557752e706e67"Disk Sanitization Steps"/>
</p>
<p>
Excellent. Now that you have enabled IIS we need to install Web Platform Installer. I have provided a link here: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 That link will provide you with all of the material you need to download to get osTicket up and running. Simply click the link and install the Web
</p>
<br />

<p>
<img src="https://camo.githubusercontent.com/dace16bc34d0e0b6e94ad2d41a59f8fd51f1f8f8156de85feab827c565330a96/68747470733a2f2f692e696d6775722e636f6d2f417848436651362e706e67"Disk Sanitization Steps"/>
</p>
<p>
Once you have installed Web Installer Platform open it. From inside the application you are going to install MySQL 5.5 Afterwards install x86 version of PHP up until 7.3. There are some failed files such as C++ redistributable package as well as PHP 7.3.8 and PHP Manager for IIS those files can be found with the install link.

<p>
<img src="https://camo.githubusercontent.com/fc49c6aac993694d74a89b0767c3e48698e7319b3e2a46a3591dc621e648a85b/68747470733a2f2f692e696d6775722e636f6d2f4a4a38625a654a2e706e67"Disk Sanitization Steps"/>
</p>

Next download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot. Afterwards rename the folder to osTicket

<p>
<img src="https://camo.githubusercontent.com/9bc12af66ae526b5e9ac382f00821d2711350408fab1aa9d2fff61fe55d4d488/68747470733a2f2f692e696d6775722e636f6d2f54554769534b692e706e67"Disk Sanitization Steps"/>
</p>

Open IIS Manager and restart the server. Once inside IIS manager go to Sites->Default->osTicket on the right, click "Browse*.80" from there your default browser should open osTicket webserver.

<p>
<img src="https://camo.githubusercontent.com/187e967bbdc82077c8b030df98634a7efb7f485989e7fdf05185063dc734b779/68747470733a2f2f692e696d6775722e636f6d2f34416b546b56302e706e67"Disk Sanitization Steps"/>

Go back into IIS manager and enable some extensions. To do this you have to go to Sites->Default->osTicket Then double click on PHP manager. Click on "Disable or enable an extension" Enable "php_intl.dll" & "php_opcache.dll" then refresh the osTicket webserver and obsereve the changes "Intl Extension" should now be enabled.

<p>
<img src="https://camo.githubusercontent.com/df63e4c9a24a7cae64600115976cbba196a898759e21ff2efa95aa0cef30f764/68747470733a2f2f692e696d6775722e636f6d2f41505a675554542e706e67"Disk Sanitization Steps"/>

Go back into c:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php rename the file to c:\inetpub\wwwroot\osTicket\include\ost-config.php Assign permissions to ost-config.php Disable inheritance->Removeall New Permissions->Everyone->all

<p>
<img src="https://camo.githubusercontent.com/f183cf6652b574ae99ea745333961613a309ba7795e415a101becb927b2bb45a/68747470733a2f2f692e696d6775722e636f6d2f316e59615947652e706e67"Disk Sanitization Steps"/>

Afterwards continue setting up osTicket in the browser (click continue) then you will name the Helpdesk to your liking. Select a default email that will receive emails from customers who submit tickets.

<p>
<img src="https://camo.githubusercontent.com/758d3bb0c9a27ce62a83eeea343a6d0464ce41ceb4f5f42784e418d56c0165e8/68747470733a2f2f692e696d6775722e636f6d2f526d566b3371352e706e67"Disk Sanitization Steps"/>

Continue Setting up osticket in the browser MySQL Database: osTicket MySQL Username: root MySQL Password: Password1 Click “Install Now!” Congratulations, hopefully it is installed with no errors! Clean up Delete: C:\inetpub\wwwroot\osTicket\setup Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)
