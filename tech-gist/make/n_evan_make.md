# GNU Make
evans make private note

# Writing make files
[tutorial to writing a makefile](https://www.cs.bu.edu/teaching/cpp/writing-makefiles/)

# Todo
- [x] Overview of ```make```
- [x] An Introduction to Makefiles
- [x] Writing Makefiles
- [ ] Writing Rules
- [ ] Writing Recipes in Rules
- [ ] How to use variables
- [ ] Conditional part of Makefiles
- [中] Functions for transforming text
- [ ] How to Run ```make```
- [ ] Using Implicit Rules
- [ ] Using ```make``` to Update Archive files
- [ ] Extending GNU ```make```
- [ ] Integrating GNU ```make```
- [ ] Features of GNU ```make```
- [ ] Incompatibilities and Missing features
- [ ] Makefiles conventions
- [中] Others

### Overview of ```make```
check version of make : ```make --version```

### An Introduction to Makefiles
Basic Makefile
```
target ...: prerequisites ...
      recipe
      ...
      ...
```
**target**, usually name of file that is generated, executable object. Target often depends on **prerequisites**

**prerequisites**, file that is used as input to create the target

**recipe**, action that make carry out.

n.b: dont forget using TAB to make indentation on recipe

```
# Makefile sample

edit : main.o kbd.o command.o display.o \
       insert.o search.o files.o utils.o
        cc -o edit main.o kbd.o command.o display.o \
                   insert.o search.o files.o utils.o

main.o : main.c defs.h
        cc -c main.c
kbd.o : kbd.c defs.h command.h
        cc -c kbd.c
command.o : command.c defs.h command.h
        cc -c command.c
display.o : display.c defs.h buffer.h
        cc -c display.c
insert.o : insert.c defs.h buffer.h
        cc -c insert.c
search.o : search.c defs.h buffer.h
        cc -c search.c
files.o : files.c defs.h buffer.h command.h
        cc -c files.c
utils.o : utils.c defs.h
        cc -c utils.c
clean :
        rm edit main.o kbd.o command.o display.o \
           insert.o search.o files.o utils.o
```

For ```clean``` is not a file, but an action, so ```clean``` did not need prerequisites. ```.PHONY``` is a target that do not refer to files. Example of ```.PHONY``` target

```
# phony target
clean:
      rm * .o temp

# phony target with .PHONY syntax
.PHONY: clean
clean:
      rm * .o temp
```

- By default, Makefile start with first target (not with name start with **.**)  
- We can simplify recipe/prerequisites by using implicit rule. Implicit rule is a rules that make makefile know what we intend to do without explicitly write it.

```
# before using implicit rule
aaa.o: aaa.c aaa.h
  cc -c aaa.c
# after using implicit rule
aaa.o: aaa.h
```

- Because of implicit rules, we can slicing prerequisites depends on what .h files they need to. Simply say, its like diagram venn.

### Writing Makefile
Makefile must know things:
* explicit rules
* implicit rules
* variables definition
* directives
* comments

By default ```make``` command will execute ```GNUmakefile/makefile/Makefile```. If we want to make include file without error if the file did not exist, we cans used ```-include filenames.mk```.
- ```.mk``` is a makefile file extension on Linux environment
- ```.mak``` is a makefile file extension on Windows environment

Make work in two disctinct phases:
  - 1st phase, read all the makefiles, variables, implicit, explicit rules
  - 2nd phase, make use internal structure to determine what targets will need to be rebuilt and invoke

We can make an "empty recipe" on make which do nothing. This done simply by giving a recipe that consist of nothing but whitespace
```
target: ;
```
One reason why we make empty recipe is :
  - to prevent target from getting implicit recipes
  - avoid error for target that will be created as side effect of another recipe

How to read makefiles with user-defined name:
```
-f <makefilename>
```

### Writing Rules
Rule Example
Rule syntax
Prerequisites type
Wildcard
Directory search
Phony target
Force targets
Empty targets
Special targets
Multiple targets
Multiple rules
Static pattern

There are 2 types of prerequisites which understood by GNU make:
  - **normal prerequisites**, make 2 statement
    - impose an order in which recipe will be invoked
    - if any prerequisites is newer than the target, it need to be rebuilt  
  - **order-only prerequisites**, is the condition if we want to impose specific ordering on the rules to be invoke _without_ forcing the target to be updated

Wildcards which being used in makefiles are the same with bash script. If you want to save the wildcard expansion on a variable
```
#rather than doing this which is not worked because it will print as string
objects = *.0

#do this function wildcard
objects := $(wildcard *.o)
```

Searching directories
  - general search
  - selective search
  - search algorithm
  - recipe search
  - implicit search
  - libraries search

Automatic variables
VPATH


### Writing recipes in rules



### Functions for transforming text
* Syntax of functions
  ```syntax
  $(function arguments)
  ```
  - function:
    - built-in      -> subst, patsubst, filter, findstring, etc
    - user-defined, using call <function-name>
  - argument:
    - separate with space from function
    - separate with coma with another args
    - if the arguments itself contain function calls, use this
      ```
      $(subst a,b,$(x))
      ```

* Text functions
  **subst**
  subtituted text
  ex:
  ```subst
    test := $(subst e,E,evan)
    all: ; @echo $(test)

    # $ make makefile
    # $ Evan
  ```
  **patsubst**
  **strip**
  **findstring**
  **filter**
  **filter-out**
  **sort**
  **word**
  **wordlist**
  **words**
  **firstword**
  **lastword**

* File name functions
  **dir**
  **notdir**
  **suffix**
  **basename**
  **addsuffix**
  **addprefix**
  **join**
  **wildcard**
  **realpath**
  **abspath**

* Conditional functions
  **if then-part else-part**

* Foreach functions
  **foreach**

* File functions
  **file**

* Call functions
  **call**

* Value functions
  **value**

* Eval function


* Origin function
  **origin**

* Flavor function
  **flavor**

* Make control function
  **error**
  **warning**
  **info**

* Shell function
  **shell**

* Guile function

### Others
#### Global variable
There are empty variable called $(TOPDIR) that defined empty to make it easy to understand value of the variable (which is path)

TOPDIR :=
BUILD_SYSTEM := $(TOPDIR)build/make/core
PWD := $(shell pwd)
SHELL := /bin/bash
BUILD_COMBOS:= $(BUILD_SYSTEM)/combo
SRC_TARGET_DIR := $(TOPDIR)build/target
SRC_API_DIR := $(TOPDIR)prebuilts/sdk/api

#### Order
* execute envsetup to preparing the functions
  $ source build/envsetup.sh && lunch
* run lunch with args to choose which combo we want to pick
  $ lunch <number>
* start to build
  $ mosesq make droid custom_images -j24 2>&1 | tee build.log
     mtk-git2\Makefile
      └─ mtk-git2\build\make\core\main.mk
          └─ mtk-git2\build\make\core\config.mk
              ├─ mtk-git2\build\make\core\math.mk                # Set up efficient math functions which are used in make.
              ├─ mtk-git2\build\make\core\pathmap.mk             # Various mappings to avoid hard-coding paths all over the place
              ├─ mtk-git2\build\make\core\project_definitions.mk # Allow projects to define their own globally-available variables
              ├─ ... Build system internal files
              |      start on page 113-163
              ├─ ... other make file with condition
              └─ mtk-git2\build\make\core\dumpvar.mk              # place where log status were written
