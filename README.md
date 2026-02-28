# Active Directory Domain Services (AD DS) Project

---

## Project Overview
This project demonstrates the setup of a structured Active Directory environment, including departmental Organizational Units (OUs), user accounts, groups, and Group Policy Objects (GPOs). It simulates a corporate network to illustrate AD DS management best practices.

---

## Table of Contents
- [Organizational Structure](#organizational-structure)
- [Users and Groups](#users-and-groups)
- [Group Policy Objects (GPOs)](#group-policy-objects-gpos)
- [Screenshots & Evidence](#screenshots--evidence)
- [Challenges Encountered](#challenges-encountered)
- [Conclusion](#conclusion)

---

## Organizational Structure
The AD hierarchy is organized by department:

| Department | OUs |
|-----------|-----|
| Technical | IT, Security Engineering, Service Technicians |
| Non-Technical | Finance, Employee Welfare, Management |

Each department contains `Users` and `Computers` OUs for better management and access control.

<details>
<summary>Visual Structure</summary>
Departments <br>
├── Technical <br>
│ ├── IT <br>
│ ├── Security Engineering <br>
│ └── Service Technicians <br>
│ <br>
└── Non-Technical <br>
├── Finance <br>
├── Employee Welfare <br>
└── Management <br>

</details>

---

## Users and Groups

### Users
Users are assigned to their respective departmental OUs.

| Department | Username | Account |
|------------|----------|---------|
| IT | Nate Okyere | nate.okyere@mylab.local |
| IT | Terrence Noah | terrence.noah@mylab.local |
| Security Engineering | Lamar Trevor | lamar.trevor@mylab.local |
| Security Engineering | Austin Reaves | austin.reaves@mylab.local |

### Groups
| Group Name | Scope | Purpose |
|------------|-------|---------|
| IT Admins | Global | Manage IT resources |
| Security Team | Global | Security management |
| Finance Team | Global | Finance operations |

> All groups are **Global scope**

---

## Group Policy Objects (GPOs)
| GPO Name | Target OU | Settings |
|----------|-----------|---------|
| Password Policy | All Users | Enforces password complexity and expiry |
| Desktop Restrictions | IT, Security | Limits access to CMD, PowerShell, Registry |
| Security Settings | All Departments | Configures audit, firewall, and login policies |

## Network Shared Drive

A network shared drive was created to centralize departmental resources. Each department has its own folder, and **access is restricted based on departmental membership**.

| Department | Shared Folder | Access Permissions |
|------------|---------------|------------------|
| IT | `\\WIN-VPH3UKS8K1A\CompanySharedDrive\IT` | Only IT group members have read/write access |
| Security Engineering | `\\WIN-VPH3UKS8K1A\CompanySharedDrive\SecurityEngineering` | Only Security Engineering group members have read/write access |
| Finance | `\\WIN-VPH3UKS8K1A\CompanySharedDrive\Finance` | Only Finance group members have read/write access |
| Employee Welfare | `\\WIN-VPH3UKS8K1A\CompanySharedDrive\EmployeeWelfare` | Only Employee Welfare group members have read/write access |
| Management | `\\WIN-VPH3UKS8K1A\CompanySharedDrive\Management` | Only Management group members have read/write access |

**Key Points:**
- Folder access is enforced using **Domain Local groups** corresponding to each department.
- Users from other departments **cannot access folders** outside their department.
- This ensures **data confidentiality and segregation** between departments.

<details>
<summary>Screenshot Example</summary>

<img width="1682" height="839" alt="image" src="https://github.com/user-attachments/assets/11249bfd-c43f-4114-949e-81838d251180" />
<br> <br>

<img width="1682" height="839" alt="image" src="https://github.com/user-attachments/assets/a2a41391-429d-4041-8f95-44c3bb9fd115" />



</details>


---

## Screenshots & Evidence
Click to expand and view screenshots:

<details>
<summary>AD Structure</summary>

<img width="1682" height="839" alt="image" src="https://github.com/user-attachments/assets/0d28586b-ceb3-41a1-b580-d4d25fc14e76" />


</details>

<details>
<summary>Users in IT OU</summary>

<img width="1682" height="839" alt="image" src="https://github.com/user-attachments/assets/340d3616-1dd3-49d0-b5a1-ac71cb1a3b30" />


</details>

<details>
<summary>GPO Example</summary>

<img width="1682" height="839" alt="image" src="https://github.com/user-attachments/assets/50cc7994-2234-420b-94d9-77d2d551ea17" />


</details>

---

## Challenges Encountered
- Trust relationship errors: `"The security database on the server does not have a computer account for this workstation."`


---

## Conclusion
- Successfully created departmental OUs and structured user accounts.
- Implemented GPOs for security and operational control.
- Demonstrated handling of common AD deployment issues.

---

