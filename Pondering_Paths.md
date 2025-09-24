# Pondering Paths

## 1. The Root

### In this challenge, we give the exact path with /pwn. This path starting with root directory is the "absolute path".

**Flag** 'pwn.college{UqDg64zURLn4uRG-_-N4PY-Mjsw.QX4cTO0wSO4kjNzEzW}'

Got the flag by starting the challenge, and giving /pwn command which is the exact path of the program.

## What I learned
Absolute path: path that starts with root directory
Root directory: where all filesystem starts which is '/'.


## 2. Program and absolute paths

### The challenge has to be executed by invoking its absolute path. Name of the challenge program is run.

**Flag** 'pwn.college{oVdW7FnahSdNsNXN-1mUmk218sm.QX1QTN0wSO4kjNzEzW}'

Run file is in the challenge directory and the challenge directory is in the / directory. Therefore, the flag can be obtained by running the command /challenge/run.

## What I learned 
A program's absolute path- from the program's directory to the root directory path followed.


## 3. Position thy self

### We have to change the directory of the challenge and execute it with cd command.

**Flag** 'pwn.college{Ypn29eQkzCgAI8NpadbrhgoIXOM.QX2QTN0wSO4kjNzEzW}'

I ran the challenge in its absolute path. This gave me a prompt that I am not in the correct directory currently. Then I used the cd command to change the directory and then ran the challenge in the new directory.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /sys/kernel directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /sys/kernel
hacker@paths~position-thy-self:/sys/kernel$ /challenge/run
Correct!!!
```
## What I learned
cd-change directory command
use of ~: shows the current directory of the program


## 4. Position elsewhere

### Change the directory to elsewhere as told and run the challenge again.

**Flag** 'pwn.college{wfDehOtDpuiDvr_tHV4AfSgvyEA.QX3QTN0wSO4kjNzEzW}'

I ran the challenge in the current directory which prompted the address of the directory I am supposed to run it in. So, I changed the directory using cd and ran the challenge in the new directory.

```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /etc
hacker@paths~position-elsewhere:/etc$ /challenge/run
Correct!!!
```
## What I learned
cd:change directory command


## 5. Position yet elsewhere

### Run the challenge on another prompted directory by changing directory

**Flag** 'pwn.college{gwQNiTCzXhZAKHtvwaN7cNKDmVv.QX4QTN0wSO4kjNzEzW}'

Ran the challenge in current working directory. Couldn't get the flag as was not int he correct directory. Changed the current working directory to the one given by using cd command. Ran the challenge in that directory and got the flag.

```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-yet-elsewhere:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
```
## What I learned
cd command


## 6. Implicit relative paths, from /

### Run the challenge using a relative path while having a current working directory of /.

**Flag** 'pwn.college{UeaZksAun8OYZKIKCMS2pcDEoOc.QX5QTN0wSO4kjNzEzW}'

I tried to run the challenge without changing the directory to root directory which gave me an 'incorrect' prompt. After which I used cd to change to / directory. Now the relative path of /challenge/run becomes challenge/run. Running this got me the flag.

```
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
```

## What I learned
cwd: current working directory
relative path: path that does not begin at the root(/)


## 7. Explicit relative paths, from /

### Get the flag using '.' in the relative path for the challenge. This is an explicit relative path.

**Flag** 'pwn.college{o6UZB4a7bfQaYWjGEKtSkLqR-0v.QXwUTN0wSO4kjNzEzW}'

First, change to root directory using cd command. Then, I tried adding '.' to the path in different ways but they just gave the prompt of being a directory. Then I ran the challenge with './' which got me the flag.

```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
```

## What I learned
explicit relative path: path to a file that starts from the current location and uses '.' for current directory and '..' for parent directory.
relative: current directory
explicit: clearly stating the starting point.
./: challenge is in this this directory only and needs to be run here.


## 8. Implicit relative path

### provide a 'naked path' for the directory and explicitly use relative paths to launch 'run' using '.'.

**Flag** 'pwn.college{89pn667GSpMB1Iy0_d9X96SG2-z.QXxUTN0wSO4kjNzEzW}'

change to /challenge directory using cd command. Then, ran it as a safety measuure due to implicit path. No command found. For explicit running, used ./ to run and got the flag.

```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
bash: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
```

## What I learned
running the run command for 'naked paths' as a safety measure in Linux in order to not execute a program having the same name any as core system utilities.


## 9. Home sweet home

### run the challenge for any file we specify as an argument on the commandline, given it must be an absolute path, the path must be inside the home directory and that the argument must be of 3 characters.

**Flag** 'pwn.college{Enyj-lk4ceZT5hynQOD-WAJva0I.QXzMDO0wSO4kjNzEzW}'

The arguement is supposed to be '/challenge/run PATH', wherein the PATH needs to have the 3 conditions. For home directory, I started with ~. For, absolute path, I used /. Faced an issue with the 3 character condition which I didn't understand completely. Upon searching, I found out that I had already used two characters with ~ and / which meant that now I needed only one character for the complete arguement which could be 'a'. Therefore, got the flag with this command.

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{Enyj-lk4ceZT5hynQOD-WAJva0I.QXzMDO0wSO4kjNzEzW}
```

## What I learned
~ expands t home/hacker or home directory
cd automatically assigns home directory if nothing specified with the command
