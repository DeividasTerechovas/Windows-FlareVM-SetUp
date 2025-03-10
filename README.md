# Reverse Engineering & Malware Analysis Lab

# Objective

This project focuses on setting up a Windows 10 virtual machine and configuring Flare-VM, a security-focused distribution for malware analysis and reverse engineering. The guide walks through installation, configuration, and security optimizations.

# Reverse Engineering/Malware Analysis Projects

| Reverse Engineering & Malwayre Analysis Project                                      | Detailed Repo        |
|-----------------------------------------------|----------------------------|
| Coming Soon         | Coming Soon|
| Coming Soon  | Coming Soon|
| Coming Soon         | Coming Soon  |
| Coming Soon        | Coming Soon  |
| Coming Soon                   | Coming Soon  |
| Coming Soon   |Coming Soon  |

# Skills Learned

Virtual Machine (VM) configuration and optimization.

Disabling Windows security features for malware analysis.

Installing and configuring Flare-VM.

Handling Windows Defender and Windows Update settings.

# Tools Used

Flare-VM – Security-focused VM setup.

VirtualBox/VMware – Virtualization platforms.

Windows 10 – Operating system for the VM.

# Steps

# 1. Setting Up the Windows 10 VM

Start the VM installation.

<img src="https://i.imgur.com/t3GH2xU.jpeg" width="500">

<img src="https://i.imgur.com/XFI2vgK.jpeg" width="500">

CHECK THE FLARE-VM WEBSITE FOR FLARE REQUIREMENT!
4GM RAM, 2 CPU CORES & 60GB STORAGE IS MINIMUM

Select the language, then proceed with the installation.

Change the network from NAT to HOST-only.

Select I do not have a key.

Choose Windows 10 Home.

Select Custom: Install Windows Only.

Select the VM driver and begin installation.

# 2. Pre-Installation Configurations

Ensure Flare-VM requirements are met.

Swap network back from HOST-only to NAT.

Install Guest Additions for easier copy-paste and file dragging.

VM Toolbar → Devices → Insert Guest Additions CD Image.

Open This PC in the VM and run VBoxWindowsAdditions-amd64.

Follow the installation prompts and restart the VM.

# 3. Disabling Windows Updates

Open Run (Windows+R), type services.msc.

Find Windows Update, double-click it.

Set Startup Type to Disabled.

Click Stop under Service status.

# 4. Disabling Windows Defender

Open Windows Security → Virus & Threat Protection → Manage Settings.

Disable Real-time protection and all other options.

Extra Step: Prevent Defender from turning on after restart.

If gpedit.msc is missing, open CMD as Admin and run:

FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F")

FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F")

Open gpedit.msc (Windows+R → gpedit.msc).

Navigate to:

Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time Protection

Enable Turn off real-time protection.

Restart the VM.

# 5. Alternative Defender Disabling (Registry Method)

Boot into Safe Mode.

Open Run (Windows+R), type regedit.

Navigate to:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Service

Change the Start value to 4 for the following keys:

Sense

WdBoot

WdFilter

WdNisDrv

WdNisSvc

WinDefend

Restart back to normal mode.

This method leaves Defender in a loading loop, preventing activation.

# 6. Creating a Baseline Snapshot

Take a screenshot and save it as BASELINE_BACKUP for reference if anything goes wrong.

# 7. Installing Flare-VM

Download Flare-VM installer:

Go to Flare-VM GitHub.

Right-click installer.ps1, save it to a Flare folder on the desktop.

Open the Flare folder, then File > Open Windows PowerShell as Administrator.

Run the following:

Unblock-File .\install.ps1
Set-ExecutionPolicy Unrestricted -Force
.\install.ps1

# 8. Post-Installation Steps

Swap network from NAT back to HOST-only.

Choose which Flare-VM tools to install (or select all).

Let the installation run (take a break, grab some tea!).

Why This Matters

Sets up a fully optimized malware analysis VM.

Provides hands-on experience with security tools.

Prepares an environment for reverse engineering and threat research.


