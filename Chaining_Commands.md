# Chaining Commands

## 1. Chaining with Semicolons

### Run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

**Flag** `pwn.college{8zEDmcPHqv-r1JsvpBD1k1E2Uaz.QX1UDO0wSO4kjNzEzW}`

Used ; to chain both commands in one line

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{8zEDmcPHqv-r1JsvpBD1k1E2Uaz.QX1UDO0wSO4kjNzEzW}
```
## What I learned
; lets us chain two or more commands together so that both commands are entered before execution of any.


## 2. Building on Success

### Chain the programs /challenge/first-success and /challenge/second using the && operator. Also, try running each command separately first to see what happens.

**Flag** `pwn.college{wfni8nabhTVxupwRJFa6di0jXeY.0lM0MDOxwSO4kjNzEzW}`

Running both challenges individually, we don't get the flag. But chaining them both using && operator will execute the commands and give the flag.

```
hacker@chaining~building-on-success:~$ /challenge/first-success
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{wfni8nabhTVxupwRJFa6di0jXeY.0lM0MDOxwSO4kjNzEzW}
```
## What I learned
&& operator allows second command to run only if the first command succeeds.


## 3. Handling Failure

### Chain /challenge/first-failure and /challenge/second using the || operator.

**Flag** `pwn.college{8fdAc6qG84hR6t7Vdg-0xWCmxFU.01M0MDOxwSO4kjNzEzW}`

Ran both the challenges using || operator.

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8fdAc6qG84hR6t7Vdg-0xWCmxFU.01M0MDOxwSO4kjNzEzW}
```
## What I learned
|| operator runs the second command only if the first command fails.


## 4. Your First Shell Script

### Run /challenge/pwn and then /challenge/college, but in a shell script called x.sh, then run it with bash.

**Flag** `pwn.college{8_Sp9ZT4C_qM2CXSkiHuOFqW6Hr.QXxcDO0wSO4kjNzEzW}`

Redirected the output of pwn program to x.sh file. Then appended the output of college program to the same file. Run the script with bash.

```
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn" > x.sh
hacker@chaining~your-first-shell-script:~$ echo "/challenge/college" >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{8_Sp9ZT4C_qM2CXSkiHuOFqW6Hr.QXxcDO0wSO4kjNzEzW}
```
## What I learned
For more complex executions, the length of the combined prompt becomes very lengthy. So, we can put these commands in a file, called a shell script, and run them by executing the file.


## 5. Redirecting Script Output

### Create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command.

**Flag** `pwn.college{UwgIPcru_KK3c_dwo8xhDH5kG25.QX4ETO0wSO4kjNzEzW}`

Redirect outputs of pwn and college command to x.sh file. Execute the file using bash and pipe the output to /challenge/solve. This gets the flag.

```
hacker@chaining~redirecting-script-output:~$ echo "/challenge/pwn" > x.sh
hacker@chaining~redirecting-script-output:~$ echo "/challenge/college" >> x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{UwgIPcru_KK3c_dwo8xhDH5kG25.QX4ETO0wSO4kjNzEzW}
```
## What I learned
We can send the output of several programs to one command by creating a shell script of all the programs and pipe its output to that one command.


## 6. Executable Shell Scripts

### Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash.

**Flag** `pwn.college{c6PtIMvBcex_TMchlEr9d4-FMsI.QX0cjM1wSO4kjNzEzW}`

Read /challenge/solve into x.sh file. Use chmod a+x to make the file executable in all modes. Run x.sh with current path to get the flag.

```
hacker@chaining~executable-shell-scripts:~$ echo "/challenge/solve" > x.sh
hacker@chaining~executable-shell-scripts:~$ chmod a+x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{c6PtIMvBcex_TMchlEr9d4-FMsI.QX0cjM1wSO4kjNzEzW}
```
## What I learned
A shell script can be called without bash command as well if we change the permissions of the file and invoke it with its original path.


## 7. Understanding Shebangs

### Create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify that the script works correctly.

**Flag** `pwn.college{UESpUtDwhrMmT5u2QpHA3bbi0by.0VOzMDOxwSO4kjNzEzW}`

Put #!/bin/bash as header of shell script and then add 'hack the planet' to the file. Make the file executable using chmod and then run the program.

```
hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ echo 'echo "hack the planet"' >> /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{UESpUtDwhrMmT5u2QpHA3bbi0by.0VOzMDOxwSO4kjNzEzW}
```
## What I learned
If program file starts with shebang (#!), Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument. Here, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash /home/hacker/solve.sh to launch the script.


## 8. Scripting with Arguments

### Write a script at /home/hacker/solve.sh that takes two arguments and outputs them in reverse order. Once the script works correctly, run /challenge/run to get the flag.

**Flag** `pwn.college{8Ka8zq-b7nPWlkQ5v0ZqH8yfkeE.0VNzMDOxwSO4kjNzEzW}`

Start the shell script with shebang, then enter the command "$2 $1" which means that the second entered argument will print first and then the second argument. Then run the file with pwn as first command and college as second. Then run the program.

```
hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{8Ka8zq-b7nPWlkQ5v0ZqH8yfkeE.0VNzMDOxwSO4kjNzEzW}
```
## What I learned
$1: first command entered  
$2: second command entered and so on  
With this we can write codes in our script which can be taken as arguments later with the file.


## 9. Scripting with Conditionals

### Write a script at /home/hacker/solve.sh that takes one argument, if the argument is "pwn", output "college". For any other input, output nothing. Once the script works correctly, run /challenge/run to get the flag.

**Flag** `pwn.college{QaCQhOmA2lfXL8JvaMilw0qWaxo.0lNzMDOxwSO4kjNzEzW}`

Make a shell script with shebang add an if statement where check whether $1 == pwn. If yes then print "college" and end the block with fi. Run the script with pwn argument and check. If college output the run the program to get the flag.

```
hacker@chaining~scripting-with-conditionals:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'if [ "$1" == "pwn" ]' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo '     echo "college"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{QaCQhOmA2lfXL8JvaMilw0qWaxo.0lNzMDOxwSO4kjNzEzW}
```
## What I learned
In bash, if statements can be written to make decisions. If statement needs a then command. And end the block with fi (reverse of if). Also use spaces between if, [, =, etc.


## 10. Scipting with Default Cases

### Write a script at /home/hacker/solve.sh that takes one argument, if the argument is "pwn", output "college". For any other input, output "nope".

**Flag** `pwn.college{gLGAy5SB5T-CUQ2K2cm6oo_f8HD.01NzMDOxwSO4kjNzEzW}`

Add else to the if statement in shell script. If first argument is "pwn", then print "college". Else statement- print "nope" and end the script. Check and run the program.

```
hacker@chaining~scripting-with-default-cases:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'if [ "$1" == "pwn" ]' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'then' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo '      echo "college"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'else' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo '      echo "nope"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ echo 'fi' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{gLGAy5SB5T-CUQ2K2cm6oo_f8HD.01NzMDOxwSO4kjNzEzW}
```
## What I learned
If-else statement in shell script and running arguments with those scripts.


## 11. Scripting with Multiple Conditions

### Write a script at /home/hacker/solve.sh that takes one argument, if the argument is "hack", output "the planet". If the argument is "pwn", output "college". If the argument is "learn", output "linux". For any other input, output "unknown".

**Flag** `pwn.college{c1int_RkwwWsR7Op30YMSUGjgF1.0FOzMDOxwSO4kjNzEzW}`

Write an elif script. If $1 == "hack", print "the planet". Elif $1 == "pwn", print "college". Elif $1 == "learn", print "linux". Else, print "unknown". End script with fi. Run the program.

```
hacker@chaining~scripting-with-multiple-conditions:~$ echo '#!/bin/bash' > ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'if [ "$1" == "hack" ]' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '    echo "the planet"' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'elif [ "$1" == "pwn" ]' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '    echo "college"' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'elif [ "$1" == "learn" ]' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'then' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '    echo "linux"' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'else' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo '    echo "unknown"' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ echo 'fi' >> ~/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{c1int_RkwwWsR7Op30YMSUGjgF1.0FOzMDOxwSO4kjNzEzW}
```

## What I learned
elif statement in shell script for multiple conditions.


## 12. Reading Shell Scripts

### /challenge/run is a shell script that requires a secret password, but that password is hardcoded into the script iself. Read the script, figure out the password, and get the flag.

**Flag** `pwn.college{QyxH7D38qM0_JdLlhr5HMQ0irab.0lMwgDOxwSO4kjNzEzW}`

Cat the program to read the shell script and see the password. Then run the challenge and enter the password to get the flag.

```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{QyxH7D38qM0_JdLlhr5HMQ0irab.0lMwgDOxwSO4kjNzEzW}
```
## What I learned
Many programs in Linux are shell scripts. We can use cat to read these programs and see how they function.