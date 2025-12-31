# AutoVer-cpp Programmers Guide

## Architecture

This is a series of bash scripts.

Advantages of bash scripts
* It's a very fast protoyping language.
* It requires very few lines of code.
* It is compatible with a very wide range of 
  Linux distributions, both old and new.
* The utility is not dependent upon a certain version
  of C++, python, certain libraries being installed, etc.

Disadvantages of bash scripts
* It will not run as a Windows native utility.
* It will be slower than something implemented in 
  a compiled language.

## Programs / commands used internally

The commands that the user should utilize are listed 
in the README.md file. 

The following are programs used internally, but are not 
intended for end user usage.

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
will always be correct (even if it sometimes says it's not back 
compatible when it is).

Strategies for merging source code repository branches. 
* Increment the larger overall (i.e. merging 1.34.4 with 2.3.56 gives 2.4.0)
* Increment the largest of each number (i.e. merging 1.34.4 with 2.3.56 gives 2.34.56)

There is room for a lot more functionality.

## Compatibility

This version is designed to work on a wide varitety of Linux distributions.

It may work in other Linux-like environments (i.e. Linux-in-Windows products), 
or Unix, but that has not been tested.

## Storage Format

AutoVerInit creates a hidden directory at the top level of
the project directory tree. The directory is named .AutoVer

## Style

Admittedly the first version of this feels like, and is,
prototype code. It was made quickly, not very formally,
and not very rigorous about following style guidelines.
That said, it works well enough to be useful for the 
project I wanted it for, so I may not get around to updating it.

Put in comments.

For bash prototype scripts, I use snake_case or PascalCase 
for variables.
If I were rewriting the project in a compiled language, 
I would use something more formal, such as a subset of
Hungarian Naming.

## TODO

Here is my wish list of things I would like this program
to do in the future. I'm open to other people working on 
these or making derivative works. I may implement a couple of these,
but probably won't implement all of them.

* Rewrite the whole code to swith from the original bash scripts 
to something more performant, such as C++, Go, Rust, or Julia.
This would be the time to start a whole new repository.

* Have tighter integrations with popular version control 
systems. At last check, the most popular were; 
  1. Git - added in version 1.2
  2. Subversion
  3. Mercurial - added in version 1.2
  4. CVS 
  5. Perforce Helix Core 
  6. Plastic SCM 
  7. Fossil
Some ways to integrate better include
  - Have it automatically update the version number 
    immediately prior to each commit. - implemented for git & hg
  - Have the version control system recognize how to 
    automatically merge branches and set the version correctly.

Give source code hosting sites (i.e. github) the capability
to automatically assign correct Semantic versions for commits
or releases, even if the makers of the code didn't.

We might be able to extend the current code to Java or C.
This has not been tested.

Extend AutoVer to apply the same version numbering principles 
to command line arguments.
This might be a simple AI task.
For now, use AutoVerManual

Extend AutoVer to apply the same version numbering 
principles to the input file format.
This might be a simple AI task.
For now, use AutoVerManual

Extend AutoVer to increment the version number when 
the required version of a prerequisite changes.
Maybe analyze configure or CMakeLists.txt
For now, use AutoVerManual

Have repositories like Anaconda and CRAN force users to
follow Semantic version numbering (at a minimum) in order 
to add new libraries into their repositories.
This would make it far easier for utilities like "conda"
to resolve version dependency issues.


