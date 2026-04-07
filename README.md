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

### Network Configuration and DNS
`ip a`: Displays all network interfaces and their IP addresses.

`ping [ipaddress/domainname]`: Tests network connectivity by sending packets to a target.

<img width="500" height="300" alt="ip a and ping" src="https://github.com/user-attachments/assets/7c5ef132-b274-454c-9089-82c9c807d034" />


`/etc/hosts`: A plain text file to map IP addresses to hostnames or domain names.

`nslookup [ipaddress/domainname]`: Queries DNS servers for domain.

`whois [ipaddress/domainname]`: Shows domain registration details(Owner, Registrar, Creation date).

### System and Hardware Info
`lsusb`: Lists all USB devices (keyboard, mouse, flash drive).

`lspci`: Lists PCI hardware(GPU, Network card, Sound card).

`/proc/cpuinfo`: A text file that shows detailed CPU information.

### Software Installation Methods
Install with .deb file (e.g Google Chrome)

<img width="500" height="300" alt="Binary Download" src="https://github.com/user-attachments/assets/a925dd6d-90e1-4e40-b69d-4f00f80c6e7f" />

`sudo apt update`: Refreshes list of available packages from repositories

`sudo apt upgrade`: Installs latest updates for installed software

`sudo apt install [package]`: Install a specific package

`sudo apt search [package]`: Find any available packages related to the keyword

`/etc/apt/sources.list`: A text file that lists software repositories

### Compiling from Source 
Install build tools: 

```bash
sudo apt install build-essential
```

Create the Source Code File (hello_world.c):

```bash
nano hello_world.c
```

Type inside the file. For example:

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    printf("This program was compiled on Ubuntu using GCC.\n");
    return 0;
}
```

Save and exit:
- Press Ctrl + O (WriteOut)
- Press Enter (confirm filename)
- Press Ctrl + X (Exit)

## Lab 1b
### Linux Services, SSH, Firewalls & Compression
#### Activity 1
Install Apache2:
```bash
sudo apt install apache2
```

<img width="500" height="300" alt="Apache2 installation" src="https://github.com/user-attachments/assets/9fa24345-9167-4316-90c4-d04615773bae" />


Go to FireFox and run 127.0.0.1

<img width="500" height="300" alt="Apache2 Running" src="https://github.com/user-attachments/assets/ffca940f-f4f1-44a2-90c2-4bbdaac4de23" />

#### Activity 2
Install SSH server and Nmap: 
`sudo apt install openssh-server nmap`

Determine IP using `ip a`

Edit index.html using nano/gedit.

<img width="500" height="300" alt="Modified index html Page" src="https://github.com/user-attachments/assets/5eb70b78-81f4-4f21-a5a0-4cbfaa7ae023" />

Theoretically, if you have someone else doing this and get their ip address with their consent, you can view their Apache. Since I do not have a second person, I'm gonna skip this, my apologies.

### Linux File Permissions and Group Access Control
Command Reference:
- ls -l
- groupadd, delgroup
- adduser, deluser
- chown, chgrp, chmod [-R]
- su [user] -s /bin/bash
- whoami
- less /etc/passwd, less /etc/group
- rm -r /home/shared

Create 3 users:
```bash
sudo adduser alice
sudo adduser bob
sudo adduser mallory
```
<img width="500" height="300" alt="user alice created" src="https://github.com/user-attachments/assets/b5971b73-50ad-42ae-9721-e80a071e723f" />
<img width="500" height="300" alt="user bob created" src="https://github.com/user-attachments/assets/48802d56-645e-4bd5-9215-23f0885538d6" />
<img width="500" height="300" alt="user mallory created" src="https://github.com/user-attachments/assets/b95e056b-d08d-420d-adc1-ec2aa3272238" />


Create Group:
```bash
sudo groupadd sharedgroup
```

<img width="500" height="300" alt="Group Created and Configured (sharedgroup at bottom)" src="https://github.com/user-attachments/assets/73844fb9-fefb-4361-b7f0-2741078d6f14" />


Create directory and create ten files inside it:
```bash
sudo mkdir /home/shared
```

<img width="500" height="300" alt="&#39;shared&#39; Directory Created" src="https://github.com/user-attachments/assets/48a6b0da-c1a7-41f2-8c08-198b0bb58b8e" />


```bash
sudo touch /home/shared/file{1..10}.txt
```

<img width="500" height="300" alt="Ten Files created in shared folder" src="https://github.com/user-attachments/assets/a057f103-3191-4dcd-a5d1-430d50a32085" />

Change group ownership and add Alice and Bob to group:
```bash
sudo chgrp -R sharedgroup /home/shared
```

<img width="500" height="300" alt="chgrp" src="https://github.com/user-attachments/assets/58a5df3f-5e27-4f15-b7e4-63e51fd0ce90" />

```bash
sudo usermod -aG sharedgroup alice
sudo usermod -aG sharedgroup bob
```

Set directory permissions, Override Bob's rights, and Remove Mallory from any group with access.
```bash
sudo chmod -R 770 /home/shared
```

<img width="500" height="300" alt="chmod" src="https://github.com/user-attachments/assets/ca50fab2-ceb6-4d23-93de-2f6e5d12ee92" />

```
sudo chmod 750 /home/shared/*
```
Switch user: `su - alice`, `su - bob`, `su - mallory`; use `whoami` and `ls -l /home/shared` to verify access:

<img width="500" height="300" alt="alice" src="https://github.com/user-attachments/assets/7fdd6f5a-2530-405f-a651-5b33fe871a0d" />

<img width="500" height="300" alt="bob" src="https://github.com/user-attachments/assets/00147261-a409-4a11-b04f-bed4505da825" />

<img width="500" height="300" alt="mallory" src="https://github.com/user-attachments/assets/f854c220-d7ca-45f8-839a-c2ab0025ac24" />

### Lab 2b

### Create an Ubuntu VM on AWS

Create an AWS account. If you have one, log in. 3.	At the top-right, select a Region, Cheapest & safest: US East (N. Virginia). Go to E2 Dashboard and click Lauch Instance.

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/216fe92b-2efd-4df2-a686-4ff42353c9b8" />

Name: aws-webserver

AMI (OS):
- Ubuntu Server 20.04 or 22.04
-	Must show Free tier eligible

Instance Type:
- t2.micro or t3.micro
- Free tier eligible

Key Pair (SSH Access):
- Click Create new key pair
- Name: aws-webserver-key
- Type: RSA
- Format: .pem
- Download and save safely
- If you lose this file, you lose access to the VM.

Network & Security Group:
- Create or edit security group:
-     Name: ssh-and-web
-     Inbound rules:
-         SSH (22) → Source: Anywhere
-         HTTP (80) → Source: Anywhere
-         AWS may warn: “open to the world” This is expected for a public web server lab.

<img width="500" height="300" alt="Security Group Configured" src="https://github.com/user-attachments/assets/8edc0314-4530-472f-bc17-898516e3aaa6" />

Storage:
- Leave default: 8 GB gp2/gp3

Click Launch instance and Start Instance.

<img width="500" height="300" alt="EC2 Instance Launched" src="https://github.com/user-attachments/assets/ee0c0c8f-3ca8-4a35-9f44-a964b97ea3f9" />

There are two ways of SSH to the instance.
#### Option 1:
- Select the instance and click the connect button

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/0778700c-be5b-4484-8238-3f4cd3359afb" />

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/f3928273-2293-4b6e-86c8-4b536b9483e5" />

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/beddc538-348f-4971-abb2-c18a193a9d0c" />

#### Option 2:
Copy the Public IPv4 address or Public DNS name.
```bash
chmod 400 aws-webserver-key.pem
ssh -i aws-webserver-key.pem ubuntu@[public-ip]
```

<img width="500" height="300" alt="SSH Access Successful" src="https://github.com/user-attachments/assets/8fcd6a43-646d-449b-8f70-62c5a9327cae" />


