# Lab Report 4
Below is a step-by-step walkthrough of how I completed the task from Lab 7, detailing the exact keys I pressed and what those keys accomplished. This is written with the assumption that I've previously completed the task successfully, properly reset my environment after completion, and haven't entered any other commands since.

## Step 4: Log into ieng6
![image](https://user-images.githubusercontent.com/110417482/221448000-72da5b67-3d7d-49fe-be32-aeb004b5b602.png)

**Keys pressed:** `<up> <enter>`

Because everything else in this task is completed remotely through the ieng6 account, the last command in the local bash history is ssh'ing into the account. Therefore, a single up arrow is enough to get the `ssh cs15lwi23aqc@ucsd.edu` command. If this is the first time attempting the task during this session and there isn't any history saved locally (my computer does this), then unfortunately I'd just have to type out the entire command manually, or copy paste it from another document. Regardless, since we generated an SSH key already during the lab, I will not need to re-enter my password to log in to the account.

## Step 5: Clone your fork of the repository from your Github account
![image](https://user-images.githubusercontent.com/110417482/221451662-cbd54df0-4a6c-447b-9dc9-dff00ad07a26.png)

**Keys Pressed:** `<ctrl + R> "git cl" <enter>`, `"cd l" <tab> <enter>`

Since I've already completed the task before, the `git clone git@github.com:ryanliulwy/lab7.git` command is in my command history, which will be the case for all of the following commands too. To access it, `<ctrl + R>` will open up a prompt to search for specific commands in my history, returning matches in order of most to least recently entered. 

![image](https://user-images.githubusercontent.com/110417482/221448727-dfaa7e1d-1e43-4b06-bdd6-e3e43f5a45ad.png)

"git cl" is precise enough to return the `git clone` command (anything less will default to one of the git commands that need to be run later in the task), so `<enter>` can be pressed right after to run the command. This creates a new directory named `lab7/`, and since I don't currently have any other file whose name starts with the letter "l" in my home directory, `"cd l" <tab> <enter>` will correctly autofill to `cd lab7/` and move me into the right working directory.


## Step 6: Run the tests, demonstrating that they fail
![image](https://user-images.githubusercontent.com/110417482/221451900-486c432d-019c-4d9c-bf4c-d927cd899764.png)

**Keys Pressed:** `<ctrl + R> "javac" <enter>`, `<ctrl + R> "java " <enter>`

I use `<ctrl + R>` to search for `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` in order to compile the jave files in the directory, typing in "javac" as the argument before hitting `<enter>` because, once again, anything less will return the wrong command. This is followed with `<ctrl + R> "java " <enter>` in order to actually run the tests with `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamples`. Note that there **must** be a space after "java" this time. Without the space, the search will match with the `javac` command we ran just before, since `<ctrl + R>` will try to return the most recent match.

## Step 7: Edit the code file to fix the failing test
![image](https://user-images.githubusercontent.com/110417482/221452169-36dc8bd5-d563-4622-9fa9-d1cb1488dfc4.png)

**Keys Pressed:** `<ctrl + R> "na" <enter>`, `<down>` 42x, `<right>` 11x, `<delete> "2" <ctrl + O> <enter> <ctrl + X>`

The first sequence will find `nano ListExamples.java` from my command history and run it. This opens up the nano interface to fix the bug at line 42, where `index1` is incremented instead of `index2` and as a result may cause an infinite loop to happen.

![image](https://user-images.githubusercontent.com/110417482/221450923-7dc529f0-ef3f-48c6-861a-e69118ec0973.png)

I don't know how to use `^W` well enough to navigate to the specific instance of `index1` I want to edit, or if that's even possible, so I kinda brute forced this segment and used down and right arrows to get to where I needed to be by hand. Once the `1` is changed to `2`, `<ctrl + O> <enter>` will save the changes made to `ListExamples.java` and `<ctrl + X>` will exit nano.

## Step 8: Run the tests, demonstrating that they now succeed
![image](https://user-images.githubusercontent.com/110417482/221452282-6ce54cf5-7d4d-4a01-abfe-2f4c171b86cb.png)

**Keys Pressed:** `<up> <up> <up> <enter>`, `<up> <up> <up> <enter>`

Since we very recently ran the same commands, pressing up 3 times will access `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` to recompile the fixed code, and pressing up 3 times after running that will access `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` once more to run the tests on the fixed code.

## Step 9: Commit and push the resulting change to your Github account (you can pick any commit message!)

**Keys Pressed:** `<ctrl + R>`
