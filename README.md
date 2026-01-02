<img width="880" height="143" alt="image" src="https://github.com/user-attachments/assets/7fe5efe1-7436-499b-a2b7-ef9347c45150" /># Project - 1 -User & File Basics
### Create a new user
`sudo useradd -m BS-1565`
- useradd command to add a new user
- -m = makes a home directory at /home/BSID
- BS-1565 this is for a new user
### Set a password for the new user 
`sudo passwd BS-1565`
- passwd to make a new passwd for the BS-1565
  
### To see if the user exists or not
`cut -d: -f1 /etc/passwd`
- cut → a command used to slice out specific parts of text
- -d: → says “use a colon (:) as the separator”
- -f1 → means “give me field number 1”
- /etc/passwd → a system file that stores user account info
### Create a file
`touch welcome.txt`
### Write a short message inside it
`echo "Welcome to your new Ubuntu account!" > welcome.txt`
### Copying to another user’s home 
`sudo cp welcome.txt /home/BS-1565/`
- cp → stands for copy
- It copies files from one place to another.
- welcome.txt → the file you want to copy
- /home/BS-1565/ → the destination folder
This is the home directory of the user BS-1565.
<img width="728" height="207" alt="image" src="https://github.com/user-attachments/assets/5c06340b-abf5-4fee-b940-64c98bd38327" />


# Project-2 - Directory Structure & Permissions
`mkdir -p devops/project/logs`
- -p -> Creates parent directories automatically


<img width="793" height="378" alt="image" src="https://github.com/user-attachments/assets/8695dcb1-0107-4276-9a2b-9bc5239cda17" />


### Breaking down 640
6 → Owner
4 → Group
0 → Others

# Project-3 - Ownership & Groups
### Create a group
- `sudo groupadd devops`

### show that the group exists or not
- `cat etc/group`

### To change the owner
`sudo chown BS-1565 teams.txt`

### Change the group
`sudo chown BS-1565:devops teams.txt`

  <img width="734" height="313" alt="image" src="https://github.com/user-attachments/assets/57aa92e7-2c4c-4e38-9044-f4ea5d599479" />

# Project - 4 - File Search & Disk Usage

`touch file1.txt file2.txt app.log system.log config.conf`

### Find all .log files
`find ~ -type f -name "*.log"`

- ~ → start searching from your home directory
- -type f → files only
- -name "*.log" → anything ending in .log

### Check disk usage
`du -sh ~`

<img width="740" height="63" alt="image" src="https://github.com/user-attachments/assets/ae1d783b-b1f0-4464-8260-1d7aed2422f4" />


### Identify the largest file
`du -ah ~ | sort -rh | head -n 10`

- du -ah ~ → size of all files, readable format
- sort -rh → largest first
- head -n 10 → top 10 biggest

<img width="742" height="219" alt="image" src="https://github.com/user-attachments/assets/aefe43b8-0fbc-46cf-8519-8e40e283eb69" />


# Project 5 - Process Managemen
### Start a background process
`sleep 300 &`
That & sends it to the background.
### List running processes & dentify the process ID (PID).
- `ps or ps aux or specific ps aux | grep slep`
### Kill the process
`kill 40263`
`kill -9 40263`
- -9 → signal SIGKILL (force quit, no questions asked)

<img width="743" height="357" alt="image" src="https://github.com/user-attachments/assets/b52e3bf6-f33a-43c0-8f26-4fda3d055d1e" />

# project -6 - Package Management
### Update package lists
`apt update`
### Install nginx
`apt install nginx`
### Check nginx service status.
`systemctl status nginx`
### Start and stop the service.
`systemctl start/stop nginx`
# project - 7 - Log File Analysis
### View the last 50 lines of syslog.
`tail -50 syslog`

<img width="723" height="348" alt="image" src="https://github.com/user-attachments/assets/3ae0ee0a-233e-45d9-8910-8b9c80c8fafc" />


### Search for "error" on syslog
`grep -i "error" syslog`

<img width="720" height="156" alt="image" src="https://github.com/user-attachments/assets/ff4db276-b82a-46b9-8c48-b062a49183d5" />
### Save output to a file
`tail -n 50 syslog | grep -i "error" > ~/error_log.txt`ls 

<img width="720" height="226" alt="image" src="https://github.com/user-attachments/assets/84536a38-4ef1-4caf-b2f7-4b6db11d6dd7" />

# project - 8 - Networking Basics
### To show the Ip address
`ip addr show`
<img width="1082" height="432" alt="image" src="https://github.com/user-attachments/assets/efcb3f26-6378-4d96-82ae-6203ca17bb46" />
### TO see the network Connectivity 
`ping google.com`
- <img width="880" height="143" alt="image" src="https://github.com/user-attachments/assets/f117b389-8d86-4214-84a1-40a95b880f37" />
## To see the list port 
`ss -tulpen`
<img width="1771" height="278" alt="image" src="https://github.com/user-attachments/assets/7e2a6d55-ffd7-448a-98f3-8d17184024de" />
## To see which process is using port 22
<img width="1740" height="114" alt="image" src="https://github.com/user-attachments/assets/626fcf6b-2756-4a3e-96b1-399788798cde" />


# Project - 9 - Shell Scripting Basics 
### Script for backup
`
su - bs1366
cat > ~/backup.sh <<'EOF'
#!/bin/bash

if [ -z "$1" ]; then
  echo "Usage: $0 <directory_path>"
  exit 1
fi

SRC_DIR="$1"

if [ ! -d "$SRC_DIR" ]; then
  echo "Error: '$SRC_DIR' does not exist or is not a directory."
  exit 1
fi

DATE="$(date +%Y-%m-%d_%H-%M-%S)"
DEST_DIR="$HOME/backups"
mkdir -p "$DEST_DIR"

BASE_NAME="$(basename "$SRC_DIR")"
BACKUP_FILE="$DEST_DIR/${BASE_NAME}_backup_${DATE}.tar.gz"

tar -czf "$BACKUP_FILE" -C "$(dirname "$SRC_DIR")" "$BASE_NAME"

echo "Backup created: $BACKUP_FILE"
ls -lh "$BACKUP_FILE"
EOF
`

### Make it executable
chmod x+ backup.sh

<img width="690" height="160" alt="image" src="https://github.com/user-attachments/assets/b73e0c66-d2db-48c7-8cb5-7f18cb19792b" />

## create a backup 
<img width="743" height="115" alt="image" src="https://github.com/user-attachments/assets/a6544754-2fb7-412c-bef1-a2a00578bf04" />


# project - 10 - Cron Job
- write `write_time.sh` file for cronjob
### Set up the crontab for every 5 min.
-   <img width="721" height="377" alt="image" src="https://github.com/user-attachments/assets/eb17c741-963c-4098-9dd1-edf1f7e3467c" />
### updating automatically
<img width="731" height="333" alt="image" src="https://github.com/user-attachments/assets/632699fb-e6d3-4216-85d0-fb9812510996" />


















