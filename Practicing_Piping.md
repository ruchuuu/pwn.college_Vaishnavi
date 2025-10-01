# Practicing Piping

## 1. Redirecting output

### Write the word PWN to filename COLLEGE using output redirection.

**Flag** 'pwn.college{o5fx4sDQjgckb7DG2Yz3sd2AczV.QX0YTN0wSO4kjNzEzW}'

Used echo to print the word PWN in the file COLLEGE using > character.

## What I learned
Three channels used in Linux, stdin, stdout and stderr denoting standard input, output and error.
'>' character helps in redirecting output of echo command to another file.


## 2. Redirecting more output

### Redirect output of /challenge/run to a file named myflag.

**Flag** 'pwn.college{ER5C2ibi_KnebxFpKnPlHH7kWa7.QX1YTN0wSO4kjNzEzW}'

Redirected output of command /challenge/run to file myflag using > character. Then read the file using cat which printed the file.

```
hacker@piping~redirecting-more-output:~$ /challenge/run>myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ER5C2ibi_KnebxFpKnPlHH7kWa7.QX1YTN0wSO4kjNzEzW}
```
## What I learned
Output can also be redirected from any other command to a file, not just echo.


## 3. Appending output

### Run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. This will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file.

**Flag** 'pwn.college{UyIQKMjDzuoZmisIhGZHM9JVMrR.QX3ATO0wSO4kjNzEzW}'

Appended /challenge/run to ~/the-flag using >> character. Then read the file to get the flag. The thing to be careful was that if I had used the > chracter, the second half of the flag woul overwrite the first.

```
hacker@piping~appending-output:~$ /challenge/run>>~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag
 |
\|/ This is the first half:
 v
pwn.college{UyIQKMjDzuoZmisIhGZHM9JVMrR.QX3ATO0wSO4kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```
## What I learned
'>>' character used to append an input into the file because simply redirecting deletes the old content of the file and overwites the new output.


## 4. Redirecting errors

### Redirect the output of /challenge/run to myflag, and the errors to instructions.

**Flag** 'pwn.college{4tWtyB3EyoUqByHeZTrTbzFGtYC.QX3YTN0wSO4kjNzEzW}'

Redirected output using > character and 2> to redirect the error to the instructions file. Then read the myflag file using cat to get the flag.

```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{4tWtyB3EyoUqByHeZTrTbzFGtYC.QX3YTN0wSO4kjNzEzW}
```
## What I learned
File Descriptor (FD) is a number that describes the channel of Linux. FD0- stdin; FD1- stdout; FD2- stderr. Hence, 1> redirects stdout and 2> redirects stderr.


## 5. Redirecting input

### Redirect the PWN file to /challenge/run and have the PWN file contain the value COLLEGE. Write that value to the PWN file using output redirection from echo.

**Flag** 'pwn.college{8b6upzwM_t3AKZmG6kgyegOUO7f.QXwcTN0wSO4kjNzEzW}'

Printed output COLLEGE to PWN using > . Then redirected input of PWN to /challenge/run using < .

```
hacker@piping~redirecting-input:~$ echo COLLEGE>PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{8b6upzwM_t3AKZmG6kgyegOUO7f.QXwcTN0wSO4kjNzEzW}
```
## What I learned
'<' character used to redirect input to programs.


## 6. Grepping stored results

### Redirect the output of /challenge/run to /tmp/data.txt. Then grep that file for the flag in hundred thousands lines of text.

**Flag** 'pwn.college{8j5PyWoMqsddsTK0PehKxPrIHPE.QX4EDO0wSO4kjNzEzW}'

Redirected the output to data.txt using >. Searched for the key pwn.college in data.txt using grep as all flags have that in common.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{8j5PyWoMqsddsTK0PehKxPrIHPE.QX4EDO0wSO4kjNzEzW}
```
## What I learned
Grepping from output redirected and stored to the file from a program.


## 7. Grepping live output

### /challenge/run will output a hundred thousand lines of text, including the flag. Grep for the flag using pipe operator.

**Flag** 'pwn.college{Qj0SxZ3RHCChgi9QLkv8JxYQLcl.QX5EDO0wSO4kjNzEzW}'

Without storing results, I used the pipe operator to grep from the live output of /challenge/run and searched for pwn.college that gave the flag.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Qj0SxZ3RHCChgi9QLkv8JxYQLcl.QX5EDO0wSO4kjNzEzW}
```
## What I learned 
Without having to store the outputs of programs in a file, we can operate on live output using | (pipe operator). stdout of /challenge/run connected to stdin of grep command in this case.


## 8. Grepping errors

### Redirect standard error and grep through it to find the flag.

**Flag** 'pwn.college{YrXyct_ARANSBHRwOrEN-LvZw_Z.QX1ATO0wSO4kjNzEzW}'

Used 2>&1 to redirect stderr to stdout and the use | for combined output to grep for pwn.college to get the flag.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{YrXyct_ARANSBHRwOrEN-LvZw_Z.QX1ATO0wSO4kjNzEzW}
```
## What I learned
| can be used only for redirecting stdout. 
'>&' redirects a file descriptor to another file descriptor. 2>&1 would redirect stderr of program to stdout. This output can then be operated with |.


## 9. Filtering with grep -v

### /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags mixed in with the real flag. Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag.

**Flag** 'pwn.college{Yij6_e-TFgjorbHSk7QMs4zX0kX.0FOxEzNxwSO4kjNzEzW}'

Filtered out "DECOY" from the live output using grep -v. Got the filtered flag.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{Yij6_e-TFgjorbHSk7QMs4zX0kX.0FOxEzNxwSO4kjNzEzW}
```
## What I learned
Word used with grep -v(invert match) command is excluded from the final findings of a search.


## 10. Duplicating piped data with tee

### /challenge/pwn must be piped into /challenge/college, but by intercepting the data to see what pwn needs from user.

**Flag** 'pwn.college{YcJXwj3z2gi1Os7LLe1o2G-CbpC.QXxITO0wSO4kjNzEzW}'

Piped pwn to college using tee in between along with creating an output file of /challenge/pwn to intercept the data. Then read the output file that showed that /challenge/pwn had to be run with a secret argument. Upon piping pwn with secret argument to college, flag was retrieved.

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee /challenge/pwn_output | /challenge/college
Processing...
WARNING: you are overwriting file /challenge/pwn_output with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat /challenge/pwn_output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "YcJXwj3z"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret YcJXwj3z | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{YcJXwj3z2gi1Os7LLe1o2G-CbpC.QXxITO0wSO4kjNzEzW}
```
## What I learned
The tee command duplicates data flowing through pipes to any number of files provided on the command line. This helps in seeing where the command went wrong and debigging it.


## 11. Process substitution for input

### Use process substitution with diff to compare the outputs of two programs (/challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag) and find the flag!

**Flag** 'pwn.college{87t8ZF3WxW0XwfKfKktTt2S80Jh.0lNwMDOxwSO4kjNzEzW}'

Used diff with <(/challenge/print_decoys) and <(/challenge/print_decoys_and_flag) which allows to pass the output of these commands as a file-like input. So diff is finding the difference between the two temporary files created. This showed the difference of the flag and printed it.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
0a1
> pwn.college{87t8ZF3WxW0XwfKfKktTt2S80Jh.0lNwMDOxwSO4kjNzEzW}
```
## What I learned 
Instead of saving each command's output to a different file, we can use Process Substitution which is <(command). This will run the command and redirect its output to a temporary file that it will create.


## 12. Writing to multiple programs

### Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands.

**Flag** 'pwn.college{sGeMecLAICi8jewZ4lPy7vtMZVD.QXwgDN1wSO4kjNzEzW}'

Used | tee to redirect output to file of /challenge/the and directly piped to /challenge/planet. All of this happens concurrently and commands run on live output.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack| tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{sGeMecLAICi8jewZ4lPy7vtMZVD.QXwgDN1wSO4kjNzEzW}
```
## What I learned
tee duplicates data to two files. Output process substitution can be performed using >(command).
rev command reads data from stdin, reverses its order and writes it to stdout.


## 13. Split-piping stderr and stdout

### Redirect /challenge/hack's stderr to /challenge/the and redirect /challenge/hack's stdout to /challenge/planet.

**Flag** 'pwn.college{oVaU-abKR7noSGdCcgJ_220Qmct.QXxQDM2wSO4kjNzEzW}'

Redirect error of hack to >() of the (output process substitution) and used pipe operator to redirect output to planet.

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{oVaU-abKR7noSGdCcgJ_220Qmct.QXxQDM2wSO4kjNzEzW}
```
## What I learned 
Redirecting error using 2> and output using |.


## 14. Named pipes

### Create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it.

**Flag** 'pwn.college{8HPWklW1ox8dOZUU26XQg_iCzfq.01MzMDOxwSO4kjNzEzW}'

Made the file using mkfifo and redirected stdout of /challenge/run to /tmp/flag_fifo using > operator. Then opened a second terminal to make the FIFO file accessible using cat command simultaneously to the command in the first terminal. This printed the flag.

```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
```
```
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{8HPWklW1ox8dOZUU26XQg_iCzfq.01MzMDOxwSO4kjNzEzW}
```
## What I learned
FIFO: First (byte) In, First (byte) Out is a special file that behaves like a pipe but we can control where FIFOs are created.
mkfifo creates a FIFO file. Writing or operating on FIFO file will be halted till the file is opened in read mode on a different console.