<<img width="2880" height="1799" alt="Rippling_Blog_Hero_IAMRelaunch_2025_" src="https://github.com/user-attachments/assets/78d315b6-4227-4ef6-a58d-9f4abf33b901" />

</p>

<h1>Creating a new user and assigning permissions</h1>
(following up on the network file share lab)In this IAM lab I’m going to  demonstrate  a step by step process of creating a user, configuring permissions based on job responsibilities, implementing security group management, assigning group memberships, and role-based access control (RBAC) Using Active Directory.
 <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure 
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Group Policy
- Active Directory Users And Computers (ADUC)

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Configuration Steps</h2>

1. Open Active Directory Users and Computers (ADUC).
2.  Navigate to the Employees OU 
3. Right click the Employees OU > New > User.
4. Enter First name, Last name,(Claye Martin ) User logon name (cmart)> Next.

<img width="3840" height="2160" alt="Pasted Graphic" src="https://github.com/user-attachments/assets/994ef86d-457d-4f57-85a1-0bbf67e14834" />

1. Set the initial password and password options > Next.
2. Review > Finish.
<img width="1920" height="1080" alt="Screenshot 2026-09-17 at 3 58 24 PM" src="https://github.com/user-attachments/assets/0798ac3e-57db-4742-a982-1fb1f0db9316" />
<img width="1920" height="1080" alt="Screenshot 2026-09-17 at 3 58 13 PM" src="https://github.com/user-attachments/assets/2324c5f9-f4e0-4980-9500-596796f1ca7f" />


Now that the user/employee is created im going to assign permissions 


<img width="1920" height="1080" alt="Screenshot 2026-09-17 at 3 59 55 PM" src="https://github.com/user-attachments/assets/7a89de12-dbc0-47a5-8f4f-3ea40bcf7318" />

1. Using Claye Martin’s username (cmart), log into the client vm and Observe that you do not have access to certain folders  
<img width="1025" height="678" alt="Decument" src="https://github.com/user-attachments/assets/2ed396a4-8c39-4870-9499-7b4c46507268" />


<img width="840" height="543" alt="Screenshot 2026-09-18 at 2 33 19 AM" src="https://github.com/user-attachments/assets/47d3d96a-9947-4ab5-a64d-849ee55998d7" />
1. Log out of Client-1 as  cmart 
2. Go back to ADUC > right click  employees> Find> Claye Martin> Right click the name  > then Properties to add groups, contact info, etc.
<img width="1920" height="1080" alt="Screenshot 2026-09-24 at 9 30 15 AM" src="https://github.com/user-attachments/assets/074207e6-acf7-4fd2-9d2a-ac404df06225" />


1. On Domain controller VM, make Claye  a member of the “ACCOUNTANTS”  Security Group
<img width="1280" height="800" alt="Screenshot 2026-09-18 at 3 03 03 AM" src="https://github.com/user-attachments/assets/7036ea2f-59a9-42a1-98bd-3d50d51f000a" />
<img width="1280" height="800" alt="Screenshot 2026-09-18 at 3 02 43 AM" src="https://github.com/user-attachments/assets/a59fb57c-43a6-4a27-b155-65767fc4be99" />


1. Sign back into Client-1 as cmart and try to access the “accounting” share in \\DC-1\

<img width="1280" height="800" alt="Screenshot 2026-09-18 at 3 07 38 AM" src="https://github.com/user-attachments/assets/3b616519-0eaa-4957-8ea1-dbdf1b89224f" />


