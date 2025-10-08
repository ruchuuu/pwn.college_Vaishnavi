# Untangling Users

## 1. Becoming root with su

### Provide hack-the-planet as password to su to become root and read the flag.

**Flag** 'pwn.college{Ed8Frjbq-LFc_nYnfyElv1aqLhh.QX1UDN1wSO4kjNzEzW}'

Run the su command, enter the password then list all files in the root directory and read not-the-flag file to get the flag.

```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls /home/hacker
COLLEGE  PWN  a  flag  instructions  myfile  myflag  not-the-flag  output  output.txt  the-flag
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
pwn.college{Ed8Frjbq-LFc_nYnfyElv1aqLhh.QX1UDN1wSO4kjNzEzW}
```
## What I learned
su (substitute user command) or sudo command can be run to become the root or the administrator of the system.


## 2. Other users with su

### Switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

**Flag** 'pwn.college{8DJ85BfZAtB8QpOSqAYo5YVXweP.QX2UDN1wSO4kjNzEzW}'

Use su to become zardus admin. Enter the password and run the program to get the flag.

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{8DJ85BfZAtB8QpOSqAYo5YVXweP.QX2UDN1wSO4kjNzEzW}
```
## What I learned
su with a username can switch to that user instead of root.


## 3. Cracking passwords

### A leak of /etc/shadow (in /challenge/shadow-leak) is given. Crack it, su to zardus, and run /challenge/run to get the flag.

**Flag** 'pwn.college{YSITZq2BevjBIngtvCrtOCtg0nO.QX3UDN1wSO4kjNzEzW}'

Cat /challenge/shadow-leak to see the zardus password. Grep the list for zardus and redirect the output to a file zardus.shadow. Use the john command to decode the file and get the password. su to zardus and enter the password. Then run the challenge to get the flag.

```
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
root:*:20182:0:99999:7:::
daemon:*:20182:0:99999:7:::
bin:*:20182:0:99999:7:::
sys:*:20182:0:99999:7:::
sync:*:20182:0:99999:7:::
games:*:20182:0:99999:7:::
man:*:20182:0:99999:7:::
lp:*:20182:0:99999:7:::
mail:*:20182:0:99999:7:::
news:*:20182:0:99999:7:::
uucp:*:20182:0:99999:7:::
proxy:*:20182:0:99999:7:::
www-data:*:20182:0:99999:7:::
backup:*:20182:0:99999:7:::
list:*:20182:0:99999:7:::
irc:*:20182:0:99999:7:::
gnats:*:20182:0:99999:7:::
nobody:*:20182:0:99999:7:::
_apt:*:20182:0:99999:7:::
systemd-timesync:*:20357:0:99999:7:::
systemd-network:*:20357:0:99999:7:::
systemd-resolve:*:20357:0:99999:7:::
mysql:!:20357:0:99999:7:::
messagebus:*:20357:0:99999:7:::
sshd:*:20357:0:99999:7:::
hacker::20357:0:99999:7:::
zardus:$6$.J8HvP7Zk0K6oC4t$mKwqz5n0w4Re44hU6hao3caWg9m4ZOt/Q9SghQAb7h4cwEIES/BZS4/D7jWi/PV8hBhygxEhnjjRPPmQjKz8w/:20369:0:99999:7:::
hacker@users~cracking-passwords:~$ grep zardus: /challenge/shadow-leak > zardus.shadow
hacker@users~cracking-passwords:~$ cat zardus.shadow
zardus:$6$.J8HvP7Zk0K6oC4t$mKwqz5n0w4Re44hU6hao3caWg9m4ZOt/Q9SghQAb7h4cwEIES/BZS4/D7jWi/PV8hBhygxEhnjjRPPmQjKz8w/:20369:0:99999:7:::
hacker@users~cracking-passwords:~$ john zardus.shadow
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04930g/s 287.1p/s 287.1c/s 287.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{YSITZq2BevjBIngtvCrtOCtg0nO.QX3UDN1wSO4kjNzEzW}
```
## What I learned
Passwords stored in /etc/password can leak and can be decrypted to get the actual password to user. Here, decrypted via John the Ripper.


## 4. Using sudo

### sudo access will be given, use it to read the flag.

**Flag** 'pwn.college{o8NvdSom9UEFKBNlZqSa3vUOm-N.QX4UDN1wSO4kjNzEzW}'

sudo ls to switch to root and list all files. Find not-the-flag and cat it with sudo command to read the flag.

```
hacker@users~using-sudo:~$ sudo ls
COLLEGE  PWN  a  flag  instructions  myfile  myflag  not-the-flag  output  output.txt  the-flag  zardus.shadow
hacker@users~using-sudo:~$ sudo cat not-the-flag
pwn.college{o8NvdSom9UEFKBNlZqSa3vUOm-N.QX4UDN1wSO4kjNzEzW}
```
## What I learned
sudo with commands directly interacts with the shell as the root.