Bandit game
Level-0
 We will type ssh bandit0@bandit.labs.overthewire.org -p 2220 and enter our password

Level-1

Now we will use following commands
cd ~
ls
cat readme
The password in readme is NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
the ls command lists the files in the current directory 
cat readme displays the contents of the "readme" file. 
Again login using ssh bandit1@bandit.labs.overthewire.org -p 2220

Level-2
after entering to level 1 we will use
cat ./-
We can also use cat file\ name\ with\ spaces
By pressing tab we can automatically arrive to that specific path
this allows us to specifically find the file

Level-3

bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ find
.
./.hidden
bandit3@bandit:~/inhere$ cat ./.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit3@bandit:~/inhere$ #or

bandit3@bandit:~/inhere$ cd ~/
bandit3@bandit:~$ find ./inhere
./inhere
./inhere/.hidden
bandit3@bandit:~$ cat ./inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit3@bandit:~$

Password:-2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

Level-4
to find password in human read only we have to login and then we have to
use ls -l to get size ,file type which is same for eveything here
cd inhere
file ./*
cat <human-readable-file>
in this case file07 is Ascii text

Level-5
We will use following commands
ls
cd inhere
find . -type f -size 1033c ! -executable -exec file {} \; | grep "ASCII text"
result we will get
maybehere00 maybehere02 maybehere04 maybehere06 maybehere08 maybehere10 maybehere12 maybehere14 maybehere16 maybehere18 maybehere01 maybehere03 maybehere05 maybehere07 maybehere09 maybehere11 maybehere13 maybehere15 maybehere17 maybehere19
bandit5@bandit:~/inhere$ find . -readable -executable -size 1033c

bandit5@bandit:~/inhere$ find . -readable ! -executable -size 1033c
./maybehere07/.file2
Password is P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

Level 6
We used 
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null | grep -v "Permission denied"
Many files got result as permisson denied except 1
we get:z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

Level-7
For this we will use 
grep millionth data.txt
Grep keyword helps to find specific word and adjacent also
We get password as:TESKZC0XvTetK0S9xNwm25STk5iWrBvP

Level-9
We can use a combination of sort and uniq to identify the line that occurs only once in the data.txt file:
sort data.txt | uniq -u
it identifies i-1 and i+1 line and if different return it
Password we got EN632PlfYiZbn3PhVK3XOGSlNInNE00t

Level-10
For human readable we will use
strings data.txt | grep "=="
We got password as G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

Level-11
We can use the base64 command to decode the content of the file and then use other 
commands to extract the password
base64 -d data.txt
We get password as 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

Level-12

tr is used for translating and allows 13 characters rotation also
cat data.txt 
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
Password we get JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

Level -13
mkdir /tmp/my_directory
cp data.txt /tmp/my_directory/
cd /tmp/my_directory
mv data.txt data
file data
If the file is compressed, we can use gzip
gzip -d data
cat data
strings data
The password we get wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

Level-14
We need to login at private SSH
ssh -i sshkey.private bandit14@localhost -p 2220
chmod 600 ~/bandit14.key
Password we get is fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

Level-15
bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
The password we get N2kgmIXJ6fShzhT2avhotn4Zcka6tnt
# BANDIT
