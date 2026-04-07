# BRG-27-labs

A file that logs my progress on the lab activities for the course

## Lab 1a
Objectives:
- Install a Virtual Machine software and the Ubuntu ISO
- Install Ubuntu on host with WSL
- Familiarise with Linux Commands

### VM Installation:

VirtualBox as choice for Virtual Machine.

Installed VirtualBox - https://www.virtualbox.org/

The Ubuntu ISO used for the VM is Ubuntu-24.04.4-Desktop.

Ubuntu - http://mirror.aarnet.edu.au/pub/ubuntu/releases/

GitHub repository set up for documentation.

<img width="500" height="300" alt="New Virtual Machine Created" src="https://github.com/user-attachments/assets/7c1528b6-85c8-456a-80e6-90513e0c1a41" />
<img width="500" height="300" alt="Ubuntu Running with GUI or CLI Access" src="https://github.com/user-attachments/assets/8067b562-e392-4c7f-91f6-67fe92f427d1" />


### WSL Ubuntu:

Enabled Windows Subsystem for Linux and Virtual Platform, installed Ubuntu using WSL.
```powershell

# wsl --install -d Ubuntu
```

<img width="416" height="106" alt="Screenshot 2026-04-05 090935" src="https://github.com/user-attachments/assets/6aaa60f2-0d90-4ad4-b29f-bf3f6456636b" />

## Linux Commands

### Basic
`pwd`: Show current directory

`cd [directory]`: Change directory

`cd ..`: Go up one level

`cd ~`: Go to home directory

### Process Monitoring
`ps -e`: Shows a snapshot of all running processes in the system

`top`: Displays real-time system activity like CPU usage, Memory Usage, and Running processes

### File & Directory Listing
`mkdir [directory]`: Create directory

`rmdir [directory]`: Remove empty directory

`rm [file]` → Delete file

`rm -r [directory]` → Delete directory

`ls`: Lists files and folders in the current directory.

  `ls -la`: Shows all files, including hidden ones.
  
  `ls -alt`: Lists all files sorted by last modified time.
  
  `ls -lah`: Same as -la but with human-readable sizes.
  
### File Creation, Editing & Viewing
`touch [filename].txt`: Creates an empty file. If file exists, updates its timestamp.

`gedit [filename].txt`: Opens a graphical text editor (GUI).

`nano [filename].txt`: Opens a terminal-based text editor.

`cat [filename].txt`: Displays file content in the terminal.

`less [filename].txt`: Views file content one page at a time. Better than cat for large files.

### File Management
`cp`: Copies files or directories.

```bash
cp [original].txt [copied].txt
```

`mv`: Moves or renames files.

For moving

```bash
mv [filename].txt [directory]
```

For renaming

```bash
mv [filename].txt [newfilename].txt
```
### System Information
`uname -a`: Displays system/kernel information

`lsb_release -a`: Shows Linux distribution details

`hostnamectl`: Displays and manages Hostname, OS info, Kernel version, and System architecture

### Super User and Permissions
`whoami`: Shows the current logged-in user.

`sudo whoami`: Runs the command as the root (superuser).

`adduser [user]`: Create a new user account.

However, permission would be denied as creating users requires administrative privileges. So, do this instead.
```bash
sudo adduser [user]
```

The root user is the most powerful account in Linux. They have unrestricted access to:
- All files
- All commands
- System configurations

#### Best Practice for Privilege Use
Do:
- Use sudo only when necessary
- Run commands as a normal user most of the time
- Double-check commands before using sudo
- Follow the principle of least privilege

Don’t:
- Log in as root for everyday tasks
- Run unnecessary commands with sudo
- Trust unknown commands with elevated privileges

