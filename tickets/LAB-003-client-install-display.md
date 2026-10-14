# LAB-003 — PC01 installation boot and display issues

Type: lab setup incident. Device: PC01.

Initial screenshot showed a CD/DVD boot prompt followed by no bootable device. Guidance was to retry with the Windows 11 ISO and press Enter before the prompt timed out. A VirtualBox input-capture popup interrupted interaction; accepting Capture allowed keyboard input into the guest. Windows Setup subsequently appeared.

After installation, the user reported a black display while the VM showed Running. Guidance included input/wake checks, waiting for first startup, and if persistently unresponsive powering off and checking VBoxSVGA, 128 MB video memory and disabled 3D acceleration.

Later screenshots showed the Windows sign-in screen and user confirmed a successful login. The exact display fix and root cause were not observed; graphics settings are troubleshooting advice, not a proven cause.

