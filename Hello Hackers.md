#Hello Hackers

##Intro to Commands

###In the first challenge, we invoke our first command, the 'hello' command, to get the flag.

**Flag** 'pwn.college{08-GGwKBTEICIEhKna9lipjqgv8.QX3YjM1wSO4kjNzEzW}'

Firstly, I got the ssh key using the ssh command. Then I faced a problem in connecting the key with the challenge and getting the flag. After searching around, I found out that I was operating on a Windows friendly directory. So, I copied the directory to a Unix freindly interface and got the flag. 
Also, the ssh key is supposed to be private but my key and key.pub were public. This I rectified using chmod 600 which helped in converting the key to rw mode.

```
cp/mnt/c/Users/Vaishnavi/key ~/.ssh/key
chmod 600 ~/.ssh/key
ssh -i ~/.ssh/key hacker@dojo.pwn.college
```

###What I learned
cat.key command
cp command
chmod 600 command


##Intro to Arguments

###In this challenge, we had to get the flag with multiple arguments- 'hello hackers' command.

**Flag** 'pwn.college{YVUCoAPan36pywdsAGkBLXDS_ds.QX4YjM1wSO4kjNzEzW}'

At first, I gave a single argument of hello, where the terminal gave me a prompt that the command should have multiple arguments. Then I gave 'hello hackers' command and got the flag.

###What I learned
Single arguments
Multiple arguments
Terminal Prompts


##Command History

###In this challenge, we had to retrieve the flag of the previous commands done and injectit into our history with an up arrow.

**Flag** 'pwn.college{EqsgJwu2bEmqPPtxhd7jFgjuUgo.0lNzEzNxwSO4kjNzEzW}'

I gave the up-arrow key in the terminal and got the flag of the previous commands.

###What I learned
Command history- typing the same commands from scratch can be time consuming. Hence, a flag can be injected for history of every command we invoke.

