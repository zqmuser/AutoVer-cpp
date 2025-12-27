# AutoVer-cpp

## Architecture

This is a series of bash scripts.

## Programs / commands used internally

The commands that the end user should utilize are 
listed in the README.md file. 

The following are programs used internally, but are not 
for end user usage.

AutoVerCompare - compare two normalized header files
  (old and new) then return MAJOR, MINOR, or PATCH

AutoVerNormalize - reformat header file so comments and
  blank spaces aren't seen as API changes.

AutoVerHeader - generate AutoVer.h file

## Limitations

The current version may not correctly handle every possible variation 
of a C++ header file. Hopefully failures should be rare. 
This utility is designed to fail on the side of incrementing version numbers. 
This ensures that using the numbering to predict back compatiblity
will always be correct if the numbers say version are back compatible.

Strategies for merging source code repository branches. 
* increment the larger overall (i.e. merging 1.34.4 with 2.3.56 gives 2.4.0)
* increment the largest of each number (i.e. merging 1.34.4 with 2.3.56 gives 2.34.56)

There is room for a lot more functionality.

## Compatibility

This version is designed to work on a wide varitety of Linux distributions.

It may work in other Linux-like environments (i.e. Linux-in-Windows products), 
or Unix, but that has not been tested.

## Storage Format

AutoVerInit creates a hidden directory at the top level of
the project directory tree. The directory is named .AutoVer

## Style

Put in comments.

For bash prototype scripts, I use snake_case or PascalCase 
for variables.

If I were rewriting the project in a compiled language, 
I would use something more formal, such as a subset of
Hungarian Naming.

## TODO

Here is my with list of things I would like this program
to do in the future. I'm open to other people working on 
these or making derivative works. I may implement a couple of these,
but probably won't implement all of them.

* Rewrite the whole code to swith from the original bash scripts 
to something more performant, such as C++, Go, Rust, or Julia.

* Have tighter integrations with popular version control 
systems. At last check, the most popular were; 
  1. Git 
  2. Subversion
  3. Mercurial 
  4. CVS 
  5. Performce Helix Core 
  6. Plastic SCM 
  7. Fossil
Some ways to integrate better include
  - Have it automatically update the version number 
    immediately prior to each commit.
  - Have the version control system recognize how to 
    automatically merge branches and set the version correctly.

Give source code hosting sites (i.e. github) the capability
to automatically assign correct Semantic versions for commits
or releases, even if the makers of the code didn't.

We might be able to extend the current code to Java or C.

Extend AutoVer to apply the same version numbering 
principles to command line arguments.
For now, use AutoVerManual

Extend AutoVer to apply the same version numbering 
principles to input file format.
For now, use AutoVerManual

Extend AutoVer to increment the version number when 
the required version of a prerequisite changes.
For now, use AutoVerManual

