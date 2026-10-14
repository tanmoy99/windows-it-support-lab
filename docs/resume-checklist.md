# Resume checklist

## Current stopping point

DC01 is operational, PC01 domain sign-in works, Staff access and S: mapping work, and Finance share access has been reported working. Automatic-lock Group Policy is deferred.

## Next session

1. Start DC01, then PC01. Check guest clocks and evaluation licence status.
2. Verify PC01 resides in ITSupportLab/Workstations.
3. Finish the Staff text-file write/edit test if not already completed.
4. Capture Finance positive write test as Priya and denied-access test as Alex.
5. Create and link Workstation - Automatic Lock to Workstations, set Interactive logon: Machine inactivity limit to 300 seconds.
6. As local LabAdmin on PC01, run elevated gpupdate /force and gpresult /r /scope computer; restart and test five minutes of inactivity.
7. Document the observed policy result before adding it to the CV.
8. Continue support exercises and create a ticket portfolio; GLPI remains uninstalled.

## Safe stopping procedure

Save documents, shut down PC01 through Windows, then shut down DC01. Documentation backup does not back up the VM disks. To preserve the running lab separately, shut down the VMs and copy their complete VM folders to an external drive with sufficient space. Never upload the VM disks to this GitHub repository.

