# AutoVer-cpp

AutoVer-cpp is a utility that will automatically assign
Semantic version numbers to C++ projects. 

Semantic versions look like MAJOR.MINOR.PATCH (i.e. 1.2.4)
Increment MAJOR if changes are not back compatible
Increment MINOR if changes are additions but still back compatible
Increment PATCH if changes are bug fix or performance only 
       ( no change to API, or UI, or internal functions )

Many projects use this version numbering system, but many 
fail to use it correctly. Failing to increment a number when
you should makes it difficult to predict if two builds will
be back compatible. If this can be automated, ideally at 
commit time, that problem could be permanently eliminated.

Although Semantic versioning is designed for software with 
a public API, many developers use it for self-contained software
because it gives both the developers and the users of the
software a sense of how significantly the software changed
from one version to another.

## Strategies for using AutoVer-cpp

There are several options for how to use AutoVer-cpp
* Run "AutoVer -y" just before every commit. 
  This will automatically assign a version for each commit
* Run "AutoVer -y" for important commits, such as when each
  new feature is complete and tested.
* Run "AutoVer -y" to keep versions on every development branch,
  or only run "AutoVery -y" for versioning on the main 
  development tip, say after every update or merge.

## Tutorial

1. Install the prerequisites for AutoVer-cpp listed below.
   A quick check is to run the commands 
```bash
which stripcmt 
which dos2unix
```
   Both of these should list the path to that program.
2. Install AutoVer-cpp following the installation directions below.
3. All AutoVer-cpp commands must be run from the top level
   directory for the project. This is often the directory 
   where the README.md file is located.
4. Initialize your project by typing 
```bash
AutoVerInit
```
   It will give you a (y/n) check to continue. 
   It is easily removed later, if you change your mind.
   If you want to start using AutoVer-cpp type "y"
   It will look for a version control system (VCS) and 
   offer optional VCS support.
5. The initialization will set the version at 0.0.1
   If you want to start a higer version number, type
```bash
AutoVerManual
```
6. In the source code file where you want to print the version add 
```cpp
#include "AutoVer.h"
printf( my_file_ptr, "Version %s\n", AutoVerString.c_str() ); 
```
**WARNING** Do NOT edit AutoVer.h instead use the AutoVer
commands to update the version.
7. The AutoVer.h file defines three integers and a string.
   The easiest option is to print AutoVerString as the
   code version.
8. If you want to check what the current version is,
   or rather was the last time you updated it, run
```bash
AutoVerList
```
9. When you are ready to update the version 
   (see the Strategies above), type
```bash
AutoVer -y
```

If you didn't configure a version control system and
later want to configure it, run
```bash
AutoVerVersionControl
```

**NOTE:** AutoVer-cpp comes with several other programs
that are not listed in this tutorial. Those are ones 
called internally. They should not be run by the user.

## Programs / commands

Follow the prerequisite and installation process below
before using these.

Run these without arguments to see input options

AutoVerInit - initial configuration so AutoVer can 
  track changes to header files for this project.
  Sets the initial version number.

AutoVer - generate the Semantic Version for the
  current header files.

AutoVerList - list the current version of this project,
  as of the last time AutoVer updated it.

AutoVerManual - manually increase version number.

AutoVerVersionControl - configure version control
  system after initial installation.

## Prerequisites for installation

Download and install the stripcmt program from
https://github.com/DimonSE/stripcmt
As of 2025, this was literally unpack and type "make", 
then put it in the PATH, or run "make install" as root.

On an HPC system, you might set that path by making 
an environment module.

Install the following, if not included with your default Linux 
installation. These should be default or optional operating 
system package installs for any major Linux distribution.
* dos2unix
* bash
* sed
* diff
* cat
* wc
* grep

## Installation

Download AutoVer-cpp

Option 1) Download a zip or tar file from github,
          then unpack it.

Option 2) Use git to download it with a command like
```bash
git clone https://github.com/zqmuser/AutoVer-cpp.git 
git clone --branch v1.1.1 https://github.com/zqmuser/AutoVer-cpp
```

Add the directory to your PATH

Option 1) Add something like this to your .bashrc file
```bash
export PATH="/FULL/PATH/TO/AutoVer-cpp:$PATH"
```
Log out and log back in after doing this.

Option 2) Copy the files to a directory such as
```bash
sudo cp AutoVer* /usr/local/bin
sudo rm /usr/local/bin/AutoVer.h
```

Option 3) On an HPC system, you might manage paths
by creating an environment module, such as using LMOD.
Only a PATH is needed.

## Uninstalling AutoVer-cpp

**NOTE** Uninstalling and reinstalling AutoVer-cpp will
restart the version numbering at 0.0.1 
If your intent is to roll version numbering backwards
(not recommended from a consistent numbering standpoint) 
write down the current version number before uninstalling 
AutoVer-cpp. We recommend documenting the roll back.

If you decide you want to completely remove AutoVer-cpp 
from your project, run the appropriate version control
command, from the following list.
``` bash
hg remove AutoVer.h .AutoVer/*
git rm -rf AutoVer.h .AutoVer
rm -r AutoVer.h .AutoVer
```

Remove AutoVer.h from your source code files.

## References

* [Semantic Versioning https://semver.org/](https://semver.org/)
* [Wikipedia Software Versioning https://en.wikipedia.org/wiki/Software_versioning](https://en.wikipedia.org/wiki/Software_versioning)


