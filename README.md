# My Basic Git Commands 🔮
---

#### Basic Configuration

To see your userName and your userEmail in your terminal use the next commands:

- git config --get user.name
- git config --get user.email

To configure your userName or your userEmail us the next commands.

- git config --global user.name "YourUserName"
- git config --global user.email "YourEmail"

The *--help* flag show you all the possible flags you can use with that git command.

If you want to merge or to rebase when you commit your changes you can run the next commands in your terminal:

- git config pull.rebase false  # merge (the default strategy)
- git config pull.rebase true   # rebase
- git config pull.ff only       # fast-forward only

To configure the initial branch name to use in all of your new repositories, use this one:

- git config --global init.defaultBranch <name>

> Names commonly chosen are 'master', 'main', 'trunk' and 'development'.re

- git config pull.rebase true
> This is very useful if you want to do a sort of fusion between your new remote repo in GitHub and your local repo in order to have the documents 

#### Local Repositories


To **initialize** a repository (if you want to have a local repository), needed to use:

- git init

> This command is used in your working directory.


To **add** files to the staging area (before you commit files) you have many options:

- git add \<fileName\>

- git add .

> Differences between them is how many files you want to add to the staging area, in the first you just add one file (the indicated) instead of the second where you add all the files living in your directory just using one command.

Whether you know about the **status** of your repository, incluiding the *tracked* and *untracked* files, or you need to commited them or just check the state of the repository, use the next command:

- git status
 
To **remove** files from the staging area (before you commit files) use the commands below:

- git rm -f \<fileName\>
- git rm --cached \<fileName\>
- git rm -r --cached .

> Main differences between these commands are, either you want to keep the file or you want to remove it even from your drive. The *first* delete the indicated file from staging area and from your driver, the *second* just from the staging area (if the file is tracked now is untracked) and the *last one* is used to remove all the untracked cached files.

To **commit** you have many options you can use (of course all of them have their main differences).

- git commit -m "Message that describes what you have done to the files or the name of your commit."
- git commit -a -m "Message that describes what you have done to the files."

> The **first** just commit your tracked files which are in the staging area. Insted of the last one wich commit the tracked files and the untracked files (both).


To **list** the commits that you have done use the next commands:

- git log
- git log --oneline

> First command allows you to see all the commits showing them from the first on the bottom to the last on top (with a short description about it like the date and the complete commit ID) and the second will show you all the commits that you have done but in a shorter form and not showing the entire commit ID just the necessary so that you can work.

Now in order to **change between commits** like if you want to back in time, you can use the next commands:

- git checkout \<commitID\> 
- git checkout master

> If you want to go back in time use the first command to return to a commit that you've done (this won't delete all the commits, just will allow you to return to the changes), on the other hand the last command allows you to return to the *master branch* (part of time when you did your first commit). 

If you want to **revert** a commit, then you have the possibility to do it, just writing the next command:

- git revert \<commitID\>

> This command will allow you to revert a commit but will not deleated it, just will do a *new* commit indicating that you have returned to the commit (changes) that is before the one you indicated.

Another possibility to **back in time** but insted of the others commands now **everything** is going to be **deleted** is: 

- git reset --hard \<commitID\>
- git reset --soft \<commitID\>
- git reset --mixed \<commitID\>

> The **first** command change your position HEAD *branch* to the commit that you have already indicated, deleting all the commits above (incluiding the files). The **second** doesn't actually remove anything, the only thing is that it gets rid of is some commits but is not actually removing any file (most used in errors or mistakes that you might have while you were doing the commit (e.g. with the commit description) and you don't want to remove files, so once you reset the commit then you re-commit with the error fixed, like redo a commit). The **third** command is very useful when you want to delete some files but from the staging area (your files are tracked and after command this, now are untracked), not from the drive of your computer, it's just like both but it is neither hard nor soft.

#### Branches

There are different ways of **creating a branch**, and these commands are listed below:

- git branch \<branchName\>
- git checkout -b \<branchName\>

> The **first** command is just creating a new branch but your HEAD is not in it. The **second** branch is creating the branch and switching to it.

To **switch** between branches you can use the next commands:

- git checkout master
- git checkout \<branchName\>

> The **first** one will take you back to the master branch insted of the other that'll take you to the branch you are indicating.

If you want to **list** all of your current **branches** you need to use the next command:

- git branch -a

Now if you want to delete a branch the next command is really useful:

- git branch -d \<branchName\>

Once you have your branch created you want to merge this branches so that they can work together. To do this sort of fusion you have the next command:

- git merge \<branchName\>

> First of all you need to check that your working directory is totally clean, that you've done all the corresponding commits. Now about the command, this one allows you to merge the *branch where you are* with the branch entered as an *input* in the command.

Then if you have initialized a git repo in your local machine, you can renamed a just-created branch via this command:

- git branch -m <name>

#### GitHub

If you want to connect a repository which is living in your local machine with a remote repository (living in GitHub) write the next commands:

- git remote add origin \<http-link\>
- git remote -v

> What this basically does is told to your repository that we want to connect it to a remote repository as a cycle with the fetch and push (git remote -v to verify if you've already linked both repositories).
> 
> The second is just to check if your remote repository is connected with the local repository.

To update the files (or "download" them) in your local machine you need to pull all of those files, so you can use the next command:

- git pull 
- git pull origin master (or main)
- git pull origin \<branchName\>

> The **first** command updates all the information in your local repository. The **second** just downloads the information within the master branch. And the **last** one update the information within the branch entered as an input.

Now to update your remote repository with the files and information we have already added and commited in our local machine, we must use the next commands:

- git push
- git push \<remote-name\> \<branch-name\>
- git push -u \<remote-name\> \<branch-name\>

> This commands allow you to update your info in your local repository. The **first** command assumes that you already have a remote repository defined for that branch. The **second** command indicates that you are pushing to a specific remote repository, in this case, \<remote-name\> to the branch indicated. The **third** and last command actually does the same as the second but is setting *remote-repository* so that you can in the future write *git push* without taking care about your repo.

To **rename** a branch, you would use the same *git push* command, but adding one more argument: the name of the branch. 

- git push \<remote-name\> \<local-branch-name\>:\<remote-branch-name\>

To **delete** a remote branch, you can use *git push* with the next notation:

- git push \<remote-name\> :\<branch-name\>
- git push \<remote-name\> --delete \<branch-name\>

> Note that there is a space before the colon.


#### .gitignore file

This feature allows you to hide some files which you don't want to show, for example all of those auto-generated files which won't cause any efect in our repository even if they are modified or not. You only need to write the *fileName* you want to hide or files if they are in a directory like ***directoryName/\****
