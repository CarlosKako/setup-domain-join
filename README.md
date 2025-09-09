<p align="center">
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d2d91604-6d56-4e1d-b542-4cd7fad6f812" />

</p>

<h1>Active Directory Setup & Domain Join</h1>
In this brief tutorial, we’ll be installing Active Directory, creating a domain, setting up an admin account, and joining a client machine to the domain. <br />



<h2>Environments and Technologies Used</h2>

- Virtualized Lab Environment
- Remote Desktop
- Active Directory Domain Services (AD DS)
- Windows Server 2022
- Networking Services

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<h2>🔑 Prerequisites</h2>

- Two virtual machines: DC-1 → Windows Server 2022 (Domain Controller) Client-1 → Windows 10/11 or Server acting as a client
- Administrator credentials
- Network connectivity
- Static IP configured
- Firewall disabled

<h2>Installing Active Directory and Creating Domain Admins</h2>

<p>
<img width="1641" height="754" alt="image" src="https://github.com/user-attachments/assets/f4729da8-6751-45a8-a21d-8e70f7bde2c8" />

</p>
<p>
Install Active Directory Domain Services

Log in to DC-1 (our domain controller VM). Open Server Manager → Click Add Roles and Features. Choose Role-based or feature-based installation, then select Active Directory Domain Services. Proceed through the wizard and install.
</p>
<br />

<p>
<img width="1428" height="756" alt="image" src="https://github.com/user-attachments/assets/022a6880-410a-43cc-baf2-ff3fb0ca146f" />

</p>
<p>
Promote DC-1 as a Domain Controller

After installation, a yellow flag will appear in Server Manager. Click Promote this server to a domain controller. Select Add a new forest. For the root domain name, type: mydomain.com (you can choose a different name, but remember it). Choose a password for the Directory Services Restore Mode (DSRM). Finish the wizard and restart the server.
➡️ After reboot, log back in as:
mydomain.com\labuser
</p>
<br />

<p>
<img width="754" height="527" alt="image" src="https://github.com/user-attachments/assets/65373373-82b0-41e6-9652-b4f75f0d1482" />

</p>
<p>
Create a Domain Admin User

Open Active Directory Users and Computers (ADUC). Right-click your domain → select New → Organizational Unit.

Name it: _EMPLOYEES

Create another OU named: _ADMINS

</p>
<br />

</p>
<img width="1159" height="537" alt="image" src="https://github.com/user-attachments/assets/cc95be60-221b-4cde-8a83-e7607e777d45" />

</p>
<p>

Create a New Domain Admin Account Inside _ADMINS, create a new user:

Full Name: Jane Doe

Username: jane_admin

Password: Cyberlab123! (same password used before) After creation, right-click Jane’s account → Add to a group… → add to Domain Admins.

➡️ Log out of DC-1 and log back in as:
mydomain.com\jane_admin

🔑 From this point forward, use jane_admin as your admin account.

</p>
<br />

</p>
<img width="301" height="153" alt="image" src="https://github.com/user-attachments/assets/08ab9b9c-2683-4b53-ba90-008cbd38b698" />

</p>
<p>
  
Join Client-1 to the Domain

Log in to Client-1.

Go to System Properties → Rename this PC (Advanced). Click Change → select Domain and type: mydomain.com. Enter domain credentials when prompted (use mydomain.com\jane_admin).

Restart Client-1. Log in using domain credentials to confirm it has successfully joined.


</p> 
<br /> 

<p/>
✅ At this point, you have:

Installed Active Directory.

Promoted DC-1 to a domain controller.

Created a domain admin account (jane_admin).

Joined Client-1 to the domain.
