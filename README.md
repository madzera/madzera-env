
<p align="center">
  <a href="#" target="_blank" >
    <img alt="MadZera Development Environment" src="./.img/madzera_reverse.png" width="300" height="300" />
  </a>
</p>

“*A single and compacted development environment is like a minimalist apartment.*”

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

“*My goal is install the minimum stuffs as possible.*”

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
	
	- Update the WSL, to get the latest version: `wsl --update`
	- Guarantee that the Windows system is using the WSL version: `wsl --set-default-version 2`
	- Install Ubuntu default version (Ubuntu 22.04.3 LTS for the current date): `wsl --install`

2. After installation, you click to open then set your username and the *root* password for the *root* user. After that, you can close the Command Prompt because we will work with the *Windows Terminal* instead.

3. Inside of Microsoft Store, also install the **Windows Terminal** (not mandatory, but recommended).
	![Windows Terminal](./.img/windows_terminal.png)
	
	3.1 You can use my preferences [`settings.json`](./1_wsl/settings.json) by importing the file.

	3.2 To import, paste the file inside of: ***%LocalAppData%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState***

4. Verify if your installation was successful installed. You just need to open a new tab inside your Windows Terminal:
![Windows Terminal - Ubuntu](./.img/ubuntu_windows_terminal.png)

Now your installation is ready. If you desire in the future to backup your entirely environment, run the command in Windows PowerShell to export your WSL in a *.tar* file:

- Stop the WSL before:
```bash
wsl --shutdown
```
- Export your current state of your WSL:
```bash
wsl --export <<IMAGE NAME>> <<TARGET FILE>>.tar
```

For importing, use:
```bash
wsl --import <<NEW IMAGE NAME>> <<SOURCE DIR FILE>> <<FILENAME>>.tar
```

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

Oh My Zsh is framework that works over the ZSH Shell. It allows you to style and customize your Shell to your liking, adding styles to your terminal, as well as helping you quite significantly when typing commands.

Oh My Zsh (ohmyzsh) runs over the ZSH Shell, which in turn is an abstraction of the Linux Bash, and Bash works over Linux's SH (Linux Shell):

`sh > bash > zsh > ohmyzsh`

For who works too much with the command lines, this tool is essential to improve your efficiency. Below, some advantages using ohmyzsh:

- The output of commands becomes more informative and enjoyable. It shows up the location, whether the directory is a Git Repository and returns the result of the command:
![Oh My ZSH ](./.img/ohmyzsh.png)
-  If you work with Docker, a platform that its commands usually are long, the ohmyzsh improves your productivity, as it auxiliates you to complete your long commands:
![Oh My ZSH - Auto Complete ](./.img/ohmyzsh_autocomplete.png)
- If you want to list `git commit` commands, to see all your previous commentaries for instance, the ohmyzsh is able to store a history of your commands by pressing ↑. In that case, this will list all commands that start with `git commit`.

Those features, supported by the Oh My Zsh are so much important, that I consider this tool essential to develop applications.

### Installation

To install this delightful terminal, you will need of the ohmyzsh and a **powerlevel10k** plugin to customize the themes of your terminal.

#### Prerequisites

- `curl` or `wget` should be installed
- `git` should be installed (recommended v2.4.11 or higher)

#### ohmyzsh installation

You just need to execute the following command, depending on if had you used `curl`or `wget`:

| Method    | Command                                                                                           |
| :-------- | :------------------------------------------------------------------------------------------------ |
| **curl**  | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **wget**  | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`   |

#### ohmyzsh configuration

After installation, I recommend to restart the Ubuntu by just closing the terminal window and reopening again, then you will be able to see a `.zshrc`file in your Ubuntu user home directory. This file contains all metadata configuration of your shell, but there are two configuration that cannot be missing:

1. You must choice the plugin theme, and in this case, you should put:

	`ZSH_THEME="powerlevel10k/powerlevel10k"`

2. Define some importants plugin in the file:

	`plugins=(git git-flow zsh-syntax-highlighting zsh-autosuggestions)`

The `.zshrc`file can have other purposes, such as I did it by defining some environments variables and configuring a toll called *asdf*, but it is not relevant for this tutorial.

If you want to use my `.zshrc` as template, you can find by clicking [here](./2_ohmyzsh/.zshrc). You just need do copy-paste to your user home directory. In that case, just do not forget to erase my own configurations that you don't use, like the environment variables and *asdf* config.

#### powerlevel10k installation

1. Run the following command:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
2. Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc` (mentioned above).

#### powerlevel10k configuration

1. Install new fonts from this [link](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k). The fonts will make your environment more ergonomic
2. You can configure the layout of your ohmyzsh by importing my configuration file inside your home directory or through prompt command.
	- You can use my *.p10k.zsh* configuration file. Just copy the [file](./2_ohmyzsh/.p10k.zsh) and paste inside your Ubuntu home directory.
	- To configure by prompt command and generating your own *.p10k.zsh* file, just run the command: `p10k configure`
	- Then, choose your preferred styles: ![p10k prompt configuration](https://res.cloudinary.com/practicaldev/image/fetch/s--71QSuVWr--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/xf9fk2sgux1niog4vhpy.gif)

Now, you have a wonderful terminal, increasing your productivity drastically.