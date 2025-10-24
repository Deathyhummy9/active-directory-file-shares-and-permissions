<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active directory file sharing and permissions(Azure)</h1>
This lab demonstrates how to configure shared folders with different permission levels, then test access as a normal user to verify restrictions. It also shows how adding a user to a security group grants additional access without directly changing their individual permissions..<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Configuration Steps</h2>
--1 Create Shared Folders on DC-1

--2 Test Access as Normal User

--3 Create ACCOUNTANTS Group

--4 Add User to Group & Retest


Step 1 Create Shared Folders on DC-1
-----------------------------------------

<img width="983" height="706" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/3cf4132f-a27c-441d-8c2e-8508de6117cf" />

Log in as: mydomain.com\jane_admin

Create folders on C:\:
read-access
write-access
no-access
accounting

Share folders and set permissions:
read-access → Domain Users → Read
write-access → Domain Users → Read/Write
no-access → Domain Admins → Read/Write

Step 2 Test Access as Normal User
--------------------------------

<img width="1022" height="581" alt="Screenshot (131)" src="https://github.com/user-attachments/assets/11a923d1-7960-4c8a-98b1-73a6feff1567" />

Log in to Client-1 as: mydomain\(what ever user u chosse)

Navigate to \\dc-1
Test folder access:

read-access → open only
write-access → open & create files
no-access → access denied



Step 3 Create ACCOUNTANTS Group
---------------------------------

<img width="1692" height="997" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/718fd740-88b0-47d0-9018-a5741c3cf808" />

On DC-1:
Open ADUC
Create security group ACCOUNTANTS

On accounting folder:
Share with ACCOUNTANTS group
Set permission → Read/Write
Test access from Client-1: the user should not be able to access yet.

Step 4 Add User to Group & Retest
----------------------------------
On DC-1:

Add <someuser> to ACCOUNTANTS group

On Client-1:

Log off and back in as <someuser>

Test \\dc-1\accounting

Access should now work (Read/Write)

Outcome
------
Proper use of shared folder permissions.

Demonstrates how group membership controls access.

Reinforces security best practices.
