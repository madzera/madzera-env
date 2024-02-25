
<p align="center">
  <a href="#" target="_blank" >
    <img alt="MadZera Development Environment" src="./.img/madzera_reverse.png" width="400" />
  </a>
</p>

“*A single compacted development environment is like a minimalist apartment.*”

## About the MadZera Env
This is a repository that represents my personal development environment. I try 
to gather all possible tools and software that assist the software development 
process into one place, compacted and extremely organized, thus avoiding the 
bureaucratic process of configuration every time there is a new machine or 
when I need to reinstall everything again for any reason.

My environment consist only into 4 parts:

|---|---|
| OS  | WSL  |
| Shell  | Oh My Zsh  |
| IDE  | Visual Studio Code  |
| Services  | Docker  |

With those basic parts, I believe that my development environment turns extremely 
portable, as I could manage to get the best of both Windows & Linux features, also 
I have a customized terminal with Oh My Zsh and an "All-in-One" development utilities
inside of VSCode, including Docker containers.

In practical terms, when I am developing some stuff, I just do anything inside of VSCode, 
as it run under Remote WSL, with a customized Oh My Zsh Integrated terminal and for every 
development tools I just need of the vast plugins world that VSCode has to offer. In case 
I need a database, cache system, building tools, etc, I just use Docker.

“*My goal is to install the minimum stuffs as possible.*”

## WSL

For me, the best OS is not Windows neither Linux. It's both of them, combined into one.
Nothing better than editing a document using Word, for example, and at the same machine using 
essential services like Docker inside of Windows. This combination turns the development process 
extremely efficient, as I could just alternate between Windows and Linux by only using ALT-TAB. With 
the WSL it still becomes better because the WSL is thought to interoperate files and commands in a easy 
way. Using a very usual example, if the user wants to run the Windows VSCode inside of Linux Terminal, 
it can be run by just typing `code` command.

The WSL evolved so much in the last years. The Linux becomes an extension of the Windows, inheriting 
environment variables from Windows, allowing the execution of some Windows utilities inside of the own Linux 
terminal, and being extremely fast, because it is not a default virtualization as it is for the VirtualBox. 
The WSL adopts the **paravirtualization** concept, not hijacking machine resources, but instead of 
that, those resources are shared for both OS, it means the Linux uses the resources in a volatile way, it 
is not fixed.

### Versions

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
		1.2.2 Guarantee that the Windows system is using the WSL version 2
		``` bash
		wsl --set-default-version 2
		```
		1.2.3 Install Ubuntu default version (Ubuntu 22.04.3 LTS for the current date)
		```bash
		wsl --install
		```
2. After installation, set the *root* password for the *root* user.
3. Inside of Microsoft Store, also install the **Windows Terminal** (not mandatory, but recommended).
![Windows Terminal](./.img/windows_terminal.png)
	3.1 You can use my preferences [`settings.json`](./1_wsl/settings.json) by import.
	3.2 To import, paste the file inside of: ** *%LocalAppData%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState* **



