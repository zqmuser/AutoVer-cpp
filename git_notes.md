# Notes on using git to manage the project

Here are some notes about commands used to generate this project.

I usually use mercurial, which is more user friendly than git,
so I'm saving this file to remind me of the git commands.

This is the project hosted on github at 
https://github.com/zqmuser/AutoVer-cpp.git

## Creating the project with git.

Install git from the Linux OS package
Also install gh (github command line interace)

git --version
git init -b main
git add .
git add .AutoVer
git config --global user.email "ME@MINE.com"
git config --global user.name "MY NAME"
git commit -m "initial minimally viable product"

Login to your account on github using the web interface
Create a new project from the github web interface

git branch -M main
git remote add origin https://github.com/zqmuser/AutoVer-cpp.git
gh auth login --web
git push -u origin main

Adding update

AutoVer -y
git checkout main
git add -A
git status -u

Add files to get tracking if needed

git commit -m "doc updates"
git tag -a v1.0.2 -m "Release version 1.0.2"
git push origin v1.0.2
git push origin main


