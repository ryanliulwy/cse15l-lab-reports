# Lab Report 5
Below is a description of a bash script I wrote to auto-complete the task from lab 7 very quickly. The bash script is run with the assumption that everything has been set up cleanly (i.e. the lab has been forked, any existing directories from previous attempts have been deleted, etc.) and that I've already ssh'd into the ieng6 account. Unfortunately, running a bash script from my local machine that tries to ssh first and then run the task commands won't work, since what ends up happening is it successfully logs in to the ieng6 account, then does none of the remaining commands until after I exit the remote server.

## Bash Script:
![image](https://user-images.githubusercontent.com/110417482/224873793-50aca5e2-847b-49fe-92e2-fd87282c8628.png)

I decided to name the file `CLDQ.sh`. Everything here is pretty straightforward, minus the command used to complete step 7 that I learned from my lab partner Jeremy during the class "competition". I'll be talking about that more in-depth, but aside from that, every other step just has the bash script execute the relevant lines which I copy and pasted from week 7. Running the bash script itself is a simple as typing `bash CLDQ.sh` and hitting enter:

![image](https://user-images.githubusercontent.com/110417482/224873957-6d3cf34c-d22d-4977-a130-21793947cf28.png)

And we are able to see the entire task be completed all in one go by the script:

![image](https://user-images.githubusercontent.com/110417482/224874095-e4988654-6641-46d2-8d5f-351880105a78.png)

## Step 5
![image](https://user-images.githubusercontent.com/110417482/224872009-f3d3ed9a-d85c-44cf-b539-9012983ba55d.png)

The first command clones the forked repository from my GitHub account, and the second command changes the working directory to the newly cloned repository folder so the rest of the commands can properly access the files needed. Interestingly enough, the cd only occurs within the bash script itself, and once the script completes my actual working directory will remain in the home directory.

## Step 6
![image](https://user-images.githubusercontent.com/110417482/224872053-4d951b97-af40-4166-b0c2-31173377920e.png)

`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` compiles the java files in the directory, while `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` will run the tests, which will show that one test fails.

## Step 7
![image](https://user-images.githubusercontent.com/110417482/224873845-859fb6d9-0494-4b2a-8e8f-b9da41479116.png)

This command is the main difference between doing the task by hand with nano and running it on a script that can't exactly use nano in the same way that we can. It still accomplishes the same task of replacing an erroneous "index1" to "index2", and here is a quick breakdown of what exactly the different parts of this command mean:
* sed: A command that stands for stream editor that can perform various functions on files such as text finding, insertion, deletion, and replacement.
![image](https://user-images.githubusercontent.com/110417482/224879019-3002783c-3198-4199-9f28-827237a3a5f0.png)

* -i: An option that saves the command's changes to the original file. Without this option, the command would print out all of the contents in the file including the change, without actually affecting the file itself.
![image](https://user-images.githubusercontent.com/110417482/224879041-02c28a72-e0b0-46d8-b01f-e97a8ef42d86.png)

* 43: specifies the line number to make changes to
* s/index1 += 1/index2 += 1/: Make a substitution. The argument on the left is the string to find and replace, and the argument on the right is the string that should replace it.
* ListExamples.java: The file to make changes to.

Once this command runs, the line of code that causes the bug will be fixed, and we can continue with the task.


## Step 8
![image](https://user-images.githubusercontent.com/110417482/224872161-18e7d68e-7dd5-4985-86b5-9ce700f59081.png)

Same commands as step 6, they will recompile the edited ListExamples file and run the tests on it. This time, since the bug has been fixed, both tests will pass.

## Step 9
![image](https://user-images.githubusercontent.com/110417482/224872145-a3f989d8-499f-4d5a-a3c2-5b915091efce.png)

Pretty standard git commands to wrap up the task. We run `git add` on ListExamples.java first, since that's the file we made edits to. Then we run `git commit` to commit the change with a message "done", but really that message can be anything it needs to be. Finally we push the changes with `git push`, so that the changes will be reflected in the GitHub repository:

![image](https://user-images.githubusercontent.com/110417482/224877826-0bbc793a-238c-4602-9da7-4ff545798f79.png)
