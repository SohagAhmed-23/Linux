# Project - 1
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


# Project-2
`mkdir -p devops/project/logs`
- -p -> Creates parent directories automatically


<img width="793" height="378" alt="image" src="https://github.com/user-attachments/assets/8695dcb1-0107-4276-9a2b-9bc5239cda17" />


### Breaking down 640
6 → Owner
4 → Group
0 → Others

# Project-3
### Create a group
- `sudo groupadd devops`

### show that the group exists or not
- `cat etc/group`

### To change the owner
`sudo chown BS-1565 teams.txt`

### Change the group
`sudo chown BS-1565:devops teams.txt`

  <img width="734" height="313" alt="image" src="https://github.com/user-attachments/assets/57aa92e7-2c4c-4e38-9044-f4ea5d599479" />

# Project - 4

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


# Project 5
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

# project -6




