# [BASH COMMAND](http://man7.org/linux/man-pages/index.html) - BUILT IN
## References
http://www.linuxintro.org/wiki/Shell_scripting_tutorial


## printenv/env
print all part of environment
```printenv
$ printenv
$ env
```

## set
set environment variable
```set
$ set $HOME=~/
```

## unset
unset environment variable
```unset
$ unset $HOME

# or set empty file to erase the value
$ export $HOME=
```

## ufw
program to managing netfilter firewall
```ufw
# show firewall is active or not
$ sudo ufw status verbose
```

## cd
builtin comand to enter the directory
```cd
$ cd directory-name/

# to go back to previous location
$ cd -
```

## break
exit process loop shell command like for, while, until

## continue
continue process shell command like for, while, until

## exec
builtin command which allow us to execute command and replace the previous command

# command
To check program exist from bash script
```command
# exist command will be printed out
$ command -v ls
ls
$ command -v git
/usr/bin/git
```

## Shebang
absolute path to the bash interpreter
```shebang
#!/bin/bash
```

## chsh
Change your shell login
```chsh
# change shell to zsh
$ chsh -s /bin/zsh
```

## lshw
list hardware
```lshw
$ lshw -class memory
```

## dmidecode
DMI table decoder
```dmidecode
$ sudo dmidecode --type memory
```

## file
check file type
```file
# to check file type
$ file <filename>

# to check all file type in current directory
$ file *

# to check all file type with mime
$ file --mime-type *
```

## lsusb
list usb devices
```lsusb
$ lsusb
```

## ls
Listing filename
```ls
# list all filename start with tty
$ ls -l tty*

# list all filename containing with tty
$ ls -l *tty*

# list all filename ending with tty
$ ls -l *tty

# list file per line (1 column)
$ ls -a | cat
```

## ifconfig
Show network interface
```ifconfig
$ ifconfig
```

## top
display linux process
```top
$ top
```

## htop
display linux process with nice GUI
```htop
$ htop
```

## pgrep
look up for signal processes based on name
```pgrep
$ pgrep sh
1905
1961
```

## ps
show running process on linux
```ps
$ ps -aux     # show all of the process
$ sudo ps -a  # show simple runned process

# note if you run ps -aux:
root         1  0.0  0.0 225868  9760 ?        Ss   19:10   0:13 /sbin/init splash
root   => username
1      => PID (Linux process ID)
19:10  => Process start time
/sbin/init splash   => actual process or command
```

## kill
kill a process by signal/PID
```kill
$ kill <pid>
# or
$ kill -signal <pid>
```

# pkill
kill a process by name
```pkill
$ pkill vim
```

## killall
kill all processes by name
```killall
$ killall sh
```

## halt
to shut down OS
```halt
$ halt
```

## du
Show estimate file space usage
```du
# check pointed filename size
$ du -sh <filename>

# check size of all file in current dir
$ du -bsh *

# check size with depth layer
$ du -h --max-depth=1
```

## l
Alias of ls  but differently
```l
# show list file on a column
$ l -C

# show list of symbolic suffix of a files
$ l   

# or
$ l -F

# explanation of suffix that been shown by using l
# /   directory
# *   executable
# @   symbolic link
# The absence of the suffix means normal file that isnt executable
```
## strings
return strings of printable characters in files
```strings
# strings [option] file_names
# return string on min length 20 char
$ strings -n 20 file1.txt
```

## grep, egrep
Global search for regulas expression. Find text inside a file.
Basic regular expression:
```regex-ref
https://regexr.com/
https://www.softwaretestinghelp.com/grep-command-in-unix
```
Example of grep
```grep/
# match 'hello' string in every line in file1.txt
$ grep "^hello" file1.txt

# match 'done' string in end of the line in file1.txt
$ grep "done$" file1.txt

# for the rest, please refer to the reference above
# egrep similar with grep -E  # extended regex

# search string on a subdirectory
$ grep -rl "string-you-looking4" /path
$ grep -Hrn "string" /path
```

## env
Run a program in a modified environment
```env
$ env
```

## find
find base on **file name**
```find
# find and remove files (not dir, not symlink) that created more than 15 days ago
$ find /tmp/ -ctime +15 -type f -exec rm {}\;

# find based on files or folder name
$ find /path/ -iname <file/foldername>

# find based on extension
$ find /path -type f -name "*.extension"

# find on this current path, with included string kernel
find . -type d | grep kernel

# find current path with exclude using -prune flag, and search *.c file exclude on ./build path
$ find . -path ./build -prune -o -name '*.c' -print

# find all extension on current path(using pipe(|) to append output from the previous command and input it to the next command)
$ find . -type f -name '*.*' | sed 's|.*\.||' | sort | uniq -c
```

## alias
show the custom alias  
```alias
# create alias for clear screen
alias c='clear'
```

## pwd
Print Working Directory (PWD), command for print path of the working directory
```pwd
$ pwd
# or
$ echo $PWD
```

## df
Show file system disk space usage
```df
$ df
```

## lsmod
Show the status kernel module
```lsmod
$ lsmod
```

## sort
sort lines of text files

## sed
stream editor for filter/transforming text

## locate
find files by name

## dmesg
print or control the kernel ring buffer

## free
display amount of free and used memory in the system

## dirname
strip last component from file name

## cp
copy files and directories

## mktemp
create a temporary file or directory

## openssl
openSSL command line tool

## cat
Concatenate files and print output
```cat
$ cat ${USERNAME}
```

## tr
translate or delete characters

## fold
wrap each input line to fit in specified

## seq
print a sequence of numbers

# nice
run a program with modified scheduling priority

## renice
alter priority of running processes

## head
output the first part of files

## read
read from a file descriptor

## rsync
fast, versatile, remote file copying tool

## warn
formatted error messages

## uname
print system information

## expr
evaluate expressions

## wc
print newline, word, and byte count for each file

## ulimit
get and user limits

## perl
the perl 5 language interpreter

## basename
strip directory and suffix from filenames

## mknod
make block or character special files

## wait, fork
basic process management

## sed
stream editor for filtering and transforming text

## tail
output the last part of files

## awk
a programming language that design for processing text-based data, either in files or data streams or using a shell pipes

# BASH COMMAND - NOT BUILT IN
## repo
tool for getting android source
[repo installer](curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo)
```repo
# for tracing error log
$ repo --trace sync -l
```

## tree
Recursive directory listing program in depth
```tree
# instalation
$ sudo apt-get install tree

# list with wildcard pattern
$ tree -P

# list all files
$ tree -a
```

## curl
Command line or script to transfer data
```curl
# install curl on ubuntu
$ sudo apt update && sudo apt upgrade
$ sudo apt install curl

# check curl
$ curl --version

# to see header of the website
$ curl -I https://www.google.co.jp/

# to download file from a server
$ curl -o <filename> <url>
```
## gdrive
command for [gdrive](https://github.com/gdrive-org/gdrive#downloads)

## adb
Android Debug Bridge (ADB) shell command
```adb
  # install adb on ubuntu >14.04
  $ sudo apt-get install android-tools-adb android-tools-fastboot
```

## gparted
GNOME partition editor. Software for configure disk partition
```gparted
# install
$ sudo apt-get install gparted
```

## git
git SVN command
```git-basic-command
# to show local branch
  $ git branch

# to delete local branch
  $ git branch -D <branch name>

# to cancel work/commit
  $ git clean -d -f

# to save later work/commit. Stash work as stack
  $ git stash

# see status of changes on repository
  $ git status

# switch branch
  $ git checkout <branch name>

# get list of tags of branch
  $ git fetch --tags
  $ git tag

# discard local changes
  $ git reset --hard

# locally stages update file
  $ git add

# create a local clone of git repository
  $ git clone

# clone specific tag on a repo url, use -depth 1 to avoiding downloading any non-current commits
  $ git clone --branch <tagname> <repourl> -depth 1

# .gitignore
# create .gitignore and fill with list of file that we want to be ignored(not to be pushed)

# .gitconfig
# create this config to set a configuration of your git
$ git config <key>

# fatal: remote origin already exists.
# first check is there any remote origin connected
$ git remote -v
# remove the remote origin
$ git remote rm origin

# kalau ada pull sama push bersamaan, dan kita sudah kadung commit, kita bisa reset posisi kita ke branch (Sourcetree)

???????
# HEAD
# git pull
  $ git pull
# patch
# diff
# cherry picking
# gitk
```

# vim
vi text editor(upgraded version)
```vim
# install

# how to use

# vim script

# cheat sheet
ESC + G             # jump to last line
ESC + gg            # jump to first line
ESC + :q            # quit
ESC + :q!           # force quit
ESC + :wq           # write and quit (save and quit)
i                   # insert/ start to edit
ESC + :set numbers  #
ESC + :set nu       # show line number
ESC + :set nonumbers# hide line number
ESC + :vi +100      # go to line 100
ESC + /yeah         # search word 'yeah'
ESC + u             # undo
ESC + d             # delete
#<text>             # search strings right on the previous cursor
?<text>             # search strings, and click N for search next
ESC + :noh          # remove highlighting



# Copy/paste
1. ESC
2. Put your cursor on the head of the string that you want to copy
3. press V to start blocking the string
4. Move the cursor using h,j,k,l
5. press y to copy
6. press P to paste
```

## googler
google search on terminal
```googler
# requirement
# python >3.5

# install
$ cd /tmp
$ git clone https://github.com/jarun/googler.git
$ cd googler
$ sudo make install
$ cd auto-completion/bash/
$ sudo cp googler-completion.bash /etc/bash_completion.d/

# how to use
$ googler ?   # googler help command
$ googler vim # search 'vim'
```

# TEMP NOTE
* go script and python script will be use through building along with makefile with shell file

aux
export
command
shift
source
trap
echoerr
finish
readonly
local
die
cygpath
set
unset

case ... in ...
  ...
esac

while ... do
...
done

if...then
  ...
else
  ...
fi

for ...
do
  ...
done

# LINUX (distro Ubuntu)
## proc/
Pseudo filesystem which does not exist, instead kernel create it in memory

## proc/meminfo
Used to report the amount of free and used memory

## proc/iomem
Contain the current map of the system memory for each physical device

## How to add all Ubuntu repositories (main, universe, selected, multiverse)
```add-repo
$ sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) main universe restricted multiverse"
```

# Hotkey
ctrl + c  : to interrupt/kill processing
ctrl + a  : to get your cursor on the head of the line
ctrl + e  : to get your cursor on the tail of the line
ctrl + d  : to exit shell
ctrl + l  : same as clear command
ctrl + u  : cut text and adding it to clipboard
ctrl + y  : paste text from clipboard
ctrl + shift up/down : scroll up/down terminal

# Scenario
### Merge 2 filesystem
Requirement
  * gparted
  * filesystem knowledge

Goal
  * learn type of filesystem
  * learn how to move bootloader (what is bootloader is)
  * learn how to resize filesystem

Solution
https://askubuntu.com/questions/101715/resizing-virtual-drive
on filesystem, swap prevent you to merge your sda1 with another disk.
Delete this file so you can merge sda1 with new disk.

# Other
1. The linux OS comprises several different pieces
  * Bootloader
  * Kernel
  * Init system
  * Daemons
  * Graphical server
  * Desktop environment
  * Applications

2. [Chain command in linux](https://www.lostsaloon.com/technology/how-to-chain-commands-in-linux-command-line-with-examples/)
```chain
# chain command for entering the find result
cd "$( dirname "$(find /path )" )"
```

# Errors
1. ```-bash: fork: Cannot allocate memory```.
  If this error happened, just restart your machine
2.
