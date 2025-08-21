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
<img width="1544" height="848" alt="create vm Password(osTicketPassword1!)" src="https://github.com/user-attachments/assets/deaa2c68-4e32-444c-ab0a-1475f0680d31" />
<img width="1072" height="940" alt="creating the virtual machine4" src="https://github.com/user-attachments/assets/a9196d61-65e5-4ebc-9564-8897fc4f08ef" />
<img width="1073" height="830" alt="create vm" src="https://github.com/user-attachments/assets/36d70136-fc1a-4079-b585-503981b3eeaf" />
<img width="1892" height="752" alt="remote desktop" src="https://github.com/user-attachments/assets/8c466dfe-f881-42c0-90c7-6ad916deca05" />
<img width="1570" height="924" alt="initial windows configuration" src="https://github.com/user-attachments/assets/e34cc44d-aaab-4135-b17e-8982ca21abd5" />








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

**unzipping File**

<img width="691" height="609" alt="extract file" src="https://github.com/user-attachments/assets/fe21b56d-cff5-490d-a1d5-48f4218dd048" />
<img width="1455" height="760" alt="extract file2" src="https://github.com/user-attachments/assets/5b7b40dc-7a32-41c3-874e-0fb570a96c66" />
<img width="868" height="635" alt="extract3" src="https://github.com/user-attachments/assets/e12d372b-89ba-4641-91a1-8fc8e1295d4c" />

**Enabling IIS with CGI**
<img width="1488" height="782" alt="control panel1" src="https://github.com/user-attachments/assets/83b0f4e8-4730-4432-a1ec-f15dde967530" />
<img width="560" height="505" alt="control panel2" src="https://github.com/user-attachments/assets/42025e1a-b466-4749-8f01-094a394fcf6d" />
<img width="1328" height="999" alt="webserver turned on" src="https://github.com/user-attachments/assets/b22a7440-bebc-4d07-81c7-d75eea4c74f7" />


**Installing PHPManagerForIIS_V1.5.0.msi**
<img width="1486" height="798" alt="php installation" src="https://github.com/user-attachments/assets/fec74360-9e53-415b-ac63-bbbe0016b5dc" />

**Installing rewrite_amd64_en-US.msi**
<img width="1493" height="817" alt="rewrite" src="https://github.com/user-attachments/assets/113b088b-d9d0-40d5-9d2d-8eff5228b92a" />
<img width="634" height="509" alt="rewrite2" src="https://github.com/user-attachments/assets/47c7100a-e54c-451b-9e09-72a365eabd83" />








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

<img width="1505" height="827" alt="new php file" src="https://github.com/user-attachments/assets/5b202cf3-721b-4a60-bf4b-3f94b9e3a288" />
<img width="904" height="678" alt="click it" src="https://github.com/user-attachments/assets/016e49ec-4d47-4fef-afa0-24e069b8107d" />
<img width="848" height="641" alt="php to c1" src="https://github.com/user-attachments/assets/15c56153-f570-49f2-bbdf-f210e7e51868" />
<img width="1016" height="650" alt="php to c2" src="https://github.com/user-attachments/assets/da85b80e-d192-4f93-8183-6cb5c750763b" />
<img width="823" height="642" alt="php to c3" src="https://github.com/user-attachments/assets/320302a6-61df-4d95-9520-02ba7eab0bd1" />






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

<img width="868" height="561" alt="osticket1" src="https://github.com/user-attachments/assets/c89ff47d-85e9-4616-80eb-56d0a5fd2834" />
<img width="1475" height="751" alt="osticket2" src="https://github.com/user-attachments/assets/2eb9b625-3ede-4eae-a66d-ca34cfc56d59" />
<img width="1441" height="764" alt="osticket3" src="https://github.com/user-attachments/assets/02e7efb6-273e-4ebc-a88a-bf341d64e8a4" />
<img width="1784" height="1004" alt="osticket4" src="https://github.com/user-attachments/assets/52423658-5da4-46b0-b84d-e6d3c7fa160b" />
<img width="1474" height="778" alt="renamed upload to osticket" src="https://github.com/user-attachments/assets/bdef3b0b-e129-48e0-af70-5adc5c9f64a8" />






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

<img width="1517" height="792" alt="fixing the xs1" src="https://github.com/user-attachments/assets/dcb5aef4-ae5a-404e-9cf1-d56e567914a3" />
<img width="1467" height="763" alt="fixing the xs2" src="https://github.com/user-attachments/assets/6ecf0d4b-bdd6-4177-bfcf-fbe9beb4cbc3" />
<img width="1274" height="628" alt="fixing the xs3" src="https://github.com/user-attachments/assets/728ca89a-4fae-4828-89c4-fd73ba65ebf2" />
<img width="1456" height="602" alt="fixing the xs4" src="https://github.com/user-attachments/assets/576df0a1-348e-450e-b6f6-0f0dcd9b6f4a" />
<img width="1084" height="888" alt="fixing the xs5" src="https://github.com/user-attachments/assets/a11c724e-801d-4f94-b5f8-d53cf19e1340" />





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

**ost-config.php file configurations**
<img width="1510" height="805" alt="rename ostsample" src="https://github.com/user-attachments/assets/8780caed-5800-491c-89a1-e02656d59f29" />
<img width="1462" height="812" alt="rename ostsample2" src="https://github.com/user-attachments/assets/4b1fcb6b-25b8-4d75-a241-89b3a7d9c6bc" />
<img width="1620" height="1002" alt="ost-config properties" src="https://github.com/user-attachments/assets/27787107-fe9e-4b67-a9c1-77ad037df11b" />
<img width="643" height="689" alt="ost-config properties2" src="https://github.com/user-attachments/assets/9783c709-e65c-44d1-a43c-a4cdc9da3100" />
<img width="1108" height="665" alt="ost-config properties3" src="https://github.com/user-attachments/assets/52f409e3-5b87-4b85-bef8-bef968f28ee5" />
<img width="1084" height="702" alt="ost-config properties4" src="https://github.com/user-attachments/assets/90c0d61e-9ff9-430d-9d9d-d9bb4a24888a" />
<img width="1080" height="675" alt="ost new permissions" src="https://github.com/user-attachments/assets/4f197f1f-a5e9-4137-9060-653b545868ef" />
<img width="1279" height="762" alt="ost new permissions2" src="https://github.com/user-attachments/assets/3a7ced0d-6d92-40c8-bd0b-7e0fc206f2bd" />
<img width="1360" height="835" alt="ost new permissions3" src="https://github.com/user-attachments/assets/f48998e1-7800-423c-946d-5cce58296c1d" />
<img width="1360" height="835" alt="ost new permissions3" src="https://github.com/user-attachments/assets/6737cbab-f8b0-46a5-bfd4-c9ab05705c38" />

**ost configurations continue**
<img width="1193" height="929" alt="ost setup continue" src="https://github.com/user-attachments/assets/5667fc61-e15b-4ee5-a6c2-d7cac0c639cd" />
<img width="544" height="869" alt="osticket basic1password(Password1)" src="https://github.com/user-attachments/assets/c570e743-835a-4018-9dc5-5bef35ccce80" />








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

<img width="1532" height="839" alt="heidiinstallation" src="https://github.com/user-attachments/assets/86f5967c-d7b5-4cad-93bd-e6addae6968a" />
<img width="788" height="654" alt="heidiinstallation2" src="https://github.com/user-attachments/assets/d3e29b63-d169-403f-99f4-4ebe406f67a7" />
<img width="1028" height="689" alt="heidiinstallation3 password(root)" src="https://github.com/user-attachments/assets/cf567581-0cf4-49b4-a71b-ed9c92aee602" />
<img width="1414" height="772" alt="heidiinstallation4" src="https://github.com/user-attachments/assets/ea6f0d87-1a0f-4120-9ea6-4f6cb0280afb" />
<img width="1380" height="780" alt="heidiinstallation5" src="https://github.com/user-attachments/assets/ba6f40d4-2e2b-4d6e-ba0f-858d8e78ebd1" />
<img width="1181" height="869" alt="back to basic installations" src="https://github.com/user-attachments/assets/ef7d990b-a8c2-487f-aeb3-fac7eec5e4d1" />
<img width="1920" height="949" alt="heidi osticket created files" src="https://github.com/user-attachments/assets/ca071aee-3800-429b-af18-2427f1a7f434" />









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

<img width="1175" height="855" alt="osticket installed" src="https://github.com/user-attachments/assets/0998b0f0-a46e-4a5a-9231-eaa3302c1eff" />
**Staff panel**
<img width="1292" height="859" alt="osticket login" src="https://github.com/user-attachments/assets/6059df36-40db-4519-99d1-42da16d8c379" />
<img width="1449" height="525" alt="osticket login2(password)" src="https://github.com/user-attachments/assets/173c218f-c279-4ce5-861d-436a61c0da8d" />
**end user URL**

<img width="1259" height="679" alt="for end users" src="https://github.com/user-attachments/assets/e37466fb-9ac7-4707-98f3-0f5571b465e5" />



**From this I learned:** how all the pieces (IIS, PHP, MySQL, and osTicket) work together to deliver a functioning help desk system.

---

## ✅ Conclusion
This project helped me understand the **full deployment process of a web application** on Windows Server using IIS, PHP, and MySQL. Setting up osTicket gave me experience with:
- Web server administration
- Database configuration
- Application troubleshooting

It was a great hands-on project that ties directly into system administration and IT support skills.
