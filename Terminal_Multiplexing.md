# Terminal Multiplexing

## 1. Launching Screen

### Launching screen will get the flag.

**Flag** `pwn.college{g-HTt9TeeLzEx_5d7meZmxLSDqJ.0VN4IDOxwSO4kjNzEzW}`

Enter screen command on terminal to get inside a screen session.

```
hacker@terminal-multiplexing~launching-screen:~$ screen
```
```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{g-HTt9TeeLzEx_5d7meZmxLSDqJ.0VN4IDOxwSO4kjNzEzW}
```
## What I learned
screen program creates virtual terminals inside the terminal. Like having multiple browser tabs for commands. And exit to exit the screen and enter terminal.


## 2. Detaching and Attaching

### For this challenge, launch screen, detach from it, run /challenge/run and reattach to see the flag.

**Flag** `pwn.college{cyGR-wFZugaR5uEKfPejsB1FkBJ.0lN4IDOxwSO4kjNzEzW}`

Launch screen using screen. Press ctrl-a + d to detach from the screen and run the program on terminal. Then reattach to the screen using screen -r. Flag will be on the screen.

```
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
```
```
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{cyGR-wFZugaR5uEKfPejsB1FkBJ.0lN4IDOxwSO4kjNzEzW}
Yes! Flag is: pwn.college{cyGR-wFZugaR5uEKfPejsB1FkBJ.0lN4IDOxwSO4kjNzEzW}
```
## What I learned
Detach from screen: ctrl-a followed by d  
Reattach from screen: screen -r  
ctrl-a is screen's activation key. Many functions can be activated by this.


## 3. Finding Sessions

### Three screen sessions have been created. One of them contains the flag. The other two are decoys. Check each one until you find it.

**Flag** `pwn.college{YpZ6xRa2NS1vl3VTmv_POwfs6dy.01N4IDOxwSO4kjNzEzW}`

List all the screen sessions. Attach to the first one using PID. The first screen itself gave the right flag.

```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        144.session_9da7198e03b2aead    (Detached)
        147.session_637ef5254ecbb021    (Detached)
        150.session_e3e9fe7ccac13e83    (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
```
```
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{YpZ6xRa2NS1vl3VTmv_POwfs6dy.01N4IDOxwSO4kjNzEzW}
pwn.college{YpZ6xRa2NS1vl3VTmv_POwfs6dy.01N4IDOxwSO4kjNzEzW}
```
## What I learned
screen -ls helps in listing all the detached screens.  
screen -r with the PID or name of the detached screen reattaches the user to that screen.


## 4. Switching Windows

### There is screen session with two windows: Window 0 and Window 1 which has a welcome message. Attach to the session with screen -r, then switch to Window 1 to get the flag.

**Flag** `pwn.college{QwgOVqF_juzs6Y7h384vD9LC1uS.0FO4IDOxwSO4kjNzEzW}`

screen -r reattached to window 1. Switched to window 0 using ctrl-a 0. Window 0 has the flag.

```
hacker@terminal-multiplexing~switching-windows:~$ screen -r
```
```
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
```
```
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{QwgOVqF_juzs6Y7h384vD9LC1uS.0FO4IDOxwSO4kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{QwgOVqF_juzs6Y7h384vD9LC1uS.0FO4IDOxwSO4kjNzEzW}
```
## What I learned
ctrl-a + c- Create new window  
ctrl-a + n- Next window  
ctrl-a + p- Previous window  
ctrl-a 0-9 - Jump directly to window 0-9  
ctrl-a " - selection menu of all windows  


## 5. Detaching and Attaching (tmux)

### For this challenge launch tmux. Detach from it. Run /challenge/run and reattach to see the flag.

**Flag** `pwn.college{QHxrt0fZ3mVAzkb0glAtRFZhn0-.0VO4IDOxwSO4kjNzEzW}`

Launch tmux using tmux command. Detach using ctrl-b + d. Run program and reattach using tmux a command. Flag is in tmux.

```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...
Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[exited]
```
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 61;1;6;7;21;22;23;24;28;32;42c echo Congratulations, here is your flag: pwn.college{QHxrt0fZ3mVAzkb0glAtRFZhn0-.0VO4IDOxwSO4kjNzEzW}
-bash: 61: command not found
-bash: 1: command not found
-bash: 6: command not found
-bash: 7: command not found
-bash: 21: command not found
-bash: 22: command not found
-bash: 23: command not found
-bash: 24: command not found
-bash: 28: command not found
-bash: 32: command not found
-bash: 42c: command not found
```
## What I learned
tmux is a modern version of screen. Its activation key is ctrl-b.  
Detach- ctrl-b + d  
Reattach- tmux attach / tmux a  


## 6. Switching Windows (tmux)

### A tmux session with two windows is created. Window 0 has the flag. Window 1 has welcome page. Get the flag.

**Flag** `pwn.college{oDDOJQeGjRe47DpcUyctsdlETaZ.0FM5IDOxwSO4kjNzEzW}`

Launch tmux. It sends us to window 1. Use ctrl-b + 0 to switch to window 0. Find the flag there.

```
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux
```
```
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
```
```
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{oDDOJQeGjRe47DpcUyctsdlETaZ.0FM5IDOxwSO4kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{oDDOJQeGjRe47DpcUyctsdlETaZ.0FM5IDOxwSO4kjNzEzW}
```
## What I learned
tmux uses ctrl-b for all the functionalities screen uses ctrl-a for.