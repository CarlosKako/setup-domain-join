<p align="center">
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d2d91604-6d56-4e1d-b542-4cd7fad6f812" />
</p>

<h1>Active Directory — Installation, Domain Setup, and Domain Join</h1>
This project demonstrates installing Active Directory Domain Services on DC-1, promoting it to a Domain Controller, creating Organizational Units and a domain admin account, and joining Client-1 to the domain. This builds directly on the Azure infrastructure configured in the previous project.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop Protocol (RDP)
- Active Directory Domain Services (AD DS)
- Windows Server 2022

<h2>Operating Systems Used</h2>

- Windows Server 2022 (DC-1)
- Windows 10 Pro (21H2) (Client-1)

<h2>High-Level Steps</h2>

1. Install Active Directory Domain Services on DC-1
2. Promote DC-1 to a Domain Controller
3. Create Organizational Units in Active Directory
4. Create a Domain Admin user account
5. Join Client-1 to the domain

---

<h2>Step 1 — Install Active Directory Domain Services</h2>

<p>
<img width="1641" height="754" alt="image" src="https://github.com/user-attachments/assets/f4729da8-6751-45a8-a21d-8e70f7bde2c8" />
</p>
<p>
I RDP'd into DC-1 and opened Server Manager. I clicked Add Roles and Features, selected Role-based installation, and chose Active Directory Domain Services. I proceeded through the wizard and completed the installation.
</p>
<br />

---

<h2>Step 2 — Promote DC-1 to a Domain Controller</h2>

<p>
<img width="1428" height="756" alt="image" src="https://github.com/user-attachments/assets/022a6880-410a-43cc-baf2-ff3fb0ca146f" />
</p>
<p>
After installation, a yellow notification flag appeared in Server Manager. I clicked Promote this server to a domain controller and selected Add a new forest. I set the root domain name to mydomain.com and configured a DSRM password. After completing the wizard, DC-1 restarted automatically. After the reboot, I logged back in using domain credentials: mydomain.com\labuser
</p>
<br />

---

<h2>Step 3 — Create Organizational Units</h2>

<p>
<img width="754" height="527" alt="image" src="https://github.com/user-attachments/assets/65373373-82b0-41e6-9652-b4f75f0d1482" />
</p>
<p>
I opened Active Directory Users and Computers (ADUC). I right-clicked the domain and created two new Organizational Units:
</p>

- _EMPLOYEES — will hold standard domain user accounts
- _ADMINS — will hold privileged administrator accounts

<p>
Organizing accounts into OUs allows Group Policy and permissions to be applied at a granular level.
</p>
<br />

---

<h2>Step 4 — Create a Domain Admin Account</h2>

<p>
<img width="1159" height="537" alt="image" src="https://github.com/user-attachments/assets/cc95be60-221b-4cde-8a83-e7607e777d45" />
</p>
<p>
Inside the _ADMINS OU, I created a new user with the following details:
</p>

- Full Name: Jane Doe
- Username: jane_admin
- Password: Cyberlab123!

<p>
After creating the account, I right-clicked Jane's account and added her to the Domain Admins security group. I then logged out of DC-1 and logged back in as mydomain.com\jane_admin. From this point forward, jane_admin is used as the primary admin account for all domain-level tasks.
</p>
<br />

---

<h2>Step 5 — Join Client-1 to the Domain</h2>

<p>
<img width="301" height="153" alt="image" src="https://github.com/user-attachments/assets/08ab9b9c-2683-4b53-ba90-008cbd38b698" />
</p>
<p>
I RDP'd into Client-1 and opened System Properties, then clicked Rename this PC (Advanced) and selected Change. I selected Domain and entered mydomain.com. When prompted for credentials, I entered mydomain.com\jane_admin. Client-1 restarted automatically after joining. After the reboot, I logged into Client-1 using domain credentials to confirm the domain join was successful.
</p>
<br />

---

<h2>Conclusion</h2>

Active Directory is now fully installed and operational. DC-1 is promoted as the domain controller for mydomain.com, Organizational Units are structured for employees and admins, a dedicated domain admin account has been created, and Client-1 has been successfully joined to the domain. The environment is ready for user provisioning and policy configuration in the next project.
