# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

* show current working directory path = pwd = it prints the path of the working directory you're on  
* creating a directory = mkdir [directory name]: It takes in a directory name as an argument, and then creates a new directory in the current working directory  
* deleting a directory = rm -r [directory name]: Delets a directory and all of its children directories  
* creating a file using `touch` command = touch [file name]: takes in a filename as an argument, and then creates an empty file in the current working directory  
* deleting a file = rm [file name]: deletes the file from the filesystem  
* renaming a file = mv [file name1] [file name2]: renames a file; we rename the first file with the name we listed in the second file  
* listing hidden files = ls -a: command lists all files and directories in the working directory, including hidden files and directories  
* copying a file from one directory to another = mv [file name] [directory name]: moves the file into the directory  
* how to go back one path step = cd.. : moves back on step on your path  
* how to go one further on the path = cd [file/directory name] : allows you to enter more files and or directories  

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

`ls`: lists all files and directories in the working directory.  
`ls -a` : The -a modifies the behavior of the ls command to also list the files and directories starting with a dot (.). Files started with a dot are hidden, and don't appear when using ls alone.  
`ls -l` : lists files and directories as a table with descriptions about each file/directory.  
`ls -lh`: list long format with readable file size  
`ls -lah`: list long format including hidden files & readable file size  
`ls -t` : sorts entries by time. By default, this option sorts the output by the modification times of files.  
`ls -Glp`: provides a detailed chart of each section of my Benjamin profile on my laptop  

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

ls -c: Displays files by file timestamp.  
ls -d: Displays only dictionaries  
ls -r: displays files in reverse order  
ls -R: Displays subdirectories as well.  
ls -1: Displays each entry on a line  

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > REPLACE THIS TEXT WITH YOUR RESPONSE

 

