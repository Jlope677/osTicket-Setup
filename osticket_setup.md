# osTicket Setup on Azure VM

This project documents my hands-on experience setting up **osTicket**, an open-source help desk system, inside an Azure Virtual Machine. I included pictures along the way to show the exact steps I took, and I’ll share what I learned from each part.

---

## 1. Creating the Azure Virtual Machine
I first created a **Windows 10 VM** in Azure with 4 vCPUs. I named it:
```bash
osticket-vm
```
Set the username and password:
```bash
Username: labuser
Password: osTicketPassword1!
```
After creating it, I logged in using Remote Desktop.

<img width="1915" height="832" alt="creating the virtual machine" src="https://github.com/user-attachments/assets/6a4af409-3efd-4f6f-8075-065164a93708" />
<img width="1910" height="788" alt="creating the virtual machine2" src="https://github.com/user-attachments/assets/775c37f7-2463-4c65-ba98-8b0bdfa13416" />
<img width="1513" height="788" alt="creating the virtual machine3" src="https://github.com/user-attachments/assets/c5d5347c-bbe9-44e4-8404-e0241f90d6a9" />
<img width="1072" height="940" alt="creating the virtual machine4" src="https://github.com/user-attachments/assets/a9196d61-65e5-4ebc-9564-8897fc4f08ef" />
<img width="1544" height="848" alt="create vm Password(osTicketPassword1!)" src="https://github.com/user-attachments/assets/deaa2c68-4e32-444c-ab0a-1475f0680d31" />
<img width="1073" height="830" alt="create vm" src="https://github.com/user-attachments/assets/36d70136-fc1a-4079-b585-503981b3eeaf" />






**From this I learned:** how to provision an Azure VM, configure resources, and connect remotely using RDP.

---

## 2. Preparing the Environment
I then downloaded and unzipped:
```bash
osTicket-Installation-Files.zip
```
to my desktop. Inside this folder, I began installing dependencies:
- Enabled IIS with CGI:
```bash
World Wide Web Services -> Application Development Features -> [X] CGI
```
- Installed:
```bash
PHPManagerForIIS_V1.5.0.msi
rewrite_amd64_en-US.msi
```

📸 *Screenshot of IIS feature selection and installs*

**From this I learned:** the importance of preparing the environment correctly before installing dependencies. IIS with CGI is required for PHP applications.

---

## 3. Installing PHP and MySQL
I created:
```bash
C:\PHP
```
and extracted:
```bash
php-7.3.8-nts-Win32-VC15-x86.zip
```
into it. After that, I installed:
```bash
VC_redist.x86.exe
```
Then I installed:
```bash
mysql-5.5.62-win32.msi
```
with settings:
```bash
Username: root
Password: root
```

📸 *Screenshot of PHP folder and MySQL installation*

**From this I learned:** how PHP and MySQL work together to support web applications like osTicket.

---

## 4. Configuring IIS
I opened IIS and registered PHP:
```bash
C:\PHP\php-cgi.exe
```
I restarted IIS to apply the changes. Then I unzipped:
```bash
osTicket-v1.15.8.zip
```
Copied the folder:
```bash
upload
```
into:
```bash
C:\inetpub\wwwroot
```
And renamed it:
```bash
osTicket
```

📸 *Screenshot of IIS setup and osTicket folder*

**From this I learned:** how to integrate PHP with IIS and host a web application.

---

## 5. Enabling PHP Extensions
I went back into IIS, opened PHP Manager, and enabled the following extensions:
```bash
php_imap.dll
php_intl.dll
php_opcache.dll
```
After enabling them, I refreshed the osTicket site in the browser and observed the changes.

📸 *Screenshot of PHP extensions being enabled*

**From this I learned:** how PHP extensions extend functionality and why enabling the correct ones is critical.

---

## 6. Configuring osTicket
I renamed the file:
```bash
C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
```
to:
```bash
C:\inetpub\wwwroot\osTicket\include\ost-config.php
```
Then I assigned permissions:
```bash
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
```
After that, I continued the setup in the browser, naming the helpdesk and setting a default email.

📸 *Screenshot of config file permissions and web setup*

**From this I learned:** how to handle configuration files securely and set up osTicket properly.

---

## 7. Setting Up Database with HeidiSQL
I installed:
```bash
HeidiSQL
```
Created a new session with:
```bash
Username: root
Password: root
```
Connected and created a database:
```bash
osTicket
```
Then I went back to the osTicket browser setup and entered:
```bash
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
```

📸 *Screenshot of HeidiSQL with osTicket DB setup*

**From this I learned:** how to create and connect a MySQL database to a web application.

---

## 8. Final Setup
I finished the installation successfully. I was able to log into the staff panel at:
```bash
http://localhost/osTicket/scp/login.php
```
And the end user URL was:
```bash
http://localhost/osTicket/
```

📸 *Screenshot of working osTicket login page*

**From this I learned:** how all the pieces (IIS, PHP, MySQL, and osTicket) work together to deliver a functioning help desk system.

---

## ✅ Conclusion
This project helped me understand the **full deployment process of a web application** on Windows Server using IIS, PHP, and MySQL. Setting up osTicket gave me experience with:
- Web server administration
- Database configuration
- Application troubleshooting

It was a great hands-on project that ties directly into system administration and IT support skills.
