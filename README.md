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
**Key Takeaways**: learn how to convert hexdump files and extract compressed files, using the xxd and various (de)compression utility commands respectively.  
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

**Bandit Level 13 → Level 14**  
**Key Takeaways**: learn how to log in to a server using a SSH (RSA) private key, using the ssh command.  
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.  
* Command: ssh -i sshkey.private bandit14@localhost
* Note: -i parameter of ssh is referring to an identity file, from which the identity key (private key) for authentication is read.
* Note: If I am not wrong, finding the IP address of localhost would require the execution of ifconfig, which is not found on the server. Thus, in place of knowing and using the localhost IP address, we can simply use the hostname itself.
* File: sshkey.private
* Password for Level 14: unknown at this point in time (use command to log into Level 14's server)

**Bandit Level 14 → Level 15**  
**Key Takeaways**: learn how to send data to another host, using the telnet command.  
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.  
* Command: telnet localhost 30000, 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
* Note: As mentioned in the previous level, the password for this level is stored in /etc/bandit_pass/bandit14.
* Password for Level 14: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
* Note: Telnet connection will be closed by host after 1 try of the password.
* Password for Level 15: BfMYroe26WYalil77FoDi9qh59eK5xNr

**Bandit Level 15 → Level 16**  
**Key Takeaways**: learn how to send data to another host using SSL encryption, using the openssl and s_client commands.  
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.  
Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…
* Command: openssl s_client -connect localhost:30001, BfMYroe26WYalil77FoDi9qh59eK5xNr
* Note: **Not sure what the helpful note given is referring to**.
* Note: Sending the password of the current level using the telnet command results in the connecting host closing its connection immediately.
* Password for Level 16: cluFn7wTiGryunymYOu4RcffSxQluehd

**Bandit Level 16 → Level 17**  
**Key Takeaways**: learn how to identify listening ports within a server, using the nmap, openssl and s_client command.  
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.  
* Command 1: nmap -A -p 31000-32000 localhost
* Note: -A parameter to nmap enables OS and version detection, script scanning, and traceroute.
* Note/Alternative: Executing nmap -p 31000-32000 localhost alone will show that only 1 TCP port, numbered 31790 is open and running unknown service. Run the same command with the -A parameter to confirm that the port speaks SSL. **Need to specify scan type used? e.g. -ST for TCP connect scan**
* Command 2: openssl s_client -connect localhost:31790, cluFn7wTiGryunymYOu4RcffSxQluehd
* Note: SSH (RSA) private key for next level is given from the SSL connection. Copy and paste the key into a file created in /tmp directory.
* Command 3: chmod 400 <SSH key filename>
* Note: Command 3 sets the permissions of the key file to be readable only by the owner of the file (which is bandit16). Without changing the permissions of the SSH key file will result in the private key being ignored, because the server deems that the permissions for the file are too open, and requires that the file is not accessible to others.
* Command 4: ssh -i <SSH key filename> bandit17@localhost
* Password for Level 17: unknown at this point in time (use command to log into Level 17's server)

**Bandit Level 17 → Level 18**  
**Key Takeaways**: learn how to compare the contents of 2 files, using the diff command.  
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.  
NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19.
* Command: diff passwords.old passwords.new
* Note: The output of the diff command is dependent on the order of the parameters supplied to the command. If passwords.new is the second parameter, the second string that is printed in the output is the password for the next level.
* Password for Level 17: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn (execute more /etc/bandit_pass/bandit17)
* Password for Level 18: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

**Bandit Level 18 → Level 19**  
**Key Takeaways**: learn how to log in to a server via SSH without running .bash files (e.g. .bashrc and .bash_logout), using the ssh command with a set of parameters.  
The password for the next level is stored in a file readme in the home directory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
* Command to log in to this level: ssh bandit18@bandit.labs.overthewire.org -p 2220 -t /bin/sh
* Note: -t parameter in the command forces pseudo-terminal allocation. /bin/sh is another kind of Unix shell. Thus, this command runs /bin/sh (*not entirely sure if .bash files are executed, and then /bin/sh is executed, or the case where the .bash files are never executed, or some other case*), preventing us from being logged out immediately upon a successful login.
* Note: Upon successful login, we observe that each line begins with only a '$' symbol without any prefix such as the green-coloured "bandit18@bandit: $" which we would expect. The wall of welcome text by OverTheWire is also missing. These differences are due to .bash files not running because of the customised ssh command with the stated parameters.
* Note: In this case, the last 2 lines in .bashrc are responsible for logging the user out immediately upon successful login.
* Password for Level 19: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

**Bandit Level 19 → Level 20**  
**Key Takeaways**: learn how to take on the role of another user, using a setuid binary.  
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
* Command: ./bandit20-do cat /etc/bandit_pass/bandit20
* Note: Executing file bandit20-do shows us that the file is a setuid ELF 32-bit LSB executable. Running the command allows us to take on the role of user bandit20 temporarily, because of the setuid (set user ID) executable.
* Password for Level 20: GbKksEFF4yrVs6il55v6gwY5aVje5f0j

**Bandit Level 20 → Level 21**  
**Key Takeaways**: learn how to open a listening port and communicate using it, using the nc command.  
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).  
NOTE: Try connecting to your own network daemon to see if it works as you think.
* Command: nc -z -v localhost 1-50000 (to find out what are the ports that are currently open)
* From the command, 7 ports are shown to be open. They are port number 22, 113, 30000, 30001, 30002, 30003 and 31790.
* Command (on terminal A): nc -l -p 1234, GbKksEFF4yrVs6il55v6gwY5aVje5f0j 
* Note: -l flag means listen mode.
* Note: Any other port number besides 1234 can be used, so long as the number is not an existing port which was already shown to be open (i.e. not one of the 7 listed ones above).
* Optional command (on terminal B): nc -z -v localhost 1234 (to test that the port 1234 had indeed been opened and is listening; However, if this command is used, then the listening side will end the connection after that and the command on terminal A has to be executed again)
* Command (on terminal B): ./suconnect 1234
* The password for Level 21 will then be printed on terminal B.
* I was initially confused by the level goal's description of "It then reads a line of text", thinking that reading a line of text is from the user input into the suconnect application.
* **How this entire level actually works**: open a listening port of our choice and send level 20's password to the suconnect, who will verify that the current level's password is correct, before the setuid bit kicks in and permissions are temporarily elevated to user bandit21 to obtain the next level's password.
* Note: Port scanning done using nc done at different points in time resulted in additional ports being shown to be open. These ports' are normally in the 35000 to 40000+ range, and appear to be open only momentarily for some reason(?).
* Note: -z means that the zero-I/O mode is used, i.e. nc only does scanning. -v means verbose.
* Note: Running the same command without the -v flag returns us no results at all.
* Note: Running the same command without specifying a range of ports results in a result stating that there are no ports to connect to. I think that only some common ports are scanned if no specific range is specified by the user.
* Note: The man page states that the use of the -v flag twice means more verbose. This actually means that the result of each individual port's scan is printed. Having only one -v flag results in only open port results being printed.
* Password for Level 21: gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

**Bandit Level 21 → Level 22**  
**Key Takeaways**: learn how to read shell scripts that form part of a cron job.  
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
* First, navigate to /etc/cron.d as mentioned, and we can see that there are 3 cronjobs for the next 3 levels respectively. These are ASCII text files.
* Open cronjob_bandit22 since it is the next level that we are tackling. We find that there is a shell script within /usr/bin that redirects its output to /dev/null, a null device that discards the information written to it.
* Open cronjob_bandit22.sh in /usr/bin and we find that the password to the next level has been also placed into a file t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv at /tmp, in addition to the usual location at /etc/bandit_pass where all the passwords are found.
* Password for Level 22: Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

**Bandit Level 22 → Level 23**  
**Key Takeaways**: learn how to read shell scripts that form part of a cron job.  
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  
NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
* This level is very similar to the previous level, except that the shell scripts are slightly less easy than the one found in the previous level.
* First, navigate to /etc/cron.d as mentioned and open cronjob_bandit23.
* Next, open cronjob_bandit23.sh in /usr/bin. From the shell script, we observe that the destination of the copying of password file is /tmp/$mytarget, where $mytarget is a variable.
* We know that the folder that holds the copy of the password file is fixed as /tmp, but the file name is the MD5 sum of the string "I am user bandit22", minus the space and dash characters at the end (not actually sure how the dash character came about during the hashing). This MD5 sum is 8169b67bd894ddbb4412f91573b38db3.
* Password for Level 23: jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
