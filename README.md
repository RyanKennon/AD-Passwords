<p align="center">
  <img src="https://github.com/user-attachments/assets/7b65e021-0e08-42ae-8da2-f57cd11aceb7" width="300" height="168" alt="image" />
</p>

# Active Directory: Account Lockout & Password Policy

This project focuses on enforcing password security and managing account lockouts within an Active Directory environment. I created a custom Account Password Policy, simulated a user account lockout, and used administrative tools to unlock the account and reset the user’s password. I then verified that the updated policy and recovery steps worked as intended. This lab demonstrates key identity security concepts, including password enforcement, lockout behavior, and user recovery procedures in a Windows Server domain.

---

## Environments and Technologies Used

- Microsoft Azure
- Active Directory Users and Computers
- Group Policy Management
- Remote Desktop Protocol (RDP)
- Microsoft PowerShell

---

## Lab Objectives

- Prepare the Active Directory environment for testing password and account lockout behavior
- Simulate a user account lockout by intentionally entering incorrect login credentials
- Create and apply a custom Account Password Policy using Group Policy Management
- Unlock a locked-out user account and reset their password through Group Policy tools
- Verify that the updated password policy and account recovery steps function as intended
- Strengthen understanding of account security, password enforcement, and user recovery procedures within a Windows Server domain environment

---

## Step-by-Step Walkthrough

### Lab Environment

- **Platform:** Microsoft Azure
- **Domain Controller:** Windows Server 2022 Datacenter
- **Client Machine:** Windows 10 Pro
- [Setup an Active Directory Domain](https://github.com/RyanKennon/AD-Domain-Setup/blob/main/README.md)
- [Setup Users in Active Directory](https://github.com/RyanKennon/AD-User-Creation-Access-Control/blob/main/README.md)

<p align="center">
  <img width="1875" height="559" alt="Untitled Diagram-Page-1 drawio" src="https://github.com/user-attachments/assets/b3bd63ba-c0ba-48da-af1d-63ac35e005d9" />
</p>

---

### 1) Create an Account Password Policy

1. On the **Domain Controller** open the **Server Manager**
2. Select **Tools** then **Group Policy Management**

<p align="center">
  <img width="1310" height="761" alt="Untitled Diagram-Page-1 drawio" src="https://github.com/user-attachments/assets/6ebebf36-19ee-4cc6-9acc-ec17be43ade2" />
</p>

3. Navigate through the **Forest** to the **Default Domain Policy**
4. Right click **Default Domain Policy** then choose **Edit**

<p align="center">
  <img width="752" height="527" alt="Untitled Diagram-Page-2 drawio" src="https://github.com/user-attachments/assets/3e2e4023-c338-4864-af0f-fff899244cdf" />
</p>

5. In the **Group Policy Management Editor** navigate through the **Policies** folder to the **Password Policy**

<p align="center">
  <img width="785" height="562" alt="Untitled Diagram-Page-3 drawio" src="https://github.com/user-attachments/assets/e6fb7b79-9cc3-4ea4-8c29-2a662c646909" />
</p>

6. Change the **Maximum Password Age** to **30 days**

<p align="center">
  <img width="715" height="589" alt="Untitled Diagram-Page-4 drawio" src="https://github.com/user-attachments/assets/b7de2388-821e-46f2-9d0c-002d54b39ac1" />
</p>

7. Change the **Minimum Password Length** to **12 characters**

<p align="center">
  <img width="1019" height="668" alt="Untitled Diagram-Page-5 drawio" src="https://github.com/user-attachments/assets/06b4eb15-f0e0-4b93-9bf4-c4b4e3740da5" />
</p>

8. Open the **Account Lockout Policy**
9. Change the **Account Lockout Threshold** to **3 invalid login attempts**

<p align="center">
  <img width="1022" height="669" alt="Untitled Diagram-Page-6 drawio" src="https://github.com/user-attachments/assets/c934b2ba-62f9-4d48-aaa0-c108e08c3784" />
</p>

10. Change the **Account Lockout Duration** to **360 minutes**

<p align="center">
  <img width="713" height="584" alt="Untitled Diagram-Page-7 drawio" src="https://github.com/user-attachments/assets/3a9d850d-33b0-43e9-91fd-48c919d9d68f" />
</p>

11. Go back to the **Group Policy Management** page
12. Right-click **Default Domain Policy**
13. Click **Enforce**

<p align="center">
  <img width="751" height="527" alt="Untitled Diagram-Page-8 drawio" src="https://github.com/user-attachments/assets/af525589-f358-4b69-9ae8-9f9a0a696945" />
</p>

---

### 2) Lockout the User's Account

1. Attempt to log into the **client Virtual Machine** using an **incorrect password** four times

<p align="center">
  <img width="567" height="369" alt="Untitled Diagram-Page-9 drawio" src="https://github.com/user-attachments/assets/888ab766-b79a-4c76-b220-5e1fe7899df0" />
</p>

---

### 3) Unlock the User's Account

1. Open **Active Directory Users and Computers**
2. Double click the **user**
3. Click **Account**
4. Check the box labeled **Unlock Account**
5. Apply the Changes

<p align="center">
  <img width="749" height="667" alt="Untitled Diagram-Page-10 drawio" src="https://github.com/user-attachments/assets/35276247-79bc-427e-a979-62ebee8d1975" />
</p>

---

### 4) Reset the User's Password

1. Right click the **user**
2. Select **Reset Password**

<p align="center">
  <img width="751" height="525" alt="Untitled Diagram-Page-11 drawio" src="https://github.com/user-attachments/assets/71c01277-8ad5-4fb3-8328-124e95e3b0f1" />
</p>

3. Enter the new password
4. Apply the Changes

<p align="center">
  <img width="377" height="254" alt="Untitled Diagram-Page-12 drawio" src="https://github.com/user-attachments/assets/8065b96f-2809-4d0c-b42a-bda8e3843270" />
</p>

---

### 5) Verify Functionality

1. Attempt to log into the **client Virtual Machine** using the updated **user credentials**

<p align="center">
  <img width="786" height="444" alt="Untitled Diagram-Page-13 drawio" src="https://github.com/user-attachments/assets/bee7a8f1-ecee-4678-b7f7-63e19546e757" />
</p>

---

## Outcome

- Successfully created and applied a custom Account Password Policy using Group Policy Management  
- Simulated an account lockout by intentionally entering incorrect login credentials  
- Unlocked the user account through Active Directory tools, restoring normal sign-in capability  
- Reset the user’s password according to the newly applied password policy requirements  
- Verified that the updated policy, lockout behavior, and account recovery process all functioned as expected  
- Demonstrated practical understanding of password enforcement, account security, and user recovery procedures within an Active Directory domain environment

---

## Skills Demonstrated

- Configuring Account Password Policies using Group Policy Management  
- Applying and managing password complexity, length, and lockout rules  
- Simulating and diagnosing account lockout events  
- Unlocking user accounts through Active Directory administrative tools  
- Resetting user passwords in accordance with policy requirements  
- Verifying authentication behavior after policy changes and account recovery  
- Strengthening practical understanding of identity security, password enforcement, and user account recovery within a Windows Server domain environment
