# OverTheWire-Bandit
This repository contains a walkthrough guide to completing the Bandit levels in the OverTheWire wargames.

This repository serves as:
1) Documentation of my methods and thought process as I solve the Bandit level challenges from OverTheWire wargames.
2) Revision guide based on the key takeaways from solving each challenge.

Level Goal
Key Takeaways
Alternatives
Misconception

# Walkthrough Guide
Bandit Level 0 → Level 1
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
bandit0 - readme - boJ9jbbUNNfktd78OOpsqOltutMc3MY1

Bandit Level 1 → Level 2
The password for the next level is stored in a file called - located in the home directory.
bandit1 - - - CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

Bandit Level 2 → Level 3
The password for the next level is stored in a file called spaces in this filename located in the home directory.
bandit2 spaces in this filename UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

Bandit Level 3 → Level 4
The password for the next level is stored in a hidden file in the inhere directory.
bandit3 .hidden pIwrPrtPN36QITSp3EQaw936yaFoFgAB

Bandit Level 4 → Level 5
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
bandit4 -file07 koReBOKuIDDepwhWk7jZC0RTdopnAYKh

Bandit Level 5 → Level 6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable
bandit5 maybehere07/.file2 DXjZPULLxYr17uwoI01bNLQbtFemEgo7

Bandit Level 6 → Level 7
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size
bandit6 ./var/lib/dpkg/info/bandit7.password HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

Bandit Level 7 → Level 8
The password for the next level is stored in the file data.txt next to the word millionth.
bandit7 data.txt cvX2JJa4CFALtqS87jk27qwqGhBM9plV

Bandit Level 8 → Level 9
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
bandit8 data.txt UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

Bandit Level 9 → Level 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.
bandit9 data.txt truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

Bandit Level 10 → Level 11
The password for the next level is stored in the file data.txt, which contains base64 encoded data.
bandit10 data.txt IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

Bandit Level 11 → Level 12
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.
bandit11 data.txt 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

Bandit Level 12 → Level 13
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)
bandit12 data8.tar 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL [must try again]
