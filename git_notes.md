# Notes on using git to manage the project

Here are some notes about commands used to generate this project.

This is the project hosted on github at 
https://github.com/zqmuser/AutoVer-cpp.git

## Creating the project with git.

install git from the Linux OS package

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
git push -u origin main

