# Pondering PATH

## 1. The PATH Variable

### Disrupt the operation of the /challenge/run program. This program will delete the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it you. Thus, make it so that /challenge/run also can't find the rm command.

**Flag** `pwn.college{EVIibBM1Lpng2F1VZgCDbj6kCl8.QX2cDM1wSO4kjNzEzW}`

Exporting PATH variable equal to blank quotations so as to clear all commands for the specific program. Then run the challenge.

```
hacker@path~the-path-variable:~$ export PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{EVIibBM1Lpng2F1VZgCDbj6kCl8.QX2cDM1wSO4kjNzEzW}
```
## What I learned
PATH variable stores a bunch of directory paths in which the shell will search for programs corresponding to commands.  
PATH="" clears all the commands stored.


## 2. Setting PATH

### /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.

**Flag** `pwn.college{cosmCkKfYnrjzETV1OIKCnPdZp5.QX1cjM1wSO4kjNzEzW}`

Set PATH variable to more_commands directory and then run /challenge/run to get the flag.

```
hacker@path~setting-path:~$ export PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cosmCkKfYnrjzETV1OIKCnPdZp5.QX1cjM1wSO4kjNzEzW}
```
## What I learned
We can overwrite the PATH variable with other desired directories if that is the only directory that we will need.


## 3. Finding Commands

### win command is somewhere in $PATH, but it won't give the flag. Instead, it's in the same directory as a flag file that was made readable. Find win with the which command, and cat the flag out of that directory.

**Flag** `pwn.college{YFMygWzIb1Jo_MZ07Z7-JtRSOg7.01NzEzNxwSO4kjNzEzW}`

Find win command's path using which. Since flag is in same directory, use cat to read the flag from its absolute path.

```
hacker@path~finding-commands:~$ which win
/challenge/paths/9245/win
hacker@path~finding-commands:~$ cat /challenge/paths/9245/flag
pwn.college{YFMygWzIb1Jo_MZ07Z7-JtRSOg7.01NzEzNxwSO4kjNzEzW}
```
## What I learned
'which' helps in finding the exact path of the command and execute it using the exact path.


## 4. Adding Commands

### Make a shell script called win, add its location to the PATH, and enable /challenge/run to find it.

**Flag** `pwn.college{o3emPR54yuSACOR1k9S0OTfmLC_.QX2cjM1wSO4kjNzEzW}`

Find path of cat using which. Then write a shell script named win starting with shebang. Write the absolute path of cat with /flag and append it to win. Make win executable in all modes. Add present working directory to the PATH variable and export it. Run challenge to get flag.

```
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ echo '#!/bin/bash' > win
hacker@path~adding-commands:~$ echo '/run/dojo/bin/cat /flag' >> win
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ export PATH="$PWD:$PATH"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{o3emPR54yuSACOR1k9S0OTfmLC_.QX2cjM1wSO4kjNzEzW}
```
## What I learned
We can add the present working directory to already there PATH varisble and not overwrite it so that other commands are not lost. Also, make shell scripts for commands we wish to make and add them to PATH.


## 5. Hijacking Commands

### This challenge will delete the flag using the rm command. But it will not print anything out for you. Get the flag using shell scripts and PATH variable.

**Flag** `pwn.college{E1OOQRY-g5mtCRaYSl0FaQ0cY-L.QX3cjM1wSO4kjNzEzW}`

Created a shell script called rm in order to trick the program into executing this script which will actually read the flag. In the script, I first catted the first argument which will be -f and not the flag so it showed me invalid option error. So I corrected it to catting the 2nd argument which will be /flag. Then changed permissions of rm to executable for all modes. Then run the program to get the flag.

```
hacker@path~hijacking-commands:~$ echo '#!/bin/bash' > rm
hacker@path~hijacking-commands:~$ echo 'cat "$2"' >> rm
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{E1OOQRY-g5mtCRaYSl0FaQ0cY-L.QX3cjM1wSO4kjNzEzW}
```
## What I learned
We can make shell scripts with the names of commands of PATH variables to trick the program into running them. Also that the terminal takes inputted argument as the 2nd argument in commands like cat.