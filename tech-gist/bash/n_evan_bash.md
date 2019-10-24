# BASH COMMAND

## Shebang
absolute path to the bash interpreter
```shebang
#!/bin/bash
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
$ ls -l *tty*
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

## ifconfig
Show network interface
```ifconfig
$ ifconfig
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

## grep
find text inside a file

## find
find base on file name

## alias
show the custom alias  

## curl
## dmesg
## aux
## pwd

## free
## gdrive
command for [gdrive](https://github.com/gdrive-org/gdrive#downloads)

## adb
Android Debug Bridge (ADB) shell command
```adb
  # install adb on ubuntu >14.04
  $ sudo apt-get install android-tools-adb android-tools-fastboot
```
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

# TEMP NOTE
* go script and python script will be use through building along with makefile with shell file

## bash function
## bash reserved word
  export
  alias
  command
  shift
  source
  dirname
  cp
  trap
  mktemp
  openssl
  cat
  tr
  fold
  head
  echoerr
  finish
  read
  rsync  
  warn
  die
  uname
  expr
  ulimit
  cygpath
  egrep
  set
  unset
  perl
  basename
  mknod
  wait
  readonly
  local
  sed
  tail

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
