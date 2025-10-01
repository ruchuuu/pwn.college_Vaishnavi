# Shell Variables

## 1. Printing Variables

### Have the shell print out the FLAG variable.

**Flag** 'pwn.college{UlnHsiE-yAVCMAJ5uJWpLAs9NfV.QX3UTN0wSO4kjNzEzW}'

Printed FLAG variable using echo by prepending the variable name with $.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{UlnHsiE-yAVCMAJ5uJWpLAs9NfV.QX3UTN0wSO4kjNzEzW}
```
## What I learned
echo command helps in printing. Variables can be printed by appending $ in front of it.

## 2. Setting Variables

### Set the PWN variable to the value COLLEGE.

**Flag** 'pwn.college{gD-G1HcwXKEIKS7xxJzp7jtjQLb.QX5UTN0wSO4kjNzEzW}'

Assigned value COLLEGE to variable PWN using = operator.

```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gD-G1HcwXKEIKS7xxJzp7jtjQLb.QX5UTN0wSO4kjNzEzW}
```
## What I learned
= used to assign values to variables. But there should be no spaces in between as the terminal will interpret it as a command and run it, not assign the value.

## 3. Multi-word Variables

### Set the variable PWN to COLLEGE YEAH.

**Flag** 'pwn.college{U3bNQsThZP93hPQRqBTLKU-6AZs.QXwYTN0wSO4kjNzEzW}'

Used double quotaion to assign the phrase to PWN variable.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{U3bNQsThZP93hPQRqBTLKU-6AZs.QXwYTN0wSO4kjNzEzW}
```
## What I learned
Since space cannot be used while assigning values to variables, double quotation can be used to assign values with spaces.


## 4. Exporting Variables

###  Invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.

**Flag** 'pwn.college{AyQsJTO6Gzs03fkCROOqqGZ7jRi.QXyYTN0wSO4kjNzEzW}'

Exported PWN variable using export command and assigned PWN value to COLLEGE but did not export it. Then ran the challenge command and got the flag.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{AyQsJTO6Gzs03fkCROOqqGZ7jRi.QXyYTN0wSO4kjNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
## What I learned
Variables set in a shell are local to that shell process. For other commands to inherit the variable, we have to export the variable using export command.


## 5. Printing Exported Variables

### Use env command to print out every exported variable set in the shell, and look through that output to find the FLAG variable.

**Flag** 'pwn.college{4IqXVyy5Cw1t28dh5zT5O14dmX0.QX4UTN0wSO4kjNzEzW}'

Ran env command and got the list of the variables. Ran env command with the FLAG variable as echo was not allowed in this challenge and got the flag.

```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=6a348bd4ad3dfd6f64f1dead19ffa905aa90c478b52fc330ff298276e509946f
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{4IqXVyy5Cw1t28dh5zT5O14dmX0.QX4UTN0wSO4kjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
hacker@variables~printing-exported-variables:~$ env $FLAG
env: ‘pwn.college{4IqXVyy5Cw1t28dh5zT5O14dmX0.QX4UTN0wSO4kjNzEzW}’: Permission denied
```
## What I learned
env is another command just like echo that can be used to access exported variables in the shell.


## 6. Storing Command Output

### Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag.

**Flag** 'pwn.college{Exm4KPQTTGLo1WoULvSNMl5vAdc.QX1cDN1wSO4kjNzEzW}'

Assigned output of /challenge/run to PWN and then printed variable PWN using echo.

```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{Exm4KPQTTGLo1WoULvSNMl5vAdc.QX1cDN1wSO4kjNzEzW}
```
## What I learned
$() can be used to assign output of command to a variable. 


## 7. Reading Input

### Use read to set the PWN variable to the value COLLEGE.

**Flag** 'pwn.college{kMT8rLqKohA0CFCgb3xMA9qDNvy.QX4cTN0wSO4kjNzEzW}'

Used read with PWN. This gave the option to eneter a value which I entered COLLEGE. This gave the flag.

```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kMT8rLqKohA0CFCgb3xMA9qDNvy.QX4cTN0wSO4kjNzEzW}
```
## What I learned
read allows reading input from the user. This way entered input can be the value assigned to the variable.


## 8. Reading Files

### Read /challenge/read_me into the PWN variable, and get the flag.

**Flag** 'pwn.college{81IEfmjkHXMo7OjEQvSyVtMka6E.QXwIDO0wSO4kjNzEzW}'

Used read to redirect /challenge/read_me into stdin of read which in turn reads into PWN. This gave the flag.

```
hacker@variables~reading-files:~$ read PWN< /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{81IEfmjkHXMo7OjEQvSyVtMka6E.QXwIDO0wSO4kjNzEzW}
```
## What I learned
Using read to redirect files to variable not just words.
