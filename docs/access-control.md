# Access control

## Intended membership and permissions

| User | Global groups | Permission group | Share |
|---|---|---|---|
| Alex Taylor | GG_Staff | GG_Staff nested in DL_Staff_Modify | Staff |
| Priya Shah | GG_Staff, GG_Finance | GG_Finance nested in DL_Finance_Modify | Staff and Finance |

Group names may appear as GG_staff and DL_staff_modify in the UI; Windows name matching is case insensitive. Both global and domain local groups are Security groups.

## Share configuration walkthrough

| Folder | Share | SMB permissions | NTFS permissions |
|---|---|---|---|
| C:\LabShares\Staff | \\DC01\Staff | Domain Admins: Full Control; DL_Staff_Modify: Change and Read | Administrators/SYSTEM: Full Control; DL_Staff_Modify: Modify |
| C:\LabShares\Finance | \\DC01\Finance | Domain Admins: Full Control; DL_Finance_Modify: Change and Read | Administrators/SYSTEM: Full Control; DL_Finance_Modify: Modify |

For each new share folder, inheritance was disabled with inherited entries converted to explicit permissions. Broad Users entries were removed. CREATOR OWNER was retained for subfolders/files. Permission-group entries apply to this folder, subfolders and files. Everyone was removed from share permissions. These are the instructed final settings; final complete ACL screenshots have not yet been captured.

Group membership changes require a fresh sign-in for client token testing. Both share permissions and filesystem permissions must permit the requested operation.

## Test record

| Test | Result recorded | Evidence level |
|---|---|---|
| Alex domain sign-in | Successful | User confirmation |
| Alex opens Staff | Successful after troubleshooting | User confirmation and mapped share screenshot |
| S: maps to Staff | Successful | Screenshot |
| Alex-Test exists in Staff | Present | Screenshot; creation sequence reported in walkthrough |
| Alex saves and edits Staff text file | Instructed | No separate result captured |
| Finance opens on PC01 | Successful | Screenshot; current user not visible |
| Priya accesses Finance | Reported as working in response to test instructions | User report; identity-specific screenshot pending |
| Priya saves/edits Finance file | Instructed | Screenshot folder is empty; write result pending |
| Alex denied Finance | Required negative test | No separate denial result captured |

## Capture remaining proof

On PC01, use whoami to establish the account for each test. As Priya, create, edit and delete a disposable test file in Finance. Sign out fully, sign in as Alex, then open \\DC01\Finance: access should be denied. Do not supply administrator credentials during employee tests. Record actual outcomes before describing Finance isolation as verified.

