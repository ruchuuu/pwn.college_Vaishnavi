# Perceiving Permissions

## 1. Changing File Ownership

### Changing the owner of the /flag file to the hacker user, and then read the flag.

**Flag** `pwn.college{YzV6xgIvhnBNvyC9jD2-Yl91I7V.QXxEjN0wSO4kjNzEzW}`

Changing the file owner to hacker user using chown command and catting the file to get the flag.

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{YzV6xgIvhnBNvyC9jD2-Yl91I7V.QXxEjN0wSO4kjNzEzW}
```
## What I learned
chown command changes the owner of the file.


## 2. Groups and Files

### Flag is readable by whatever group owns it, but this group is currently root. Change the group ownership of the flag file, and read the flag.

**Flag** `pwn.college{s_mdcsMxLdjYW3g42nRONru82XQ.QXxcjM1wSO4kjNzEzW}`

Check the groups using id command. List the flag file. Change group owner from root to hacker, then cat it to read the flag.

```
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root root 60 Oct  8 11:32 /flag
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root hacker 60 Oct  8 11:32 /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{s_mdcsMxLdjYW3g42nRONru82XQ.QXxcjM1wSO4kjNzEzW}
```
## What I learned
chgrp changes the owner of the group and id shows all the groups the user is a part of.


## 3. Fun With Groups Names

### The name of the group that your user is in is randomized. Use the id command to figure that name out, then chgrp to get the flag.

**Flag** `pwn.college{cHfkjEnfcWxpTCX5bdGOG_Vb3Kj.QXycjM1wSO4kjNzEzW}`

Used id to see all groups. List all files to see the owner of the file. Change the group owner to grp21266 and then cat it to get the flag.

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp21266) groups=1000(grp21266)
hacker@permissions~fun-with-groups-names:~$ ls -l
total 44
-rw-r--r-- 1 hacker grp21266   4 Sep 27 19:07 COLLEGE
-rw-r--r-- 1 hacker grp21266   8 Sep 29 17:39 PWN
-rw-r--r-- 1 root   grp21266  60 Sep 24 18:12 a
-rw-r--r-- 1 hacker grp21266  27 Oct  8 10:34 flag
-rw-r--r-- 1 hacker grp21266 829 Sep 29 17:34 instructions
-rw-r--r-- 1 hacker grp21266   0 Sep 27 19:20 myfile
-rw-r--r-- 1 hacker grp21266  95 Sep 29 17:34 myflag
lrwxrwxrwx 1 hacker grp21266   5 Sep 25 14:40 not-the-flag -> /flag
-rw-r--r-- 1 root   grp21266  77 Sep 29 18:59 output
-rw-r--r-- 1 root   grp21266  77 Sep 29 19:00 output.txt
-rw-r--r-- 1 hacker grp21266 437 Sep 27 19:46 the-flag
-rw-r--r-- 1 hacker grp21266 133 Oct  8 09:55 zardus.shadow
hacker@permissions~fun-with-groups-names:~$ chgrp grp21266 /flag
hacker@permissions~fun-with-groups-names:~$ ls -l /flag
-r--r----- 1 root grp21266 60 Oct  8 11:49 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{cHfkjEnfcWxpTCX5bdGOG_Vb3Kj.QXycjM1wSO4kjNzEzW}
```
## What I learned
Group owner's names can be changed using chgrp command.


## 4. Changing Permissions

### Change the permissions of the /flag file to read it.

**Flag** `pwn.college{wudcUx4w4jLk3fG4a3_I8iAdbNh.QXzcjM1wSO4kjNzEzW}`

Use chmod with o+r to make the file readable to other(all) users and the catted it to get the flag.

```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{wudcUx4w4jLk3fG4a3_I8iAdbNh.QXzcjM1wSO4kjNzEzW}
```
## What I learned
chmod command allows to change the existing modes of files/programs.  
u-user  
g-group  
o-other  
a-all  
(+)- enabling & (-)- denabling  
r-read, w-write and x-execute


## 5. Executable Files

### The /challenge/run program will give the flag, but must first be made executable.

**Flag** `pwn.college{cTov_KIHiZESmXQaXxLsUY8yinx.QXyEjN0wSO4kjNzEzW}`

Change mode to executable for all modes using chmod a+x and then run the program to get the flag.

```
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{cTov_KIHiZESmXQaXxLsUY8yinx.QXyEjN0wSO4kjNzEzW}
```
## What I learned
Files can be executed in all modes using chmod a+x.


## 6. Permission Tweaking Practice

### Change the permissions of the /challenge/pwn file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you chmod /flag to make it readable for yourself. Launch /challenge/run to get started.

**Flag** `pwn.college{I0FnVW3yDvj0dZdwqFMy78fkxih.QXwEjN0wSO4kjNzEzW}`

Launch /challenge/run. Look at the needed permissions list to see all the permissions needed to be given using chmod. Do this 8 times to see current permissions of /flag. Make the file readable to user using chmod u+r command. Cat it and get the flag.

```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r-xr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go+x /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-xr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rwxr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+w /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rw-rwxr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+w /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--rwxrwx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-w /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r--rwxrwx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+w /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": rw-rwxrwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxrwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+x /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rwxrwxrwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ------rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug-rwx /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ------rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o-x /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{I0FnVW3yDvj0dZdwqFMy78fkxih.QXwEjN0wSO4kjNzEzW}
```
## What I learned
All ways to give read, write and execute permissions for all modes- user, group and world via chmod command.


## 7. Permissions Setting Practice

### This level extends the previous level by requesting more radical permission changes, which you will need = and ,-chaining to achieve.

**Flag** `pwn.college{4juT7v-8TtRmHABraTVGsS4I8h0.QXzETO0wSO4kjNzEzW}`

Launch /challenge/run and set permissions according to requirement 8 times using '=' & '-' operators. Then set user permission to read only and cat the file to get flag.

```
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr---w-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,o=w /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": r-xr---w-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw--wxr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=wx,o=rx /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rw--wxr-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w---xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=x,o=rw /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": -w---xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr-----
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=r,o=- /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r-xr-----
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w--wx-wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=wx,o=wx /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": -w--wx-wx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwx--xr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=x,o=rx /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rwx--xr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x---rw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=-,o=rw /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": r-x---rw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw---x-w-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=x,o=w /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{4juT7v-8TtRmHABraTVGsS4I8h0.QXzETO0wSO4kjNzEzW}
```
## What I learned
Setting permissions, for example- chmod u=r /flag will set the flag file to be only readable to the user. Not writable or executable.


## 8. The SUID Bit

### Add the SUID bit to the /challenge/getroot program in order to spawn a root shell cat the flag.

**Flag** `pwn.college{8lu-YPxF9LZDjPdz1DRTh6QANAE.QXzEjN0wSO4kjNzEzW}`

Add SUID bit to the program using chmod u+s. Run the program to run it as root. Cat the flag file int he shell and get the flag.

```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{8lu-YPxF9LZDjPdz1DRTh6QANAE.QXzEjN0wSO4kjNzEzW}
```
## What I learned
The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do. Instead, the "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file. The chmod u+s command adds SUID bit to a file and gives the user the ownership of it.