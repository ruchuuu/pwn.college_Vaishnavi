# Comprehending Commands

## 1. Cat: not the pet, but the command

### Flag has to be read with operating the cat command on the flag file in the home directory.

**Flag** 'pwn.college{cXeQvqOxjf-u8biQGg7kCZkpccS.QXxcTN0wSO4kjNzEzW}'

Since the flag was copied to the flag file, I used cat command with flag argument to read what was in the file flag and got the flag.

## What I learned
cat: helps in reading what is given in the file.


## 2. Catting absolute paths

### Read the flag by catting it from its absolute path, not from the home directory.

**Flag** 'pwn.college{cnxucfgh1f__2m6L5RYiZ-KsMdQ.QX5ETO0wSO4kjNzEzW}'

For absolute path, I used / before file and used it (/file) with cat command to get the flag.

## What I learned
cat can read files from different locations/directories as well, as long as absolute path is mentioned.


## 3. More catting practice

### We need to retrieve the flag from a random directory without using cd command and read it with cat.

**Flag** 'pwn.college{8_9wGz0W2LnHGxib8dUtH_h4Shs.QXwITO0wSO4kjNzEzW}'

In the beginning of the terminal, it is told that the flag is hidden in the file /usr/share/ca-certificates-java/flag. So I used the cat command with the absolute path of the flag with the file and got the flag.

## What I learned 
Reading files with absolute path of the flag using cat command.


## 4. Grepping for a needle in a haystack

### Finding the flag in a file of thousand lines of text using grep command.

**Flag** 'pwn.college{wyN2DeKVdH70KvtzgGJ8rbfr1ec.QX3EDO0wSO4kjNzEzW}'

Flag always starts with 'pwn.college', so I gave the argument 'grep pwn.college /challenge/data.txt' with grep trying to find pwn.college in the absolute path of the text file.

## What I learned 
grep command: finding keywords in files
A flag will always begin with pwn.college


## 5. Comparing files

### Find the flag by comparing two files with same content apart from the flag in one of them.

**Flag** 'pwn.college{ce-rKKCR9GYIx05YeiMI4hvrJWi.01MwMDOxwSO4kjNzEzW}'

I compared the two files given in the challenge using diff command. This gave 0a1 meaning after line 0 of file 1, add line 1 of file 2 which is the flag from file 2.

```
hacker@commands~comparing~files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
0a1
> pwn.college{ce-rKKCR9GYIx05YeiMI4hvrJWi.01MwMDOxwSO4kjNzEzW}
```
## What I learned
diff command
0a1 statement
2c2 statement: line 2 changed with 'word' in first file being replaced by 'word1' in second file.
(<):first file
(>):second file


## 6. Listing files

### List the files in /challenge, find the name of the file and run it.

**Flag** 'pwn.college{8FU2JWQKq47P9vRXam3cDrDZwIq.QX4IDO0wSO4kjNzEzW}'

I listed all the files with ls, found the renamed run file, and ran it with /challenge.

## What I learned
ls command: lists all the files in the directory.


## 7. Touching files

### Create two files using touch and run the challenge to get the flag.

**Flag** 'pwn.college{U5NAaN41kCe9Kr0uTtSD26xdngP.QXwMDO0wSO4kjNzEzW}'

First created the /twp/pwn file using touch command with absolute path, then created the /tmp/college file using touch similarly. Then ran /challenge/run to get the flag.

## What I learned
touch command used to create new files in directories.


## 8. Removing files

### Delete a created file in the home directory using rm command and run the challenge.

**Flag** 'pwn.college{wrrKUVfSngs5q4qDYdWBBEtqr7R.QX2kDM1wSO4kjNzEzW}'

Used rm command to remove the delete_me file and then ran /challenge/check to get the flag.

## What I learned
rm command to delete a file from the directory.


## 9. Moving files

### Move the /flag file into /tmp/hack-the-planet using mv command and run the challenge to get the flag.

**Flag** 'pwn.college{4_sfZvZU5UJA0JGDzgVHbtR47kV.0VOxEzNxwSO4kjNzEzW}'

Created a flag file using touch. Changed directory to /tmp. Created hack-the-planet file in it. Changed to home directory and moved /flag to /tmp/hack-the-planet. Then ran /challenge/check to get the flag.

## What I learned
mv command used to move files from one location/directory to another by giving absolute path.


## 10. Hidden files

### Find the flag in the hidden file using ls with special command -a.

**Flag** 'pwn.college{094b3mz0OhlfggVIGb699y4Rwwv.QXwUDO0wSO4kjNzEzW}'

Used ls -a to list even the hidden files. Found .flag-14864116724717 as a hidden file. Read the file using cat command and got the flag.

## What I learned
Special command ls -a to find hidden files in the directory.


## 11. An Epic Filesystem Quest

### Find the flag using ls and cat commands along with the help of hints and clues.

**Flag** 'pwn.college{E2XvZYiy_znbD6UMRYTkvfJTqTh.QX5IDO0wSO4kjNzEzW}'

Listed all the files in the directory, found SNIPPET file matching the HINTS and read it with cat. Got the first clue which gave a different directory. Changed with cd, listed files, got WHISPER. Read WHISPER and got the next clue with next directory. Without using cd, listed the files using absolute path and read INSIGHT-TRAPPED. Got another clue and repeated the pattern till I got the flag upon reading one of the files.

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
SNIPPET  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin      challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat SNIPPET
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/media/platform/qcom/camss

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/media/platform/qcom/camss
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/platform/qcom/camss$ ls
Makefile      camss-csid.h            camss-csiphy.c  camss-ispif.h    camss-vfe.c    camss-video.h
WHISPER       camss-csiphy-2ph-1-0.c  camss-csiphy.h  camss-vfe-4-1.c  camss-vfe.h    camss.c
camss-csid.c  camss-csiphy-3ph-1-0.c  camss-ispif.c   camss-vfe-4-7.c  camss-video.c  camss.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/platform/qcom/camss$ cat WHISPER
Great sleuthing!
The next clue is in: /usr/share/racket/pkgs/drracket-plugin-lib/lang/compiled

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/platform/qcom/camss$ ls /usr/share/racket/pkgs/drracket-plugin-lib/lang/compiled
INSIGHT-TRAPPED  debugger-language-interface_rkt.dep  debugger-language-interface_rkt.zo  info_rkt.dep  info_rkt.zo
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/platform/qcom/camss$ cat /usr/share/racket/pkgs/drracket-plugin-lib/lang/compiled/INSIGHT-TRAPPED
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/nvme
The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/platform/qcom/camss$ cd /opt/linux/linux-5.4/drivers/nvme
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/nvme$ ls -a
.  ..  .SECRET  .built-in.a.cmd  Kconfig  Makefile  built-in.a  host  target
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/nvme$ cat .SECRET
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/net/nfc/hci
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/nvme$ cd /opt/linux/linux-5.4/net/nfc/hci
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/net/nfc/hci$ ls
HINT  Kconfig  Makefile  command.c  core.c  hci.h  hcp.c  llc.c  llc.h  llc_nop.c  llc_shdlc.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/net/nfc/hci$ cat HINT
Tubular find!
The next clue is in: /usr/share/icons/Humanity/apps/192
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/net/nfc/hci$ ls /usr/share/icons/Humanity/apps/192
TRACE  yelp-icon-big.svg
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/net/nfc/hci$ cat /usr/share/icons/Humanity/apps/192/TRACE
Yahaha, you found me!
The next clue is in: /opt/libslub/.git/logs/refs/remotes/origin
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/net/nfc/hci$ cd /opt/libslub/.git/logs/refs/remotes/origin
hacker@commands~an-epic-filesystem-quest:/opt/libslub/.git/logs/refs/remotes/origin$ ls
HEAD  TIP
hacker@commands~an-epic-filesystem-quest:/opt/libslub/.git/logs/refs/remotes/origin$ cat TIP
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/pinctrl/spear

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/libslub/.git/logs/refs/remotes/origin$ cd /opt/linux/linux-5.4/drivers/pinctrl/spear
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/pinctrl/spear$ ls
EVIDENCE  Makefile          pinctrl-spear.c  pinctrl-spear1310.c  pinctrl-spear300.c  pinctrl-spear320.c  pinctrl-spear3xx.h
Kconfig   pinctrl-plgpio.c  pinctrl-spear.h  pinctrl-spear1340.c  pinctrl-spear310.c  pinctrl-spear3xx.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/pinctrl/spear$ cat EVIDENCE
Lucky listing!
The next clue is in: /etc/ld.so.conf.d

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/pinctrl/spear$ cd /etc/ld.so.conf.d
hacker@commands~an-epic-filesystem-quest:/etc/ld.so.conf.d$ ls
BLUEPRINT  i386-linux-gnu.conf  libc.conf  x86_64-linux-gnu.conf  zz_i386-biarch-compat.conf  zz_x32-biarch-compat.conf
hacker@commands~an-epic-filesystem-quest:/etc/ld.so.conf.d$ cat BLUEPRINT
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{E2XvZYiy_znbD6UMRYTkvfJTqTh.QX5IDO0wSO4kjNzEzW}
```
## What I learned
cd, ls, cat, la -a commands


## 12. Making directories

### Make a /tmp/pwn directory and make a college file. Then run the challenge.

**Flag** 'pwn.college{YWZI2Vbu3GZ35HViG14LujeK5Hg.QXxMDO0wSO4kjNzEzW}'

Changed directory to /tmp. Made pwn directory using mkdir. Created college file using touch and ran the challenge using /challenge/run. Got the flag.

## What I learned
mkdir command to make new directory.


## 13. Finding files

### Find the flag hidden in a random directory on the filesystem using find command.

**Flag** 'pwn.college{snEIRmyT0pdKG3HlXUMYn0lSMs6.QXyMDO0wSO4kjNzEzW}'

Used 'find / -name flag' to find the name flag in the whole filesystem. Got many filesystems not accessible but used cat to read one which was accessible and got the flag (cat /usr/share/racket/collects/setup/infotab/flag).

## What I learned
find: find particular words (with -name) or files in systems or directories.


## 14. Linking files

### Use symlink to link the flag file with challenge file to get the flag.

**Flag** 'pwn.college{Aee7nWDHBVsMYN7DzcG38IEq0LW.QX5ETN1wSO4kjNzEzW}'

Used symlink ln -s to link flag with absolute path /home/hacker/not-the-flag and ran the challenge to get the flag.

```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{Aee7nWDHBVsMYN7DzcG38IEq0LW.QX5ETN1wSO4kjNzEzW}
```
## What I learned
Hard link: reference the original file directly.
Soft (symbolic) link:  special type of file that references another file.
ln -s: command for symlink










