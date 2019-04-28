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

# Walkthrough Guide
*Bandit Level 0 → Level 1*
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.  
File: readme  
Password for Level 1: boJ9jbbUNNfktd78OOpsqOltutMc3MY1  
* Key Takeaways: learning how to log into a server using SSH from a command-line terminal.

*Bandit Level 1 → Level 2*  
The password for the next level is stored in a file called - located in the home directory.  
File: -  
Password for Level 2: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9  
* Key Takeaways: learning how to read files with special characters, which is "-" in this case.

Bandit Level 2 → Level 3  
The password for the next level is stored in a file called spaces in this filename located in the home directory.  
* Key Takeaways: learning how to read files with spaces in its file name.
File: spaces in this filename  
Password for Level 3: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK  
* Command: cat spaces\ in\ this\ filename  
* Alternatives: cat "spaces in this filename"

Bandit Level 3 → Level 4  
The password for the next level is stored in a hidden file in the inhere directory.  
File: .hidden  
Password for Level 4: pIwrPrtPN36QITSp3EQaw936yaFoFgAB

Bandit Level 4 → Level 5  
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  
File: -file07  
Password for Level 5: koReBOKuIDDepwhWk7jZC0RTdopnAYKh

Bandit Level 5 → Level 6  
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
* human-readable
* 1033 bytes in size
* not executable  
File: maybehere07/.file2  
Password for Level 6: DXjZPULLxYr17uwoI01bNLQbtFemEgo7

Bandit Level 6 → Level 7  
The password for the next level is stored somewhere on the server and has all of the following properties:
owned by user bandit7
owned by group bandit6
33 bytes in size  
File: ./var/lib/dpkg/info/bandit7.password
Password for Level 7: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

Bandit Level 7 → Level 8  
The password for the next level is stored in the file data.txt next to the word millionth.  
File: data.txt  
Password for Level 8: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

Bandit Level 8 → Level 9  
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.  
File: data.txt  
Password for Level 9: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

Bandit Level 9 → Level 10   
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.  
File: data.txt  
Password for Level 10: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

Bandit Level 10 → Level 11  
The password for the next level is stored in the file data.txt, which contains base64 encoded data.  
File: data.txt  
Password for Level 11: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

Bandit Level 11 → Level 12  
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.  
File: data.txt  
Password for Level 12: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

Bandit Level 12 → Level 13  
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!).  
File: data8.tar  
Password for Level 13: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
