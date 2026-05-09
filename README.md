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
I RDP'd into DC-1 and opened <strong>Server Manager</strong>. I clicked <strong>Add Roles and Features</strong>, selected Role-based installation, and chose <strong>Active Directory Domain Services</strong>. I proceeded through the wizard and completed the installation.
</p>
<br />

---

<h2>Step 2 — Promote DC-1 to a Domain Controller</h2>

<p>
<img width="1428" height="756" alt="image" src="https://github.com/user-attachments/assets/022a6880-410a-43cc-baf2-ff3fb0ca146f" />
</p>
<p>
After installation, a yellow notification flag appeared in Server Manager. I clicked <strong>Promote this server to a domain controller</strong> and selected <strong>Add a new forest</strong>. I set the root domain name to <strong>mydomain.com</strong> and configured a DSRM password. After completing the wizard, DC-1 restarted automatically.

After the reboot, I logged back in using domain credentials:
</p>
