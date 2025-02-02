<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Configurations in Azure</h1>
This lab is a follow up to the lab where I installed Active Directory and created a domain controller. I will now be configuring Active Directory and allowing a client to join the domain as well as creating user accounts. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Configuration Steps</h2>


<img width="1280" alt="Screenshot 2025-01-22 at 2 55 49 PM" src="https://github.com/user-attachments/assets/db6dfae8-a64e-4ae9-ba70-c994beed9454" />
<img width="1280" alt="Screenshot 2025-01-22 at 2 56 21 PM" src="https://github.com/user-attachments/assets/f648a754-ba92-41b9-aafe-12bd01303718" />

After installing Active Directory on the domain controller VM, I created two Organizational Units (OUs): _EMPLOYEES and _ADMINS. In the _ADMINS OU, I created a user, Jane Doe, and granted her administrative privileges by adding her to the Domain Admins security group. I'll now log off as labuser and log in as jane_admin for further changes.



<img width="1280" alt="Screenshot 2025-01-22 at 3 05 36 PM" src="https://github.com/user-attachments/assets/af46fe48-d93e-436c-8df6-0f32574e2de9" />

Before joining the domain, configure the client’s DNS to point to the domain controller's private IP. In the Azure portal, go to the Networking tab, select Network Interface, set the DNS server to the domain controller’s private IP, and save. Restart the client VM to apply the changes.


<img width="1280" alt="Screenshot 2025-01-22 at 3 21 31 PM" src="https://github.com/user-attachments/assets/046c7897-802d-4068-9ac5-c915dc1f426e" />
<img width="1280" alt="Screenshot 2025-01-22 at 3 25 19 PM" src="https://github.com/user-attachments/assets/b8e084dc-274d-40c5-b634-5ec5cab168a9" />

To join the client VM to the domain, go to the System menu, click "Rename this PC (advanced)," and select "Change." Enter the domain name and credentials (using Jane Doe’s account). Afterward, the client will appear in the "Computers" section of Active Directory Users and Computers on the domain controller.


<img width="1280" alt="Screenshot 2025-01-24 at 9 55 06 AM" src="https://github.com/user-attachments/assets/a0917ead-2b08-4169-a303-e627339a5543" />

To enable Remote Desktop for non-admin users, log in as an administrator (Jane), open System Properties, go to Remote Desktop, and allow Domain Users access. Now, non-admin users can log in to Client-1. A Group Policy could automate this, but it's not used in this lab.


<img width="1280" alt="Screenshot 2025-01-24 at 9 58 13 AM" src="https://github.com/user-attachments/assets/2819c51c-7c22-40b6-a7f2-86f8efe41211" />

<img width="1280" alt="Screenshot 2025-01-24 at 9 58 48 AM" src="https://github.com/user-attachments/assets/03859d3e-94ab-4692-8b62-45b76df0fe2c" />

<img width="1280" alt="Screenshot 2025-01-24 at 9 59 53 AM" src="https://github.com/user-attachments/assets/31b10385-574d-47e1-ba4b-4c86dcab13c8" />

Users can be created manually or via a script. In this lab, I’ll use a PowerShell script. On the domain controller, open PowerShell ISE as an admin (ensure you're logged in with an admin account). Create a new file, paste the script into the ISE console, and run it to create the user accounts.


<img width="1280" alt="Screenshot 2025-01-24 at 10 05 02 AM" src="https://github.com/user-attachments/assets/8d10c19c-8979-4db2-865a-dd887e8fdb77" />

Once the users are created, you can sign in to Client-1 using one of the newly created accounts from the PowerShell script. Just choose a user and log in with the domain context.
