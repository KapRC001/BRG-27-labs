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

Compile with GCC:
```bash
gcc hello_world.c -o hello_world_executable
```

Run executable:
```bash
./hello_world_executable
```
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

### File Search, Analysis & Archiving in Linux
 `find . -name "*.txt"`: Find all .txt files in the current directory and subdirectories.
 `grep`: Searches for patterns in text files.
 `du -a`: Estimates file and directory space usage.
 
 <img width="500" height="300" alt="du -a" src="https://github.com/user-attachments/assets/7d9571f6-0259-4808-b307-4f12b36daac9" />

 `sed -e 's/\s/\n/g'`: Replace all whitespace with newlines.
 
<img width="500" height="300" alt="sed" src="https://github.com/user-attachments/assets/02855960-a08f-4a95-925a-9671579b1c61" />

## Lab 2b

### Create an Ubuntu VM on AWS

Create an AWS account. If you have one, log in.	At the top-right, select a Region, Cheapest & safest: US East (N. Virginia). Go to E2 Dashboard and click Lauch Instance.

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
- Name: ssh-and-web
- Inbound rules:
  SSH (22) → Source: Anywhere
  HTTP (80) → Source: Anywhere
  AWS may warn: “open to the world” This is expected for a public web server lab.

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

<img width="500" height="500" alt="SSH Access Successful" src="https://github.com/user-attachments/assets/8fcd6a43-646d-449b-8f70-62c5a9327cae" />


### Cloud Web Server Deployment
#### File Transfer & Permissions:
- `wget [file url]`: Download remote files to VM.
- `sudo cp [filename].txt [directory]`: Move them into the web directory.
- `scp -i key.pem localfile ubuntu@IP:/home/ubuntu/`: Copy files from local to VM.
- `chmod` or change ownership if facing file access issues.

Run `sudo apt update` and install Apache using `sudo apt install apache2`.

<img width="500" height="300" alt="Apache Installed" src="https://github.com/user-attachments/assets/c3f38b76-7f8a-4542-9966-cf9d4dca439a" />


Access the server using its public IP in a browser.

<img width="500" height="300" alt="Apache Tested" src="https://github.com/user-attachments/assets/3aba3c40-de6d-4544-9aa9-13b4770941aa" />


Modify `/var/www/html/index.html` using nano and test the changes live.
```bash
sudo nano /var/www/html/index.html
```

<img width="500" height="300" alt="Custom index html Edited" src="https://github.com/user-attachments/assets/eeb3ab90-76da-4920-b9b4-5563644d0a00" />


#### Download and copy files to `/var/www/html/` using `wget` and `sudo cp`. For my example:
```bash
wget https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf
```
<img width="500" height="300" alt="External File Downloaded with wget" src="https://github.com/user-attachments/assets/b7924e11-350c-4c11-94cb-df7b1bc31cea" />

```bash
sudo cp dummy.pdf /var/www/html/
```
<img width="500" height="300" alt="File Copied to Web Root" src="https://github.com/user-attachments/assets/5109c0fb-8869-46e2-8fdb-a7329e3e6bd4" />


#### Create hyperlinks in `index.html` using anchor `<a>` tags:
```bash
sudo nano /var/www/html/index.html
```
Add the following:

<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/d8fcfc89-fa3d-4237-91dc-4dd6589ebabd" />

Save and exit:
- Press Ctrl + O (WriteOut)
- Press Enter (confirm filename)
- Press Ctrl + X (Exit)

Go back and check on the changes made, there should be button called "Click me" that will send you to the linked pdf.

<img width="500" height="300" alt="Link Inserted in HTML Page" src="https://github.com/user-attachments/assets/4dc30c51-ccc1-4917-845c-dad2eb59d501" />


#### Test access using different devices and browsers:
This is an image of accessing the server with the host computer.

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/6e3d65a0-91fb-40ca-9781-29547bce1c65" />

## Lab 2b
### Introduction to Bash Scripting & System Automation
#### Navigating the File System and Managing Files
```bash
mkdir LabFiles
```
**What command did you use to create a directory?**

I used the `mkdir` command to make a directory called LabFiles

Create a note.txt:
```bash
cat > notes.txt << "EOF"
This is my lab notes file.
Created on $(date)
Topics covered: Linux commands, file manipulation, and directory management.
EOF
```
**How can you view file content without a GUI editor?**

There are several command-line commands to view file content without opening a GUI editor, such as:
```bash
cat note.txt
```

<img width="500" height="300" alt="Directory and File Operations Completed" src="https://github.com/user-attachments/assets/8c28e409-ae2b-41e0-923b-090bc61854dd" />


**What is the difference between cp and mv?**

The main difference is that `cp` (copy) duplicates a file, leaving the original intact, while `mv` (move) relocates or renames a file, removing it from its original location.

#### Creating and Executing Basic Bash Scripts
Create a script using a text editor, such as `hello_world.sh`:
```bash
nano hello_world.sh
```
Type the following content:
```bash
#!/bin/bash
# This is my first bash script
echo "Hello, World! This is my custom bash script."
echo "Current date and time: $(date)"
echo "Running as user: $(whoami)"
```

Save and exit:
- Press Ctrl + O (WriteOut)
- Press Enter (confirm filename)
- Press Ctrl + X (Exit)

<img width="500" height="300" alt="hello_world sh script" src="https://github.com/user-attachments/assets/99419246-e847-44b0-8a12-e2698a0631c5" />

Change Permissions with `chmod 777`:
```bash
chmod 777 hello_world.sh
```

What `chmod 777` means:
- 7 = Owner: read(4) + write(2) + execute(1) = 7
- 7 = Group: read(4) + write(2) + execute(1) = 7
- 7 = Others: read(4) + write(2) + execute(1) = 7

<img width="500" height="300" alt="chmod 777 hello_world sh" src="https://github.com/user-attachments/assets/3b55e1e7-77c3-431c-895c-b14dcbff1061" />

Execute the Script:
```bash
./hello_world.sh
```

<img width="500" height="300" alt="Output of script execution" src="https://github.com/user-attachments/assets/09fc3c49-18e9-48a1-b33c-4420ed4e1e44" />

**What is chmod +x for?**

`chmod +x` is used to add execute permission to a file. The `+x` flag adds (+) execute (x) permission for the owner, group, and others.

**Why is #!/bin/bash used?**

The line `#!/bin/bash` is called a shebang. It tells the operating system which interpreter to use when executing the script.

**How can you personalize script output?**

You can personalize script output by using variables, command substitution, user input, and formatted text.

## Lab 3a
### Domain, DNS and TLS Certificates with Let's Encrypt

Ensure inbound ports 22 (SSH), 80 (HTTP), and 443 (HTTPS) are open:
- Under EC2 Navigation, go to Security Group.
- Click on the Security Group ID used for the instance.
- Click Edit Inbound Rules.
- Add HTTPS.
- Click save.

<img width="500" height="300" alt="Screenshot 2026-04-08 022232" src="https://github.com/user-attachments/assets/c28ef43c-ee77-4bf4-bf53-48d8ca258c4d" />

Register a domain. For my example, I signed into DuckDNS using the GitHub account and created a domain name:

<img width="500" height="300" alt="Domain Name Registered" src="https://github.com/user-attachments/assets/87b3965d-4b93-46c4-8b01-c05c6ef44472" />

Create an A record pointing your domain to the public IP of your server:

<img width="500" height="300" alt="Screenshot 2026-04-08 023321" src="https://github.com/user-attachments/assets/4d58756e-f268-4031-9fa9-b2fcdd554923" />

(Note: The webserver keeps giving out new ip addresses every time you start the instance, the one below was the address at that time.)

<img width="500" height="300" alt="A Record Created" src="https://github.com/user-attachments/assets/b9e649dd-8d8e-4c39-9dc8-8bc3c7545549" />

Check the domain:

<img width="500" height="300" alt="Apache Welcome Page via Domain" src="https://github.com/user-attachments/assets/cd9d7c34-4885-4719-bfb4-d91d1cfecd23" />

DNS propagation:

<img width="500" height="300" alt="DNS Test Output" src="https://github.com/user-attachments/assets/652252fd-ac34-4fe1-aadd-76fac4f796f1" />

Install Certbot:
```bash
sudo apt install certbot python3-certbot-apache
```

<img width="500" height="300" alt="Certbot Installed" src="https://github.com/user-attachments/assets/6442469b-562b-4576-af3c-80a24a4f11ea" />

Generate and install the certificate:
```bash
sudo certbot --apache
```

<img width="500" height="300" alt="Certbot Success Message" src="https://github.com/user-attachments/assets/6b344d42-779b-47fd-8207-e0238494c815" />

Check HTTPS lock icon and certificate in browser:

<img width="500" height="300" alt="HTTPS with Lock Icon" src="https://github.com/user-attachments/assets/2e21a726-b429-463d-aee4-147b5cb3f10d" />

Certbot Auto Renewal:

`certbot renew --dry-run`: Tests the renewal process without actually renewing any certificates. It's a safe way to verify that automatic renewal will work when needed.
```bash
sudo certbot renew --dry-run
```

<img width="500" height="300" alt="Certbot Auto-Renewal Dry Run Successful" src="https://github.com/user-attachments/assets/d97e2923-dea1-4e10-9b67-255098d8af11" />

Cron Job or System Timer Check:

**Method 1:** Check systemd Timer
```bash
sudo systemctl list-timers | grep certbot
```

If nothing shows up:
```bash
sudo systemctl list-timers --all | grep -i certbot
```

Verify if timer is enabled:
```bash
sudo systemctl status certbot.timer
```

**Method 2:** Cron Job

Check cron.d directory:
```bash
ls -la /etc/cron.d/certbot
```

View contents in the cron file:
```bash
cat /etc/cron.d/certbot
```

Test Auto-Renewal:
```bash
sudo certbot renew --dry-run
```

<img width="500" height="300" alt="Cron Job or System Timer Check" src="https://github.com/user-attachments/assets/426ce337-b524-4b3f-bbcc-a42403c29084" />

HTTPS Redirect Enabled:

Using curl to Check Redirect
```bash
curl -I http://kaprc.duckdns.org
```

## Lab 3b
### Bash Backup Scripting, Cron Jobs & Cloud Export

**echo and variables**
```bash
name="Alice"
age=25
location="Singapore"

echo "My name is $name"
echo "I am $age years old"
echo "I live in $location"

greeting="Welcome, $name!"
echo "$greeting"

echo "In 5 years, I will be $((age + 5)) years old"
```

<img width="500" height="400" alt="echo and variables" src="https://github.com/user-attachments/assets/0c25464e-ff78-4ddb-bdca-2ed1b9a94908" />

**Arithmetic with (( ))**

```bash
# Basic arithmetic
a=10
b=5

echo a = $a, b = $b

# Addition
echo a + b = $((a + b))

# Subtraction
echo a - b = $((a - b))

# Multiplication
echo a  b = $((a  b))

# Division
echo a  b = $((a  b))

# Modulo (remainder)
echo a % b = $((a % b))

# Increment and decrement
counter=1
echo Initial counter $counter
((counter++))
echo After counter++ $counter
((counter--))
echo After counter-- $counter

# Compound operations
((a += 5))
echo a += 5 - a = $a

((b = 2))
echo b = 2 - b = $b

```<img width="652" height="698" alt="Arithmetic with (( ))" src="https://github.com/user-attachments/assets/9d293e4b-e8a1-44dc-a17b-c3d405eacade" />

#### Basic For Loop Summation

```bash
# Sum 1 to 10 using for loop
sum=0
for i in {1..10}
do
    echo Adding $i to sum (current sum $sum)
    ((sum += i))
done
echo =========================================
echo Final sum of 1 to 10 is $sum
```

<img width="500" height="300" alt="Basic For Loop Summation" src="https://github.com/user-attachments/assets/7f335855-e208-4dbb-8805-fdfb9f181117" />

**Create test files and directories in `/home/ubuntu/Documents`:**
```bash
cd /home/ubuntu/Documents

mkdir -p project1/src
mkdir -p project1/docs
mkdir -p project2/data
mkdir -p project2/backup
mkdir -p archive/2024
mkdir -p archive/2025

touch project1/README.md
touch project1/src/main.c
touch project1/src/helper.c
touch project1/docs/guide.txt
touch project2/data/dataset.csv
touch project2/backup/old_data.bak
touch archive/2024/report.pdf
touch archive/2025/notes.txt

echo "Hello World" > project1/README.md
```

**Write a Bash script to recursively copy `/Documents` to `/backup`:**
Create the script
```bash
nano /home/ubuntu/testscript
```
Input the content:
```bash
#!/bin/bash
# testscript - Recursive backup script
# This script copies /home/ubuntu/Documents to /home/ubuntu/backup/

echo "        BACKUP SCRIPT EXECUTED           "
echo "Date: $(date)"
echo "User: $(whoami)"
echo ""

# Define source and destination
SOURCE="/home/ubuntu/Documents"
DESTINATION="/home/ubuntu/backup"

# Check if source directory exists
if [ ! -d "$SOURCE" ]; then
    echo "ERROR: Source directory $SOURCE does not exist!"
    echo "Please create it first with: mkdir -p $SOURCE"
    exit 1
fi

# Create destination directory if it doesn't exist
if [ ! -d "$DESTINATION" ]; then
    echo "Creating destination directory: $DESTINATION"
    mkdir -p "$DESTINATION"
fi

# Perform recursive copy
echo "Starting recursive copy..."
echo "Copying from: $SOURCE"
echo "Copying to:   $DESTINATION"
echo ""

cp -rv "$SOURCE/"* "$DESTINATION/" 2>/dev/null

# Check if copy was successful
if [ $? -eq 0 ]; then
    echo ""
    echo "BACKUP COMPLETED SUCCESSFULLY!"
    echo ""
    echo "Files and folders in backup directory:"
    ls -la "$DESTINATION"
else
    echo ""
    echo "ERROR: Backup failed!"
    exit 1
fi

echo ""
echo "Script finished at: $(date)"
```

Save and exit:
- Ctrl + O (WriteOut)
- Enter (confirm)
- Ctrl + X (Exit)

Set Execute Permission:
```bash
chmod 777 /home/ubuntu/testscript
```

Run the script:
```bash
/home/ubuntu/testscript
```

<img width="500" height="300" alt="Screenshot 2026-04-08 034229" src="https://github.com/user-attachments/assets/a292ac34-2666-4887-9c40-c7d8fb44a2ab" />

Verify backup:
```bash
ls -la /home/ubuntu/backup/
```

<img width="500" height="300" alt="Screenshot 2026-04-08 034531" src="https://github.com/user-attachments/assets/dd5c0cd2-d5dd-4430-99c4-949c95a176ad" />


**Script Moved to /usr/bin and Tested**

Move Script to `/usr/bin/`:
```bash
sudo mv ~/testscript /usr/bin/
```

Change Ownership with `sudo chown`:
```bash
sudo chown root:root /usr/bin/testscript
```

Set secure permissions:
```bash
sudo chmod 755 /usr/bin/testscript
```

Test Script from Any Directory. For this case, I decided to test from the tmp directory:
```bash
cd /tmp
testscript
```

**Zip backup with filename based on current date using `date` and `zip`.**

Update script:
```bash
sudo nano /usr/bin/testscript
```
Replace with this:
```bash
#!/bin/bash
# testscript - Backup and Archive Script
# Creates a dated ZIP archive of the Documents directory

echo "     BACKUP & ARCHIVE SCRIPT EXECUTED    "
echo "Date: $(date)"
echo "User: $(whoami)"
echo ""

# Define source and destination
SOURCE="/home/ubuntu/Documents"
BACKUP_DIR="/home/ubuntu/backup"
DEST="/home/ubuntu"  # Where the ZIP file will be saved

# Get current date for filename
now=$(date +"%d_%m_%y")
archive_name="backup_$now.zip"
archive_path="$DEST/$archive_name"

echo "Archive will be created as: $archive_name"
echo ""

# Check if source directory exists
if [ ! -d "$SOURCE" ]; then
    echo "ERROR: Source directory $SOURCE does not exist!"
    echo "Please create it first with: mkdir -p $SOURCE"
    exit 1
fi

# Create backup directory if it doesn't exist
if [ ! -d "$BACKUP_DIR" ]; then
    echo "Creating backup directory: $BACKUP_DIR"
    mkdir -p "$BACKUP_DIR"
fi

# Step 1: Recursive copy to backup directory
echo "▶ Step 1: Copying $SOURCE to $BACKUP_DIR"
cp -r "$SOURCE/"* "$BACKUP_DIR/" 2>/dev/null

if [ $? -ne 0 ]; then
    echo "   No files to copy or source is empty."
fi

echo "   Copy complete."
echo ""

# Step 2: Create dated ZIP archive
echo "▶ Step 2: Creating ZIP archive of backup directory"
echo "   Source: $BACKUP_DIR"
echo "   Destination: $archive_path"

# Remove old archive if it exists
if [ -f "$archive_path" ]; then
    echo "   Removing old archive: $archive_name"
    rm "$archive_path"
fi

# Create the zip archive
zip -r "$archive_path" "$BACKUP_DIR"

if [ $? -eq 0 ]; then
    echo ""
    echo "   ZIP archive created successfully!"
else
    echo ""
    echo "   ERROR: Failed to create ZIP archive!"
    exit 1
fi

# Step 3: Show the created archive
echo ""
echo "ARCHIVE COMPLETED SUCCESSFULLY!"
echo ""
echo "Created archive:"
ls -la "$archive_path"
echo ""
echo "Archive contents preview:"
unzip -l "$archive_path" | head -20

echo ""
echo "Script finished at: $(date)"
```

At first, it did not work as zip was not installed beforehand.
To resolve it:
```bash
sudo apt update
sudo apt install zip -y
```

Run script:
```bash
testscript
```

<img width="500" height="300" alt="Screenshot 2026-04-08 040314" src="https://github.com/user-attachments/assets/b1607be6-f44f-4f03-85b0-b0ba1de07867" />

Verify the file name:

<img width="500" height="93" alt="Screenshot 2026-04-08 040405" src="https://github.com/user-attachments/assets/15ff4970-478f-49dc-8052-618e8e55e199" />


**Cronjob Set Up for Hourly Backup**

 Edit `/etc/crontab`:
 ```bash
sudo nano /etc/crontab
```

Add this at the end:
```bash
# Hourly backup script (at 9 minutes past each hour)
9 * * * * ubuntu /usr/bin/testscript
```

<img width="500" height="300" alt="Cronjob Set Up for Hourly Backup" src="https://github.com/user-attachments/assets/eec6d98c-9e51-4001-8317-0ae27628cebf" />

## Lab 4
### Additional Server Service

For my chosen additional server service, it was Docker.

**Step 1: Remove old Docker versions (if any)**
```bash
sudo apt remove -y docker docker-engine docker.io containerd runc
```

**Step 2: Install Docker using Ubuntu repository**
```bash
sudo apt install -y docker.io
```
<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_10_36_51" src="https://github.com/user-attachments/assets/7bc1eec8-622f-43b8-89a2-798336306771" />

**Step 3: Start and enable Docker service**
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_10_39_35" src="https://github.com/user-attachments/assets/f6229f1c-8a4a-44a6-965b-c8d52f5c45ff" />

**Step 4: Verify Docker installation**
```bash
docker --version
sudo docker run hello-world
```

<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_10_41_36" src="https://github.com/user-attachments/assets/4af62baf-4b88-4f82-a957-059fab4155bc" />

**Run a Web Server Container**

Run Nginx web server on port 8080:
```bash
docker run -d --name webserver -p 8080:80 nginx
```

<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_11_02_58" src="https://github.com/user-attachments/assets/1222d0b0-4d51-4863-bb98-599c7fd45248" />

Verify if it is running:
```bash
docker ps
curl localhost:8080
```

<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_11_05_19" src="https://github.com/user-attachments/assets/9e5cc285-85b5-4050-8acc-608e6d2e3c75" />


<img width="500" height="300" alt="VirtualBox_VM_08_04_2026_12_05_18" src="https://github.com/user-attachments/assets/e00ef40b-2af6-4245-8c82-eeff6709cbab" />

