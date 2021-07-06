# How to install Ubuntu 20.04 + WSL2 + VScode + Windows Terminal + ZSH + PowerLevel10K + WSLU + WSL Sudo + Anaconda + Jupyter Notebook
## Table of Contents
- [WSL](#WSL)
  - [Requirements](#Requirements)
    - [Updating Windows 10](#Updating-Windows-10)
    - [Upgrading Windows 7, 8, 8.1](#upgrading-windows-7-8-81)
  - [Enabling Windows Subsystem for Linux](#Enabling-Windows-Subsystem-for-Linux)
    - [Method1 Using Settings](#Method1-Using-Settings)
    - [Method2 Using PowerShell](#Method2-Using-PowerShell)
  - [Installing Ubuntu 20.04](#installing-ubuntu-2004)
    - [Method1 Using Microsoft Store](#method1-using-microsoft-store)
    - [Method2 Using PowerShell](#Method2-using-powershell-1)
    - [Method3 Using Windows Package Manager](#)
      - [Installing Windows Package Manager](#)
- [WSL2](#WSL2)
  - [Requirements](#Requirements-1)
  - [Enabling Windows Subsystem for Linux](#Enabling-Windows-Subsystem-for-Linux)
    - [Method1 Using Settings](#Method1-Using-Settings)
    - [Method2 Using PowerShell](#Method2-Using-PowerShell)
  - [Updating WSL](#)
- [VSCode](#VSCode)
  - [Requirements](#Requirements)
  - [Installing](#)
    - [Method1 Using Setup File](#)
    - [Method2 Using Windows Package Manager](#)
  - [Configuring](#)
  - [Best Extensions](#)
- [Windows Terminal](#Windows-Terminal)
  - [Requirements](#Requirements)
  - [Installing](#)
    - [Method1 Using Microsoft Store](#method1-using-microsoft-store)
    - [Method2 Using PowerShell](#Method2-using-powershell-1)
    - [Method3 Using Windows Package Manager](#)
  - [Adding Ubuntu Tab to Windows Terminal](#)
  - [Configuring](#)
    - [commandline](#)
    - [colorScheme](#)
    - [fontFace](#)
    - [icon](#)
  - [Changing Default Console](#)
- [ZSH](#ZSH)
  - [Installing](#)
  - [Configuring](#)
    - [fuzzy finder fzf](#)
    - [git docker](#)
    - [zsh-completions](#)
    - [kubectl](#)
- [PowerLevel10K](#Installing-PowerLevel10K)
- [WSLU](#Installing-WSLU)
- [WSL Sudo](#Installing-WSL-Sudo)
- [Anaconda](#Anaconda)
- [Jupyter Notebook](#Jupyter-Notebook)

## WSL
### Requirements
- Windows 7, 8, 8.1 do not support WSL. 
- Versions lower than 1803 of Windows 10 do not support WSL.

To check, press the <kbd>⊞ Win</kbd> + <kbd>R</kbd> keys and run `winver` , you should see your version of Windows 10:

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
Press the <kbd>⊞ Win</kbd> + <kbd>R</kbd> keys and run `optionalfeatures` , you should see Windows Features:

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

![Store install](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Store%20Ubuntu-20.04.jpg)
###### Method2 Using PowerShell
1. Open Powershell and Type the following command to create folder `appx` on `C:\` directory and press Enter:

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

###### Method3 Using Windows Package Manager
To use Windows Package Manager, you should install it first:

1. Open Powershell and Type the following command to create folder `appx` on `C:\` directory and press Enter:

`mkdir c:\appx`

2. Type the following command to navigate to `appx` directory and press Enter:

`cd c:\appx`

Type the following command to download Ubuntu and press Enter:

`Invoke-WebRequest -Uri https://github.com/microsoft/winget-cli/releases/download/v1.0.11692/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle -OutFile WPM.msixbundle -UseBasicParsing`

Type the following command to install Ubuntu and press Enter:

`Add-AppxPackage .\WPM.msixbundle`
Open Powershell or Command Prompt and Type the following command to install Ubuntu 20.04

`winget install Canonical.Ubuntu`

The first launch will do the actual installation and will take a few seconds. The setup will also ask you for a username and a password for your Ubuntu configuration.
## WSL2
### Requirements
- For x64 systems: Version 1903 or higher, with Build 18362 or higher.
- For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
- Builds lower than 18362 do not support WSL 2.
If you have an older version, Following [the instructions here](#Updating-Windows-10)
### Enabling Virtual Machine Platform
###### Method1 Using Settings
Press the <kbd>⊞ Win</kbd> + <kbd>R</kbd> keys and run `optionalfeatures` , you should see Windows Features:

![Enable VMP](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Enable%20VMP.jpg)

Check the `Virtual Machine Platform` option and click the OK button.Then click the Restart now button.
###### Method2 Using PowerShell
Open PowerShell as an admin and run the following script:

`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

After the script is complete, you need to reboot your machine, since this enables new Windows features.
### Updating WSL
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

Now, You have Ubuntu-20.04 on version 2
## VSCode  
### Requirements
.NET Framework 4.5.2 or higher is required for VS Code. You can download latest version from [here](https://dotnet.microsoft.com/download/dotnet-framework)
### Installing
###### Method1 Using Setup Files
Go to [here](https://code.visualstudio.com/download) and download the latest installer for your Windows and follow the installation wizard to set up VS Code.

###### Method2 Using Windows Package Manager
Open Powershell or Command Prompt and Type the following command to install Visual Studio Code

`winget install Microsoft.VisualStudioCode`

### Configuring
To edit your VS Code configuration in JSON, open the command palette (Go to View -> Command Palette, or Press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>), type `Open Settings JSON` and select `Preferences: Open Settings (JSON)`:

![search setting.json]()

The `settings.json` file with all the non-default VS Code settings will open:

![setting.json]()

You can use these additional settings:
```
"editor.wordSeparators": "`~!@#$%^&*()=+[{]}\\|;:'\",.<>/?",
"editor.renderWhitespace": "all",
"diffEditor.ignoreTrimWhitespace": false,
"update.mode": "none",
"extensions.autoUpdate": false,
"window.title": "[${folderName}]${separator}${dirty}${activeEditorShort}${separator}${appName}",
"files.trimTrailingWhitespace": true,
"editor.tabSize": 2
```
- `editor.wordSeparators`: I removed the — from the word separators so I can select identifiers with a — in it via double-click on a word (sometimes these can be used in bash scripts)
- `editor.renderWhitespace`: I always want to see all the spaces in my source files
- `diffEditor.ignoreTrimWhitespace` : when I do a git merge, I want to see the differences due to space changes
- `update.mode` and `extensions.autoUpdate`: I don’t want the extensions to autoupdate, I need to control when they are updated as sometimes with WSL they break
- `window.title` : I added the [foldername] to the beginning of the window title, so I can recognize different go projects instances by their folder names (I can have 5 or 6 open at the same time, this is a saviour!)
- `files.trimTrailingWhitespace` : when a file is saved, all the extra spaces at the end of a line are trimmed out
- `editor.tabSize`: I like to use 2 spaces for tabs

Add the ones you want to use to your settings.json file and save it:

### Best Extensions
- [vscode-icons by VSCode Icons Team](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons)
- [Project Manager by Alessandro Fragnani](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)
- [Git Graph by mhutchie](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
- [Git Tree Compare by Maik Riechert](https://marketplace.visualstudio.com/items?itemName=letmaik.git-tree-compare)
- [GitLens — Git supercharged by Eric Amodio](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Git History by Don Jayamanne](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
- [Python by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Python Type Hint by njqdev](https://marketplace.visualstudio.com/items?itemName=njqdev.vscode-python-typehint)
- [Pyright by ms-pyright](https://marketplace.visualstudio.com/items?itemName=ms-pyright.pyright&ssr=false#overview)
- [Python Indent by Kevin Rose](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent)
- [Sort lines by Daniel Imms](https://marketplace.visualstudio.com/items?itemName=Tyriar.sort-lines)
- [Sourcery by sourcery](https://marketplace.visualstudio.com/items?itemName=sourcery.sourcery)
- [Tabnine AI Code Completion by TabNine](https://marketplace.visualstudio.com/items?itemName=TabNine.tabnine-vscode&ssr=false)
- [Python Preview by dongli](https://marketplace.visualstudio.com/items?itemName=dongli.python-preview)
- [AREPL for python by Almenon](https://marketplace.visualstudio.com/items?itemName=almenon.arepl)
- [Python Test Explorer for Visual Studio Code by Little Fox Team](https://marketplace.visualstudio.com/items?itemName=LittleFoxTeam.vscode-python-test-adapter)
- [Python Docstring Generator by Nils Werner](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring)
- [python snippets by Ferhat Yalçın](https://marketplace.visualstudio.com/items?itemName=frhtylcn.pythonsnippets)
- [Visual Studio IntelliCode by Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
- [Jupyter by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- [Django by Baptiste Darthenay](https://marketplace.visualstudio.com/items?itemName=batisteo.vscode-django)
- [Code Spell Checker by Street Side Software](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Bookmarks by Alessandro Fragnani](https://marketplace.visualstudio.com/items?itemName=alefragnani.Bookmarks)
- [Better Comments by Aaron Bond](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
- [Settings Sync by Shan Khan](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [Peacock by John Papa](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock&ssr=false#overview)
- [Bracket Pair Colorizer 2 by CoenraadS](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2)
- [Indent-Rainbow by oderwat](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)
- [Indenticator by SirTori](https://marketplace.visualstudio.com/items?itemName=SirTori.indenticator)
- [Dash by Budi Irawan](https://marketplace.visualstudio.com/items?itemName=deerawan.vscode-dash)
- [Auto Rename Tag by Jun Han](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)
- [Auto Close Tag by Jun Han](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)

## Windows Terminal
### Requirements
Versions 1903 (build 18362) of Windows 10
### Installing
###### Method1 Using Microsoft Store
1. Open Microsoft Store.
2. Search for the Windows Terminal
3. Select the Windows Terminal to install on your device.

![Store install](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Store%20windows%20terminal.jpg)
###### Method2 Using PowerShell
1. Open Powershell and Type the following command to create folder `appx` on `C:\` directory and press Enter:

`mkdir c:\appx`

2. Type the following command to navigate to `appx` directory and press Enter:

`cd c:\appx`

Type the following command to download Windows Termianl and press Enter:

`Invoke-WebRequest -Uri https://github.com/microsoft/terminal/releases/download/v1.8.1444.0/Microsoft.WindowsTerminal_1.8.1444.0_8wekyb3d8bbwe.msixbundle -OutFile Terminal.msixbundle -UseBasicParsing`

Type the following command to install Windows Terminal and press Enter:

`Add-AppxPackage .\Terminal.msixbundle`

###### Method3 Using Windows Package Manager
Open Powershell or Command Prompt and Type the following command to install Windows Terminal

`winget install Microsoft.WindowsTerminal`
### Configuring
 Windows Terminal will install and open with the default shell (PowerShell), let’s set Ubuntu to be the default console on Windows Terminal. Press the <kbd>Ctrl</kbd> + <kbd>,</kbd> keys or select the Settings menu as in the picture below:
 
 ![setting Terminal]()
 
 
###### Changing Default Console

###### commandline

###### colorScheme

###### fontFace

###### icon

## ZSH

## PowerLevel10K
## WSLU
## WSL Sudo
## Anaconda
## Jupyter Notebook
