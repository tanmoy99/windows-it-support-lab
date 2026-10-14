# LAB-001 — Staff share access denied

Type: lab incident. Affected resource: \\DC01\Staff. Fictional user: Alex Taylor.

## Symptom

Windows displayed that the user did not have permission to access the Staff share.

## Investigation and actions

Checked Alex's membership in GG_Staff, nested membership of GG_Staff in DL_Staff_Modify, SMB Change/Read permission and NTFS Modify permission. Alex membership was visible in the screenshot. Instructed a full sign-out/sign-in to refresh group membership.

## Outcome

User confirmed access worked. A subsequent screenshot shows Staff mapped as S: and the Alex-Test folder present.

## Root cause and limits

The precise setting changed was not recorded. Do not claim a specific missing group or permission was proven to be the root cause. File write/edit verification remains to document separately.

