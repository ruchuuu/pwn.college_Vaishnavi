# Data Manipulation

## 1. Translating characters

### /challenge/run will print the flag but will swap the casing of all characters. Undo it with tr and get the flag.

**Flag** 'pwn.college{Q71ZDCSiA14xku7MmYU907JRlRk.01MxEzNxwSO4kjNzEzW}'

Run the challenge and pipe the output with tr changing a-z to A-Z and A-Z to a-z.

```
hacker@data~translating-characters:~$ /challenge/run | tr a-zA-Z A-Za-z
yOUR CASE-SWAPPED FLAG:
pwn.college{Q71ZDCSiA14xku7MmYU907JRlRk.01MxEzNxwSO4kjNzEzW}
```
## What I learned
tr translates characters it receives over stdin and prints them to stdout. It translates characters provided in its first argument to the character provided in its second argument.


## 2. Deleting characters

### There are some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them.

**Flag** 'pwn.college{saBJuR6JKlqMfT86xON5e6HPAw9.0FNxEzNxwSO4kjNzEzW}'

Pipe the challenge program's output to input where tr -d is used to delete ^ and %.

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{saBJuR6JKlqMfT86xON5e6HPAw9.0FNxEzNxwSO4kjNzEzW}
```
## What I learned
tr -d with characters can be used to delete the said characters from the input.


## 3. Deleting newlines

### Delete the newlines injected in the flag with tr's -d flag and the escaped newline specification.

**Flag** 'pwn.college{cbL3XNpHen9wuhotpoxrGLm04xo.0VNxEzNxwSO4kjNzEzW}'

Piped the output of program to tr -d "\n" which deletes the new lines in the flag.

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{cbL3XNpHen9wuhotpoxrGLm04xo.0VNxEzNxwSO4kjNzEzW}
```
## What I learned
\n represents a newline and a newline can be deleted using the tr -d command.


## 4. Extracting the first lines with head

### /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag.

**Flag** 'pwn.college{s_DjtQ-irb_aPR_hkZN0BQb1xHm.0lNxEzNxwSO4kjNzEzW}'

Pipe pwn's output to head -n 7 (first 7 lines) and pipe that output to college.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{s_DjtQ-irb_aPR_hkZN0BQb1xHm.0lNxEzNxwSO4kjNzEzW}
```
## What I learned
head command displays the first 10 lines of output. To get desired number of lines, we can use head -n 7 in this case to get just 7 lines.


## 5. Extracting specific sections of text

### /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" to join them together into a single line.

**Flag** 'pwn.college{gIxDRTtfkuFC3pIeEn1ciEFxxAQ.01NxEzNxwSO4kjNzEzW}'

Run the program to see the column number of the flag. Then use cut -d " " -f2 to extract that column and then use tr -d "\n" to delete the newlines.

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
13359 p
14866 w
7180 n
27616 .
70 c
9152 o
10183 l
3091 l
25455 e
8188 g
4106 e
11581 {
10815 g
14213 I
15806 x
10395 D
651 R
4690 T
25524 t
19182 f
29478 k
24090 u
3655 F
22420 C
21710 3
13739 p
561 I
6076 e
27555 E
7753 n
30832 1
8989 c
24115 i
5592 E
13983 F
7759 x
25602 x
20515 A
26132 Q
25224 .
31993 0
32751 1
14701 N
19774 x
14601 E
6194 z
15330 N
6105 x
17920 w
22501 S
311 O
20700 4
11733 k
1656 j
22018 N
13294 z
3498 E
20262 z
23140 W
23442 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f2 | tr -d "\n"
pwn.college{gIxDRTtfkuFC3pIeEn1ciEFxxAQ.01NxEzNxwSO4kjNzEzW}
```
## What I learned
cut can be used to extract specific colums. -d specifies how columns are separated and -f specifies the field number.


## 6. Sorting data

### There's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end.

**Flag** 'pwn.college{km7pdsexpTgJom7aGtsoVNujKIA.0FM0MDOxwSO4kjNzEzW}'

Since, alphabetically flag comes at the end, sort the file in reverse (Z-A). First flag is the correct flag.

```
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{km7pdsexpTgJom7aGtsoVNujKIA.0FM0MDOxwSO4kjNzEzW}
pwn.college{km7pdsexpTgJom7aGssoVNujKHA.0FM0MDOxwSO4kjNzEzW}
pwn.college{km7pdsexpTgJom6aGtsoUMujKIA.0FM0MDOxwSO4kjNzEzW}
pwn.college{km7pdsexpTgJnl7aGtsoVNujJIA.0FM0MDNxwSO4kjNzEzW}
pwn.college{km7pdsexoTgJom7aGtsoVNujKIA.0FM0MDOxwRO4kjNzEzW}
pwn.college{km7pdsexoTgJom7aGtsoVNuiKIA.0FM0MDOxwSO4kjNzEzW}
pwn.college{km7pdsexoTgJom7aGtrnVNujKIA.0EM0MCOwvSN4kiNzEyW}
pwn.college{km7pdsdxpTgJom7aGtsoVNujKIA.0FM0MCOxwSO4kjNzEzW}
pwn.college{km7pdsdxoTgJom7aGtroVNujKIA.0FM0MDOxwSO4kjNzEzV}
pwn.college{km7pcsdxpTfJom7aFtsoVNujJHA.0FL0MDOxvSN4kjNzDzW}
pwn.college{km6pdsexpTgJom7aGsroVNujKIA.0FL0MDOwwSO4kjNzEzW}
pwn.college{km6pdrexoTgJol7aFtsoUNujKHA.0FL0MDOxwSO3kjMzDzV}
pwn.college{km6pcsexpTgJom6aFtsoVNujKIA.0FM0MCOxwSO4kjMzEzV}
pwn.college{kl6pdsexoTgJom6aGsroUNujKIA.0EM0MDOxvRN3kiNyEzW}
pwn.college{jm7pdsexpTgJom7aGssoVNujKIA.0FM0MDOwvSO4kiNzEzW}
pwn.collegd{km7pdsexpTgJom6aGtsnVMtjKIA.0FM0MCOxwRO4kjNzEyV}
pwn.collegd{jm7odsexpTgJom7aFtsnUNujJIA.0FM0MDOxwSO4kjNzEzW}
pwn.collegd{jm6pdrdxpTgJom7aGtsoUNujKIA.0FM0MDOxwSO4jjNyEzV}
pwn.collegd{jl7pdsexpTgJom7aFtsoUNujKIA.0EM0MDNxwSO4kiNzEzV}
pwn.collefe{km7pdsexpTgJom7aGtsoVNtjKIA.0FM0MDNxwSO4kjNzEzW}
pwn.collefe{km6ocsdxoSgJol7aGtsnVNujKIA.0FM0MCOxvSO3jjNzEyW}
pwn.collefd{kl7odsexpTfJom7aFsroVNujKHA.0EL0LDOwvSO4jjMzEzV}
pwn.colldgd{km7pdsdxoTgJol7aGtsoVNuiKIA.0FM0LDOxwSO4kiNyEzW}
pwn.colldfd{km7pdsdwoTgJnl7aFssoUMuiKHA.0EM0MDOxwSN4kjNzEyW}
pwn.colkege{km6pdsdwpTgJnm7aGtsnVMujJIA.0FL0LDOxwSO4kjNyEzV}
pwn.colkefd{jl7pdrexoSgJol7aGtroVNtjKIA.0FM0MDOxwRO4kiNzEzW}
pwn.coklege{km7pdsexpTfJom7aGssoVNujKHA.0FM0MDOxwSO4jiMzEzW}
pwn.coklege{kl7pdsexpTgJom7aGtsoVNujKHA.0FM0MDOxwSN4kjNzDzW}
pwn.coklege{kl7pdsexpTgJom7aGssoVNujJIA.0FM0LDNxwSO4kjMzEzW}
pwn.coklege{kl7pdrexpTgJnm7aGtsoVMujJIA.0FM0LDOxwSO4jjMzDzV}
pwn.coklegd{km7odrdxpTgJnm6aFtsoVNujKIA.0FM0MDNxwSO4kjNzDzW}
pwn.cokkegd{kl6odsexoTgIom7aGssoUNtiKIA.0EL0MDOwvSO3kjNzEyW}
pwn.cnllege{km7pdsdwoTfJnm6aGtsoVNujKIA.0EM0MDNxwSO4kiNzEzW}
pwn.cnllefe{km7pdsexpTfJom7aGtsnVNujKIA.0FM0MDOxwSO4kjNzEzW}
pwn.cnlkege{jm7pdsexpTgIol6aGtsoVMujKIA.0FM0MDOwwSO4kjMzDzW}
pwn.cnklege{km6pdsexpTgJom7aGtsnVNujKIA.0FM0MCOwwSO4jjNzEzW}
pwn.cnkldgd{jm7pdrexoSgIol7aGssnVNujJIA.0FM0MDOwwRN3jjMyEyW}
pwn.bollege{km6pdsewpSfJom7aGtsoVNuiJIA.0EM0LDNxwSO4jjMyEyW}
pwn.bollegd{km6pdsexpTgJom6aGtsnVNtjKIA.0FM0MDOxwSO4kiNzEyW}
pwn.bollegd{km6pdsewpTgJom7aFtsoUNtjJIA.0EM0MDOxwSO4jjNzEzW}
pwn.bolldgd{kl7odsewpTgJom7aGtrnVMujKIA.0FM0LDOwvSO3kjNzDzW}
pwn.bolkdge{km6pdsexpTfJnm6aGssoVMujKIA.0FM0LDOxvRN4kjNzEyW}
pwn.bokldgd{jm7pcsdwpTfJom7aFtsnUNujKIA.0EL0MDNxvSN4kiNzDzV}
pwn.bnllegd{km7pdrexpTgJol7aFtsnUNujKIA.0FM0MDOxwSO4kiNzEzW}
pwn.bnllegd{jm7pdsexpTgIom7aGtsoVNuiKIA.0FL0MDOxwSO4kjNzEzW}
pwn.bnllefd{km6pdrexpTfIom7aGsrnVMujKIA.0EL0MDOxwRN3kjMzDyV}
pwn.bnlldgd{km7pdsdxpTfJol6aFtsoUNuiKIA.0FL0MDOwwSO3jiMzEzW}
pwn.bnlkefd{jl7pdsewoSgJol6aFtrnVNuiKIA.0FM0LDOxwSO4jjMzDyW}
pwn.bnkkdge{km7pdsexpTfIol7aGtsoVNuiJHA.0FM0LDOxvSO4jjMzDzV}
pwm.college{km7pdsexpTgJom7aGtsoVMujKIA.0FM0MDOxwSO4kiNzDzW}
pwm.college{km7pdsewpTfJom7aGtroVNujKIA.0FM0MDOxwRO4kjNzEzW}
pwm.college{kl7pdsexpTgJom7aGssoVNtjJIA.0FM0MDOxwSO4kjNzEzW}
pwm.collegd{km6pdsewoSgJom7aFtsoUNuiKIA.0EM0MCOxwSO4kjNzDzW}
pwm.colkege{jl6pcrdxpTgIol7aFssoUMuiKIA.0FL0LCNxvSO3kjNzEzV}
pwm.bollege{km7pdsdxpSfJom6aGtsoVNujKIA.0FM0LDNwwSN4jjMzEyV}
pwm.bollege{jl7pdsewpSgIol7aGtsoUNuiKIA.0EL0MDOxwSO4kjNzDzW}
pwm.bollefe{kl7odsewoSgJom7aGssoUNujKIA.0FM0LDNxvRO3kjNzEzW}
pwm.bolkefe{kl7pcrexpSfJom7aGsrnVMtjKIA.0FM0MCOwwSO4kiNzEzW}
pwm.bnlkdge{km7pcsexpSgJnl7aGtroVNujKIA.0EM0MDOxwSO4kjMyEzW}
pvn.college{km7pdsexpTgJom7aGtsoVNujKIA.0FM0MDOxwSO4kjNzEzW}
pvn.college{km7odsexpSfIol7aFssnVMtiJHA.0EM0MCOwwSO3jjMzEzW}
pvn.colldgd{km6pdsdxpTgJom7aFtroUMuiJIA.0EL0LCOxwSN4kjNzDzV}
pvn.colldgd{jl7pdsexpSfIom7aFtsoVNtjKHA.0FL0MDNwvSO4kiNzEzW}
pvn.colldfe{jm7pcrexpTfIol6aFtsoVNuiKIA.0EM0MCOxwRO3jiNzEzV}
pvn.colkegd{jm7odsdxoSgJom7aGssoVNtiJHA.0EL0MDOwwSO3kiMyDzW}
pvn.cnllege{km7pdsexpTgJom7aFtsoVNujKIA.0FM0MDOxwSO4kjNzEzW}
pvn.cnllege{km7pcrdxpTfJom7aGtsnUMtiJIA.0EM0LDNxwRO3kiMzDyW}
pvn.bollege{km6pcrdwpTgJom7aGtsoVNujJHA.0EM0MDOxvSO4kiNzEzV}
pvn.bollegd{km7pdrexoTgIom7aGsroVNtiKIA.0EM0MCOwvRN4kiNzEyW}
pvm.cokkege{km7pdsewpTgJnm7aGtroVNujKIA.0FM0LDOxwRO4kjNyDzW}
pvm.boklege{jl6pdsexpTgJol7aGtsoUMujJIA.0FL0MDNwwSO4kjNzDzW}
pvm.bnlldge{kl6ocsdwpTfJom7aGssoVMtjJHA.0FL0LDOxwSO4jjMzEzV}
pvm.bnlkege{km7odsdxoTfJnl7aFtsnUNujJIA.0FL0MDNxwRO3kiNyEzW}
own.college{km7pdrexoSfJom7aGtsoVNuiJIA.0FM0MDOxwSO3kjNzEzW}
own.collefe{km7pdsdwoTfJnm7aFtsnUNtjJIA.0FM0LCOxwSN4kiNzEzW}
own.colldfe{kl7pdrdwpSgIol7aGtroVNuiJIA.0FL0MDNwwSO4jjNyEyV}
own.colkdge{kl7odsdxpTgJol7aGssoVNtjKHA.0EL0MDOxvRO3jiMzEzW}
own.coklege{km7pdsexpTgJom7aGssoUNujKIA.0FM0MDOxwRO4jjNzEzW}
own.cokkdge{km7pcrexpTfJol7aGtroVMujKIA.0FM0MCOxvSO4jjMzEzW}
own.cokkdge{km6pdrexpTfJom7aGtsnVNuiKIA.0FM0MDOxwSO4kjNzEzV}
own.cnllege{km7pdrewpTgJom6aGtsoUNujKIA.0FM0LDOxvRN3kjNzDzV}
own.cnllefd{km7pdsdwpSfJnl6aGssnUNuiKIA.0EM0MDNxwSO4kiNzEyW}
own.cnlkege{km7pdsexpSgIom7aFtsoUNtjKHA.0FM0MCNwwSO4kjNzEzW}
own.cnkldfd{jm7pcsexoTgJom7aGtsoVNuiKIA.0EL0MDOxwSO4kiNzDzW}
own.boklege{km7pdsewpTfIom7aGtsoVNujKIA.0FM0MCNxvSO4kjMzEyV}
own.boklefe{km6pdrexpTgJnl6aGsroVMtjKHA.0EM0LCOwwRN4kjNzEzW}
own.bokkege{km6ocsdxpSgJnm7aFssoVMtjJIA.0FM0MCNxwSN3kjNzDzW}
own.bnllege{km7ocsexpTgJol7aGtsoVMujKIA.0FL0MDNwvSO4jjNzDzW}
own.bnllege{kl7pdsewoTgIom7aGtsoVMtjKIA.0FM0LDOxwSN4jjNzDzW}
owm.colkege{km7pdrexpTgInm7aFtroVNujKIA.0EM0MCOxwSO3kjNyEzW}
owm.cokkefe{jm7pdsewoSgJom7aGtsoUNtiKHA.0FL0LCNxwSN3kjNyEzV}
owm.bollegd{kl6pdsdxoTgJom6aFtrnVNujKIA.0FL0MDOwvSO4jjNyEzV}
owm.bolkege{km7odrexoTgJom7aFsroVNujJIA.0EM0MCOxwRN4kjNzEzW}
ovn.colkdgd{km7pdrexpTgIom7aGtsoVMujKIA.0FM0LCOwwSN4jjNzEzW}
ovn.cokkegd{jm7pdsexpSfJol7aFssnVNtjJIA.0EM0LDOxwSO3jjNzDyW}
ovn.bollege{jm6pdrdxoTgIom7aFtroUNujKIA.0EL0MDOxwRN4kjNyDzV}
ovn.bolkdge{jm6ocsexpTfIom7aGtrnVNtjJIA.0EM0MDOxvSO4jiNzDzW}
ovm.colkegd{km7odrexpTgJom7aGtsoVNuiKIA.0EM0LDOwvSN4jiNzEyV}
ovm.cnkkege{jm7pcsexpTgJnm7aGssoVNujJHA.0EL0MDNxwSN4kiNzEyW}
ovm.bolkege{km7pdsewpSgIol6aFtrnUNujJIA.0EM0MCOwwSO4kjMzEyW}
ovm.bnlldge{kl7ocsdxoTgJom7aGssoUNuiKHA.0FM0MCOwwRN3jjNzEzW}
```
## What I learned
sort -r sorts in reverse alphabetical order
-n does numeric sort
-u sorts unique lines only
-R gives random order