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
### Process Monitoring
**ps -e**: Shows a snapshot of all running processes in the system
**top**: Displays real-time system activity like CPU usage, Memory Usage, and Running processes
### File & Directory Listing
**ls**: Lists files and folders in the current directory.
  **ls -la**: Shows all files, including hidden ones.
  **ls -alt**: Lists all files sorted by last modified time.
  **ls -lah**: Same as -la but with human-readable sizes.
### File Creation, Editing & Viewing
**touch**: Creates an empty file. If file exists, updates its timestamp.

```bash
touch [filename].txt
```

**gedit**: Opens a graphical text editor (GUI).

```bash
gedit [filename].txt
```

**nano**: Opens a terminal-based text editor.

```bash
nano [filename].txt
```

**cat**: Displays file content in the terminal.

```bash
cat [filename].txt
```

**less**: Views file content one page at a time. Better than cat for large files.

```bash
less [filename].txt
```
