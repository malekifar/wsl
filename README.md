# How to install Ubuntu 20.04 + WSL2 + VScode + Windows Terminal + Anaconda + Git + ZSH + WSLU + WSL Sudo
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
    - [Method3 Using Windows Package Manager](#method3-using-windows-package-manager)
      - [Installing Windows Package Manager](#)
- [WSL2](#WSL2)
  - [Requirements](#Requirements-1)
  - [Enabling Windows Subsystem for Linux](#Enabling-Windows-Subsystem-for-Linux)
    - [Method1 Using Settings](#Method1-Using-Settings)
    - [Method2 Using PowerShell](#method2-using-powershell-2)
  - [Updating WSL](#updating-wsl)
- [VSCode](#VSCode)
  - [Requirements](#requirements-2)
  - [Installing](#installing)
    - [Method1 Using Setup File](#method1-using-setup-files)
    - [Method2 Using Windows Package Manager](#method2-using-windows-package-manager)
  - [Configuring](#configuring)
  - [Extensions](#extensions)
    - [Best Extensions](#best-extensions)
- [Windows Terminal](#Windows-Terminal)
  - [Requirements](#requirements-3)
  - [Installing](#installing-1)
    - [Method1 Using Microsoft Store](#method1-using-microsoft-store-1)
    - [Method2 Using PowerShell](#method2-using-powershell-3)
    - [Method3 Using Windows Package Manager](#method3-using-windows-package-manager-1)
  - Adding Ubuntu Tab to Windows Terminal =>coming soon
  - [Configuring](#configuring-1)
    - [fontFace](#fontface)
    - [colorScheme](#colorscheme)
    - [icon](#icon)
  - [Changing Default Console](#changing-default-console)
- [Anaconda](#anaconda)
  - [Installing](#installing-2)
  - [Conda init](#conda-init)
- [Git](#git)
- [ZSH](#ZSH)
  - [Installing](#installing-3)
  - [Installing oh-my-zsh](#installing-oh-my-zsh)
  - [Conda init](#onda-init-1)
  - [ZSH Plugins](#zsh-plugins)
    - [fuzzy finder fzf](#fuzzy-finder-fzf)
    - [autojump](#autojump)
    - [zsh-autosuggestions](#zsh-autosuggestions)
    - [enhancd](#enhancd)
    - [zsh-completions](#zsh-completions)
    - [fast Syntax Highlighting](#fast-syntax-highlighting)
    - [git, docker, colored-man-pages, colorize, dash & command-not-found](#git-docker-colored-man-pages-colorize-dash--command-not-found)
- [ZSH Themes](#zsh-themes)
  - [PowerLevel10K](#Installing-PowerLevel10K)
  - [Agnoster](#agnoster)
  - [robbyrussell](#robbyrussell)
- [WSLU](#Installing-WSLU)
- [WSL Sudo](#Installing-WSL-Sudo)

- [Jupyter Notebook](#Jupyter-Notebook)

## [WSL](https://github.com/microsoft/WSL)
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
Open PowerShell as an Administrator (Press <kbd>⊞ Win</kbd> + <kbd>X</kbd> keys then select `Windows PowerShell (Admin)` and run the following script:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

After the script is complete, you need to reboot your machine, since this enables new Windows features.

Once you complete the steps, the environment will be configured to download and run the distros of Linux on Windows 10.
### Installing Ubuntu 20.04
###### Method1 Using Microsoft Store
1. Open Microsoft Store.
2. Search for the Ubuntu
3. Select the Ubuntu 20.04 to install on your device.

![Store install](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Store%20Ubuntu-20.04.jpg)
###### Method2 Using PowerShell
Open Powershell and Type the following command to download Ubuntu in temp folder and install it then press Enter:
- For x64:

```powershell
cd C:\windows\Temp; Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile Ubuntu.appx -UseBasicParsing; Add-AppxPackage .\Ubuntu.appx
```
- For ARM64: 

```powershell
cd C:\windows\Temp; Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004arm -OutFile Ubuntu.appx -UseBasicParsing; Add-AppxPackage .\Ubuntu.appx
```

###### Method3 Using Windows Package Manager
To use Windows Package Manager, you should install it first:

Open Powershell and Type the following command to download Windows Package Manager in temp folder and install it then press Enter:

```powershell
cd C:\windows\Temp; Invoke-WebRequest -Uri https://github.com/microsoft/winget-cli/releases/download/v1.0.11692/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle -OutFile WPM.msixbundle -UseBasicParsing; Add-AppxPackage .\WPM.msixbundle
```

Open Powershell or Command Prompt and Type the following command to install Ubuntu 20.04

```powershell
winget install Canonical.Ubuntu
```

The first launch will do the actual installation and will take a few seconds. The setup will also ask you for a username and a password for your Ubuntu configuration.
## [WSL2](https://github.com/microsoft/WSL2-Linux-Kernel)
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
Open PowerShell as an Administrator (Press <kbd>⊞ Win</kbd> + <kbd>X</kbd> keys then select `Windows PowerShell (Admin)` and run the following script:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

After the script is complete, you need to reboot your machine, since this enables new Windows features.
### Updating WSL
Once your PC has rebooted, we need to update the WSL 2 Linux kernel.Follow the download link, an msi installation will complete the update:
- For x64 systems: [WSL2 Linux kernel update package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
- For ARM64 systems: [WSL2 Linux kernel update package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)

![Installation MSI](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Installation%20WSL2.png)

OK, now it is time to set WSL2 to be the default for all WSL installations. Trust me, you don’t need to use WSL version 1 ever again. Open PowerShell and run:

`wsl --set-default-version 2; wsl --set-version Ubuntu-20.04 2; wsl -l -v`

Now, You have Ubuntu-20.04 on version 2
## [VSCode](https://github.com/microsoft/vscode)
### Requirements
.NET Framework 4.5.2 or higher is required for VS Code. You can download latest version from [here](https://dotnet.microsoft.com/download/dotnet-framework)
### Installing
###### Method1 Using Setup Files
Go to [here](https://code.visualstudio.com/download) and download the latest installer for your Windows and follow the installation wizard to set up VS Code.

###### Method2 Using Windows Package Manager
Open Powershell or Command Prompt and Type the following command to install Visual Studio Code

```powershell
winget install Microsoft.VisualStudioCode
```

### Configuring
To edit your VS Code configuration in JSON, open the command palette (Go to View -> Command Palette, or Press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>), type `Open Settings JSON` and select `Preferences: Open Settings (JSON)`:

![search setting.json](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/search%20setting.json.jpg)

The `settings.json` file with all the non-default VS Code settings will open:

![setting.json](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/setting.json.jpg)

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

![addedsetting.json](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/addedsetting.json.jpg)
### Install an extension
To install an extension, select the Install button. Once the installation is complete, the Install button will change to the Manage gear button.

![Install an extension](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Install%20an%20extension.jpg)
### Extensions
VSCode has many extensions. You can find a list of pre-installed extensions at [here](https://marketplace.visualstudio.com)
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
- [Material Theme by Equinusocio](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme)
- [Noctis by Liviu Schera](https://marketplace.visualstudio.com/items?itemName=liviuschera.noctis)
- [Solarized by Ryan Olson](https://marketplace.visualstudio.com/items?itemName=ryanolsonx.solarized)
- [Remote - WSL by Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)
- [Auto Rename Tag by Jun Han](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)
- [Auto Close Tag by Jun Han](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)

## [Windows Terminal](https://github.com/microsoft/terminal)
### Requirements
Versions 1903 (build 18362) of Windows 10
### Installing
###### Method1 Using Microsoft Store
1. Open Microsoft Store.
2. Search for the Windows Terminal
3. Select the Windows Terminal to install on your device.

![Store install](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/Store%20windows%20terminal.jpg)
###### Method2 Using PowerShell
1. Open Powershell and Type the following command to download Windows Terminal in temp folder and install it then press Enter:

```powershell
cd C:\windows\Temp; Invoke-WebRequest -Uri https://github.com/microsoft/terminal/releases/download/v1.8.1444.0/Microsoft.WindowsTerminal_1.8.1444.0_8wekyb3d8bbwe.msixbundle -OutFile Terminal.msixbundle -UseBasicParsing; Add-AppxPackage .\Terminal.msixbundle
```

###### Method3 Using Windows Package Manager
Open Powershell or Command Prompt and Type the following command to install Windows Terminal

```powershell
winget install Microsoft.WindowsTerminal
```
### Configuring
 Windows Terminal will install and open with the default shell (PowerShell), let’s set Ubuntu to be the default console on Windows Terminal. Press the <kbd>Ctrl</kbd> + <kbd>,</kbd> keys or select the Settings menu as in the picture below:
 
 ![setting Terminal](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/terminal-setting.jpg)
 
###### fontFace
Open Powershell and Type the following command to download [requirement fonts](https://github.com/ryanoasis/nerd-fonts) in temp folder and install it then press Enter:
```powershell
cd C:\windows\Temp; Invoke-WebRequest -Uri https://github.com/malekifar/wsl/releases/download/v1.0/Fonts.zip -OutFile Fonts.zip; Expand-Archive C:\windows\Temp\Fonts.zip -DestinationPath C:\windows\Temp; .\install.ps1
```
###### colorScheme
###### icon
![setting_complete](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/setting_complete.png)
###### Changing Default Console
## [Anaconda](https://www.anaconda.com/)
### Installing
Type the following command to download Windows Terminal in temp folder and install it then press Enter:
- For x86:
```zsh
cd /tmp && curl https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh --output anaconda.sh && bash anaconda.sh
```
- For ARM64:
```zsh
cd /tmp && https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-aarch64.sh --output anaconda.sh && bash anaconda.sh
```
You’ll receive these following outputs:
```
Output:

Welcome to Anaconda3 2021.05

In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>>  
```
Press <kbd>Enter</kbd> to continue and then press <kbd>Enter</kbd> to read through the license. Once you’re done reading the license, you’ll be prompted to approve the license terms:
```
Output:

Do you approve the license terms? [yes|no]
```
As long as you agree, type `yes`.
```
Output:

Anaconda3 will now be installed into this location:
/home/usename/anaconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/home/username/anaconda3] >>> 
```
At this point, you’ll be prompted to choose the location of the installation. You can press <kbd>Enter</kbd> to accept the default location, or specify a different location to modify it.
```
output:

Preparing transaction: done
Executing transaction: done
installation finished.
Do you wish the installer to initialize Anaconda3
by running conda init? [yes|no]
[no] >>> 
```
Type `yes` so that you can initialize Anaconda3. You’ll receive some output that states changes made in various directories. One of the lines you receive will thank you for installing Anaconda.
```
Output:

Thank you for installing Anaconda3!
```
### Conda init
```zsh
source ~/anaconda3/etc/profile.d/conda.sh && conda init bash && conda init zsh
```
## [Git](https://github.com/git/git)
Install Git using apt-get:
```zsh
sudo apt-get update && sudo apt-get install git
```
## [ZSH](https://github.com/zsh-users/zsh)
### Installing
Type the following commands to update apt and install zsh then press Enter:

```zsh
sudo apt update && sudo apt install zsh
```

Now set zsh to be your default shell:
```zsh
chsh -s $(which zsh)
```
Open a new terminal and the initial zsh prompt will show up, signaling that zsh is now the default shell. At this point pick <kbd>2</kbd> — it will populate the zsh configuration file `~/.zshrc` with defaults.

Let’s check again that zsh is the default shell:

```zsh
echo $SHELL && $SHELL --version
```

you should get the following results:

![shell version](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/shell%20version.jpg)

### Installing [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh)
Now we can install oh-my-zsh

```zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)
```

Notice that oh-my-zsh updated your `~/.bashrc` file and made a backup of the old one. Also notice that the prompt changed now, it is just your username.

OK, we are readty to customize oh-my-zsh next.
### Conda init
```zsh
source ~/anaconda3/etc/profile.d/conda.sh && conda init zsh
```
### ZSH Plugins
Oh-My-ZSH has many plugins. You can find a list of pre-installed plugins at [here](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins)

###### [fuzzy finder fzf](https://github.com/junegunn/fzf)
```zsh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.zsh/.fzf && ~/.zsh/.fzf/install
```
###### [autojump](https://github.com/wting/autojump)
```zsh
git clone git://github.com/wting/autojump.git ~/.zsh/autojump && cd ~/.zsh/autojump && ./install.py && echo "source ~/.autojump/etc/profile.d/autojump.sh" >> ~/.zshrc
```
###### [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
```zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions && echo "source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
```
###### [enhancd](https://github.com/b4b4r07/enhancd)
```zsh
git clone https://github.com/b4b4r07/enhancd ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/enhancd && echo "source ~/.oh-my-zsh/custom/plugins/enhancd/init.sh" >> ~/.zshrc
```
###### [zsh-completions](https://github.com/zsh-users/zsh-completions)
```zsh
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/zsh-completions && echo "source ~/.oh-my-zsh/custom/plugins/zsh-completions/zsh-completions.plugin.zsh" >> ~/.zshrc
```
###### [fast Syntax Highlighting](https://github.com/zdharma/fast-syntax-highlighting)
```zsh
git clone https://github.com/zdharma/fast-syntax-highlighting ${ZSH_CUSTOM:=~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting && echo "source ~/.oh-my-zsh/custom/plugins/fast-syntax-highlighting/fast-syntax-highlighting.plugin.zsh" >> ~/.zshrc
```
###### [git](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git), [docker](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker), [colored-man-pages](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colored-man-pages), [colorize](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colorize), [dash](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dash) & [command-not-found](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/command-not-found)
```zsh
sed -i 's/plugins=\(.*\)/plugins=\(git docker zsh-completions colored-man-pages fast-syntax-highlighting colorize dash command-not-found\)/g' ~/.zshrc
```
### ZSH Themes
We are going to make our color pretty and prompt useful. There are a lot of themes in oh-my-zsh, you can see them [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes):
###### [PowerLevel10K](https://github.com/romkatv/powerlevel10k)(recommended)
```zsh
sed -i 's/ZSH_THEME=".*"/ZSH_THEME="powerlevel10k\/powerlevel10k"/g' ~/.zshrc
```
![powerlevel10k](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/powerlevel10k.jpg)
###### Agnoster
```zsh
sed -i 's/ZSH_THEME=".*"/ZSH_THEME="agnoster"/g' ~/.zshrc
```
![Agnoster]()
###### robbyrussell
```zsh
sed -i 's/ZSH_THEME=".*"/ZSH_THEME="robbyrussell"/g' ~/.zshrc
```
![robbyrussell](https://raw.githubusercontent.com/malekifar/wsl/main/screenshots/robbyrussell.jpg)
## [WSLU](https://github.com/wslutilities/wslu)
This is a collection of utilities for Windows 10 Linux Subsystem, such as retrieving Windows 10 environment variables or creating your favorite Linux GUI application shortcuts on Windows 10 Desktop. To install it:
```zsh
sudo apt install gnupg2 apt-transport-https && wget -O - https://pkg.wslutiliti.es/public.key | sudo tee -a /etc/apt/trusted.gpg.d/wslu.asc && echo "deb https://pkg.wslutiliti.es/debian buster main" | sudo tee -a /etc/apt/sources.list && sudo apt update && sudo apt install wslu && sudo apt-get remove lynx links links2
```
For changing your default browser:
```zsh
wslview -r $(wslpath -au 'exe file of browser')
```
For Chrome:
```zsh
wslview -r $(wslpath -au 'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe')
```
For Firefox:
```zsh
wslview -r $(wslpath -au 'C:\Program Files\Mozilla Firefox\firefox.exe')
```
For Edge:
```zsh
wslview -r $(wslpath -au 'C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe')
```
## [WSL Sudo](https://github.com/Chronial/wsl-sudo)
This tool allows you to run applications in windows elevated user mode from a non-elevated wsl shell. To install it:
```zsh
mkdir ~/.wudo && cd ~/.wudo && git clone https://github.com/Chronial/wsl-sudo.git && alias wudo="python3 ~/.wudo/wsl-sudo/wsl-sudo.py"
```
