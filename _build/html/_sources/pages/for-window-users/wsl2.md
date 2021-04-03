# Linux on Window by WSL 2

Developing on Window is not a struggle thing anymore with the Linux environment. Besides, by using paralelly 2 OS, you have all of the benefits of both environment, for example Linux for developing, Window for officing and gaming or somethings which is the upsides of Window.

> So cool, right? 

Although sometimes it still can not be as the real Linux but don't worry, the communication of the WSL 2 - the key magic mentioned today - is stronger everyday, you can find others help to tackle the issues.

Now let get started!
 
## 1. Window PC, Laptop

### Enable the Window Subsystem for Linux

Open the PowerShell and run the command below to enable this requirement for using any Linux distribution on Window

```shell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Go to next step.

### Check the requirement for WSL2

``` {important}
The Window 10 version need to be from version `1903` and build `18362`
```

To check the Window 10 version:

* Open `Run` or use the combo **Window + R**

```{figure} images/runapp.png
:name: runapp

Window Run
```

* Type `winver` then **ENTER**

```{figure} images/winver.png
:name: winver

Window Version
```

### Enable the Virtual Machine feature

Continue run this command in PowerShell to enable the virtual machine feature on Window

```shell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

```{important}
Now, you need to restart the computer, to make the changes affect to system.
```

### Download and install the Linux kernel update package

The current kernel is the original Window version. To use Linux, you need to update to the Linux kernel by the package 

* Link for x64 system: **[link](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)**

* Link for ARM64 system: **[link](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)**

* Open file `.msi` to instal the kernel update package

* Restart the computer

### Set the WSL 2 as default

Run this command in PowerShell:

```shell
wsl --set-default-version 2
```

### Download the Linux distribution and start using:

#### Download
Go to Microsoft Store and download your favorite Linux distro.
For example, I choose Ubuntu 18.04 below

```{figure} images/store.png
:name: store

Ubuntu 18.04 in Microsoft Store
```

#### Install

Just go to **Start Menu** and run the **Ubuntu 18.04**, or you can use **Search** to search for it

```{figure} images/install.png
:name: install

Ubuntu 18.04 in Microsoft Store
```
For the first time, it requires you create your username and password for Ubuntu, after that you can use it normally like any terminal on Ubuntu or MacOS

#### Some other options to run Ubuntu terminal except the Ubuntu app 

##### PowerShell

Run:

```
wsl --distribution/-d <Name of Linux Distribution>
```

```{figure} images/wsl-powershell.png
:name: wsl-powershell

Using Ubuntu command in PowerShell
```

##### Window Terminal

If this is the first time you hear the term "Window Termminal", let go to this [Microsoft documentation](https://docs.microsoft.com/en-us/windows/terminal/get-started) to find out. This app is so fancy (for me)

```{figure} images/winterminal.png
:name: winterminal

Window Terminal fancy appearance
```

* Choose Ubuntu 18.04 after click on the **down arrow** and start to use Ubuntu

```{figure} images/wsl-winterminal.png
:name: wsl-winterminal

Window Terminal fancy appearance
```

#### (Coming soon) Visual Studio Code

### (Coming soon) Use Linux GUI with computer screen 

## 2. Window Server (Coming soon)

