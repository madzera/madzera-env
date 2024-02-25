
<p align="center">
  <a href="#" target="_blank" >
    <img alt="MadZera Development Environment" src="./.img/madzera_reverse.png" width="400" />
  </a>
</p>

“*A single compacted development environment is like a minimalist apartment.*”

## About the MadZera Development Environment
This is a repository that represents my personal development environment. I try to gather all possible tools and software that assist the software development process into one place, compacted and extremely organized, thus avoiding the bureaucratic process of configuration every time there is a new machine or when I need to reinstall everything again for any reason.

My environment consist only into 4 parts:

| Sofftware | Description |
|---|---|
| OS  | WSL  |
| Shell  | Oh My Zsh  |
| IDE  | Visual Studio Code  |
| Services  | Docker  |

With those basic parts, I believe that my development environment turns extremely portable, as I could manage to get the best of both Windows & Linux features, also I have a customized terminal with Oh My Zsh and an "All-in-One" development utilities inside of VSCode, including Docker containers.

In practical terms, when I am developing some stuff, I just do anything inside of VSCode, as it run under Remote WSL, with a customized Oh My Zsh Integrated terminal and for every 
development tools I just need of the vast plugins world that VSCode has to offer. In case I need a database, cache system, building tools, etc, I just use Docker.

“*My goal is to install the minimum stuffs as possible.*”

## WSL

For me, the best OS is not Windows neither Linux. It's both of them, combined into one.
Nothing better than editing a document using Word, for example, and at the same machine using essential services like Docker inside of Windows. This combination turns the development process extremely efficient, as I could just alternate between Windows and Linux by only using ALT-TAB. With the WSL it still becomes better because the WSL is thought to interoperate files and commands in a easy way. Using a very usual example, if the user wants to run the Windows VSCode inside of Linux Terminal, it can be run by just typing `code` command.

The WSL evolved so much in the last years. The Linux becomes an extension of the Windows, inheriting environment variables from Windows, allowing the execution of some Windows utilities inside of the own Linux terminal, and being extremely fast, because it is not a default virtualization as it is for the VirtualBox, for instance. The WSL adopts the **paravirtualization** concept, not hijacking machine resources, but instead of that, those resources are shared for both OS, it means the Linux uses the resources in a volatile way, it is not fixed.

Another powerful advantage of using WSL is treating the system like a 'box', as you can store and take the system anywhere else. You can export and backup the current state of your system in a single *.tar* file and import this in another machine. Additionally, it is recommended to take periodic backups because you can recover your system when a failure occurs.

### Versions

| OS | Version |
|---|---|
| WSL Version  | 2  |
| Windows  | 11  |
| Linux Distro  | Ubuntu 22.04.3 LTS  |

### Installation

1. You can install WSL by using Microsoft Store or by command line:
	1.1 You can download the Ubuntu distro inside of Microsoft Store.
	![Microsoft Store - Ubuntu](./.img/microsoft_store.png)
	1.2 Alternatively, you can run the following commands:
		1.2.1 Update the WSL, to get the latest version
		``` bash
		wsl --update
		```
		1.2.2 Guarantee that the Windows system is using the WSL version 
		``` bash
		wsl --set-default-version 2
		```
		1.2.3 Install Ubuntu default version (Ubuntu 22.04.3 LTS for the current date)
		```bash
		wsl --install
		```
2. After installation, you click to open then set your username and the *root* password for the *root* user. After that, you can close the Command Prompt because we will work with the *Windows Terminal* instead.
3. Inside of Microsoft Store, also install the **Windows Terminal** (not mandatory, but recommended).
	![Windows Terminal](./.img/windows_terminal.png)
	3.1 You can use my preferences [`settings.json`](./1_wsl/settings.json) by importing the file.
	3.2 To import, paste the file inside of: ***%LocalAppData%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState***
4. Verify if your installation was successful installed. You just need to open a new tab inside your Windows Terminal:
![Windows Terminal - Ubuntu](./.img/ubuntu_windows_terminal.png)

Your installation is ready.

### Configuration

As I said before, the Windows OS and WSL share the same resources from your machine. Howerver, you can determine the maximum resources the WSL can use. Those resources are related to CPUs cores, memory and memory swap.

This configuration is determined by creating a file inside of your *USER HOME* directory of your Windows OS. The file has to be named as `.wslconfig`.

**Do not forget to place this file in your Windows home directory**.

My WSL configuration uses 5 CPUs cores and 16GB of memory in a machine that has 64GB of memory with 10 CPUs core. In my opinion, using 8GB of memory is enough to run WSL, as your number of Docker images grows, you can configure WSL to use more resources.

Following, there is the code for the configuration example or, you can download my [`.wslconfig`](./1_wsl/.wslconfig):
```bash
	[wsl2]
	memory=8GB
	processors=2
	swap=1GB
```

## Oh My Zsh