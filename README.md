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



