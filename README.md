<img src="./assets/logos/octocat.png" align="right" width="160" height="128">

# GitHub Tutorial by [Alex](https://github.com/alexy4744)

## Git vs. GitHub

Git allows for version control of your files. It allows you to save snapshots (commits) of your files throughout different file changes. Git does not depend on GitHub.

GitHub, on the other hand, is a service that holds remote repositories. It ***requires*** Git (unless you want to upload files manually). GitHub allows you to create remote repositories, where you can use Git to push your commits to a remote repository. Because it is a remote repository, it allows for collaboration with multiple people.

---
## 🌈 Creating your local repository

First, if you haven't created a directory, type `mkdir FOLDERNAME`  

Now, `cd` into your folder and type `git init`, assuming you already have Git installed

`git init` basically a command that initializes Git in your working directory, allowing you to utilitize all of Git's other commands.

It basically creates a hidden folder named `.git`, and turns your directory into a *repository*.

A *repository* is basically a directory with **Git** initialized.

To verify whether Git has been successfully initialized in the correct directory, you can use `ls -a` to view all files/folders including hidden ones

You should see a hidden folder called `.git` in your working directory.  
> <img src="./assets/visuals/ls-a.jpg">

This means that Git has sucessfully set up your local repository

---
## 🌈 Creating your remote repository.

If you do not have a GitHub account, create one [**here**](https://github.com/join?source=header-home)

After that, you can click [**here**](https://github.com/alexy4744?tab=repositories) to view all your repositories *(or click on your avatar and click "Your Repositories" in the dropdown)*.

You should see a green button called **New** on the upper right side of your screen.  
> <img src="./assets/visuals/new-repo-button.jpg">

Now enter your repository name, it **should** match the name of your local repository. Then click on "Create Repository".

Now, you have both your local and remote repositories created.

---
## 🔗 Connecting your local and remote repository
For every new remote and local repository created, we need to establish a connection between them in order to push commits to your remote from the local.

**There are 2 ways of establishing a connection.**
1. **SSH**  
    * ***NOTE: This should only be done once unless you need to add more SSH keys***

    * In order to establish a SSH connection with between our local and remote, we first need to get a SSH key from our IDE.

    * Each IDE varies, but in order to get one from Cloud9, we can go [**here**](https://c9.io/account/ssh) and copy the first public SSH key for public repositories, or the second one for private repositories.  
       > <img src="./assets/visuals/ssh-keys.jpg">
    
    * We can then add the SSH key into our GitHub account  [**here**](https://github.com/settings/ssh/new), then add a title and paste the key in, then click on "**Add SSH Key**".
   
    * Now go back to your repository and copy the SSH url.  
       > <img src="./assets/visuals/clone-with-ssh.jpg">

2. **HTTPS**
    * ***NOTE: HTTPS requires you to sign in to GitHub, unless you have some sort of credential manager that allows Git to save and remember your credentials.***
    
    * In order to get the HTTPS url for your repository, simply copy the HTTPS url.  
       > <img src="./assets/visuals/clone-with-https.jpg">

After we have copied the URL (HTTPS or SSH) for our remote repository, we can go back in to our terminal, and `cd` into our working directory if you are already not in it.

To tell Git to connect to a remote, type `git remote add origin <URL>`, where \<URL> is the URL you copied...

> `remote` basically means remote repository.  
  `add` tells Git to *add* a new remote for this local repository.  
  `origin` is the nickname we will refer to as the remote repository URL. This can be changed to be whatever you like.

To check if our connection has been successfully added, type `git remote -v`, where the `-v` flag means *verbose*, which will show all of our remotes.

Git should output something similar to this:
* **SSH**
  ```bash
  origin  git@github.com:<USERNAME>/<REPOSITORY NAME>.git (fetch)
  origin  git@github.com:<USERNAME>/<REPOSITORY NAME>.git (push)
  ```
* **HTTPS**
  ```bash
  origin  https://github.com/<USERNAME>/<REPOSITORY NAME>.git (fetch)
  origin  https://github.com/<USERNAME>/<REPOSITORY NAME>.git (push)
  ```

---
## 🌊 Workflow & Commands

Once we have edited our files and want to push to our remote repository, here are the following commands you can follow.

The Git workflow basically consists of edit => add => commit => push.

1. **Edit your files.**

2. **Adding/removing files to the stage.**

    The staging area is basically where you can prepare what files should be committed or not. You can add or remove file(s) from the stage.
   
    To view the current files that are on the stage, type `git status`. If files have been modified and not been added on to the stage, it will show `modified: FILENAME.md` in red.
   
    To add specific file(s) onto the stage, type `git add FILENAME.md`. This will add one single file onto the stage. You can attach more file names after the first one to add multiple specfic files.
   
    To add **ALL** unstaged files onto the stage, type `git add .`.
   
    To remove specific file(s) from the stage, type `git checkout FILENAME.md`. As with `git add`, you can always add extra file names to remove multiple files from the stage at once. Removing files from the stage **WON'T** delete our files in our working directory.
   
    Once we have added our files onto the stage, you can verify them by running `git status` again. The files highlighted in green should reflect the files that we have added onto the stage with `git add`.
  
3. **Commiting files on our stage.**  

    Once we have our files added onto the stage, we can now commit those files. Commiting simply means taking a snapshot of our files with all of our changes. We can then push these commits onto GitHub.
   
    To commit our files, we can use `git commit -m "MESSAGE"`, where the `-m` flag stands for *message*, which allows us to enter a string to be used as a commit message.
    
    Commit messages are useful for keeping track all of the changes we have done over time. In additon, commit messages should be short and concise, and also in **PRESENT** tense, not *past* tense even though it seems very tempting.
    
    To verify/view all past commits, type `git log`. This will output all previous commits, from the newest to the o  ldest. 
    
    To exit `git log`, press "Q" on your keyboard.
    
    🎉 Tada, you have succesfully created your first commit!
    
4. **Pushing our commit to our remote repository.**

    Once we have a commit, you can push it to your remote repository.  
    Keep in mind that you can **ONLY PUSH COMMITS**, nothing else.  
    You will run into errors if you try to push with no commits.
    
    To push our commit to our GitHub repository, type `git push`.
    
    ***However***, since this is our first time pushing, we need to type `git push origin master`
    
    `origin` is basically the nickname of our remote repository's SSH/HTTPS url, while `master` simply means the master branch aka the default branch.
    
    If you want to tell Git to always push to `origin master`, we can use the `-u` flag. The `-u` flag basically means upstream,
    
    So if we run `git push -u origin master`, this will tell Git to remember so that the next time you push again, Git will automatically push to `origin master`. This is only ran once, unless you want to change the remote/branch, otherwise, you can type `git push` for any other pushes.
    
    Git should now output something similar to this in your terminal
    ```bash
    Warning: Permanently added 'github.com,192.30.253.113' (RSA) to the list of known hosts.
    Counting objects: 3, done.
    Delta compression using up to 8 threads.
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 1.17 KiB | 1.17 MiB/s, done.
    Total 3 (delta 1), reused 0 (delta 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To github.com:alexy4744/github-tutorial.git
    1ead3a2..b56c6a9  master -> master
    ```
    
    Now, if you go back to your GitHub repository, you should see the files that were added to the staging area; now lives in your remote repository, along with the commit messages you have set! 😎
    
    🥂 Viola! You have just intergrated Git into your workflow!
    
---
## ↪ Rolling Back Changes

* `git checkout -- FILENAME` - Discards all changes and files that are currently not staged.

* `git reset HEAD FILENAME` - Removes a file from the staging area.

* `git reset --soft HEAD~1` - Undo the previous commit, but leaves the files on the staging area while keeping the changes intact.
  * `~<NUMBER>` - The amount of commits to undo, i.e. `~1`

* `git reset HEAD~1` - Undo the previous commit, but **REMOVES** the files from the staging area while keeping the changes intact.

* `git reset --hard HEAD~1` - Undo the previous commit, but **REMOVES** the **FILES AND CHANGES**. The commit will be removed from the history.

* `git reset --hard SHA` - Rollback to a previous commit with the SHA provided. Changes will be **LOST**. Any commits after the commit with the provided SHA will be removed from the history.

* `git revert SHA [...]` - Creates a commit that is opposite from the commit provided by the SHA. It will do the opposite of that commit i.e. if you added files, it will remove them on the new commit.

---
## 💑 Collaboration

GitHub allows for collaboration with multiple people. You can submit pull requests to a repository to merge your changes to the original repository. You can also be invited to be added as a contributor to a repository and have full push access without forking/cloning.

[**Fork**](https://help.github.com/articles/fork-a-repo/) - Create a copy of a remote repository to your account. You will have full push access to the forked repository as it is under your GitHub account. It will **NOT** create a local repository (that's where cloning comes in).
  
[**Clone**](https://help.github.com/articles/cloning-a-repository/) - Create a local repository from a remote repository, basically "cloning" the remote to your working directory. 
  
You can clone anyone's remote repository, however, if you are not a invited contributor, or if its not owned by you, you will not have permissions to push to it.
  
* When you clone a repository, you do not need to follow any steps mentioned in:
  * Setting up your local repository
  * Creating your remote repository
  * Connecting your local and remote repository
      
   Git will take care of those steps for you.
      
[**Pull Request**](https://help.github.com/articles/about-pull-requests/) - A request to merge your forked repository with the original repository. Pull requests can be accepted/denied by moderators.

---
#### Fork/Clone
* This method is used when you are not an invited contributor, meaning you don't have direct push access just by adding it to your remote in Git.

1. First we need to fork the original repository. To fork the repository, press on the ***fork*** button on the upper right hand corner.  
    > <img src="./assets/visuals/fork-button.jpg">

2. After it has been forked, GitHub will redirect you to the forked repository under your account name. We can now copy the repository URL to clone it. Click on the green ***Clone or download*** button and copy either the SSH/HTTPS url.  
    > <img src="./assets/visuals/clone-download-button.jpg">

3. Go back to your terminal and type `git clone <URL>`, where `<URL>` is the link you just copied.

4. Once it has finished cloning, you can do the same Git workflow mentioned in the ***🌊 Workflow & Commands*** section, which is edit => add => commit => push.

#### Submitting a pull request
* ***NOTE: You don't have to submit a pull request for everytime you fork/clone, its completely optional. For example, if you want to just have a personal version of a repository with your personal edits for you own uses, it wouldn't make sense to submit a pull request.***

Once you have pushed all the changes you wish, we can submit a *pull request* to merge our forked repository with the original repository.

To submit a pull request:
  1. Click on the ***Pull request*** button in your forked repository.  
      > <img src="./assets/visuals/pull-request-button.jpg">

  2. You should now be redirected to this page, where you can compare changes  
      > <img src="./assets/visuals/comparing-changes.jpg">   
    
      Hopefully, it should say ***Able to merge. These branches can be automatically merged.***

      If you have a merge conflict,which basically means that GitHub cannot automatically merge the 2 repos because of conflicting changes, you would need to [**resolve**](https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/) them.
      
      Otherwise, click on the big green button called ***Create pull request*** and enter the title and description.
      
  3. From here, it is completely dependent whether reviewers will accept or deny your pull request. If it is accepted, your changes will be added into the original repository. If it is denied, basically nothing will happen.

---
#### Inviting collaborators to your repository.
* By inviting collaborators to your repository, it eliminates the need of forking, cloning and creating pull requests in order for a change to be merged to the repository.

  When a collaborator is invited, they can simply clone the repository and have instant push access to it.

1. On your repository's page, click on the ***Settings*** tab.  
    > <img src="./assets/visuals/settings-tab.jpg">

2. Now click on the ***Collaborators*** tab. Enter the username/email and click on ***Add collaborator***.  
    > <img src="./assets/visuals/collabarator-tab.jpg">

3. Now click on the ***Copy invite link*** next to their name on the list and it should be sent to the user for them to accept the invitation.  
    > <img src="./assets/visuals/copy-invite-link.jpg">

4. Once the user has accepted the invite, they will have push access permanently unless removed as a collabarator.

---
## ❗ Error Handling
It is common to run into errors while using Git.

1. ***Nothing added to commit but untracked files present***
    ![](https://lh5.googleusercontent.com/Dz5M5ZgTugbP-Iy6-A_69pENX0j9uwxbjjXhKxKWcZtVZFYpSF9P6EBEv-oCUWTOsSyQPrcrcTTMSLCRnqzbBZUyNYeob1nJx7BluL_zoKyUpf2vGCUgRag534AHFTjnI481QX_s)

    * **Problem**: This error occurs when there are no files on the stage. The cause of this issue is that you probably used `git commit` before using `git add`, therefore no files can be committed since there are no files on the stage in the first place.
   
    * **Resolution**: Add your files to the stage by running `git add`, then run `git commit`.
  
2. ***Nothing to commit, working directory clean***
    ![](https://lh5.googleusercontent.com/Bs4sTaP8Gi-aWxFhPdzfYR0gbObpv3Rj54m5sH4qNiZ90RA9iNzLH4QSr6UmQxTEFABKKFeq3UFQiGTU8RZItSvJJL6u9h0f3fByxBRbvCgBIQicnJ7bAC4oDOfqwNNOwdU_58Er)

    * **Problem**: Your file was not saved properly, therefore, when you ran `git add`, it essentially added no files since the changes were not saved.
      
    * **Resolution**: Make sure your file is saved properly before adding and committing. To prevent this in the future, you can run `git status` to make sure the file is actually added on the stage.
      
3. ***GNU Nano Editor appears while committing***
    ![](https://lh6.googleusercontent.com/Mz-XY6iymLhC8VEU-V5U4_OMIAatJbCLJckfYKCpUW9HWm44SR93HiHp5Wl9IV5IDA58f0fdLowZQQpo8TjBRdSsi2CzUDUOzlOpysIlyffaPH-XVWXv8xcqTY-czmij6mmfHNGw)

    * **Problem**: You most likely forgot to include the `-m` flag along with a string to be included as a message. Basically you ran `git commit` standalone, when you should have ran `git commit -m "MESSAGE"`.

    * **Resolution**: Press **^X** (Control + X) to exit the editor. To avoid this problem in the future, just make sure you included a `-m` flag along with a message.
      
4. ***Fatal: no configured push destination***
    ![](https://lh5.googleusercontent.com/hoYfwegzWBSoJ6dOMOSENxzkVXOhhZGp4RgqZfWtw4xdjbGwJrsNCPc_pLvaQkyOz70GEF6I1qOvN1zeZZK-mHzYFwFpSGgeR8tUtW1zG-E2Eq6vnSwyR3vF-GOB63GRymd72rjK)

    * **Problem**: You have not yet establish a connection with your remote repository for Git to push to.
    
    * **Resolution**: Find your remote repository's SSH/HTTPS clone/download link, and then run `git remote add origin <URL>` to add the remote. Refer back to ***🔗 Connecting your local and remote repository*** for more details.

    
5. ***The current branch master has no upstream branch***
    ![](https://lh6.googleusercontent.com/dLpQrX6mceb7sGp48cXPqVMBpIuU1tteNlTajOu4RUzI2zZdZOm3GeXyLxQhFGT5Mw2HakvctyCXHTSjgDa7PRtKPV_Lwr8fcOkNJOBQ0ao0_UT-8SwRcHF7VInkUcC6UVkFav84)

    * **Problem**: You did not specify a branch for Git to push to. Since you ran `git push` without setting an upstream remote/branch as an argument, Git does not know where to push to.
    
    * **Resolution**: Type `git push origin master`, instead of just `git push`. If you want to use `git push`, and have Git remember where to push to, run this command once, `git push -u origin master`. Refer back to ***🌊 Workflow & Commands #4*** for more details on what the command does.

6. ***Blinking cursor in the terminal***
    ![](https://lh6.googleusercontent.com/uVHFw1fcxhCMfwWKNFrcnn17EgIgcsUyjcXd0e0tZlgukCS02RNb9tF0QDT_ybRfvJFxn0lO4XMpwtc4YbpnUxR2XhTiJToXv9Qh8w8VPxribgcKvxAUpCM4iDTJg9o2SqEY8aDA)

    * **Problem**: The terminal is waiting for you to finish your input after you have entered a command. This usually happens with Git when you don't close your strings with quotation marks properly, etc
    
    * **Resolution**: Either finish your input by typing it in and then pressing `ENTER`, or press `^C` (Control + C) to interrupt and exit the current state.
    
7. ***Everything up-to-date while trying to push***
    ![](https://lh3.googleusercontent.com/BRA2hy0TZPgS9IO9_lJ-t0bjdYH3ncor6mZwUMZvS2ubQUE3XskfkBYbVpUPChBeDH3B3vbpheEUuwSq3SKX9psbV2ksjFp-XxRBBMoDT3o7ydVl7x8U7IRuYjbqS6CqxE4UpbaZ)

    * **Problem**: While the file is added onto the stage, you forgot to commit the files first before pushing them. Since `git push` can only push commits, if there are no commits, then there is nothing updated and therefore it tells you that everything is up to date.
    
    * **Resolution**: Run `git commit -m "MESSAGE"` first, then run `git push`. Refer to ***🌊 Workflow & Commands*** to view how the Git workflow works.
    
8. ***You ran `git add` with neither `-A (--all)` or `--ignore-removal`     whose behavior will change in Git 2.0 with respect to paths you         removed.***
    ![](https://lh6.googleusercontent.com/dd3RrJCaQ8szk7uoz0_DxLpA4A_nq3bJlir_rfe4nKmfAUNsV3v3pLIXroPL5lJiDfOY0cBSrIv3xhu9h1gaICBTntl9FR-elr16TEhOZ3T7Kl0pHSp3OVO5OPHa04XobQMvMafJ)

    * **Problem**: This deprecation warning appears because you have tried to add files that have been deleted in your working directory, but Git does not know whether it should still continue tpadding those files to the stage or not.
    
    * **Resolution**: Run either `git add -A` to add all files including deleted files to the stage, or `git add --ignore-removal` to ignore the deleted files and only add files that still exists to the stage.

9. ***Pathspec did not match any file(s) known to Git while                 committing***
    ![](https://lh6.googleusercontent.com/otc58G_fLcXIB1WmwLUwVrloqMhz9tMX8L_9c7jVQNXIVK7y_lzpz2nExwnfUX-BGFAvEFqCFMMLKMFhf-80bUbUVF2uZdk7dHzxdpNpJKHMXGgWDR-Mf821to_J1Y5-kjK54wYT)

    * **Problem**: You have forgotten to include the `-m` flag when adding a commit message. Since the `-m` flag did not exist, Git thought it must be a file path, therefore this error is thrown.
    
    * **Resolution**: Include the `-m` flag before adding your commit message, refer to ***🌊 Workflow & Commands #3*** to view more details about commiting files.
    
10. ***src: refspec master does not match any.***
    ![](https://lh4.googleusercontent.com/dyrWfITi7vphhukOW6VXS-vX7MSIWrIyPxI_Fbb0eDSXiGwBY8DD3sRfRQ-EmBQ2frODa71mvY8c-RlDLPukG0ks7FN8EYpYGWAQz1U-APxr8pDXXbuHr0FI9TTZFdDu2PXUtJ4Z)

    * **Problem**: You have no commits to push because you have not added any files onto the stage. Your Git workflow is completely wrong
    
    * **Resolution**: You have to edit your files, add your files to the stage, commit your files, then you can push it to your remote. Refer to ***🌊 Workflow & Commands*** to see how it works in-depth.
    
11. ***bash: cd: workspace: No such file or directory***
    ![](https://lh5.googleusercontent.com/r8HALYxa25rXHifw_elRN8llPtDo4ppqe-PwYmd1HzqNm6-f9MQT42prK1C9Xy4i055g26RJknHLeVsqs46iTeKOSMA5ImJIkwWWb85Z_G6Pbtk8deaic0-AgBKHtw9GzFCVspIE)

    * **Problem**: This is a problem with a Bash command and not with Git. Basically you have tried to `cd` into a directory that doesn't exist, in this case, back into `workspace`.
    
    * **Resolution**: Run `cd ~/workspace` to go back to your workspace directory. `~` basically means the `/root` directory, and this is where your workspace directory normally lives inside of.
    
12. ***Git won't "un-initialized"***
    ![](https://lh5.googleusercontent.com/MrV65HzYD-Nl6aN34jnQyll5h9rQdqCgXmPSchBs8KLwA_STsBIbfkNXsHyguxVQTqtemk9dDRiUmQO3-14jzr7ZPDY0U4WoBPL3JaWGEm3bvrqpHCvkCLfpjfQQnNxheWImYju1)

    * **Problem**: Git must have been initialized in some other parent directory. You must be in a subfolder of a repository, therefore when you ran `rm -rf .git`, there was nothing to remove because `.git` does not live in there.
    
    * **Resolution**: Try using `cd ..` to navigate to parent directories and `ls -a` to check whether it is in there or not. If you have found your `.git` folder, run `rm -rf .git ` again to remove Git.