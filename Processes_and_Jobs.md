# Processes and Jobs

## 1. Listing Processes

### /challenge/run renamed to a random filename, and you cannot ls the /challenge directory. But it is also launched, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag.

**Flag** 'pwn.college{IALtej5tfy5P6_RD8rwSTcSZi1Y.QX4MDO0wSO4kjNzEzW}'

Pass the ps -efww command to see the non-truncated running process list. Find the renamed challenge program and run it.

```
hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:00 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 18:00 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 18:00 ?        00:00:00 /challenge/14657-run-31032
root         135     132  0 18:00 ?        00:00:00 sleep 6h
hacker       137       0  0 18:01 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143     137  0 18:01 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       153     143  0 18:02 pts/0    00:00:00 ps -efww
hacker@processes~listing-processes:~$ /challenge/14657-run-31032
Yahaha, you found me! Here is your flag:
pwn.college{IALtej5tfy5P6_RD8rwSTcSZi1Y.QX4MDO0wSO4kjNzEzW}
```
## What I learned
Overall, ps -ef and ps aux are used to list running processes. Adding ww at the end does not truncate the whole path to the process.


## 2. Killing Processes

### /challenge/run refuses to run while /challenge/dont_run is running! You must find the dont_run process and kill it. 

**Flag** 'pwn.college{IwYXV5Cgck_Zt-W-B5epd-aaZ-N.QXyQDO0wSO4kjNzEzW}'

List the running processes and grep the output for /challenge/dont_run. Kill its Process ID and then run the program to get the flag.

```
hacker@processes~killing-processes:~$ ps -efww | grep /challenge/dont_run
hacker       136     135  0 18:11 ?        00:00:00 /challenge/dont_run
hacker       163     145  0 18:19 pts/0    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{IwYXV5Cgck_Zt-W-B5epd-aaZ-N.QXyQDO0wSO4kjNzEzW}
```
## What I learned
kill command can be used to kill a process with its Process ID (PID).


## 3. Interrupting Processes

### /challenge/run refuses to give the flag until you interrupt it.

**Flag** 'pwn.college{ooBg-mlgQF1_MlulIIbbem2y6FF.QXzQDO0wSO4kjNzEzW}'

Run the program, then interrupt it with ctrl+c to get the flag.

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{ooBg-mlgQF1_MlulIIbbem2y6FF.QXzQDO0wSO4kjNzEzW}
```
## What I learned
ctrl-c interrupts whatever application is waiting on input from the terminal.


## 4. Killing Misbehaving Processes

### There's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which /challenge/run wants to write your flag. Kill this process.

**Flag** 'pwn.college{gAlzu6qzDwvSUdUH7TCYDW2SxRC.0FNzMDOxwSO4kjNzEzW}'

List the processes, find the decoy challenge and kill it using PID. Then read the fifo flag.

```
hacker@processes~killing-misbehaving-processes:~$ ps auxww
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   18:30   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.0  0.0 231708  2560 ?        S    18:30   0:00 /run/dojo/bin/sleep 6h
root         137  0.0  0.0   4132  1280 ?        S    18:30   0:00 /bin/bash /challenge/.init
root         138  0.0  0.0   4132  1280 ?        S    18:30   0:00 /bin/bash /challenge/.init
root         139  0.0  0.0   5204  3520 ?        S    18:30   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140  0.0  0.0   2744  1600 ?        S    18:30   0:00 sleep 6h
root         141  0.0  0.0   2744  1600 ?        S    18:30   0:00 sleep 6h
hacker       142  0.0  0.0  13516  9280 ?        Ss   18:30   0:00 /usr/bin/python /challenge/decoy
hacker       144  0.0  0.0 231576  3520 pts/0    Ss   18:30   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       150  0.0  0.0 231972  4160 pts/0    S    18:30   0:00 /run/dojo/bin/bash --login
hacker       160  0.0  0.0 233600  3840 pts/0    R+   18:34   0:00 ps auxww
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
ps pwn.college{gAlzu6qzDwvSUdUH7TCYDW2SxRC.0FNzMDOxwSO4kjNzEzW}
```
## What I learned
Killing misbehaving processes like /challenge/decoy and kill them.


## 5. Suspending Processes

### Run another copy of the challenge using the same terminal.

**Flag** 'pwn.college{40DVQpmxbGsvCneD4Pb9AvsL8iP.QX1QDO0wSO4kjNzEzW}'

Run the program, then suspend it using ctrl+z and run it again to get the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         139     130  0 18:56 pts/0    00:00:00 bash /challenge/run
root         141     139  0 18:56 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         139     130  0 18:56 pts/0    00:00:00 bash /challenge/run
root         146     130  0 18:56 pts/0    00:00:00 bash /challenge/run
root         148     146  0 18:56 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{40DVQpmxbGsvCneD4Pb9AvsL8iP.QX1QDO0wSO4kjNzEzW}
```
## What I learned
ctrl+z can be used to suspend a running program.


## 6. Resuming Processes

###  Run needs to be suspended and then resumed.

**Flag** 'pwn.college{UZzjjidNd4UGe5iOW5TM3ab-3-E.QX2QDO0wSO4kjNzEzW}'

Run the program then suspend using ctrl+z and then resume it using fg and put it back in the foreground of the terminal.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{UZzjjidNd4UGe5iOW5TM3ab-3-E.QX2QDO0wSO4kjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```
## What I learned
Resume a suspended process using fg to run it in the foreground of the terminal.


## 7. Backgrounding Processes

### Run another copy of the program in same terminal but not suspended.

**Flag** 'pwn.college{EYLMQLiMkhENBAMGgWKD32OBdIm.QX3QDO0wSO4kjNzEzW}'

Run the program, suspend it using ctrl-z, resume it in the background using bg command, run another program to get the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S+   bash /challenge/run
root         140 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S    bash /challenge/run
root         148 S    sleep 6h
root         149 S+   bash /challenge/run
root         151 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{EYLMQLiMkhENBAMGgWKD32OBdIm.QX3QDO0wSO4kjNzEzW}
```
## What I learned
bg command resumes the process in the background.


## 8. Foregrounding Processes

### Run the challenge by foregrounding a backgrounded process.

**Flag** 'pwn.college{gh0oU2rYE6kLE8uS3TytvrDOuST.QX4QDO0wSO4kjNzEzW}'

Run the program, suspend it using ctrl-z, background it with bg command and then foreground with fg command. This will get the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{gh0oU2rYE6kLE8uS3TytvrDOuST.QX4QDO0wSO4kjNzEzW}
```
## What I learned
Foregrounding a process that is running in the background.


## 9. Starting Backgrounded Processes

### Launch /challenge/run backgrounded for the flag.

**Flag** 'pwn.college{oO5w5vns3UVHoGbNLKsxmROntrL.QX5QDO0wSO4kjNzEzW}'

Run the program with & appended to it to start the program from background without suspending it.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{oO5w5vns3UVHoGbNLKsxmROntrL.QX5QDO0wSO4kjNzEzW}
```
## What I learned
To background processes right from the start without having to suspend them, append & to the command.


## 10. Process Exit Codes

### Retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument.

**Flag** 'pwn.college{MmJUO0OKVpkpWAABqm86QapAyKc.QX5YDO1wSO4kjNzEzW}'

Run get-code, this exits with an error code. Read the error code using $?. Apply the code as an argument to the submit-code program. This gives the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
159
hacker@processes~process-exit-codes:~$ /challenge/submit-code 159
CORRECT! Here is your flag:
pwn.college{MmJUO0OKVpkpWAABqm86QapAyKc.QX5YDO1wSO4kjNzEzW}
```
## What I learned
? variable used to access the exit code of a command and $ to prepend the variable in order to read the exit code which many times may be an error code and not just 0 (success) and 1 (error).