
# INDEX

| Level 00 | Level 01 | Level 02 | Level 03 | Level 04 |
|----------|----------|----------|----------|----------|
| [Level 0](#bandit-level-0) | [Level 1](#bandit-level-1) | [Level 2](#bandit-level-2) | [Level 3](#bandit-level-3) | [Level 4](#bandit-level-4) | 

| Level 05 | Level 06 | Level 07 | Level 08 | Level 09 |
|----------|----------|----------|----------|----------|
| [Level 5](#bandit-level-5) | [Level 6](#bandit-level-6) | [Level 7](#bandit-level-7) | [Level 8](#bandit-level-8) | [Level 9](#bandit-level-9) |

| Level 10 | Level 11 | Level 12 | Level 13 | Level 14 |
|----------|----------|----------|----------|----------|
| [Level 10](#bandit-level-10) | [Level 11](#bandit-level-11) | [Level 12](#bandit-level-12) | [Level 13](#bandit-level-13) | [Level 14](#bandit-level-14) |

| Level 15 | Level 16 | Level 17 | Level 18 | Level 19 |
|----------|----------|----------|----------|----------|
| [Level 15](#bandit-level-15)   | [Level 16](#bandit-level-16) | [Level 17](#bandit-level-17) | [Level 18](#bandit-level-18) | [Level 19](#bandit-level-19) |

| Level 20 | Level 21 | Level 22 | Level 23 | Level 24 |
|----------|----------|----------|----------|----------|
| [Level 20](#bandit-level-20)   | [Level 21](#bandit-level-21) | [Level 22](#bandit-level-22) | [Level 23](#bandit-level-23) | [Level 24](#bandit-level-24) |

| Level 25 | Level 26 | Level 27 | Level 28 | Level 29 |
|----------|----------|----------|----------|----------|
| [Level 25](#bandit-level-25)   | [Level 26](#bandit-level-26) | [Level 27](#bandit-level-27) | [Level 28](#bandit-level-28) | [Level 29](#bandit-level-29) |

| Level 30 | Level 31 | Level 32 | Level 33 | Level 34 |
|----------|----------|----------|----------|----------|
| [Level 30](#bandit-level-30)   | [Level 31](#bandit-level-31) | [Level 32](#bandit-level-32) | [Level 33](#bandit-level-33) | [Level 34](#bandit-level-34) |

 
# Walkthrough Bandit by OverTheWire                   

## Bandit level 0

### **Goals:**
- Log into the game using ssh.
- Find the password for the next level located in a file called _'readme'_ located in the home directory.

### **Commands:**
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```
where:
* _ssh_ is the command to log into a remote server using the Secure Shell protocol.
* _bandit0_ is the username for level 0.
* _bandit.labs.overthewire.org_ is the hostname of the server.
* _-p 2220_ specifies the port number to connect to (2220 in this case).
* _ls_ is the command to list files and directories in the current directory.
* _cat_ is the command to display the contents of a file.

### Password
> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If


## Bandit level 1

### **Goals:**
- Find the password for the next level located in a file called _'-'_ located in the home directory.

### **Commands:**
```bash
cat ./"-"
```


**Watch the file called _'Bandit1.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx


## Bandit level 2

### **Goals:**
- Find the password for the next level located in a file called _'--spaces in this filename--'_ located in the home directory.

### **Commands:**
```bash
cat ./"--spaces in this filename--"
```

**Watch the file called _'Bandit2.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Bandit level 3

### **Goals:**
- Find the password for the next level located in a hidden file located in the _'inhere'_ directory.

### **Commands:**
```bash
bandit 3

ls -alps
cd inhere
ls -la
cat ...Hiding-From-You
```

where:
* _bandit_  is a function in Bash that allows you to switch between different Bandit levels by specifying the level number as an argument.
```bash
bandit() {
  ssh -p 2220 bandit"$1"@bandit.labs.overthewire.org
}

```
* _3_ is the level number you want to switch to.
* _ls -alps_ is a command that combines several options for the _ls_ command:
  * _-a_ lists all files, including hidden files (those starting with a dot).
  * _-l_ provides a detailed listing format, showing file permissions, ownership, size, and modification date.
  * _-p_ appends a slash (/) to directory names to distinguish them from regular files.
  * _-s_ displays the size of each file in blocks.
* _cd_ is the command to change the current directory.
* _inhere_ is the name of the directory you want to navigate into.
* _cat ...Hiding-From-You_ is the command to display the contents of the hidden file named _'...Hiding-From-You'_.

**Watch the file called _'Bandit3.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Bandit level 4

### **Goals:**
- Find the password for the next level located in the only human-readable file in the _'inhere'_ directory.

### **Commands:**
```bash
file ./*
```

where:
* _file_ is a command used to determine the type of a file.
* _*_ is a wildcard that represents all files in the current directory.


**Watch the file called _'Bandit4.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Bandit level 5
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

### **Goals:**
- Find the password for the next level located in a file somewhere under the _'inhere'_ directory that is:
  - human-readable
  - 1033 bytes in size
  - not executable.
 

### **Commands:**
```bash
ls -alps
find . -type f -size 1033c ! -executable | xargs cat
```

where:
* _find . -type f -size 1033c ! -executable_ is a command that searches for files with specific criteria:
  * _find ._ starts the search in the current directory (.).
  * _-type f_ specifies that we are looking for files (not directories).    
    * _-size 1033c_ looks for files that are exactly 1033 bytes in size (c stands for bytes).
    * _! -executable_ excludes executable files from the search results.
* _| xargs cat_ takes the output of the previous command (the list of files found) and passes it as arguments to the _cat_ command, which displays the contents of those files.
  * _|_ is the pipe operator, which takes the output of one command and uses it as input for another command.
  * _xargs_ is a command that builds and executes command lines from standard input.


**Watch the file called _'Bandit5.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Bandit level 6

### **Goals:**
- Find the password for the next level located somewhere on the server that is:
  - owned by user bandit7
  - owned by group bandit6
  - 33 bytes in size.

### **Commands:**
```bash
cd ..
cd ~
find / -user bandit7 -group bandit6 -size 33c
find / -user bandit7 -group bandit6 -size 33c | grep password 
cat /var/lib/dpkg/info/bandit7.password
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null | xargs cat
```

where:
* _cd .._ is the command to move up one directory level; if you want to do it the hard way.
And if you get lost, you can always return to your home directory with:
* _cd ~_ is the command to change the current directory to the user's home directory.
* _find / -user bandit7 -group bandit6 -size 33c_ is a command that searches for files with specific criteria:
  * _find /_ starts the search from the root directory (/).
  * _-user bandit7_ specifies that we are looking for files owned by the user bandit7.
  * _-group bandit6_ specifies that we are looking for files owned by the group bandit6.
  * _-size 33c_ looks for files that are exactly 33 bytes in size (c stands for bytes).
* _| grep password_ pipes the output of the previous command to the _grep_ command, which filters the results to only include lines that contain the word "password". 
Sometimes the grep command only highlights the matching part, so you have all the lines in the console.
To fix that, you can use:
* _2>/dev/null_ redirects any error messages (like permission denied) to /dev/null, effectively ignoring them.
  * _2>_ redirects the standard error (file descriptor 2) to the specified location.
  * _/dev/null_ is a special file that discards all data written to it.


**Watch the file called _'Bandit6.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Bandit level 7

### **Goals:**
- Find the password for the next level located in the file _'data.txt'_ next to the word _'millionth'_.

### **Commands:**
```bash
cat data.txt | grep millionth
```

where:
* _grep_ is a command-line utility used to search for specific patterns or strings within files or input.
* _millionth_ is the specific word you are searching for in the file _data.txt


**Watch the file called _'Bandit7.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Bandit level 8

### **Goals:**
- Find the password for the next level located in the file _'data.txt'_ and is the only line of text that occurs only once

### **Commands:**
```bash
sort data.txt  | uniq -u
```

where:
* _sort_ is a command-line utility that arranges the lines of text in a specified order, typically in ascending or alphabetical order.
* _uniq -u_ is a command-line utility that filters out duplicate lines from a sorted input, displaying only the unique lines that occur exactly once.
 * _-u_ option tells uniq to only print unique lines.
If you dont sort the file first, uniq will only remove consecutive duplicate lines, so sorting is necessary to ensure all duplicates are adjacent.


**Watch the file called _'Bandit8.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Bandit level 9

### **Goals:**
- Find the password for the next level located in the file _'data.txt'_ in one of the few human-readable strings, preceded by several ‘=’ characters.

### **Commands:**
```bash
strings data.txt | grep '=='
```

where:
* _strings_ is a command-line utility that extracts printable strings from binary files.


**Watch the file called _'Bandit9.cast'_ to see in real time the recording of the terminal of this level**

### Password 
> FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Bandit level 10

### **Goals:**
- Decode the file _'data.txt'_ which is encoded in base64 to find the password for the next level.

### **Commands:**
```bash
base64 -d data.txt
```

where:
* _base64 -d_ is a command-line utility that decodes data encoded in base64 format.
  * _-d_ option specifies that the operation is to decode the input data.

**Watch the file called _'Bandit10.cast'_ to see in real time the recording of the terminal of this level**

### Password 
The password is
 > dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr


## Bandit level 11

### **Goals:**
-  LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit11.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 12

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit12.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 13

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit13.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 14

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit14.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 15

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit15.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 16

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit16.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 17

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit17.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 18

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit18.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 19

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit19.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 20

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit20.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 21

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit21.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 22

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit22.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 23

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit23.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 24

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit24.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 25

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit25.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 26

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit26.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 27

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit27.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 28

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit28.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 29

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit29.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 30

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit30.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 31

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit31.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 32

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit32.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 33

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit33.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL

## Bandit level 34

### **Goals:**
- LLLL
 

### **Commands:**
```bash
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL
```

where:
* _LLL_ LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


**Watch the file called _'Bandit34.cast'_ to see in real time the recording of the terminal of this level**

### Password 
LLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLLL


