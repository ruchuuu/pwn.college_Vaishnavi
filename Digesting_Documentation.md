# Digesting Documentation

## 1. Learning from documentation

### Run the challenge by passing --giveflag argument given in its documentation.

**Flag** 'pwn.college{cSE7UN4WPt3kFFAgTo10i2A5m8K.QX0ITO0wSO4kjNzEzW}'

Gave the command /challenge/challenge (absolute path) with --giveflag to retrieve the flag.

## What I learned
Documentation of programs helps us figure out which arguments to use and how to run the programs.
--giveflag command


## 2. Learning Complex Usage

### Get the flag by using --printfile argument in the challenge.

**Flag** 'pwn.college{Qkh8kVM5fLsFO9lEzyD5WQeZIhf.QX1ITO0wSO4kjNzEzW}'

First listed out all files of the directory. Two files- flag and not-the-flag displayed. Used the --printfile argument with flag first but got nothing. Then did the same with not-the-flag file and got the flag.

```
hacker@man~learning-complex-usage:~$ ls
a  flag  not-the-flag
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile flag
Correct argument! Here is the flag file:
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile not-the-flag
Correct argument! Here is the not-the-flag file:
pwn.college{Qkh8kVM5fLsFO9lEzyD5WQeZIhf.QX1ITO0wSO4kjNzEzW}
```
## What I learned
--printfile argument that prints the content of the file when given.


## 3. Reading Manuals

### Open the manual of the challenge and use the secret option given to print the flag.

**Flag** 'pwn.college{E2DQIkCyjwI0m4cLto_gKloBYdE.QX0EDO0wSO4kjNzEzW}'

Opened the manual for challenge using 'man challenge'. The description showed that using the --kyjwmc NUM argument with 204 as NUM prints the flag. Then ran the challenge with absolute path and the argument to get the flag.

## What I learned
Manual: info about a command you pass as an argument.
man command: opens the manual.
PgUp/PgDn to navigate the man page.


## 4. Searching Manuals

### Find the option that gives the flag by searching the challenge man page.

**Flag** 'pwn.college{QJ2bTc4ZYWXi5-sm4CYvDunF2u6.QX1EDO0wSO4kjNzEzW}'

Opened the man page using man challenge. Searched flag keyword with / (/flag) in the man page. Found --djyxhm argument to give the flag. Quit the man page and used the argument with challenge program to get the flag.

## What I learned
Search in man page with / and hit n to go next, N to go to previous result and ? to search backwards.


## 5. Searching For Manuals

### Read the manpage for man to figure out how to search for the right manpage and get the flag according to the options given in the correct manpage.

**Flag** 'pwn.college{ojjxhP8Lw7Q5iHNFrj0YUy-61z4.QX2EDO0wSO4kjNzEzW}'

Opened the manpage for man with the man man command. Under description, the examples given showed that 'man -k keyword' helps in searching the short description for the keyword entered. Quit the manpage and ran man -k with challenge keyword and got the correct manual. Opened the manpage and got the value with argument to enter to get the flag. Ran it with the challenge program and got the flag.

```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
ojjxhwirjy (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man ojjxhwirjy
hacker@man~searching-for-manuals:~$ /challenge/challenge --ojjxhw 875
Correct usage! Your flag: pwn.college{ojjxhP8Lw7Q5iHNFrj0YUy-61z4.QX2EDO0wSO4kjNzEzW}
```
## What I learned
man man command prints the manpage for all the manuals of the database.


## 6. Helpful Programs

### Run program using --help argument. Get documentation and get flag with help of that.

**Flag** 'pwn.college{g2gwSqyyJqY9sgfaa2BA41x0GMQ.QX3IDO0wSO4kjNzEzW}'

Used --help argument with challenge program. Got optional arguments. Used --print-value to get the secret value. Take the secret value with --give-the-flag argument and get the flag.

```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge --print-value
The secret value is: 292
hacker@man~helpful-programs:~$ /challenge/challenge --give-the-flag 292
Correct usage! Your flag: pwn.college{g2gwSqyyJqY9sgfaa2BA41x0GMQ.QX3IDO0wSO4kjNzEzW}
```
## What I learned
--help | -h | -? | help | /?: gives the documentation of a program when they don't have a man page.


## 7. Help for Builtins

### Lookup for help for challenge command as a shell builtin, not program, and find the secret value to run it.

**Flag** 'pwn.college{gwqndwuuEPgY_E508U-61Mgr3S7.QX0ETO0wSO4kjNzEzW}'

Ran help for challenge and got the secret value to be "gwqndwuu". This time it is not a program so ran the challenge without absolute path and with --secret argument and the value and got the flag.

```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "gwqndwuu".
hacker@man~help-for-builtins:~$ challenge --secret gwqndwuu
Correct! Here is your flag!
pwn.college{gwqndwuuEPgY_E508U-61Mgr3S7.QX0ETO0wSO4kjNzEzW}
```
## What I learned
Some commands do not have man page or help options. They are built into the shell. We can get its documentation by running help builtin command.
