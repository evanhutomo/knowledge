# PYTHON NOTE
----------------------------------------PYCHARM HOTKEYS MAC--------------------------------------------------

alt + fn + F12     = open/closing terminal
cmd + fn + F2      = terminate debug / run
cmd + 5            = close bottom window
ctrl + shift + d   = debug
ctrl + shift + r   = run

----------------------------------------PYCHARM HOTKEYS MAC--------------------------------------------------

## Macbook Pro evanhutomo

__Common Note__
- Ada 2 python v2.7 terinstall di mac, untuk cek pathnya -> type -a python
- /usr/bin/python       -> python bawaan dari mac
  /usr/local/bin/python -> python yang udah terlanjut ak isi sama packages (pip, dll)
-

__The Hitchiker Guide to Python (http://docs.python-guide.org/en/latest/)__
- ketik import this untuk mengeluarkan zen python (get used to learn with python common convention)

HINDARI
- Circular dependency, mksdnya antar module saling bergantung satu sama lain
- Spagheti code -> no proper segmentation, for loop procedure, dll
- Ravioli code  -> membuat snippet code yang sejenis berulangkali
- Terlalu sering menggunakan global state
- menggunakna import *, be specific
  ex :
  *BEST*
  import modu
  [...]
  x = modu.sqrt(4) <- gunanya agar kita tau sqrt tu ada di module 'modu'

HINDARI
- membuat nama module dengan . (dot), dan _ (underscore)
- membuat namespace module terlalu dalam
  ex: impor deep.module.is.suck as damn

*Package*
  Setiap projek yang ada file __init__.py = python package


__________________________________________GIST__________________________________________________

# use shebang on first line of python script, then we can execute that file without typing python anymore
# for an instance ->  #!/usr/local/python
# for checking a path which python that we are using -> which python
# then when we wanna run the script, just type

# before
$ python script.py

# after
$ ./script.py

# python debugging
python -m pdb <python.py>

# use this code below the shebang to set the encoding character in utf-8 as a normal encoding file
# -*- coding: utf-8 -*-

# check which python did we used
type -a python

# open leafpad
leafpad <filename>

# how to change hostname on raspberry pi
sudo nano /etc/hosts
# change the very last of line which is has default value 'raspberrypi' with whatever hostname you wanna put on
sudo nano /etc/hostname
# change with the same hostname you put in the previous step
sudo /etc/init.d/hostname.sh
sudo reboot

dpkg-reconfigure keyboard-configuration   # pick keyboard layout etc
dpkg-reconfigure console-setup  # pick console font size etc
/etc/init.d/console-setup reload  # make changes effective (or reboot)

# open folder (with GUI) in raspberry pi
xdg-open <folder_name>

# switch to earlu terminal console
ctrl + alt + F1 / F2

# how to see list of variable, function on a module
dir()
ex :
  import sys
  print(dir(sys))

# locals() is built-in function which return a dictionary name of a local variable if we called it
def test(args):
    locVar = 1
    locVar2 = 'yiha'

    print locals()

test('this is localvar')

# list comprehension is the way to abbreviating a block of code into one-listed-lined expression
x = 1
blue = [x**2 for x in range(10)]
print(blue)

# prevent motion from running without a camera connected
https://programmaticponderings.wordpress.com/tag/motion/

# [WARN] kernel lacks cgroups or memory controller not avaiable, not starting cgroups...
solve this warn with adding a line of this command before elevator=deadline
cgroup_enable=memory

# how to know version of python package on interactive python
>>> from pkg_resources import require
>>> require('<package_name>')[0].version

# TKINTER PEP 8
# There are 3 built-in layout manager : pack, grid, place
# pack  -> organize widget in horizontal and vertical positioning
# place -> absolute positioning
# grid  -> organize widget in 2-dimensional positioning

# _privateVar     -> python used single prefix underscore to indicate private variables
# __privateMethod -> python used double prefix underscore to indicate private method

# variable -> lowercase, every word separate with underscore
# constant variable -> uppercase, every word separate with underscore
# class -> camelcase
# function -> lowercase, every word separate with underscore
# indentation -> 4 spaces, dont use tabs (set your IDE/text editor when you use tabs it will generate space)
# comparison -> dont compare explicitlye (True / False), but implisitly like -> if var_comp:  or    if not var_comp:

a = [1,2,3]
b = [5,5,5,5]

a.append(b)
>>> [1,2,3,[5,5,5,5]]

a.extend(b)
>>> [1,2,3,5,5,5,5]

list.insert(n, elem)
a.insert(2, 'test')
>>> [1,2,'test',3]

del list[n]
del a[0]
>>> [2,'test',3]

list.sort() -> mengurutkan element di list
list.remove(n) -> hapus element n

var = sorted(list) -> mengurutkan list

a = [1,2,3]
if 3 in a:
  print 'yup, theres 3 in list a'
else:
  print 'nope'

a.index(3)  # looking for element value to a given value and return the position
>>> 2

b = [1,2,3,3,3,3] # counting number of time that value is found
b.count(3)
>>> 4

a = [[0], 1]
# to copy one list to another variable
b = a[:]  # using slicing operator
# or
b = a * 1
# or
b = a + []

import copy
var = copy.deepcopy(list)   # copying list without reference

# convert list to tuple and vice versa
list((tuple))
tuple([list]])

a = set([1,2,3])

bb = frozenset(a) # frozenset tidak dapat diubah nilainya

# String
split()
join()
lstrip()
rstrip()
strip()
#converting string to any kind of variable type
int(), float()

startswith(), endswith()
count()
find()
replace()

isdigit()
isalpha()
islower()
isuppper()

"{0} is a {1}".format('evan', 'programmer')
>>> evan is a programmer

"{name} is a {job}".format(name='evan', job='programmer')

# Dictionaries
a = {1:'one', 2:'two', 3:'three', 4:'four'}
len(a)  # >>> 4

a.keys()    # >>> [1,2,3,4]
a.values()  # >>> ['one', 'two', 'three', 'four']
a.items()   # >>> [(1, 'one'),(2, 'two'),(3, 'three'),(4, 'four')]
del(a.keys[1])  # >>> [(1, 'one'),(3, 'three'),(4, 'four')]

<keys> in <dictionary>
4 in a    # >>> True / False

a.get(2, 'kalo nda ada ini keluar')
# >>> 'two'

bbb = aaa.copy()  # copy dict aaa ke bbb
bbb.update(<dict>)  # udpate value of dictionary

# enumerate for looping
x = [1,3,-4,2,90,-8]
for i, n in enumerate(x): # i adalah index, n adalah value
  if n < 0:
    print "found a neg number on index ", i

zip(x,y) #
# contoh
a = [1,2,3]
b = ['a', 'b', 'c']
d = zip(a,b)
# >>> [(1, 'a'), (2, 'b'), (3, 'c')]

# example of finding *.py file on January
ls -l *.py | grep Jan

# Returning More Than One Value
# make a class first
class Konverter:
  def hitung(self, kelvin):
    celcius = kelvin - 273
    fahrenheit = celcius * 9 / 5 + 32
    return celcius, fahrenheit

from gui2 import Konverter
ins = Konverter() # make ins as an instance variable
a, b, = ins.hitung(340)
a
# >>> 67
b
# >>> 152
__________________________________________GIST________________________________________________
