# 🛡️ Active Directory Security Lab (Student Project)

This project simulates a real-world enterprise **Active Directory (AD)** environment using a Windows Server virtual machine. The goal is to understand domain structures, user and group management, GPO enforcement, auditing, and simulation of common attack vectors like **Kerberoasting** and **ASREPRoasting** in a safe and isolated lab setup.

> 🔐 Built entirely using PowerShell and manual configuration inside a virtual environment.

---

## 🌐 OU Structure Implemented

```text
forest.local
├─ OU=INDIA
│  ├─ OU=PUNE
│  │  └─ OU=MARKETING (User: Ravi)
│  └─ OU=CHENNAI
│     └─ OU=HR (User: Hari)
├─ OU=FRANCE
│  └─ OU=PARIS
│     └─ OU=DESIGN (User: Adrien)
└─ OU=SOUTH_KOREA
   └─ OU=SEOUL
      └─ OU=MARKETING (User: Kim Yoo Jung)
```

---

## 🛠️ Active Directory Security Lab — Progress Updates

### ✅ Week 1

#### 🔧 AD Domain Controller Setup
- Created Windows Server VM via VirtualBox
- Installed Active Directory Domain Services (AD DS)
- Promoted server to Domain Controller for domain: `FOREST.local`
- Configured DNS during AD DS installation

#### 🗂️ Organizational Unit (OU) Structure
- Created **country-level OUs**: INDIA, FRANCE, SOUTH_KOREA
- Nested **city and department OUs**: PUNE/MARKETING, CHENNAI/HR, PARIS/DESIGN, SEOUL/MARKETING
- Added additional OUs: `GROUPS`, `INTERNS`

#### 👥 Users and Groups
- Created users: Ravi, Adrien, Hari, Kim Yoo Jung, etc.
- Assigned each user to their respective OU and department
- Created Security Groups: `Finance_Team`, `IT_Admins`
- Assigned users to groups based on roles

#### 🔐 Group Policy Objects (GPOs)
- Enforced **password complexity** and **account lockout** policies
- Applied GPOs to specific OUs (e.g., restrictions on INTERNS group)
- Verified policy application with `gpresult /r` and `gpupdate /force`

#### 🧑‍💼 Delegation of Control
- Delegated permissions to HR leads for user management tasks like password resets
- Scoped delegation using ADUC (Active Directory Users and Computers)
- Tested role-based delegation within OU scope

---

### ✅ Week 2

#### 🖼️ Implementation Proof & Documentation
Screenshots and configuration exports are saved in a structured format

#### 🛡️ Attack Simulations and Monitoring

**Kerberoasting**
- Used PowerView to enumerate SPNs
- Requested service tickets and extracted hashes with Rubeus
- Observed corresponding Event IDs in Event Viewer: `4769`, `4624`

**ASREPRoasting**
- Attempted to exploit accounts with `Do not require Kerberos preauthentication`
- Used tools like Rubeus to extract AS-REP encrypted data
- Simulated failed attempts and ensured proper configuration to prevent abuse

**Audit Logging**
- Enabled advanced auditing through GPO
- Exported logs to `AD_Logs/` directory for review:
  - Security logs
  - Logon attempts
  - GPO application status
  - Delegation activities

**Brute Force Attack & Account Lockout**
- Simulated brute force attempts using common tools/scripts on low-privilege user accounts
- Triggered account lockout after a defined number of failed logins (e.g., 5 attempts)
- Verified lockout in Event Viewer via Event IDs: `4740` (account locked), `4625` (failed logon)
- Validated the effectiveness of password policies and lockout GPOs
---

## 📁 Repository Structure

```text
AD-Security-Lab/
├── Screenshots/            # Proof of implementation (PDFs)
├── Scripts/                # PowerShell automation scripts
├── AD_Logs/                # Exported Event Viewer logs 
└── README.md               # Project documentation
```

---

## 🏁 Conclusion

This project provided hands-on exposure to the foundational elements of managing an Active Directory environment, from basic setup to advanced simulations of real-world attack vectors. Skills developed include:

- Designing scalable OU structures
- Role-based access and delegation using ADUC
- Enforcing and troubleshooting Group Policy
- Simulating and defending against Kerberoasting & ASREPRoasting
- Auditing and log collection for blue-team visibility

> 🎯 This lab is a foundational step toward understanding red-team and blue-team roles in enterprise environments. It bridges theory and practical implementation in a safe, testable setup using only a Windows Server VM and PowerShell.

---
