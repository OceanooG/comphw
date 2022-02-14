###Github tutorial step by step
Hi, This is a step by step tutorial on how to use git and its commands to submit projects, this tutorial will use a coding example as contex to show you how to set up git and using git to submit your work to github. FYI, this tutorial is based on MAC OS by apple.
####Step 1 - Github Account 
Before we do anything on our Terminal with git commands, you will need a GitHub acount. 
You can vist The [Github](https://github.com/) official website to create an free acount. 
- First, Pick a username 
- Secondly, Enter your email address 
- Lastly, Chose a password and sign up for Github. 
####Step 2 - Install Git
Now that you have a Github account, we can start setting up git on your computer. Most versions of Mac OS will have `Git` installed and you can activate it through the terminal widown with `git version`.
If you don't have git installed you can also install `Git` using home brew. 
    - Open the terminal app and install `git` with: `brew install git`
    - After installation complete, you can use `git version` again to varify the installation.
#### Step 3 - Identity Set up 
After installing `Git`, the first thing we want to do is to tell `git` your identity.  The following command will save your information and use it every time you commits something to github. 
```
$ git config --global user.name "may"
$ git config --global user.email maymom@example.com
```
you can also verify your information using `git confi --list`.
#### Git overview 
Now that we have set up `git` and `github`, we should quickly og over the four data stores of Git. There are four parts in Git's life-cyle 
- Working tree -> Files currently stored on your computer
- Staging area -> Files/changes ready to be committed 
- Local Repository -> Files(including their history) that have been committed and stored locally on your computer 
- Remote Repository -> Files(including history) that have been comitted and stored either on a sever such as github, or a different computer. 
#### Initialization and adding 
The following python code will be used to illustrate how to use git. It will be stored in a txt file: `factorial.txt`
```Python
# Python program to find the factorial of a number provided by the user.
num = 7
factorial = 1
if num < 0:
   print("Sorry, factorial does not exist for negative numbers")
elif num == 0:
   print("The factorial of 0 is 1")
else:
   for i in range(1,num + 1):
       factorial = factorial*i
   print("The factorial of",num,"is",factorial)
```
After creating this file, we must let git keep track its changes, and we must initialize a repo within the directory that it's located in. 
`$ cd <directory path>` -> This command will navigate to the rirectory. 

Now, we can initialize a **Git Repository** with:
`$ git init`
Once the Repository is initialized, we can add our files to the stagin area using:
`$ gt add <file name>`
if you have mutiple files, you can use the following command to add all of them at once
`$ git add -A`
#### Commit 
After we have added our file to the staging area, we would want to commit our file to our local repository. 
we can use:
`$ git commit -m "<a message or a comment>"`
As introduced above, the local repository will include all editing history. So, if you added more function or detailes in our python code, such as adding an array. We can repeat the process of add and commit:
```
$ git add -A
$ git commit -m "New array added"
```
Now, git have recorded our commit and record the change history. 
#### Remote Repository sync
Now that we have already finished all of our changes, of the python code and commited to the local repository. We now need to link our local repo with a remote repo that is independent from our computer. Since we have already create an github acoun, we will be using Github as our platform to link. Now, create a new Repository and copy the link that is provided under `Quick setup` in github. 
link local repo with remote repo using:
`$ git remote add origin <url link>`
we must **push** our changes and the python code to the remote repo. we can use the following command:
`$ git push -u origin <branch name>`
usually the branch name is set default as **main**. Also if you would like to push any later commits to the same branch, u can just use:
`$ git push`
if you lost the local file, or someone did some changes on your project, and you want to download a remote repository hosted on Github, we can use:
`$ git clone <repository url>`

####Branching 
Imagine the git repository is a tree, our initial branch will be the trunk, and all other `branches` that we create later is the branch branching out from the trunk. these branches is like a duplicate of your original branch. You can make changes without affecting or editing you original branch. 
We can use the following command to create a new branch:
`$ git branch <name of new branch>`
in our case, we can create a branch called "remainder".
`$ git branch remainder`
we can swich from tha main branch to the new `remainder` branch using:
`$git cheout <branch name>`
in out case:
`$git cheout remainder`
Now lets add our changes 
```Python
# Python program to find the factorial of a number provided by the user. it can also check the remainder for you
num = 7
factorial = 1
if num < 0:
   print("Sorry, factorial does not exist for negative numbers")
elif num == 0:
   print("The factorial of 0 is 1")
else:
   for i in range(1,num + 1):
       factorial = factorial*i
   print("The factorial of",num,"is",factorial)
num = input("Enter a number: ")
div = input("Enter a divisor: ")
while num >= div:
    num -= div
print num
```
And we can use the same command above where we used to update changes and new commits. 
```
$ git add -A
$ git commit -m "Added remainder func."
```
as said before, the changes will no not be reflected on the main branch. 
####Merging 
Right now we have two branch with different content in them. If we want to combine these two branch we can use what we call the **Merging** method the merge the branches. 
before we merge, we should navigate back to the main branch:
`$ git checkout <mainl branch name>`
use the following command to merge:
`$ git merge remainder`. 
after the branch being merged successfully, we can delete the **remainder** branch using:
`$ git branch -d remainder`
#### Stashing
Stahsing is basically taking away the dirty state of our working directory. We can save these currently unwanted changes and saves it on a stack. we can also re-use these changes later on.
so imagine we have some bugs or issue on our main branch, and we need to fix them. however, we want to use them later on. so we can use:
in our case, lets save our changes in the **main** branch, then run:
`$ git stash -u`
now we fix the bug. after that, we can commit and push to remote 
if you would like to use the fixed changes, we can use the following code to get our stashed changes back:
`$ git stash pop`
#### Pull request
This is the final step for us to submitt our project to our team leader. 
The pull request is essentialy submitting the commit that you previously pushed to the your own remote repo to a different persons's remote repo. 
Now go toyour repository on gihub, you should see a notification about recent pushes on you main branch. Then, click the `Compare & pull request` button, which will navigate you to the pull request page where you add comments and description. 
Now window should show all of your branches and the commit that you have made. Once you create the pull request and select the branch and commits, you should be done. Last you team leader will aprove your pull request and merge you project to their remote repo. 
Congrats! you are done!



