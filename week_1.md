# Lab Report 1

Hello future reader! This is a brief tutorial about logging into a course-specific account on ieng6 for remote access.

## Installing VSCode
If you've taken a CS class at UCSD before, chances are you already have VSCode installed on your computer.
In case you don't, you can download it for free from https://code.visualstudio.com/ by following
the instructions provided on the website. It should be pretty straightforward, and there are versions available
for both Windows and Mac users.

Once you have it installed, you can open a new VSCode window, which should look something like this:
![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/vscode.png?raw=true)

## Remotely Connecting
To remotely connect, you'll need to know your course-specific account and password.
If you don't have that ready, try following these instructions: [TUTORIAL](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit)

If you're on windows, you'll also need to install `git` from https://gitforwindows.org/. Once you've installed, follow
[these instructions](https://stackoverflow.com/questions/42606837/how-do-i-use-bash-on-windows-from-the-visual-studio-code-integrated-terminal/50527994#50527994)
to make `git bash` your default terminal in VSCode.

Once you have finished setting up, open a terminal in VSCode using Ctrl/Cmd + `. For CSE 15L, enter the following command into the terminal:

`$ ssh cs15lwi23zz@ieng6.ucsd.edu`

Replace the "zz" with whatever specific letters your account uses, which can be located via https://sdacs.ucsd.edu/~icc/index.php. Once you enter this,
you'll get a message asking if you wish to continue; enter "yes". If everything goes right, your window should display something like this:

![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/remote_connection.png?raw=true)

## Trying out Commands
You are now successfully connected remotely! Try running different commands. Some commands to get started include:
* `cd`, which changes the current directory to a specified one if the path is found
* `ls`, which lists files located under the current directory
* `pwd`, which prints the full path name of the current directory
* `mkdir`, which creates a new directory
* `cp`, which can copy files or directories

Have fun!
![Image](https://github.com/ryanliulwy/cse15l-lab-reports/blob/main/screenshots/image.png?raw=true)
