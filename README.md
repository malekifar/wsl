# How to install Ubuntu 20.04 + WSL2 + Windows Terminal + ZSH + PowerLevel10K + WSLU + WSL Sudo + VScode + Jupyter Notebook
## Table of Contents
- [Installing WSL](#Installing-WSL)
  - [Requirements](#Requirements)
    - [Updating Windows 10](#Updating-Windows-10)
    - [Upgrading Windows 7, 8, 8.1](#upgrading-windows-7-8-81)
  - [Enabling Windows Subsystem for Linux](#Enabling-Windows-Subsystem-for-Linux)
    - [Method1 Using Settings](#Method1-Using-Settings)
    - [Method2 Using PowerShell](#Method2-Using-PowerShell)
  - [Installing Ubuntu 20.04](#installing-ubuntu-2004)
    - [Method1 Using Microsoft Store](#method1-using-microsoft-store)
    - [Method2 Using PowerShell](#Method2-using-powershell-1)
- [Installing WSL2](#Installing-WSL2)
  - [Requirements](#Requirements-1)
  - [Enabling Windows Subsystem for Linux](#Enabling-Windows-Subsystem-for-Linux)
    - [Method1 Using Settings](#Method1-Using-Settings)
    - [Method2 Using PowerShell](#Method2-Using-PowerShell)
- [Installing Windows Terminal](#Installing-Windows-Terminal)
  - [Requirements](#Requirements)
- [Installing WSH](#Installing-WSH)
- [Installing PowerLevel10K](#Installing-PowerLevel10K)
- [Installing WSLU](#Installing-WSLU)
- [Installing WSL Sudo](#Installing-WSL-Sudo)
- [Installing VSCode](#Installing-VSCode)
- [Installing Jupyter Notebook](#Installing-Jupyter-Notebook)

## Installing WSL
### Requirements
- Windows 7, 8, 8.1 do not support WSL. 
- Versions lower than 1803 of Windows 10 do not support WSL.

To check, press the Windows+R keys and run `winver` , you should see your version of Windows 10:

![winver](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/winver.jpg)
###### Updating Windows 10
If you have an older version, you can get it manually through the [Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).

![Updating Windows10](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Update%20Build.jpg)
###### Upgrading Windows 7, 8, 8.1
If you have a Windows 7, 8 or 8.1, you can upgrade it to Windows 10 manually through the [Create Windows 10 installation media](https://www.microsoft.com/en-us/software-download/windows10).

![Upgrade to Win10](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Upgrade%20to%20Win10.jpg)

Now that you have the right version of Windows, you can install WSL.
### Enabling Windows Subsystem for Linux
###### Method1 Using Settings
Press the Windows+R keys and run `optionalfeatures` , you should see Windows Features:

![Enable WSL](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Windows_Features.webp)

Check the `Windows Subsystem for Linux` option and click the OK button.Then click the Restart now button.
###### Method2 Using PowerShell
Open PowerShell as an admin and run the following script:

`dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

After the script is complete, you need to reboot your machine, since this enables new Windows features.

Once you complete the steps, the environment will be configured to download and run the distros of Linux on Windows 10.
### Installing Ubuntu 20.04
###### Method1 Using Microsoft Store
1. Open Microsoft Store.
2. Search for the Ubuntu
3. Select the Ubuntu 20.04 to install on your device.

![Store install]()
###### Method2 Using PowerShell
1. Type the following command to create folder `appx` on `C:\` directory and press Enter:

`mkdir c:\appx`

2. Type the following command to navigate to `appx` directory and press Enter:

`cd c:\appx`

Type the following command to download Ubuntu and press Enter:
- For x64 systems:

`Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile Ubuntu.appx -UseBasicParsing`
- For ARM64: 

`Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004arm -OutFile Ubuntu.appx -UseBasicParsing`

Type the following command to install Ubuntu and press Enter:

`Add-AppxPackage .\Ubuntu.appx`

The first launch will do the actual installation and will take a few seconds. The setup will also ask you for a username and a password for your Ubuntu configuration.
## Installing WSL2
### Requirements
- For x64 systems: Version 1903 or higher, with Build 18362 or higher.
- For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
- Builds lower than 18362 do not support WSL 2.
If you have an older version, Following [the instructions here](#Updating-Windows-10)
### Enabling Virtual Machine Platform
###### Method1 Using Settings
Press the Windows+R keys and run `optionalfeatures` , you should see Windows Features:

![Enable VMP](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Enable%20VMP.jpg)

Check the `Virtual Machine Platform` option and click the OK button.Then click the Restart now button.
###### Method2 Using PowerShell
Open PowerShell as an admin and run the following script:

`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

After the script is complete, you need to reboot your machine, since this enables new Windows features.
Once your PC has rebooted, we need to update the WSL 2 Linux kernel.Follow the download link, an msi installation will complete the update:
- For x64 systems: [WSL2 Linux kernel update package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
- For ARM64 systems: [WSL2 Linux kernel update package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)

![Installation MSI](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Installation%20WSL2.png)

OK, now it is time to set WSL2 to be the default for all WSL installations. Trust me, you don’t need to use WSL version 1 ever again. Open PowerShell and run:

`wsl --set-default-version 2`

The result is not very exciting, but it will come handy soon.Now ensure that WSL is correctly using version 2 for Ubuntu-20.04:

`wsl --list -v`

If this is still showing version 1, you can run the upgrade command:

`wsl --set-version Ubuntu-20.04 2`

<kbd>+</kbd>
<code>settings.json</code>
Now, You have Ubuntu-20.04 on version 2
## Installing Windows Terminal
### Requirements
Versions 1903 (build 18362) of Windows 10
## Installing WSH
## Installing PowerLevel10K
## Installing WSLU
## Installing WSL Sudo
## Installing VSCode
## Installing Jupyter Notebook
