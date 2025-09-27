# File Globbing

## 1. Matching with *

### Change directory to /challenge using cd but the following argument should be of at most four characters. Run the program.

**Flag** 'pwn.college{U27x9CuIBjb-GXBvNvQUbu38rfU.QXxIDO0wSO4kjNzEzW}'

To have at most 4 characters after cd, I used globbing as cd /ch*. This is total of 4 characters and changes the directory to /challenge. Then I ran the challenge and got the program.

```
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{U27x9CuIBjb-GXBvNvQUbu38rfU.QXxIDO0wSO4kjNzEzW}
```
## What I learned
Globbing with * : To not write the complete paths everytime, we can use * to shorten the name.
Doesn't work with / and . starting files. (eg-/ */hacker).


## 2. Matching with ?

### Change directory to /challenge with cd but by replacing c and l in challenge with ?. Run the program.

**Flag** 'pwn.college{IraJ_WMslXLEgl2ub5jLomsVPCX.QXyIDO0wSO4kjNzEzW}'

Gave command with argument as- cd /?ha??enge. Changed the directory to /challenge and ran the program to get the flag.

## What I learned
While * can replace multiple characters, ? replaces only a single character.


## 3. Matching with []

### Change working directory to /challenge/files and run challenge with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

**Flag** 'pwn.college{cgeF3sioCDaUdO2ulppYyevLufq.QXzIDO0wSO4kjNzEzW}'

Changed directory to /challenge/files. Ran challenge with file_[bash].

```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{cgeF3sioCDaUdO2ulppYyevLufq.QXzIDO0wSO4kjNzEzW}
```
## What I learned
Instead of replacing characters, [] encloses parts of names of multiple files.


## 4. Matching paths with []

### From home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h.

**Flag** 'pwn.college{0iC-MHr8pXEEvad0yGMr5Re1i0l.QX0IDO0wSO4kjNzEzW}'

Ran /challenge/run with absolute path /challenge/files and bracket-globbed form of multiple files.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{0iC-MHr8pXEEvad0yGMr5Re1i0l.QX0IDO0wSO4kjNzEzW}
```
## What I learned
Running absolute paths with bracket-globs.


## 5. Multiple globs

### Change directory and run /challenge/run, providing a single argument of 3 characters or less globbed with two * globs in it that covers every word that contains the letter p.

**Flag** 'pwn.college{8jVAeiDjM7iP3vcDbkp0IuKQyrw.0lM3kjNxwSO4kjNzEzW}'

Listed the files with p in /challenge/files directory. Found pwing, splendid, happy, optimistic, uplifting files containing p. For 3 characters with 2 * and all words having p, I ran the programme with * p* argument. Got the flag.

```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{8jVAeiDjM7iP3vcDbkp0IuKQyrw.0lM3kjNxwSO4kjNzEzW}
```
## What I learned
For multiple files, using multiple globs * to find them. * could be any character or no character at all.


## 6. Mixing globs

### Change directory and, using globbing write a single 6 characters or less glob that when passed as an argument to /challenge/run will match the files "challenging", "educational", and "pwning".

**Flag** 'pwn.college{8dCHyru79ehdaBcPdX0MtfpsJUQ.QX1IDO0wSO4kjNzEzW}'

Changed directory, listed files and used bracket-glob to club the first letters of the 3 files as they are unique and used * to glob the rest file name.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{8dCHyru79ehdaBcPdX0MtfpsJUQ.QX1IDO0wSO4kjNzEzW}
```
## What I learned
Using [] for multiple files and * for rest of the file name together to find multiple files.


## 7. Exclusionary globbing

### Go to /challenge/files and run /challenge/run with all files that don't start with p, w, or n using ! or ^.

**Flag** 'pwn.college{QQReCiMMeaYt-Pmu5B1AqOZPPWn.QX2IDO0wSO4kjNzEzW}'

For all files the don't start with p,w,n, I changed directory then ran /challenge/run with argument in bracket-globs with ! and * for rest of the file name - [!pwn]*.

```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{QQReCiMMeaYt-Pmu5B1AqOZPPWn.QX2IDO0wSO4kjNzEzW}
```
## What I learned
! or ^ can be used as the first element in bracket-glob to exclude the files that start with the characters contained in [].


## 8. Tab completion

### Flag is copied to /challenge/pwncollege. Cat the file without typing the whole filename but using the tab key.

**Flag** 'pwn.college{8xdBxGwJ7REgaVPg0GorkCJsSi1.0FN0EzNxwSO4kjNzEzW}'

Used cat to read the flag. But only typed till 'cat /challenge/pwn'. Rest, used the tab key to automatically input 'college'. This gave the flag.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{8xdBxGwJ7REgaVPg0GorkCJsSi1.0FN0EzNxwSO4kjNzEzW}
```
## What I learned
Using tab key instead of * glob to reduce the risk of including unintended files and letting the filename be completed automatically with tab.


## 9. Multiple options for tab completion

### There is a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p and get the flag!

**Flag** 'pwn.college{EDL2EAVXFfR40NqJn5kCNO3ehSY.0lN0EzNxwSO4kjNzEzW}'

Change directory to /challenge/files. Typed cat p. Used tab to get pwn. Tab key twice to get all options. Found pwncollege-flag. Next cat pwnc. Tab key to cat pwncollege-. Tab twice for filtered options. Next type f. Double tab for options. Type fl. Double tab for options. Type fla. Double tab for last two options. End with flag to get the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-f
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-fl
pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-fla
pwncollege-flag      pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag
pwn.college{EDL2EAVXFfR40NqJn5kCNO3ehSY.0lN0EzNxwSO4kjNzEzW}
```
## What I learned
When multiple file names start with the same letter, use double tab key to get the options for the filenames.


## 10. Tab completion on commands

### Type pwncollege and hit the tab key to auto-complete it and get the flag.

**Flag** 'pwn.college{cYr0NNpdsa4fjMdrwP8Ubrclofc.0VN0EzNxwSO4kjNzEzW}'

Typed pwncollege and used tab key to get the rest of the command. Ran it and got the flag.

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-1096
Correct! Here is your flag:
pwn.college{cYr0NNpdsa4fjMdrwP8Ubrclofc.0VN0EzNxwSO4kjNzEzW}
```
## What I learned
Tab completion can also be applied on commands, not just files. But shouldn't be done often because several auto completes without double checking can cause wrong commands to run.
