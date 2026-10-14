# Setup record

## Host and VM configuration

Host screenshot: AMD Ryzen 7 5800HS, 16 GB RAM, Windows 11 Home. VirtualBox version supplied by user: 7.2.14. Hardware virtualisation was reported enabled.

| VM | OS | RAM and CPUs | Disk |
|---|---|---|---|
| DC01 | Windows Server 2025 Standard Evaluation, Desktop Experience | 4096 MB and 2 CPUs instructed; settings not separately captured | 60 GB dynamic disk instructed |
| PC01 | Windows 11 Enterprise Evaluation | 4096 MB and 2 CPUs instructed; settings not separately captured | 80 GB virtual disk shown in installer |

Both VMs use NAT Network `ITSupportLab`, with virtual cable connected. The lab walkthrough disabled NAT Network DHCP, requiring static guest addresses. Keep sufficient free space on the host as dynamic disks grow.

## DC01

1. Installed Windows Server Desktop Experience and renamed the guest DC01.
2. Configured IPv4 10.10.10.10, mask 255.255.255.0, gateway 10.10.10.1 and DNS 10.10.10.10.
3. Installed the Active Directory Domain Services role and promoted the server into a new forest named itsupport.test.
4. Selected Windows Server 2025 forest/domain functional levels; DNS and Global Catalog enabled. Kept default database/log/SYSVOL paths.
5. Created a private DSRM password. No passwords are stored in this repository.
6. Prerequisite checks passed. The standalone test domain generated a DNS delegation warning, which did not block promotion.
7. Rebooted and signed in as ITSUPPORT\Administrator.

Verified in PowerShell:

```powershell
Get-ADDomain | Select-Object DNSRoot, NetBIOSName
Resolve-DnsName -Name DC01.itsupport.test -Type A
Get-SmbShare -Name SYSVOL,NETLOGON
```

Observed results: itsupport.test / ITSUPPORT; DC01 A record 10.10.10.10; both NETLOGON and SYSVOL present.

## Active Directory structure

Created ITSupportLab with Employees, Workstations and Groups child OUs. Existing Finance, HR, IT and Sales OUs were also visible at the domain root; their contents were not inventoried. DC01 remains in Domain Controllers.

Employees: Alex Taylor (alex.taylor) and Priya Shah (priya.shah). Ordinary employee accounts were used for access tests. A local LabAdmin account exists on PC01 for workstation administration.

## PC01

1. Installed Windows 11 from the Enterprise evaluation ISO onto the 80 GB virtual disk.
2. Used a local LabAdmin setup account.
3. Walkthrough assigned 10.10.10.20/24, gateway 10.10.10.1 and DNS 10.10.10.10.
4. Joined itsupport.test using authorised domain administrator credentials through sysdm.cpl.
5. Alex domain sign-in succeeded after an initial incorrect-credentials problem.
6. Moving PC01 from Computers to ITSupportLab/Workstations was instructed; verify placement before linking workstation policies.

## Useful tools

| Command | Purpose |
|---|---|
| dsa.msc | Active Directory Users and Computers on DC01 |
| gpmc.msc | Group Policy Management on DC01 |
| ncpa.cpl | Guest network adapters |
| sysdm.cpl | Computer name and domain membership |
| whoami /groups | Current user's security group token |

