# Active Directory Security Lab (Student Project)

This project simulates a real-world enterprise Active Directory environment using a Windows Server VM. The goal is to understand domain structures, user management, GPO enforcement, and simulate common attack scenarios like Kerberoasting and privilege escalation — all in a safe lab setup.

> 🔐 Built entirely using PowerShell and hands-on configuration inside a virtual environment.

OU Structure to be implemented :

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

## 🛠️ Active Directory Security Lab — Progress Update

✅ Week 1

🔧 AD Domain Controller Setup

Windows Server VM created via VirtualBox

AD DS role installed

Domain created: FOREST.local

Promoted to Domain Controller

🗂️ Organizational Unit (OU) Structure

Country-level OUs: INDIA, FRANCE, SOUTH_KOREA

City/Department sub-OUs: PUNE/MARKETING, PARIS/DESIGN, etc.

Additional OUs: GROUPS, INTERNS

👥 Users and Groups

Created test users (e.g. Ravi, Adrien, Hari) and assigned them to correct OUs

Created security groups like Finance_Team, IT_Admins

Assigned users to groups

🔐 Group Policy Objects (GPOs)

Password complexity + lockout policies applied

GPO targeting interns (command prompt restrictions, etc.)

Verified with gpresult and gpupdate

🧑‍💼 Delegation of Control

Delegated specific rights to users (e.g., reset password rights for HR lead)

Tested role-based delegation within OU scope
