# OverTheWire-Bandit
This repository contains a walkthrough guide to completing the Bandit levels in the OverTheWire wargames.

This repository serves as:
1) Documentation of my methods and thought process as I solve the Bandit level challenges from OverTheWire wargames.
2) Revision guide based on the key takeaways from solving each challenge.

Each level of the walkthrough guide summarises the:
1) Level Goal (taken verbatim from #insert link to OverTheWire page#)
2) Key Takeaways
3) Alternatives (if any)
4) Common misconceptions (if any)

**Tip**: For those using the Windows Command Prompt to ssh into each level's server, you can right-click on the cmd after copying the password unlocked from the previous level. The right-click pastes the password which was copied. Using the normal shortcut keys to paste (CTRL+V or SHIFT+INSERT) did not work for me.

# Walkthrough Guide
**Bandit Level 0 → Level 1**  
**Key Takeaways**: learn how to log into a server using SSH from a command-line terminal.  
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.  
* File: readme
* Password for Level 1: boJ9jbbUNNfktd78OOpsqOltutMc3MY1

**Bandit Level 1 → Level 2**   
**Key Takeaways**: learn how to read files with special characters, which is "-" in this case.  
The password for the next level is stored in a file called - located in the home directory.  
* File: -
* Password for Level 2: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

**Bandit Level 2 → Level 3**  
**Key Takeaways**: learn how to read files with spaces in its file name.  
The password for the next level is stored in a file called spaces in this filename located in the home directory.  
* Command: cat spaces\ in\ this\ filename
* Alternatives: cat "spaces in this filename"
* File: spaces in this filename
* Password for Level 3: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

**Bandit Level 3 → Level 4**  
**Key Takeaways**: learn how to see all files in a directory, by using the -a (--all) argument to the ls command.  
The password for the next level is stored in a hidden file in the inhere directory.  
* File: .hidden
* Password for Level 4: pIwrPrtPN36QITSp3EQaw936yaFoFgAB

**Bandit Level 4 → Level 5**  
**Key Takeaways**: learn how to discover the type of a file, by using the file command.  
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  
* Command: file ./-file*
* Note: human-readable file means a file with only ASCII text in this context.
* File: -file07
* Password for Level 5: koReBOKuIDDepwhWk7jZC0RTdopnAYKh

**Bandit Level 5 → Level 6**  
**Key Takeaways**: learn how to find a targeted file given a set of properties, by using the find command.  
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
human-readable  
1033 bytes in size  
not executable  
* Command: find -type f -readable ! -executable -size 1033c
* Alternative: find -size 1033c (go straight for the most distinguishing property out of all the ones listed; this works in this context only because there was only 1 file which was 1033 bytes in size)
* Note: suffix 'c' is found after 1033 to specify the units to be bytes. The command will not work if no units were stated.
* Note: optional to include a '.' (dot) after the find command and before specifying the type, to indicate that all directories and files are being searched.
* Additional practice: learn how to find files of size greater than or less than a given size.
* File: maybehere07/.file2
* Password for Level 6: DXjZPULLxYr17uwoI01bNLQbtFemEgo7

**Bandit Level 6 → Level 7**  
**Key Takeaways**: learn how to find a targeted file given a set of properties, by using the find command (similar to previous one, except with a different set of search criteria).  
The password for the next level is stored somewhere on the server and has all of the following properties:
owned by user bandit7  
owned by group bandit6  
33 bytes in size
* Note: Since it is stated that the password is stored somewhere on the server, we must first navigate to the root folder. cd .. twice from the home directory, and then pwd to verify that we are in the root directory. We should only see the slash ('/') character from running pwd.
* Command: find -user bandit7 -group bandit6 -size 33c
* Note: There are a lot of files which match the given property, but all of these files (except one) cannot be accessed, as seen from the string of "Permission denied" messages displayed. Only one search result does not have this message.
* File: ./var/lib/dpkg/info/bandit7.password
* Password for Level 7: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

**Bandit Level 7 → Level 8**  
**Key Takeaways**: learn how to search for a specific word within a file, by using the grep command.  
The password for the next level is stored in the file data.txt next to the word millionth.  
* Command: grep millionth data.txt
* File: data.txt
* Password for Level 8: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

**Bandit Level 8 → Level 9**  
**Key Takeaways**: learn how to search within a file given a set of criteria, by using the sort and uniq commands, in addition to piping within the terminal.  
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.  
* Command: cat data.txt | sort | uniq -u
* Note: -u argument indicates to print only the unique lines.
* File: data.txt
* Password for Level 9: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

**Bandit Level 9 → Level 10**   
**Key Takeaways**: learn how to search for strings within a file that does not contain only ASCII characters, by using the strings and grep command.  
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.  
* Note: Running the file data.txt command tells us that the file is a data file, and does not contain only ASCII text. Hence, it was mentioned that there are only a few human-readable strings.
* Command: strings data.txt | grep ===
* File: data.txt
* Password for Level 10: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

**Bandit Level 10 → Level 11**  
**Key Takeaways**: learn how to decode base64 encoded data, using the base64 command.  
The password for the next level is stored in the file data.txt, which contains base64 encoded data.  
* Command: base64 -d data.txt
* Note: -d argument indicates decoding of data.
* File: data.txt
* Password for Level 11: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

**Bandit Level 11 → Level 12**  
**Key Takeaways**: learn how to transform strings, using the tr command.  
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.  
* Command: cat data.txt | tr A-Za-z N-ZA-Mn-za-m
* Note: Inverted commas or square brackets around the parameters of the tr command are not required.
* File: data.txt
* Password for Level 12: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

**Bandit Level 12 → Level 13**  
**Key Takeaways**: learn how to .  
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!).  
* Step 1: First, make a new directory of your choice under /tmp. Next, copy data.txt to this new directory. There is no need to rename it in my opinion since I felt that I had to remember one more different file name to keep track of where I started.
* Step 2: The file command would state data.txt as a file with ASCII text, but if you view the file contents, it is actually a hex dump. Command to convert the hexdump into binary: xxd -r data.txt > newdata.txt
* Step 3: file newdata.txt shows us that the converted hexdump contains gzip compressed data. Using gunzip to unzip the gzip compressed data gives an error of unknown suffix -- ignored, because the file extension is .txt, which does not match what gunzip is looking for (which is .tar.gz). Hence, rename the file with mv newdata.txt newdata.tar.gz. Then, run gunzip newdata.tar.gz, which gives newdata.tar.
* Step 4: file newdata.tar shows us that the file was compressed with bzip2. However, this file extension does not match what bunzip2 is looking for (which is .bz2). Hence, rename the file with mv newdata.tar newdata.bz2. Then, run bunzip2 newdata.bz2, which gives newdata.
* Step 5: file newdata shows us that the file was compressed with gzip. Rename the file using mv newdata newdata.tar.gz to give the file the appropriate file extension. Run gunzip newdata.tar.gz to get newdata.tar.
* Step 6: file newdata.tar shows us that the file was compressed with POSIX tar. Run tar -xf newdata.tar to get data5.bin. The -x parameter tells tar to extract the files, while the -f parameter tells tar the name and path of the compressed file.
* Step 7: file data5.bin shows us that the file was compressed with POSIX tar. Run tar -xf data5.bin to get data6.bin.
* Step 8: file data6.bin shows us that the file was compressed with bzip2. Rename the file with mv data6.bin data6.bz2. Run bunzip2 data6.bz2 to get data6.
* Step 9: file data6 shows us that the file was compressed with POSIX tar. Run tar -xf data6 to get data8.bin. No need to rename data6 to data6.tar before running the tar command.
* Step 10: file data8.bin shows us that the file was compressed with gzip. Rename the file using mv data8.bin data8.tar.gz. Run gunzip data8.tar.gz to get data8.tar.
* Step 11: file data8.tar shows us that the file contains only ASCII text, which is the password to the next level.
* File: data8.tar
* Password for Level 13: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
